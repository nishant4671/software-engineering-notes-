📘 Unit VI – Notes (Metrics & Quality Management)
markdown
# UNIT VI – METRICS & QUALITY MANAGEMENT

## PART A: PRODUCT METRICS

| Phase | Example Metrics |
|-------|-----------------|
| Analysis | #requirements, #use cases, volatility |
| Design | #modules, cohesion, coupling, DIT, NOC |
| Code | LOC, cyclomatic complexity, comment density, nesting depth |
| Testing | Coverage %, defect density, DRE, #test cases |
| Maintenance | MTTF, MTBF, change request backlog |

**DRE (Defect Removal Efficiency)** = (defects found before release) / (defects before + after release)

---

## PART B: PROCESS METRICS

### Process Framework
Generic activities: Communication → Planning → Modeling → Construction → Deployment

### CMMI (Capability Maturity Model Integration) – 5 Levels

| Level | Name | Description |
|-------|------|-------------|
| 1 | Initial | Chaotic, individual heroics |
| 2 | Managed (Repeatable) | Basic project management |
| 3 | Defined | Standardized across org |
| 4 | Quantitatively Managed | Measured & controlled |
| 5 | Optimizing | Continuous improvement |

### Process Patterns
Reusable best practices (e.g., Daily Standup, Retrospective)

### Process Assessment
Evaluation against model (CMMI/ISO) → maturity rating + improvement roadmap

---

## PART C: QUALITY MANAGEMENT

### Software Quality Concepts
McCall’s factors: correctness, reliability, efficiency, integrity, usability, maintainability, flexibility, testability, portability, reusability, interoperability.

### Software Quality Assurance (SQA)
Activities to monitor and ensure quality: planning, reviews, audits, standards, metrics, change control.

### Software Reviews

| Type | Formality |
|------|-----------|
| Peer review | Low |
| Walkthrough | Medium |
| Technical review | High |
| Formal Technical Review (FTR) | Highest |

### Formal Technical Review (FTR) – Exam focus
**Roles:** Moderator, Author, Reviewers, Scribe (management absent)

**Process:**
1. Planning
2. Preparation (individual study)
3. Meeting (find defects, not solutions)
4. Rework
5. Follow‑up

**Outcome:** Defect list + accept/reject decision

### Statistical Software Quality Assurance (SSQA)
- Sample modules, estimate defect density, use control charts
- Efficient for large systems

### Software Reliability
**Probability of failure‑free operation for specified time under specified conditions.**

Metrics:
- **MTTF** (Mean Time To Failure)
- **MTBF** = MTTF + repair time
- Failure rate λ = 1/MTTF (if constant)

### ISO 9000 Quality Standards
- Family of international standards for Quality Management Systems (QMS)
- **ISO 9001** (certification standard) – requirements: document control, process approach, customer focus, continuous improvement
- ISO 9000‑3: guidelines for software

**CMMI vs ISO 9001:**
- CMMI: software‑specific, maturity levels 1‑5
- ISO 9001: generic, pass/fail certification (minimum acceptable)