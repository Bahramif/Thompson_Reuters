---
marp: true
theme: default
paginate: true
size: 16:9
style: |
  section {
    padding: 35px 45px 45px 45px;
    font-size: 17px;
    background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
  }
  h1 {
    font-size: 32px;
    margin-bottom: 15px;
    margin-top: 0px;
    color: #1a237e;
    border-bottom: 2px solid #3949ab;
    padding-bottom: 6px;
  }
  h2 {
    font-size: 24px;
    margin-top: 8px;
    margin-bottom: 10px;
    color: #283593;
  }
  h3 {
    font-size: 20px;
    margin-top: 6px;
    margin-bottom: 8px;
    color: #3949ab;
  }
  ul, ol {
    margin-top: 3px;
    margin-bottom: 3px;
  }
  li {
    margin-bottom: 3px;
    line-height: 1.25;
  }
  p {
    margin-bottom: 6px;
    line-height: 1.25;
  }
  strong {
    color: #1a237e;
  }
  code {
    background: #f5f5f5;
    padding: 1px 3px;
    border-radius: 2px;
    font-size: 15px;
  }
  table {
    font-size: 15px;
    margin: 4px 0;
  }
  th, td {
    padding: 3px 6px;
  }
  pre {
    font-size: 12px;
    margin: 4px 0;
    line-height: 1.2;
  }
  .columns {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 15px;
    width: 100%;
  }
  .column {
    padding: 0 5px;
  }
---

<!-- _class: lead -->
<!-- _paginate: false -->

# Deep Research System Design

**Preserving Domain-Specific Expert Thinking**

*Designing a Deep Research Assistant for Financial Services*

---

## 1. Problem Framing & Understanding

<div class="columns">

<div class="column">

### The Challenge

📊 **Problem**: Senior analysts spend **35-40%** of time re-discovering existing insights

💡 **Opportunity**: Leverage **15 years** of proprietary analytical frameworks and expert reasoning

🎯 **Critical Success Factor**: System must preserve domain-specific thinking, not just retrieve documents

✅ **Available Asset**: ~**2,500** expert-curated Q&A pairs (golden dataset)

### Success Criteria

1. ✅ Preserve and surface unique analytical frameworks
2. ✅ Answer complex queries requiring synthesis across reports and time periods
3. ✅ Handle ambiguous queries with proactive clarification
4. ✅ Deliver accurate, well-sourced answers maintaining expert rigor
5. ✅ Provide consistent, trustworthy responses for client-facing work

</div>

<div class="column">

### Capability Self-Assessment

**Strengths:**
- System architecture & design
- Evaluation framework design
- Quality assurance strategies
- Multi-agent system coordination

**Areas for Growth:**
- Deep financial domain expertise (will rely on analysts)
- Regulatory compliance nuances (will consult legal)
- Firm-specific framework knowledge (will learn from corpus)

### What Would Change My Approach?

- Different acceptable hallucination thresholds
- Regulatory constraints on AI-generated content
- Golden dataset quality/coverage gaps
- Infrastructure limitations

</div>

</div>

---

## 2. AI-Assisted Design Process

<div class="columns">

<div class="column">

### LLM Usage & Transparency

**What We Used LLMs For:**
- 🔍 Research and synthesis of state-of-the-art approaches
- 🏗️ Architecture design brainstorming and validation
- 📊 Evaluation framework design
- 📝 Document structure and content organization

### Example Effective Prompts

1. *"Research state-of-the-art knowledge graph approaches for RAG systems in 2024, including Think-on-Graph, KGoT, and hallucination mitigation strategies"*

2. *"Design a multi-stage evaluation framework for financial research systems using offline golden sets and online LLM-as-judge approaches"*

</div>

<div class="column">

### What LLM Got Wrong

- ❌ **Over-simplification**: Missed importance of versioning and temporal reasoning
- ❌ **Generic solutions**: Had to redirect from generic RAG to domain-specific framework preservation
- ❌ **Evaluation gaps**: Lacked specificity for financial domain metrics

### What Couldn't Be Delegated

