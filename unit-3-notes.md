📘 Unit III – Notes (Software Design)
markdown
# UNIT III – SOFTWARE DESIGN

## 1. DESIGN CONCEPTS

| Concept | Definition | Analogy |
|---------|------------|---------|
| **Abstraction** | Hide details; show only essentials | Car steering wheel (not engine) |
| **Modularity** | Divide system into independent pieces | Lego bricks |
| **Information Hiding** | Hide internal data/algorithm from others | Vending machine internals |
| **Functional Independence** | Module does one thing, low external dependence | Specialized toolbox |
| **Refinement** | Stepwise decomposition from high to low level | Recipe: Bake cake → Mix, Bake, Cool |
| **Refactoring** | Restructure code without changing behavior | Tidying a messy desk |

## 2. COHESION (inside module – high is good)

| Level (best → worst) | Description | Example |
|----------------------|-------------|---------|
| Functional | Single specific task | `calculateTax()` |
| Sequential | Output of one part = input to next | Read → parse → validate |
| Communicational | Same data, different operations | Update + delete on same table |
| Procedural | Multiple tasks in sequence, unrelated data | Init, check, load config |
| Temporal | Tasks related by time | `startup()` doing many things |
| Logical | Similar tasks selected by flag | `handleAllIO(type)` |
| Coincidental | Completely unrelated | `avg + printLogo` |

## 3. COUPLING (between modules – low is good)

| Level (best → worst) | Description | Example |
|----------------------|-------------|---------|
| Data | Simple data parameters | `calc(a, b)` |
| Stamp | Pass whole structure, use part | `process(emp.name)` |
| Control | Pass flag that controls logic | `sort(data, ascending)` |
| External | Share global variable | Two funcs read `errno` |
| Common | Share global data space | `global int x` |
| Content | Directly modify another’s internal data | `A.B.internal = 5` |

## 4. ARCHITECTURAL STYLES (PCMV)
Pipe & Filter: Input → [F1] → [F2] → Output
Client‑Server: [Client] ↔ [Server]
MVC: [Model] ⇄ [Controller] ⇄ [View]
Layered: UI → Business → Data → DB

text

## 5. MAPPING DFD TO ARCHITECTURE

**Transform Mapping:**
Input flow → Transform center → Output flow
↓ ↓ ↓
Input modules → Transform modules → Output modules

text

**Transaction Mapping:**
[User choice] → (Transaction center) →┬→ Action module 1
├→ Action module 2
└→ Action module 3

text

## 6. AGILE DESIGN – SOLID PRINCIPLES

| Principle | Meaning |
|-----------|---------|
| **S**ingle Responsibility | One class, one reason to change |
| **O**pen/Closed | Open for extension, closed for modification |
| **L**iskov Substitution | Subtype must replace parent without breaking |
| **I**nterface Segregation | Many small interfaces > one fat interface |
| **D**ependency Inversion | Depend on abstractions, not concretions |

## 7. REFACTORING IN AGILE

- **When:** Before adding feature, after bug fix, during review
- **Examples:** Extract method, rename variable, remove duplicates, split large class
- **Significance:** Reduces technical debt, improves maintainability, enables continuous delivery
