Here is your **extensive and detailed** Unit II notes, now expanded with more examples, sub‑topics, additional diagrams, and deeper explanations – all inside a code window.

```markdown
# UNIT II – SOFTWARE REQUIREMENTS ENGINEERING & ANALYSIS (EXTENSIVE NOTES)

## 1. INTRODUCTION TO REQUIREMENTS ENGINEERING
- **Requirement:** A condition or capability needed by a user to solve a problem or achieve an objective (IEEE definition).
- **Requirements Engineering (RE):** The process of discovering, analyzing, documenting, validating, and managing requirements.
- **Why important?** Most software failures trace back to incorrect or incomplete requirements.

## 2. TYPES OF SOFTWARE REQUIREMENTS – DETAILED

### 2.1 Functional Requirements
- **Definition:** Describe what the system **must do** – specific behaviors, functions, or features.
- **Format:** Usually “System shall …”
- **Examples (Library Management System):**
  - System shall allow a student to search for books by title, author, or ISBN.
  - System shall issue a book only if the student has no overdue books.
  - System shall calculate fine at ₹2 per day for overdue books.
- **Exam tip:** If you can write a test case for it, it’s likely functional.

### 2.2 Non‑Functional Requirements (NFRs)
- **Definition:** Constraints on **how well** the system performs its functions. Also called quality attributes.
- **Remember using PRUS+SM:**
  - **P**erformance – response time, throughput, latency.
  - **R**eliability – uptime, mean time between failures (MTBF).
  - **U**sability – learnability, efficiency of use, memorability.
  - **S**ecurity – confidentiality, integrity, availability.
  - **S**calability – handles growth in users/data.
  - **M**aintainability – ease of fixing and enhancing.
- **Examples:**
  - The system shall respond to search queries within 2 seconds for up to 1000 concurrent users. (Performance)
  - The system shall be available 99.9% of the time excluding scheduled maintenance. (Reliability)
  - A new librarian shall be able to issue a book within 5 minutes of first use. (Usability)
  - All user passwords must be hashed using bcrypt. (Security)
- **Important distinction:** If an NFR is violated, the system still works but poorly.

### 2.3 Domain Requirements
- **Definition:** Requirements that come from the **application domain** – laws, regulations, industry standards, organizational policies.
- **Examples:**
  - Medical software: “The system must maintain an audit trail of all accesses to patient records” (HIPAA).
  - Banking: “All money transfers above ₹50,000 must be logged and reported to RBI” (regulatory).
  - Airline: “Flight booking system must follow IATA (International Air Transport Association) message formats.”
- **Key point:** Users often forget to state them because they seem “obvious” within the domain.

### 2.4 User Requirements
- **Definition:** High‑level statements of what the user wants, written in **natural language** without technical jargon.
- **Usually the starting point:** User requirements are refined into **system requirements** (more precise, technical).
- **Examples (from a student for an exam portal):**
  - “I want to see my grades as soon as the teacher uploads them.”
  - “The system should remind me about upcoming assignment deadlines.”
  - “As a teacher, I want to download an Excel report of all student scores.”

### Comparison Table – All Four Types

| Requirement Type | Perspective | Level of Detail | Example (Hotel Booking System) |
|----------------|--------------|------------------|--------------------------------|
| **User** | End user | High‑level, vague | “I want to cancel my booking without penalty up to 24 hours before.” |
| **Functional** | System | Precise, testable | “System shall allow cancellation without charge if current time > check‑in time minus 24 hours.” |
| **Non‑functional** | System | Quality metric | “Cancellation confirmation email shall be delivered within 30 seconds.” |
| **Domain** | Industry | Constraint | “Must comply with GDPR – user must explicitly consent to data storage.” |

## 3. REQUIREMENT ANALYSIS TECHNIQUES – DETAILED

### 3.1 Viewpoints
- **Definition:** A way of looking at the system from a particular stakeholder’s perspective.
- **Common viewpoints:**
  - **User viewpoint** – tasks, usability, features.
  - **Manager viewpoint** – cost, schedule, progress.
  - **Regulator viewpoint** – compliance, safety.
  - **Developer viewpoint** – feasibility, architecture.
- **Advantage:** Reduces the chance of missing critical requirements.
- **Diagram (text):**
```
        [User] ──(tasks, ease of use)──┐
        [Manager] ──(budget, timeline)──┼──> [Requirements Set]
        [Regulator] ──(laws, audit)────┘