- 🎯 Domain-specific assumptions and risk assessment
- ⚖️ Trade-off decisions based on firm priorities
- ❓ Critical questions for leadership
- 🏢 Final architecture decisions requiring business context

</div>

</div>

---

## 3. System Architecture Overview

<div style="display: grid; grid-template-columns: 90px 1fr 90px; gap: 8px; height: 100%; align-items: stretch;">

<!-- Left Sidebar: Quality Assurance & Governance -->
<div style="background: #7b1fa2; border-radius: 6px; padding: 15px 8px; color: white; font-weight: bold; font-size: 13px; display: flex; align-items: center; justify-content: center; writing-mode: vertical-rl; text-orientation: mixed;">
<div>⬇️ Quality Assurance<br>& Governance</div>
</div>

<!-- Main Architecture Layers -->
<div style="display: flex; flex-direction: column; gap: 6px; justify-content: space-between;">

<!-- Layer 1: Document Ingestion & Processing (Blue) -->
<div style="background: #e3f2fd; border: 2px solid #1976d2; border-radius: 6px; padding: 10px 15px; position: relative; display: flex; flex-direction: column; justify-content: center;">
<div style="font-size: 18px; font-weight: bold; color: #1565c0; margin-bottom: 4px;">Document Ingestion & Processing Layer</div>
<div style="font-size: 14px; color: #424242; line-height: 1.3;">Ingest proprietary documents (research reports, due diligence, memos). Extract proprietary analytical frameworks, entities, relationships, and temporal metadata. Preserve expert reasoning patterns and framework versioning. Output: Structured knowledge ready for graph construction.</div>
<div style="position: absolute; right: 12px; top: 50%; transform: translateY(-50%); color: #1976d2; font-size: 18px;">⌄</div>
</div>

<!-- Layer 2: Knowledge Graph Construction (Orange) -->
<div style="background: #fff3e0; border: 2px solid #f57c00; border-radius: 6px; padding: 10px 15px; position: relative; display: flex; flex-direction: column; justify-content: center;">
<div style="font-size: 18px; font-weight: bold; color: #e65100; margin-bottom: 4px;">Knowledge Graph Construction Layer</div>
<div style="font-size: 14px; color: #424242; line-height: 1.3;">Build domain-specific knowledge graph preserving proprietary frameworks as first-class entities. Store entities (companies, instruments), relationships, framework definitions, temporal dimensions, and expert reasoning patterns. This is the critical layer for preserving and surfacing the firm's unique analytical methodology.</div>
<div style="position: absolute; right: 12px; top: 50%; transform: translateY(-50%); color: #f57c00; font-size: 18px;">⌄</div>
</div>

<!-- Layer 3: Hybrid Retrieval System (Green) -->
<div style="background: #e8f5e9; border: 2px solid #388e3c; border-radius: 6px; padding: 10px 15px; position: relative; display: flex; flex-direction: column; justify-content: center;">
<div style="font-size: 18px; font-weight: bold; color: #2e7d32; margin-bottom: 4px;">Hybrid Retrieval System Layer</div>
<div style="font-size: 14px; color: #424242; line-height: 1.3;">Semantic search (50%), knowledge graph traversal (35%), and keyword matching (15%) work together to find framework-relevant content. Framework-aware retrieval prioritizes documents that use proprietary methodologies. Enables synthesis across multiple reports and time periods.</div>
<div style="position: absolute; right: 12px; top: 50%; transform: translateY(-50%); color: #388e3c; font-size: 18px;">⌄</div>
</div>

<!-- Layer 4: Multi-Agent Query Processing (Teal) -->
<div style="background: #e0f2f1; border: 2px solid #00897b; border-radius: 6px; padding: 10px 15px; position: relative; display: flex; flex-direction: column; justify-content: center;">
<div style="font-size: 18px; font-weight: bold; color: #00695c; margin-bottom: 4px;">Multi-Agent Query Processing Layer</div>
<div style="font-size: 14px; color: #424242; line-height: 1.3;">Specialized agents handle complex queries: Understanding (intent classification, ambiguity detection), Decomposition (break into sub-queries), Retrieval Orchestration (coordinate multi-modal search), Synthesis (apply framework reasoning), and QA (fact-checking). Handles ambiguous queries with proactive clarification.</div>
<div style="position: absolute; right: 12px; top: 50%; transform: translateY(-50%); color: #00897b; font-size: 18px;">⌄</div>
</div>

