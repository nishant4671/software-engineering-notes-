Below are your **complete notes for Unit I and Unit II**, each inside a separate code window (markdown formatting). All diagrams, flowcharts, and tables are included as text-based art, ready for you to copy, save, or print.

---

## 📘 Unit I – Notes (Software Engineering Fundamentals & Process Models)

```markdown
# UNIT I – SOFTWARE ENGINEERING FUNDAMENTALS & PROCESS MODELS

## 1. WHAT IS SOFTWARE?
- Set of instructions (programs) + data + documentation.
- **Analogy:** Hardware = body; Software = brain.

## 2. TYPES OF SOFTWARE
| Type               | Purpose                          | Example                 |
|--------------------|----------------------------------|-------------------------|
| System Software    | Runs computer itself             | Windows, Linux, drivers |
| Application Software | Helps user do tasks            | MS Word, Chrome, WhatsApp |

## 3. CHARACTERISTICS OF SOFTWARE (LCDC)
- **L**ogical, not physical (intangible)
- **C**ustom built (not manufactured)
- **D**eveloped, not assembled
- **C**omplex & changeable (doesn't wear out but deteriorates)

## 4. ATTRIBUTES OF GOOD SOFTWARE (MURC + Efficiency/Portability)
- **M**aintainability – easy to fix/enhance
- **U**sability – easy to learn/use
- **R**eliability – works correctly over time
- **C**orrectness – meets requirements

## 5. SOFTWARE ENGINEERING
- Systematic application of engineering principles to software development, operation, maintenance.

## 6. KEY CHALLENGES (CHC)
- **C**omplexity – millions of lines of code
- **H**eterogeneity – different devices/OS
- **C**hange – requirements constantly evolve

## 7. SYSTEMS ENGINEERING vs SOFTWARE ENGINEERING
| Aspect              | Systems Engineering               | Software Engineering       |
|---------------------|-----------------------------------|----------------------------|
| Scope               | Whole system (hardware+software)  | Only software part         |
| Example             | Fighter jet + radar + pilots      | Navigation software only   |

## 8. SOFTWARE DEVELOPMENT PROCESS MODELS

### A. TRADITIONAL MODELS

#### 1. Waterfall Model
- **Diagram:** 
```
Requirements → Design → Implementation → Testing → Deployment → Maintenance
(no going back)
```
- **Use when:** Fixed requirements, small project.
- **Cons:** Rigid, late error detection.

#### 2. V-Model (Verification & Validation)
- **Diagram:**
```
Requirements ──────────────→ Acceptance Testing
   │                            │
Design (High-level) ────────→ System Testing
   │                            │
Design (Detailed) ──────────→ Integration Testing
   │                            │
Coding ─────────────────────→ Unit Testing
```
- **Use when:** High reliability needed (medical devices).

#### 3. Evolutionary Model
- Build small version → feedback → improve iteratively.
- **Analogy:** Essay drafts.

#### 4. Spiral Model (Risk-driven)
- **Diagram (conceptual):**
```
Loop1: prototype
Loop2: more features
Loop3: full system
(Each loop: objectives → risk analysis → develop → plan next)
```
- **Use when:** Large, high-risk, evolving requirements.

#### 5. CBSE (Component-Based)
- Assemble from pre-made components (like Lego blocks).

#### 6. Unified Process (UP) – RUP
- Phases: Inception → Elaboration → Construction → Transition.

#### 7. Rapid Application Development (RAD)
- Fast prototyping, minimal planning, uses tools.
- **Use when:** Time-critical, small team.

#### 8. Prototyping Model
- Build low-fidelity mock-up → user refines → final system.
- **Types:** Throwaway (discard after feedback) / Evolutionary (keep improving).

### B. AGILE MODELS

#### Agile Manifesto Values
- Individuals & interactions over processes & tools
- Working software over comprehensive documentation
- Customer collaboration over contract negotiation
- Responding to change over following a plan

#### 1. Extreme Programming (XP)
- Practices: TDD, pair programming, small releases, continuous integration, simple design.

#### 2. Scrum
- **Roles:** Product Owner, Scrum Master, Development Team.
- **Artifacts:** Product Backlog, Sprint Backlog, Increment.
- **Events:** Sprint (1-4 weeks), Daily Scrum, Sprint Review, Retrospective.
- **Diagram:**
```
Product Backlog → Sprint Planning → Sprint → Working Increment
                       ↑              ↓
                  Daily Scrum ← Retrospective & Review
```

## 9. COMPARISON TABLE – TRADITIONAL vs AGILE
| Traditional          | Agile                    |
|----------------------|--------------------------|
| Plan-driven          | Change-driven            |
| Heavy documentation  | Working software preferred |
| Testing at end       | Continuous testing       |
| Customer at milestones | Customer on-site       |

## 10. SELF-TEST (Unit I)
1. What are the three key challenges of software engineering? (CHC)
2. Which model is risk-driven? (Spiral)
3. Name two attributes of good software.
4. Is Agile a process model or a philosophy? (Philosophy)
5. What does the V in V-model stand for? (Verification & Validation)
```