```

### 3.2 Interviewing
- **Types:**
  - **Structured:** Pre‑prepared questions, same for all. Good for large numbers.
  - **Unstructured:** Open‑ended conversation. Good for deep exploration.
  - **Group interview / JAD (Joint Application Development):** Multiple stakeholders together. Fast but can be dominated by vocal individuals.
- **Best practices:** Record sessions (with permission), prepare question lists, follow up with summaries.

### 3.3 Scenarios
- **Definition:** A concrete, step‑by‑step story of interaction between an actor and the system.
- **Structure (template):**
  - **Scenario name:** e.g., “Successful cash withdrawal”
  - **Actor:** Registered bank customer
  - **Pre‑condition:** Customer has valid card and sufficient balance.
  - **Normal flow:**
    1. Customer inserts card.
    2. ATM prompts for PIN.
    3. Customer enters correct PIN.
    4. ATM shows menu.
    5. Customer selects “Withdraw”.
    6. Customer enters amount.
    7. ATM checks balance → sufficient.
    8. ATM dispenses cash.
    9. ATM prints receipt (optional).
    10. ATM returns card.
  - **Post‑condition:** Balance reduced by amount + fee; customer has cash.
  - **Exceptions (alternate flows):**
    - Invalid PIN → card retained.
    - Insufficient balance → message shown, no cash.
    - ATM out of cash → message shown, cancel transaction.
- **When to use:** Complex interactions, safety‑critical systems, user training.

### 3.4 Use‑Cases
- **Definition:** A formal, UML‑based technique to describe **what** the system does, not **how**.
- **Components:**
  - **Actor:** External entity (human or other system) that interacts.
  - **Use‑case:** A specific goal the actor wants to achieve (verb + noun).
  - **System boundary:** Rectangle around all use‑cases.
- **Relationships (important for exam):**
  - **Include (`<<include>>`)** – A use‑case **always** calls another. Example: `Withdraw Cash <<include>> Validate PIN`.
  - **Extend (`<<extend>>`)** – A use‑case **optionally** extends another. Example: `Withdraw Cash <<extend>> Print Receipt`.
  - **Generalization** – A child actor inherits parent’s use‑cases. Example: `Manager` inherits from `Employee`.
- **Text‑based diagram (use‑case diagram):**
```
+--------------------------------------------------+
|                   ATM System                     |
|                                                  |
|  [Customer] -----> (Withdraw Cash)               |
|                 \-> (Check Balance)              |
|                 \-> (Transfer Funds)             |
|                    ▲                             |
|                    │ <<include>>                 |
|                    │                             |
|                 (Validate PIN)                   |
|                                                  |
|  [Maintenance] --> (Refill Cash)                 |
|                 \-> (Collect Deposits)           |
+--------------------------------------------------+
```
- **Use‑case description (text table format):**

| Element | Value |
|---------|-------|
| Use‑case name | Withdraw Cash |
| Actor | Customer |
| Pre‑condition | Customer authenticated (PIN validated) |
| Trigger | Customer selects “Withdraw” |
| Normal flow | 1. System asks for amount. 2. Customer enters amount. 3. System checks balance. 4. System dispenses cash. 5. System updates balance. 6. System returns card. |
| Post‑condition | Cash dispensed, balance reduced |
| Exceptions | Insufficient balance → error message, no cash |

## 4. MODELLING TECHNIQUES – EXTENSIVE

### 4.1 Data Flow Diagrams (DFD)
- **Purpose:** Show how data moves through the system; independent of control flow (unlike flowcharts).
- **Levels of DFD:**
  - **Context Diagram (Level 0):** Single process representing whole system, external entities, data flows. Highest level.
  - **Level 1 DFD:** Decompose the single process into major sub‑processes.
  - **Level 2 DFD:** Further decomposition.
- **Logical vs Physical DFD:**
  - **Logical DFD** – *What* processes occur, independent of technology (e.g., “Validate order”).
  - **Physical DFD** – *How* they occur, including technology (e.g., “Clerk enters order into terminal”, “Server runs validation script”).
- **Symbols (Yourdon/DeMarco notation):**
  - **Process** – circle or rounded rectangle. Numbered (e.g., 1.0, 1.1).
  - **External Entity** – rectangle (square). Placed at edges.
  - **Data Store** – two parallel lines (or open‑ended rectangle). Labeled like “D1 Orders”.
  - **Data Flow** – arrow. Labeled with data name (e.g., “Order Details”).
- **Example – Level 1 DFD for Order System (text diagram):**
```
[Customer] ----(Order + Payment)----> (1.0 Verify Payment)
                                           │
                                           ▼ (Valid Payment)
                                     (2.0 Process Order) ----> [D1 Orders File]
                                           │
                                           ▼ (Shipping Request)
                                     [Warehouse System] (external entity)