<!-- Layer 5: Framework-Aware Answer Generation (Purple) -->
<div style="background: #f3e5f5; border: 2px solid #7b1fa2; border-radius: 6px; padding: 10px 15px; position: relative; display: flex; flex-direction: column; justify-content: center;">
<div style="font-size: 18px; font-weight: bold; color: #6a1b9a; margin-bottom: 4px;">Framework-Aware Answer Generation Layer</div>
<div style="font-size: 14px; color: #424242; line-height: 1.3;">Generate answers maintaining analytical rigor and expert voice. Inject framework definitions into prompts, use framework-specific reasoning templates, maintain expert terminology. Provide structured output with citations, framework application, temporal context, and confidence assessment. Ensures consistent, trustworthy responses for client-facing work.</div>
<div style="position: absolute; right: 12px; top: 50%; transform: translateY(-50%); color: #7b1fa2; font-size: 18px;">⌄</div>
</div>

<!-- Layer 6: Quality Assurance & Hallucination Mitigation (Dark Gray/Slate) -->
<div style="background: #eceff1; border: 2px solid #546e7a; border-radius: 6px; padding: 10px 15px; position: relative; display: flex; flex-direction: column; justify-content: center;">
<div style="font-size: 18px; font-weight: bold; color: #455a64; margin-bottom: 4px;">Quality Assurance & Hallucination Mitigation Layer</div>
<div style="font-size: 14px; color: #424242; line-height: 1.3;">Multi-stage guardrails: pre-generation checks, during-generation grounding verification, post-generation fact-checking against knowledge graph. Leverage golden dataset (~2,500 Q&A pairs) for training detection models and benchmarking. Ensure accuracy and prevent fabricated information. Target hallucination rate <5%.</div>
<div style="position: absolute; right: 12px; top: 50%; transform: translateY(-50%); color: #546e7a; font-size: 18px;">⌄</div>
</div>

<!-- Layer 7: Evaluation & Monitoring Layer -->
<div style="background: #f1f8e9; border: 2px solid #689f38; border-radius: 6px; padding: 10px 15px; position: relative; display: flex; flex-direction: column; justify-content: center;">
<div style="font-size: 18px; font-weight: bold; color: #558b2f; margin-bottom: 4px;">Evaluation & Monitoring Layer</div>
<div style="font-size: 14px; color: #424242; line-height: 1.3;">Comprehensive evaluation using golden dataset (offline) and LLM-as-judge (online). Measure framework preservation, domain expertise retention, answer quality, and system reliability. Continuous monitoring of performance metrics, failure mode detection, and feedback loops for improvement.</div>
</div>

</div>

<!-- Right Sidebar: Evaluation & Monitoring -->
<div style="background: #d32f2f; border-radius: 6px; padding: 15px 8px; color: white; font-weight: bold; font-size: 13px; display: flex; align-items: center; justify-content: center; writing-mode: vertical-rl; text-orientation: mixed;">
<div>⬇️ Evaluation<br>& Monitoring</div>
</div>

</div>

### How Domain Expertise is Preserved

**Framework Extraction & Storage:** Document Processing layer extracts proprietary analytical frameworks, reasoning patterns, and methodology from documents, storing them in Knowledge Graph with version tracking.

**Framework-Aware Processing:** All layers are framework-aware—retrieval prioritizes framework-relevant content, generation uses framework templates, and QA validates framework adherence.

**Expert Reasoning Patterns:** Multi-Agent layer captures and enforces expert decision paths, while Evaluation layer continuously measures framework usage against golden dataset benchmarks.

---

## 4. Document Processing & Knowledge Extraction

<div class="columns">

<div class="column">

### Processing Pipeline

**Stage 1: Document Ingestion**
- Format normalization (PDF, Word, Markdown)
- Metadata extraction (author, date, framework type, version)
- Quality filtering (duplicates, corrupted files)

