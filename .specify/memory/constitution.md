# AACSB Accreditation Automator — Project Constitution

**Version**: 1.0
**Ratified**: October 2, 2026
**Last Amended**: October 2, 2026
**Applies to**: All specifications, plans, tasks, and code in this repository

This constitution states the non-negotiable principles of the AACSB Accreditation
Automator for Kean University's College of Business and Public Management (CBPM).
Every specification, plan, task list, and line of code in this project MUST comply
with these principles. Where a principle and a convenience conflict, the principle
wins. Amendments follow the Governance section at the end of this document.

---

## Principle I — The Guideline Is the Single Source of Truth

All classification rules, thresholds, contribution lists, and definitions come from
one document: **"CBPM Faculty Qualifications Definitions, Effective Fall 2026"**
(pages FQ-1 to FQ-6). No rule may be invented, approximated, or imported from
generic AACSB guidance where the CBPM guideline speaks. Rules MUST be stored as
versioned configuration (a *rule version*), never scattered through program code,
so that a guideline revision produces a new rule version — not a code change.
Where the guideline is ambiguous, the ambiguity MUST be flagged for human decision
and recorded; the system MUST NOT silently guess.

*Rationale: the tool's output will be examined by an AACSB peer review team. A
number that cannot be traced to FQ-1 through FQ-6 is a liability, not a feature.*

## Principle II — Deterministic Decisions, AI Assistance Only

The system is neuro-symbolic by design. A large language model MAY extract
structured data from documents and MAY draft records, explanations, and questions.
A language model MUST NEVER decide a classification, a ratio, or a qualification.
All decisions are made by deterministic rule code whose behavior can be tested,
reproduced, and explained line by line. Degree relatedness is a human judgment;
the system MAY mark it "clear" or "unclear" and MUST refer every "unclear" case
to a human, marking the affected classification provisional until resolved.

*Rationale: an accreditation decision that cannot be reproduced cannot be defended.*

## Principle III — Human Verification Before Any Record Locks

No data becomes official by machine action alone. Every faculty record follows the
lifecycle **Draft → Needs Info → Submitted → Verified → Locked**. The faculty
member attests to their own record ("I have verified"); a chair or coordinator
verifies it; only then is a classification snapshot locked. Locked snapshots are
immutable — corrections create a new snapshot; history is never rewritten.

*Rationale: the attestation in the original design sketch is not a formality. It is
the audit record that makes the data defensible.*

## Principle IV — Free and Open-Source Only

The tool MUST operate with no paid subscriptions and no per-seat costs, for use by
university faculty. Every component — application framework, database, hosting
during pilots, AI access, libraries — MUST be free or open-source, and every
component MUST be replaceable without rebuilding the system. Adding any dependency
requires a recorded cost check: *what does this cost at \$0/month, forever, and what
replaces it if its free tier disappears?*

*Rationale: a tool the college cannot afford to keep is a pilot, not a system.*

## Principle V — Confidential Data, Minimum Exposure

Faculty records, CVs, and classifications are confidential institutional data,
career-relevant to the people they describe. Therefore: development, testing, and
pilot environments use **invented (synthetic) faculty data only**; no real record
enters any environment until Kean IT and the university's data-governance owner
have approved the system in writing and the pre-launch checklist in the
architecture document (Section 9.6) is fully signed off. Row Level Security MUST be
enabled on every database table. Direct identifiers MUST be stripped from any text
sent to an external AI service, and only the minimum necessary text may be sent.
Secrets and API keys MUST live in host secret settings — never in code, never in
this repository, never in chat.

*Rationale: see Architecture Document v1.2, Section 9 (Security Plan).*

## Principle VI — Every Result Must Be Reproducible and Auditable

Every classification result MUST record: the rule version that produced it, the
locked snapshot it was computed from, and the evidence counted for and against.
Every human override MUST carry a reason and is written to the audit log with the
actor and timestamp. Given the same snapshot and the same rule version, the system
MUST produce the identical result, forever.

*Rationale: reproducibility is what separates a record from an opinion.*

## Principle VII — Structured Records Are the System of Record, Not CVs

The database of structured, verified records is the system of record. A CV is an
*input* used at onboarding; it is never the source of truth. If information is
missing from a CV, the system asks the faculty member for it (the completeness
checker); it does not lower its standards to what a document happened to contain.
Teaching-assignment data comes from registrar/chair imports, because no CV
contains it and Tables 3-1 and 3-2 depend on it.

*Rationale: "do not depend on the CV" is a founding requirement of this project.*

## Principle VIII — Simplicity and Standard Technology

Prefer boring, standard, widely understood technology: Python, Streamlit,
PostgreSQL, Git, Docker. Do not adopt tooling whose scale exceeds the problem
(a college of a few hundred faculty): no Kubernetes, no microservices, no message
queues beyond a simple background worker. Every significant technology choice MUST
be recorded as an Architecture Decision Record (ADR) with its alternatives and
reasoning.

*Rationale: the maintainer is a domain expert, not a software team. The system must
remain understandable — and hand-over-able — to one person plus IT support.*

## Principle IX — Nothing Merges Without Passing Checks

No change enters the main branch unless, in order: (1) the specification it
implements is current; (2) linting and code-quality checks pass (Ruff);
(3) security scans pass (Bandit for code, pip-audit for packages); (4) the
automated tests pass — including the classification **golden dataset** of faculty
cases classified by hand against the guideline. A failing check is a stop, not a
warning.

*Rationale: machines are tireless inspectors; use them before humans have to be.*

## Principle X — Specifications Change Before Code Changes

Specifications are living documents. When a decision changes — a guideline
revision, a policy ruling, a corrected interpretation — the specification is
updated and re-reviewed *first*, and the code change follows. Code that contradicts
a current specification is a defect, even if it "works."

*Rationale: this is the discipline that separates spec-driven development from
documenting whatever the code happened to do.*

---

## Technology Constraints (Summary)

- Language: Python. Interface: Streamlit. Database: PostgreSQL (via Supabase in
  pilot stages; standard PostgreSQL throughout, so hosting can move).
- Rules: a standalone, versioned rule-engine package, independently testable.
- Deployment: free cloud stages for pilots; Docker Compose as the packaging for
  institutional hosting. Version control: Git/GitHub for all code *and* documents.
- AI services sit behind a provider interface and can be swapped (cloud free
  tiers today; a locally hosted model if the institution requires it).

## Development Workflow

For every feature: **Specify → Clarify → Plan → Tasks → Analyze → Implement →
Verify**. The specification and plan are reviewed as documents by the project
owner before implementation begins. Implementation proceeds one task at a time;
Principle IX checks run after each task; each completed task is committed to Git.

## Governance

- This constitution is amended by written proposal, owner approval, and a version
  bump recorded at the top of this file with the date and a one-line summary.
- After any amendment, all active specifications MUST be re-checked for alignment
  (Spec Kit `/speckit.analyze` or an equivalent manual review) before further
  implementation.
- Any specification, plan, or code found to conflict with this constitution is
  defective by definition and is corrected to conform — the constitution is never
  edited retroactively to bless a violation.
