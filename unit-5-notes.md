📘 Unit V – Notes (Implementation & Testing)
markdown
# UNIT V – IMPLEMENTATION TECHNIQUES & TESTING

## PART A: CODING & MAINTENANCE

### 1. Good Coding Practices
- Meaningful names
- Consistent indentation
- Comment *why*, not *what*
- Small functions (single responsibility)
- No hard‑coded constants
- Error handling

### 2. Refactoring
Restructure code without changing external behavior.

**Techniques:** Extract method, rename, inline, remove duplicates, split class.

### 3. Software Maintenance (CAPA)

| Type | What |
|------|------|
| **C**orrective | Fix bugs |
| **A**daptive | New environment (OS, hardware) |
| **P**erfective | Improve performance/features |
| **P**reventive | Prevent future problems |

### 4. Reengineering Process Model
Old System → Reverse Engineering → Understanding →
→ Code/Data Restructuring → Forward Engineering → New System

text

**Reverse Engineering:** Code → Design (understand existing system)
**Forward Engineering:** Requirements → Design → Code (normal development)

---

## PART B: SOFTWARE TESTING

### 1. Software Testing Life Cycle (STLC)
1. Requirement Analysis
2. Test Planning
3. Test Case Development
4. Environment Setup
5. Test Execution
6. Test Closure

### 2. White‑Box Testing (Internal view)
- Based on code structure
- Techniques:
  - **Basis Path Testing:** Use control flow graph + cyclomatic complexity = number of independent paths to test
  - **Control Structure Testing:** Branch, loop, condition testing

### 3. Black‑Box Testing (External view)
- Based on requirements
- Techniques:
  - Equivalence Partitioning (group inputs)
  - Boundary Value Analysis (edges of groups)
  - Decision Table
  - State Transition

### 4. Types of Testing (scope order)

| Test Type | Scope | Who |
|-----------|-------|-----|
| Unit | Single function | Developer |
| Integration | Modules together | Developer/Tester |
| Regression | Re‑run tests after change | Tester |
| Validation | Meets customer needs? | Tester + Customer |
| System | Whole system | Tester |

### 5. Debugging
Finding, analyzing, and removing the cause of failure.

**Steps:** Reproduce → Locate → Analyze → Fix → Retest → Document

### 6. Defect Life Cycle
[New] → [Assigned] → [Open] → [Fixed] → [Verified] → [Closed]
↑ ↓ ↓ ↓
└─ [Rejected] [Deferred] [Reopen] ←──┘

text

| State | Meaning |
|-------|---------|
| New | Logged, not reviewed |
| Assigned | Given to developer |
| Open | Being worked on |
| Fixed | Change made |
| Verified | Tester confirms |
| Closed | Done |
| Rejected | Not a real defect |
| Deferred | Future release |
| Reopen | Fix failed, back to dev |