**Stage 2: Framework Extraction**
- Identify proprietary analytical frameworks
- Extract framework parameters and methodologies
- Capture reasoning patterns and decision trees

**Stage 3: Entity & Relationship Extraction**
- Named Entity Recognition (NER) for financial entities
- Relationship extraction (ownership, analysis_of, influences)
- Temporal entity extraction (events, predictions with dates)

**Stage 4: Knowledge Graph Population**
- Map entities to KG nodes, create relationship edges
- Attach framework metadata to relevant nodes

</div>

<div class="column">

### Quality Metrics

| Metric | Target |
|--------|--------|
| Extraction Accuracy | >90% |
| Framework Coverage | >85% |
| Temporal Alignment | >95% |
| Processing Time | <2 min/doc |

</div>

</div>

---

## 5. Domain-Specific Ontology Capture

<div class="columns">

<div class="column">

### How Domain Expertise is Captured

**Proprietary Framework Representation:**
- Framework name, version, and evolution history
- Input parameters (market conditions, risk factors)
- Decision logic and reasoning patterns
- Expected outputs and confidence calibration

**Entity Types:**
- Companies (industry, geography, market cap)
- Financial Instruments (equity, debt, derivatives)
- Markets & Sectors
- Analysts (with expertise areas)
- Frameworks (proprietary analytical methods)

**Relationship Types:**
- `analyzes` (analyst → company/instrument)
- `applies_framework` (analysis → framework)
- `influences` (factor → company/outcome)
- `temporal_evolution` (view → historical_view)
- `contradicts` (analysis → analysis)

</div>

<div class="column">

### Distinguishing Generic vs. Proprietary

**Generic Financial Information:**
- Market data, stock prices
- Standard financial metrics
- Public company information

**Firm's Unique Perspective:**
- Proprietary analytical frameworks
- Expert reasoning patterns
- Framework-specific evaluation criteria
- Historical prediction accuracy
- Confidence calibration methods

**Ontology Metrics:**
- Coverage: % of domain concepts captured (>90%)
- Completeness: Avg relationships per entity (>3)
- Accuracy: Human validation (>95%)
- Framework Representation: % of known frameworks captured (>85%)

</div>

</div>

---

## 6. Information Retrieval System Design

### Hybrid Retrieval Architecture

**1. Semantic Search (50%)** - Fine-tuned embeddings, FAISS vector store
**2. Knowledge Graph Traversal (35%)** - Cypher/SPARQL queries, multi-hop reasoning
**3. Keyword Matching (15%)** - BM25 algorithm, metadata filtering

### Retrieval Fusion & Metrics

**Weighted Combination:** Semantic 50% + Graph 35% + Keyword 15%
**Re-ranking:** Cross-encoder model, framework relevance, temporal recency

| Metric | Target |
|--------|--------|
| Recall@10 | >90% |
| Precision@5 | >85% |
| MRR | >0.8 |
| Framework Match | >75% |
| Latency (P95) | <500ms |

---

## 6. Context Engineering & Answer Generation

<div class="columns">

<div class="column">

### Context Structuring

**Multi-Source Context:**
1. Primary sources (top retrieved documents)
2. Framework context (analytical framework definitions)
3. Temporal context (historical evolution of queries)
4. Expert reasoning (captured patterns from corpus)

**Context Prioritization:** Recency → Authority → Framework alignment → Citation network

### Answer Generation Approach

**Framework-Aware Generation:**
- Inject framework definitions, use framework-specific templates
- Maintain expert voice and terminology

**Structured Output:**
1. Executive Summary
2. Key Findings (with citations)
3. Framework Applied
4. Supporting Evidence
5. Temporal Context
6. Confidence & Limitations

</div>

<div class="column">

### Quality Metrics

| Metric | Target |
|--------|--------|
| Answer Relevance | >4.0/5.0 |
| Citation Accuracy | >95% |
| Framework Adherence | >80% |
| Expert Voice | >4.0/5.0 |
| Confidence Calibration | >0.7 |

