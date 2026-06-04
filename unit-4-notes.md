📘 Unit IV – Notes (Change Management & SCM)
markdown
# UNIT IV – CHANGE MANAGEMENT & SCM

## 1. SOFTWARE CONFIGURATION MANAGEMENT (SCM)

**Definition:** Tracking and controlling changes to software artifacts.

**Elements of SCM (ICCA):**
- **I**dentification – what to control (SCIs)
- **C**ontrol – formal change approval
- **C**onfiguration Audit – verify delivered matches docs
- **A**ssessment / Status Reporting – inform stakeholders

## 2. BASELINE & SCIs

- **Baseline:** Frozen snapshot at a point in time (e.g., requirements baseline)
- **SCI (Software Configuration Item):** Any controlled artifact (code, docs, test scripts, config files)

## 3. SCM REPOSITORY

Central storage for all SCIs + version history + metadata + relationships (e.g., GitHub)

## 4. CHANGE CONTROL PROCESS
Change Request → Submit → Evaluate (impact, cost, risk) →
→ CCB Approve/Reject → If approved → Implement → Review → Close

text

**CCB = Change Control Board** (PM, lead dev, QA lead)

## 5. VERSION CONTROL (GIT)

| Concept | Meaning |
|---------|---------|
| Commit | Save version with message |
| Branch | Parallel line of development |
| Merge | Combine branches |
| Pull Request | Request to merge branch with code review |
| Tag | Named snapshot (e.g., v1.0) |

## 6. GIT FEATURE BRANCH WORKFLOW
main ──────●─────────────●─────────────●
\ / /
feature ●──●──●─────── /
other \──●──●──────

text

**Steps:**
1. Create branch from `main`
2. Work, commit, push
3. Open Pull Request (PR)
4. Review, update if needed
5. Merge to `main`
6. Delete branch

## 7. CONTINUOUS INTEGRATION (CI)

**Definition:** Merge code many times/day → automatic build + test.

**CI Workflow:**
Commit → CI server detects → build → run tests →
→ success: OK / fail: alert team

text

**Benefits of CI (exam list):**
- Early bug detection
- Reduced merge conflicts
- Faster feedback
- Main branch always stable
- Encourages small commits

## 8. CONTINUOUS DELIVERY (CD)

**Definition:** After CI, automatically deploy to staging (or production) with minimal manual intervention.

**Key principles:**
- Build once, deploy many
- Automate everything
- Fast pipeline
- Same process for all environments
- Version everything
- Ready to rollback

**CI vs CD:**
- CI = build + test after every commit
- CD = automatic deployment after CI