(1.0) also sends ----> (Payment Status) ----> [Customer]
```
- **Rules:** Every process must have at least one input and one output data flow. Data cannot move directly from one store to another without a process.

### 4.2 Entity Relationship Diagram (ERD)
- **Purpose:** Show data structure – entities (tables), attributes (fields), relationships (associations).
- **Symbols (Chen or Crow’s Foot):**
  - **Entity** – rectangle (e.g., Student, Course)
  - **Attribute** – ellipse (oval) connected to entity (e.g., StudentName, StudentID)
  - **Relationship** – diamond (e.g., Enrolls, Teaches)
  - **Cardinality** – numbers or symbols (1, N, 0..*)
- **Example ERD (text diagram with cardinality):**
```
[Student]  (1) ── Enrolls in ── (0..*)  [Course]
    │                                    │
 (StudentID, Name, Major)              (CourseID, Title, Credits)
```
- **Interpretation:** One Student can enroll in zero‑to‑many Courses; one Course can have many Students (many‑to‑many).
- **ERD vs DFD comparison:**
  - ERD = **static** data model (structure)
  - DFD = **dynamic** process model (behavior)

### 4.3 Data Dictionary
- **Definition:** A central repository that defines all data elements used in the system (DFDs, ERDs, etc.).
- **Typical entries (for each data element):**
  | Field | Description | Example for “CustomerID” |
  |-------|-------------|--------------------------|
  | Name | Unique identifier | CustomerID |
  | Alias | Alternative names | CustID, CID |
  | Type | Data type | Integer |
  | Length | Size | 5 digits |
  | Range/Values | Allowed values | 10000 to 99999 |
  | Default | Default value | N/A |
  | Where used | DFD/ERD reference | DFD process 2.0, ERD Student entity |
- **Example entries:**
  - `CustomerID = 5-digit integer (10000-99999)`
  - `OrderTotal = Decimal (10,2) , range 0.00 – 999999.99`
  - `Gender = Enumerated {M, F, O}`
- **Why important?** Prevents ambiguity (e.g., “CustomerID” means different things to different teams).

## 5. REQUIREMENT VALIDATION – DETAILED

- **Definition:** Checking requirements documents for errors before development begins.
- **What to check (properties – remember C3U):**
  - **Correctness** – Are they true requirements?
  - **Completeness** – Are any requirements missing?
  - **Consistency** – No two requirements contradict.
  - **Unambiguity** – Only one interpretation.
  - **Realism** – Feasible within budget/schedule.
  - **Verifiability** – Can we test this requirement?
- **Validation techniques (exam favourite – list at least 4):**
  1. **Reviews / Walkthroughs** – Team goes through SRS line by line.
  2. **Prototyping** – Build a mock‑up; user tries it.
  3. **Test‑case generation** – Attempt to write tests; if impossible, requirement is not testable.
  4. **Automated consistency checking** – Tools detect conflicting requirements.
  5. **Model validation** – Simulate DFD/ERD with sample data.
- **Key exam phrase:** *Validation asks “Are we building the right product?”*  
  *Verification asks “Are we building the product right?”*

## 6. SOFTWARE REQUIREMENT SPECIFICATION (SRS) – DETAILED

- **Definition:** An official document that describes all requirements for a software system. Serves as a contract between customer and developer.

### IEEE Std 830-1998 Recommended Structure (exam standard):
1. **Introduction**
   - 1.1 Purpose (why this document)
   - 1.2 Document Conventions (typography, icons)
   - 1.3 Intended Audience (developers, testers, managers)
   - 1.4 Product Scope (what the system will and will not do)
   - 1.5 References (other documents)

2. **General Description**
   - 2.1 Product Perspective (how it fits into existing systems)
   - 2.2 User Characteristics (technical level, training)
   - 2.3 Operating Environment (hardware, OS, network)
   - 2.4 Design/Implementation Constraints (e.g., must use Java, must be web‑based)
   - 2.5 Assumptions and Dependencies

3. **Specific Requirements** (the core)
   - 3.1 External Interfaces (user, hardware, software, communication)
   - 3.2 Functional Requirements (organized by feature, each with ID)
   - 3.3 Non‑functional Requirements (performance, safety, security, etc.)
   - 3.4 Logical Database Requirements (data retention, schema)

4. **Appendices**
   - Glossary, analysis models (DFD, ERD), to‑be‑determined list

### Example SRS snippet (Functional requirement):
```
REQ‑FUNC‑001: The system shall authenticate a user by email and password.
Priority: High
Source: Customer requirement #A3
Verification: Demonstrate test case where correct credentials grant access, incorrect deny.
```

### Characteristics of a good SRS (exam mnemonic – **CUCUR**):
- **C**orrect
- **U**nambiguous
- **C**omplete
- **U**nderstandable by all stakeholders
- **R**anked for importance/stability

## 7. FEASIBILITY STUDY – DETAILED (TELOS expanded)

Performed **before** full requirements engineering to decide whether the project should proceed.

| Type | Key Questions | Example (School Bus Tracking App) |
|------|---------------|-------------------------------------|
| **Technical** | Do we have the right hardware, software, skills? | Can we integrate GPS and mobile networks? Do we know Android/iOS? |
| **Economic** | Cost vs benefit (ROI, payback period) | Development cost ₹10L; annual savings ₹3L → payback ~3.3 years. |
| **Legal** | Any copyright, data privacy, regulatory issues? | Student location data – need parental consent (COPPA). |
| **Operational** | Will users accept and actually use it? | Bus drivers may resist using the app; need training. |
| **Schedule** | Can we deliver by the deadline? | Client wants in 3 months, but development needs 6 – not feasible. |

- **Output:** A feasibility report with go/no‑go recommendation.

## 8. COMPLETE REQUIREMENTS ENGINEERING PROCESS – FLOWCHART

```text
+---------------------------+
|     Feasibility Study     |
| (TELOS analysis)          |
+------------+--------------+
             ↓