</div>

</div>

---

## 7. Agentic Multi-Step System Design

### Multi-Agent Architecture Flow

**Query Input** → **Understanding Agent** (Intent classification, ambiguity detection)
↓
**Decomposition Agent** (Break into sub-queries, parallel vs. sequential)
↓
**Retrieval Orchestrator** (Coordinate multi-modal retrieval, merge results)
↓
**Synthesis Agent** (Combine information, apply framework reasoning)
↓
**Quality Assurance Agent** (Fact-checking, hallucination detection)
↓
**Final Answer**

### Agent Responsibilities & Metrics

| Agent | Responsibilities |
|-------|-----------------|
| Understanding | Intent classification, ambiguity detection |
| Decomposition | Break queries into sub-queries |
| Retrieval Orchestrator | Coordinate multi-modal retrieval |
| Synthesis | Combine information, apply frameworks |
| QA | Fact-checking, hallucination detection |

**Reliability Metrics:** Task Completion >90%, Coordination Accuracy >95%, Error Recovery >80%, Availability >99.5%

---

## 8. Quality Assurance & Hallucination Mitigation

<div class="columns">

<div class="column">

### Multi-Stage Guardrails

**Stage 1: Pre-Generation**
- Verify query answerable, check context retrieval

**Stage 2: During Generation**
- Grounding verification, framework consistency, temporal consistency

**Stage 3: Post-Generation**
- Fact extraction & KG verification, citation accuracy, confidence calibration

### Hallucination Detection Strategies

**1. KG Verification** - Extract claims → Verify entities/relationships in KG
**2. Source Attribution** - Every claim must have citation, verify sources contain claim
**3. Consistency Analysis** - Compare with retrieved documents, detect contradictions
**4. Self-Evaluation** - LLM self-assessment, uncertainty expression, refusal when low confidence

</div>

<div class="column">

### Leveraging Golden Dataset (~2,500 Q&A Pairs)

**Training:**
- Fine-tune hallucination detection models on golden Q&A pairs
- Learn patterns of correct vs. hallucinated answers
- Calibrate confidence thresholds based on expert-curated examples
- Extract framework application patterns from expert answers

**Evaluation:**
- Benchmark hallucination rate on golden set (target: <5%)
- Track false positive/negative rates for detection models
- Continuously improve detection accuracy
- Use for continuous model refinement

**Metrics:**
| Metric | Target |
|--------|--------|
| Hallucination Rate | <5% |
| False Positive Rate | <2% |
| Citation Accuracy | >98% |
| Verification Coverage | >90% |

</div>

</div>

---

## 9. Evaluation Framework

<div class="columns">

<div class="column">

### Offline Evaluation (Golden Set)

**Dataset Split:**
- Training 2,000 (80%)
- Validation 250 (10%)
- Test 250 (10%)

**Metrics per Component:**
- **Retrieval**: Recall@10, Precision@5, MRR, Framework match rate
- **Answer Generation**: BLEU/ROUGE, Citation accuracy, Framework adherence
- **Overall**: End-to-end accuracy, Hallucination rate, User satisfaction

### Online Evaluation (LLM-as-Judge)

**Judge Model:** GPT-4 or Claude (fine-tuned on financial domain)

**Evaluation Criteria (5-point scale):**
1. Relevance
2. Accuracy
3. Completeness
4. Framework Adherence
5. Expert Voice

</div>

<div class="column">

### Continuous Evaluation

- Real-time for 10% of production queries
- Feedback loop
- A/B testing

### Domain Expertise Preservation Metrics

**Framework Usage Rate** >75%
**Methodology Consistency** Agreement with history
**Expert Reasoning Capture** Human evaluation
**Ontology Coverage** >90%

</div>

</div>

---

## 10. System Performance & Monitoring

<div class="columns">

<div class="column">

### Performance Characteristics

**Latency:**
- Simple <3s
- Complex <15s
- Very Complex <45s (P95)

**Throughput:**
- 100+ concurrent users
- 10,000+ queries/day
- 5x peak capacity

**Accuracy:**
- Quality score >4.0/5.0
- Hallucination <5%
- Citation accuracy >95%