---

## 📘 Unit II – Notes (Software Requirements Engineering & Analysis)

```markdown
# UNIT II – SOFTWARE REQUIREMENTS ENGINEERING & ANALYSIS

## 1. TYPES OF SOFTWARE REQUIREMENTS

| Type                | Focus                                | Example                                    |
|---------------------|--------------------------------------|--------------------------------------------|
| **Functional**      | What the system MUST DO              | "System shall send email on order confirm" |
| **Non-functional**  | How well it does it (quality)        | "Email sent within 5 seconds"              |
| **Domain**          | Industry/regulatory constraints      | "Must comply with PCI-DSS"                 |
| **User**            | High-level, natural language         | "I want to reset my password easily"       |

**Non-functional categories (PRUS):** Performance, Reliability, Usability, Security, Scalability, Maintainability.

## 2. REQUIREMENT ANALYSIS TECHNIQUES

### Viewpoints
- Gather requirements from different stakeholders (e.g., user, manager, regulator).
- **Analogy:** Blind men and elephant.

### Interviewing
- Structured (fixed questions) / Unstructured (open) / Group.

### Scenarios
- Story of interaction: actor, pre-condition, normal flow, post-condition, exceptions.
- **Example (ATM):** Insert card → enter PIN → select amount → get cash → return card.

### Use-Cases
- Formal representation: Actor + Use-case (goal) + includes/extends.
- **Text diagram:**
```
[Customer] --- (Withdraw Cash) ---> ATM System
              (Check Balance)
              (Transfer Funds)
```
- **Include** = mandatory sub-function (e.g., Login).
- **Extend** = optional behavior (e.g., Print Receipt).

## 3. MODELLING TECHNIQUES

### Data Flow Diagram (DFD)
- Shows **data movement**. Symbols (Yourdon):
  - Circle/rounded rect = Process
  - Open rectangle = External entity
  - Parallel lines = Data store
  - Arrow = Data flow

**Logical DFD** (what) vs **Physical DFD** (how).

**Example DFD (order system):**
```
[Customer] --- (Order Details) ---> (1.0 Validate Order) ---> (Valid Order) ---> [Order File]
                                    │
                                    └--- (Invalid Notice) ---> [Customer]
```

### Entity Relationship Diagram (ERD)
- Shows **data structure**.
- Rectangle = Entity, Ellipse = Attribute, Diamond = Relationship.

**Example ERD:**
```
[Student] ---- (Enrolls in) ---- [Course]
    │                              │
 (StudentID, Name)              (CourseID, Title)
```

**DFD vs ERD:** DFD = process view (what happens to data); ERD = data view (how data is structured).

### Data Dictionary
- Central repository of data definitions (name, type, length, allowed values, location).

## 4. REQUIREMENT VALIDATION
- Checking for: correctness, completeness, consistency, unambiguity, realism.
- **Techniques:** Reviews, prototyping, test-case generation, automated checks.
- **Key phrase:** Validation = building the **right** product (vs verification = building product **right**).

## 5. SOFTWARE REQUIREMENT SPECIFICATION (SRS)
**IEEE 830 Standard Structure:**
1. **Introduction** (purpose, scope, definitions)
2. **General description** (user characteristics, constraints)
3. **Specific requirements** (functional, non-functional, interfaces)
4. **Appendices**

**Typical SRS item format:**
- ID: FUNC-01
- Description: System shall validate user login.
- Priority: High
- Source: Customer

## 6. FEASIBILITY STUDY (TELOS)
| Type         | Question                                  |
|--------------|-------------------------------------------|
| **T**echnical | Do we have the technology/skills?        |
| **E**conomic  | Is cost-benefit positive? (ROI)          |
| **L**egal     | Any regulatory violation?                |
| **O**perational| Will users adopt it?                    |
| **S**chedule  | Can we deliver on time?                  |

## 7. REQUIREMENTS ENGINEERING PROCESS FLOWCHART
```
Feasibility Study
       ↓
Elicitation (Interview, Scenarios, Use-cases)
       ↓
Analysis (Viewpoints, DFD, ERD, Data Dictionary)
       ↓
Validation (Reviews, Prototyping)
       ↓
Specification (SRS Document)
```

## 8. SELF-TEST (Unit II)
1. Give one functional and one non-functional requirement for a library system.
2. What shape represents a **process** in a DFD? (Circle/rounded rect)
3. In ERD, what does a diamond represent? (Relationship)
4. Name three validation techniques.
5. What does TELOS stand for?
6. “System shall load page within 2 seconds” – functional or non-functional?
7. Differentiate scenario and use-case.
8. List the three main sections of IEEE 830 SRS (excluding appendices).
```

---