+------------+--------------+
|   Elicitation (Discovery)  |
| - Interviewing            |
| - Scenarios               |
| - Use-cases               |
+------------+--------------+
             ↓
+------------+--------------+
|   Analysis & Modelling     |
| - Viewpoints              |
| - DFD (logical/physical)  |
| - ERD                     |
| - Data Dictionary         |
+------------+--------------+
             ↓
+------------+--------------+
|   Validation (Checking)    |
| - Reviews / Walkthroughs  |
| - Prototyping             |
| - Test-case generation    |
+------------+--------------+
             ↓
+------------+--------------+
|   Specification (SRS)      |
| IEEE 830 document         |
+---------------------------+
```

## 9. ADDITIONAL EXAM TIPS

- **Short answer questions:** Definitions of functional/NFR, difference between logical/physical DFD, SRS structure.
- **Long answer questions:** Explain use‑case relationships (include/extend) with diagram; draw a Level 1 DFD for a given system; write a feasibility report.
- **Common mistakes:** Confusing validation vs verification; forgetting domain requirements; mixing up scenario and use‑case.

## 10. SELF‑TEST (EXTENDED – 15 QUESTIONS)

1. List the four types of software requirements. Give one original example for each (not from notes).
2. What is the difference between `<<include>>` and `<<extend>>` in use‑case diagrams? Draw a small diagram.
3. Draw a context diagram (Level 0 DFD) for an **Online Shopping Cart**.
4. What are the three symbols used in an ERD (excluding attributes)? What does each represent?
5. Explain with an example: **Logical DFD** vs **Physical DFD**.
6. What properties should a good SRS have? (Use mnemonic CUCUR)
7. Name five requirement validation techniques.
8. What does TELOS stand for? Explain each with a one‑line question.
9. Write a **scenario** (normal flow + one exception) for “User resets forgotten password”.
10. What is a data dictionary? Give two example entries.
11. “System shall encrypt all data in transit” – functional or non‑functional? Justify.
12. Differentiate **validation** and **verification** in one sentence each.
13. Draw a use‑case diagram for a **Library Management System** with actors: Student, Librarian; use‑cases: Borrow Book, Return Book, Pay Fine, Add Book (librarian only).
14. List the four main sections of IEEE 830 SRS.
15. What is the purpose of a feasibility study? Under which feasibility would you check “Will the new system conflict with existing union rules?” (Answer: Operational)

---
**END OF UNIT II EXTENSIVE NOTES**
```

These notes are now significantly longer and more detailed. If you need even more depth in any specific section (e.g., full worked example of DFD with levels 0,1,2), just tell me.