### Monitoring & Observability

**System Health:**
- API response times (P50/P95/P99)
- Error rates, Queue depth
- KG query performance

</div>

<div class="column">

**Quality Metrics:**
- Hallucination detection rate
- Confidence distribution
- Citation coverage
- User feedback

**Business Metrics:**
- Query volume by type
- User adoption
- Answer quality trends
- Framework usage

### Failure Mode Detection & Recovery

**Error Detection:**
- Low confidence → Flag
- High hallucination spike → Alert
- Retrieval failures → Fallback
- Agent failures → Escalate

**Recovery:**
- Automatic retry with backoff
- Fallback to simpler methods
- Human-in-the-loop escalation
- Circuit breakers

</div>

</div>

---

## 11. Key Trade-offs & Design Decisions

| Decision | Rationale | Trade-off |
|----------|-----------|-----------|
| **Hybrid Retrieval** (Semantic + Graph + Keyword) | Maximizes recall while maintaining precision | Increased complexity but better results |
| **Multi-Agent Architecture** | Better handling of complex queries and error isolation | Coordination overhead vs. modularity benefits |
| **Multi-Stage Guardrails** (moderate thresholds) | Balance between safety and usability | Some valid answers may be flagged vs. higher safety |
| **Automated Framework Extraction** (with human validation) | Scalability with quality assurance | Some frameworks may need manual correction |
| **Hybrid Evaluation** (LLM + Human) | Scalable evaluation with human oversight | LLM evaluation may miss nuances vs. cost-effectiveness |
| **Quality over Speed** | Financial research prioritizes accuracy | Slightly slower responses vs. higher trust |

---

## 12. Uncertainty & Experiments

<div class="columns">

<div class="column">

### What We're Genuinely Uncertain About

1. **Framework Extraction Accuracy**: Will automated extraction capture all nuances of proprietary frameworks?
   - *Experiment*: Manual validation of 100 framework extractions vs. automated

2. **Hallucination Detection Precision**: Can we achieve <5% hallucination rate consistently?
   - *Experiment*: A/B test different detection thresholds on golden set

3. **User Trust Adoption**: Will analysts trust system enough for client-facing work?
   - *Experiment*: Pilot with 5 analysts, measure trust scores over time

4. **Temporal Reasoning Accuracy**: Can system accurately handle time-evolving views?
   - *Experiment*: Test on 50 temporal queries from golden set

</div>

<div class="column">

### What We'll Test First

1. **Retrieval Effectiveness**: Evaluate retrieval metrics on golden set split
2. **Framework Extraction**: Validate extraction accuracy on known frameworks
3. **Answer Quality**: LLM-as-judge evaluation on sample queries
4. **Hallucination Rate**: Measure on golden set before production

### Where We Expect to Be Wrong

1. **Initial Hallucination Rate**: Likely higher (~10-15%) before tuning
2. **Framework Coverage**: May only capture 60-70% initially, needs iteration
3. **User Adoption**: Trust building may take longer than expected
4. **Query Latency**: Complex queries may exceed targets initially

</div>

</div>

---

## 13. Complex Query Examples

<div class="columns">

<div class="column">

### Example 1: Exploratory Query
**Query:** *"What do we know about renewable energy investments in Southeast Asia?"*
- Identified as exploratory synthesis query
- Decomposition into sub-queries (regions, sectors, time periods)
- Graph traversal + semantic search finds 12 reports (2020-2024)
- Synthesis with framework (Risk-Return Analysis)
- Output: Structured answer with citations and temporal evolution

### Example 2: Methodological Query
**Query:** *"How have we historically evaluated regulatory risk in emerging markets?"*
- Identifies as framework/methodology query
- Retrieves framework definitions and historical applications
- Graph traversal: framework → region → risk assessment
- Output: Framework definition + historical examples + evolution timeline

</div>

<div class="column">

### Example 3: Temporal Query
**Query:** *"How has our view on interest rate sensitivity evolved from 2020 to 2024?"*
- Temporal query identified with date range filter
- Retrieval with time filters (2020-2024)
- Graph query finds interest_rate → analysis → company relationships over time
- Synthesis compares views across time periods
- Output: Evolution narrative with date-specific citations and reasoning changes

