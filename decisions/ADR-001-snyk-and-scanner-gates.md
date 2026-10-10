# ADR-001 — Snyk: optional extra check, not a required gate

**Status:** Proposed — needs Abhi's approval before it counts as a decision
**Date:** October 6, 2026
**Governed by:** Constitution v1.0, Principle IV (Free and Open-Source Only),
Principle VIII (record significant technology choices as an ADR),
Principle IX (Nothing Merges Without Passing Checks)

## The one-picture version

There is one inspection station before code can merge. The required
inspectors work locally, are open-source, and have no usage cap.
Snyk may stand next to them as an extra pair of eyes, but the line
must never stop because Snyk is absent, capped, or withdrawn.

## What was considered

Abhi found Snyk Code (snyk.io/lp/snyk-code-checker/) on October 6, 2026
and asked where it fits. Snyk Code scans your own code for security
flaws and offers fix advice in the editor — the same job as the code
security scanners already discussed for this project.

Why it cannot be a required gate:

1. **It is a commercial product with a free tier, not open-source.**
   Principle IV requires free *and* open-source, replaceable forever.
   Snyk's own documentation puts the free plan at 100 Snyk Code tests
   per billing period, and those limits apply to private projects —
   this repository will be private.
2. **The scan runs on Snyk's cloud.** The code contains no faculty
   data, so this is not a data-exposure problem under Principle V,
   but it is one more external account the project would depend on.
3. **A capped gate can block the project.** If the monthly test
   allowance runs out, a required Snyk check would stop merges for a
   reason that has nothing to do with the code.

## Discrepancy found while drafting this ADR — needs one decision

The documents and the October 6 chat answer do not name the same
required stack:

- **Constitution Principle IX and the starter-kit README** list the
  required checks as: Ruff (quality), Bandit (code security),
  pip-audit (packages), plus the automated tests / golden dataset.
- **The October 6 answer about Snyk** described the required gates as
  "Bandit + Semgrep" for code security.

Semgrep (open-source, runs locally) appears in the earlier scanner
explanation but was never written into Principle IX. Pick one and
make the documents match:

- **Option A — Keep the gate as written:** Bandit only. Semgrep is,
  like Snyk, an optional extra. No constitution change needed.
- **Option B — Add Semgrep to the gate:** amend Principle IX to list
  Bandit + Semgrep for code security, with a version bump and date
  recorded at the top of the constitution, per its Governance section.

## Proposed decision

1. Required merge gates stay local, open-source, and uncapped.
2. Snyk's free tier MAY be run in Antigravity during development as
   an optional extra check. Its findings are advisory; its absence,
   failure, or cap never blocks a merge.
3. No Snyk account, token, or configuration is committed to the
   repository, and the project plan never lists Snyk as a dependency.
4. Abhi chooses Option A or B above; the losing document (chat summary
   or constitution) is then corrected so there is one stack, stated
   one way, everywhere.

## Cost check (required by Principle IV)

- At $0/month, forever: the required gates (Ruff, Bandit, pip-audit,
  and Semgrep if Option B is chosen) cost nothing and cannot be
  withdrawn. Snyk at $0 is capped at 100 Code tests per period.
- If Snyk's free tier disappears: nothing in the pipeline breaks,
  because nothing depends on it. That is the point of this decision.
