# Spec Kit Starter — AACSB Accreditation Automator

Two documents, drafted October 2, 2026, that put this project on the
spec-driven approach (GitHub Spec Kit structure). They are plain Markdown —
no tool needs to be installed to use them.

## What's here and where it goes in the repository

| File in this starter | Repository location | What it is |
|---|---|---|
| `.specify/memory/constitution.md` | *same path* | The project's non-negotiable principles (v1.0). Every future spec, plan, and task is checked against it. |
| `specs/001-classification-engine/spec.md` | *same path* | The first feature specification: the SA/PA/SP/IP/A classification engine, sourced line-by-line from the CBPM Fall 2026 guideline (FQ-1 to FQ-6). |

Copy both into the project repository **keeping the folder paths exactly** —
Spec Kit (and any AI agent) looks for them in those places.

## How to work with them in Antigravity

1. Open the repository in Antigravity.
2. At the start of a build session, instruct the agent:
   *"Read `.specify/memory/constitution.md` and
   `specs/001-classification-engine/spec.md`. Propose a `plan.md` for this
   feature in the same folder, consistent with the Architecture Document
   v1.2. Do not write code yet."*
3. Review the plan as a document. Then ask for `tasks.md` (small, ordered
   tasks). Review again.
4. Have the agent implement **one task at a time**. After each task: run the
   checks (Ruff, Bandit, pip-audit, tests), then commit to Git.
5. Before the classification engine is considered done, run the golden
   dataset (SC-001): at least 25 faculty cases classified by hand against
   the guideline must match the engine 100% — including the administrator
   regression case written into the spec (User Story 4, scenario 3).

Optional: the official Spec Kit CLI (`specify init`) can generate this same
scaffolding automatically and adds slash commands (`/speckit.specify`,
`/speckit.plan`, `/speckit.tasks`, `/speckit.analyze`). Installing it is a
convenience, not a requirement — these files already follow its format.

## Open items inside the spec (need human decisions)

The spec deliberately flags three `[NEEDS CLARIFICATION]` points rather
than guessing — resolve them with the accreditation coordinator and record
the answers in the rule version / mapping table:

1. The six-year window boundary: calendar years or exact dates?
2. Whether AACSB-sponsored events attended by non-administrators also
   count as professional-engagement items.
3. (Resolved by the mapping table as it is built: which list each
   guideline item counts toward, per category.)

## Suggested order of the remaining specifications

1. `002-data-capture-and-completeness` — forms, CV onboarding, the
   ask-for-what's-missing loop, attestation.
2. `003-verification` — Crossref/OpenAlex checks, journal quality, CCOR
   workflow, link checking.
3. `004-teaching-and-reporting` — registrar imports, participating
   designations (FQ-6), Tables 3-1 and 3-2, the 40/90/75 checks.

The Architecture Document v1.2 remains the plan-level reference for all of
them.