### Example 4: Ambiguous Query
**Query:** *"Tell me about the European market"*
- Ambiguity detected (which market? what time period? what aspect?)
- Clarification generated: *"Which European market? (Equity, Fixed Income, Credit, etc.) What time period? What specific aspect?"*
- System waits for clarification before proceeding

</div>

</div>

---

## 14. Implementation Roadmap

### Phase 1: Foundation (Months 1-3)
**Deliverable:** MVP with basic query answering
- Document processing pipeline, Basic knowledge graph construction
- Simple retrieval system (semantic search), Initial golden dataset annotation

### Phase 2: Intelligence (Months 4-6)
**Deliverable:** System with framework awareness
- Framework extraction and ontology construction, Hybrid retrieval system
- Basic answer generation with citations, Offline evaluation framework

### Phase 3: Advanced Capabilities (Months 7-9)
**Deliverable:** Production-ready system for pilot
- Multi-agent architecture, Advanced hallucination detection
- Temporal reasoning, Online evaluation (LLM-as-judge)

### Phase 4: Production & Scale (Months 10-12)
**Deliverable:** Production system with full observability
- Performance optimization, Monitoring and alerting
- User feedback integration, Continuous improvement pipeline

---

## 15. Assumptions & Critical Questions

<div class="columns">

<div class="column">

### Key Assumptions (8)

1. Data Quality: Corpus well-structured with metadata
2. Expert Availability: Senior analysts available for annotation/validation
3. Infrastructure: Scalable cloud infrastructure available
4. Adoption: Analysts willing to use system once trust established
5. Regulatory Compliance: System can meet financial services requirements
6. Golden Dataset Quality: 2,500 Q&A pairs adequately represent domain
7. LLM Capabilities: Foundation models fine-tunable for financial domain
8. Framework Stability: Analytical frameworks remain relatively stable

### Key Risks & Mitigation

**Hallucination** → Multi-stage guardrails
**Loss of expert nuance** → Framework extraction
**System complexity** → Phased implementation
**Trust barriers** → Transparency & HITL

</div>

<div class="column">

### Critical Questions for Leadership

1. What hallucination rate is acceptable for different use cases?
2. How to handle conflicting information from different time periods?
3. What is acceptable latency for complex queries?
4. What are compliance requirements for AI-generated client content?
5. What is budget for ongoing human annotation and validation?

</div>

</div>

---

## 15. Data Governance & Security

<div class="columns">

<div class="column">

### Data Governance

**Access Control:**
- Role-based access (analyst, senior analyst, admin)
- Document-level permissions
- Query logging and audit trails

**Versioning:**
- Document version tracking
- Framework version management
- Knowledge graph change logs

**Compliance:**
- Financial services regulations (SEC, FINRA)
- Data retention policies
- Right to be forgotten

</div>

<div class="column">

### Security Measures

**Data Protection:**
- Encryption at rest and in transit
- Secure API endpoints (OAuth 2.0)
- PII detection and masking

**System Security:**
- Regular security audits
- Vulnerability scanning
- Incident response procedures

**Privacy:**
- Query anonymization for evaluation
- User data protection
- Audit trail compliance

</div>

</div>

---

## 16. Conclusion & Next Steps

### Key Design Principles

1. **Domain Expertise First**: Every component preserves expert thinking
2. **Quality over Speed**: Accuracy and trust prioritized
3. **Transparency**: Clear citations and confidence scores
4. **Continuous Improvement**: Evaluation-driven development

### Success Factors

- Comprehensive evaluation framework
- Strong hallucination mitigation
- Framework-aware processing
- Multi-stage quality assurance

### Immediate Next Steps

1. Validate assumptions with leadership
2. Begin golden dataset expansion and annotation
3. Build document processing MVP
4. Design detailed knowledge graph schema
5. Set up evaluation infrastructure

**Thank you!** *Ready for 25-minute presentation + 50-minute Q&A*
