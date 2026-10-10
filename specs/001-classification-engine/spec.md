# Feature Specification: Faculty Classification Engine

**Feature Branch**: `001-classification-engine`
**Created**: October 2, 2026
**Status**: Draft
**Authoritative Input**: "CBPM Faculty Qualifications Definitions, Effective Fall 2026"
(pages FQ-1 to FQ-6) — cited as (FQ-n) throughout. Supporting reference:
AACSB Accreditation Automator Architecture Document v1.2, Sections 5 and 6.
**Governed by**: Project Constitution v1.0 (Principles I, II, V, VI, IX in particular)

---

## Purpose

Given one faculty member's *verified* record, determine their AACSB qualification
category — **SA, PA, SP, IP, or A** — exactly as the CBPM Fall 2026 guideline
defines it, explain the determination in plain language, and state precisely what
is missing when a category is not met. The engine's output feeds classification
snapshots and, downstream, Tables 3-1 and 3-2 (separate specifications).

## User Scenarios & Testing

### User Story 1 — A faculty member knows where they stand (Priority: P1)

A faculty member views their current classification and, for the next higher
category, a specific list of what they still need ("one more quality journal
article; two more intellectual contributions"), computed from their own locked
record — never from an unverified draft.

**Acceptance scenarios**:

1. **Given** a locked record meeting SA exactly at the minimum (2 quality
   peer-reviewed articles + 3 additional intellectual contributions, related
   doctorate), **when** the engine runs, **then** the result is SA with a
   per-category breakdown showing the counts used.
2. **Given** a locked record one article short of SA, **when** the engine runs,
   **then** the result shows SA as *not demonstrated* and the gap list names the
   specific shortfall in plain language.

### User Story 2 — The coordinator gets defensible classifications (Priority: P1)

The accreditation coordinator runs the engine over all locked records for an
academic year and receives one classification per faculty member, each traceable
to its evidence and to the rule version that produced it, suitable for snapshot
locking.

**Acceptance scenarios**:

1. **Given** 25 locked records, **when** the engine runs twice, **then** both
   runs produce identical results (reproducibility, Constitution Principle VI).
2. **Given** a record in Draft or Submitted status, **when** the engine runs,
   **then** that record produces *no official classification* (Principle III).

### User Story 3 — A peer reviewer can re-derive any result (Priority: P1)

An AACSB peer review team member selecting any classification can see: which
rule version decided it, which contributions were counted, which were excluded
and why (e.g., outside the review window, journal quality not evidenced),
and which human approvals stand behind exceptions.

### User Story 4 — Administrator pathways need no manual exceptions (Priority: P2)

Deans, administrators, and chairs are evaluated under the guideline's adjusted
paths, and administrators returning to faculty receive their transition
designation automatically from dates on record (FQ-2).

**Acceptance scenarios**:

1. **Given** a chair with a related doctorate, 1 quality article and 3 additional
   intellectual contributions, **when** the engine runs, **then** SA is met under
   the administrator path (FQ-1).
2. **Given** an administrator with 2 AACSB-sponsored events and only 3 total
   contributions, **when** the engine runs, **then** PA is met under the
   administrator events path (FQ-2).
3. **Given** an administrator whose only engagements are 2 consulting activities
   (not AACSB-sponsored) and 2 total contributions, **when** the engine runs,
   **then** PA is **not** met — the administrator path requires AACSB-sponsored
   events specifically. *(Regression scenario: the 2026 prototype classified
   this case as PA. It must never recur.)*
4. **Given** a doctoral administrator whose return-to-faculty date is 2 years
   before the review date, **when** the engine runs, **then** the result is PA
   with basis "transition designation, year 2 of 3" (FQ-2), regardless of
   contribution counts.

### User Story 5 — A chair sees department gaps early (Priority: P2)

A department chair reviewing the department's not-yet-locked results sees which
members are one or two items short of the next category, in time to act before
the reporting year closes.

### Edge Cases

- A doctorate earned exactly at the boundary of "within the past six years."
- Contributions dated in the earliest month of the six-year window.
- An ongoing role (no end date): counts as in-window, but is flagged for a
  recency confirmation by the faculty member.
- An article in a journal appearing on none of the approved lists and without a
  CCOR approval: MUST NOT count toward the SA article minimum; it may still be
  recorded and shown in the evidence with the reason it was not counted.
- A faculty member meeting several categories: the highest category in the
  order SA → PA → SP → IP is the result; the breakdown still shows all.
- A record whose degree relatedness is marked "unclear": result is
  **provisional**, excluded from official ratios and tables until a human
  resolves the relatedness question.
- Adjunct without a master's degree and without a recorded Dean's approval:
  IP is not demonstrated, and the gap names the missing approval (FQ-4).

## Functional Requirements

### Inputs and eligibility

- **FR-001**: The engine MUST classify only records in Verified or Locked status.
  Draft, Needs Info, and Submitted records produce no official result.
- **FR-002**: The engine MUST evaluate every category for every eligible record
  and report a per-category outcome (met / not demonstrated) with the counts
  behind it — not merely the final label.

### Review window

- **FR-003**: The review period is **six (6) years** for all categories (FQ-1 to
  FQ-4). Only contributions dated within the window count. The exact boundary
  rule (calendar years vs. exact dates) is a rule-configuration setting
  [NEEDS CLARIFICATION: confirm boundary convention with the accreditation
  coordinator and record it in the rule version].

### Degrees and relatedness

- **FR-004**: Doctoral qualification means a doctorate in a discipline related
  to the faculty member's teaching field, with the guideline's exceptions:
  a JD or similar terminal law degree qualifies the holder to teach business
  law / legal environment (FQ-1a, FQ-2a); a graduate degree in taxation, or a
  combination of law and accounting graduate degrees, qualifies the holder to
  teach taxation (FQ-1b, FQ-2b).
- **FR-005**: Relatedness is designated on the record by a human. If relatedness
  is not recorded as established, any classification is provisional (see Edge
  Cases) and the engine MUST say why.

### Scholarly Academics (SA) — FQ-1

- **FR-006**: SA is met if the doctorate was earned within the past six (6)
  years (initial qualification), subject to FR-005.
- **FR-007**: Otherwise SA is met with at least **two (2) articles in quality
  peer-reviewed journals** within the window **and** at least **three (3)
  additional intellectual contributions** from the SA list (FQ-1).
- **FR-008**: For Deans, administrators, and department chairs, the article
  minimum in FR-007 is **one (1)**; the three additional contributions are
  unchanged (FQ-1).
- **FR-009**: An article counts toward the FR-007/FR-008 minimum only if its
  journal's quality is evidenced by an approved ranking — **ABDC, SCImago
  (SJR), ABS, or JCR** — or by a recorded **CCOR approval** (FQ-5). The engine
  MUST record, per article, which basis applied.
- **FR-010**: Articles beyond the minimum count toward the additional
  intellectual contributions, as the FQ-1 list provides.

### Practice Academics (PA) — FQ-2

- **FR-011**: PA is met with a total of **four (4) contributions** within the
  window, of which at least **two (2)** are from the Professional Engagement
  Activities list (FQ-2).
- **FR-012**: Deans, administrators, and chairs may instead meet PA by active
  participation in at least **two (2) AACSB-sponsored events** within the
  window. AACSB-sponsored participation MUST be a distinctly tagged item on
  the record; ordinary professional engagements MUST NOT satisfy this
  requirement.
- **FR-013**: A doctoral-degreed administrator returning to a faculty position
  is designated PA for the first **three (3) transition years** from the
  recorded return-to-faculty date (FQ-2), independent of contribution counts.

### Scholarly Practitioners (SP) — FQ-3

- **FR-014**: SP requires a related master's degree **and** a recorded initial
  qualification of significant and substantive professional experience (FQ-3).
  Counts alone MUST NOT produce SP without that record; the gap list names it.
- **FR-015**: SP is met with **three (3) intellectual contributions** within the
  window, including **one (1) refereed publication (article, book chapter, or
  case)** and at least two further contributions from the SP list (FQ-3).

### Instructional Practitioners (IP) — FQ-4

- **FR-016**: IP requires a related master's degree **and** a recorded initial
  qualification of significant and substantive professional experience (FQ-4).
- **FR-017**: IP is met with at least **three (3) contributions** within the
  window, of which at least **two (2)** are from the Professional Engagement
  Activities list (FQ-4).
- **FR-018**: An adjunct without a master's degree may meet IP only with a
  recorded Dean's approval based on professional experience (FQ-4). Without
  that approval, IP is not demonstrated.

### Additional Faculty (A) — FQ-5

- **FR-019**: If no category above is met, the result is **A**, with the full
  per-category breakdown and gaps still reported.

### Output, precedence, and explanation

- **FR-020**: Categories are evaluated in the order SA, PA, SP, IP; the final
  classification is the highest category met (FR-019 otherwise).
- **FR-021**: Every result MUST include: the final classification; the
  per-category outcomes with counted and required numbers; a plain-language
  basis statement citeable to the guideline (e.g., "SA met under FQ-1: 2 quality
  articles + 3 additional contributions"); and, for each category not met, a
  gap list of specific, actionable missing items.
- **FR-022**: Items excluded from counting MUST be listed with the reason
  (outside window; quality not evidenced; wrong list for the category;
  duplicate under the mapping table).

### Rules as configuration (Constitution Principle I)

- **FR-023**: All thresholds, windows, and contribution lists MUST come from a
  versioned rule configuration that also contains the **mapping table**
  (guideline list item → contribution type) per category. A guideline revision
  creates a new rule version; classification code does not change.
- **FR-024**: Every result MUST record the identifier of the rule version that
  produced it, and re-running the engine on the same locked snapshot with the
  same rule version MUST reproduce the identical result.

## Key Entities (conceptual)

- **Faculty Record** — degrees, role flags (administrator, chair, adjunct),
  administrator history and return-to-faculty date, relatedness designations.
- **Contribution** — one item from the guideline's lists, typed via the mapping
  table, dated, with evidence links; AACSB-sponsored events distinctly tagged.
- **Journal Quality Evidence** — the ranking (ABDC / SJR / ABS / JCR) or CCOR
  approval standing behind an article.
- **CCOR Approval** — journal, requester, documentation, decision, date (FQ-5).
- **Initial Qualification Record** — the significant professional experience
  standing behind SP/IP (FQ-3, FQ-4), attested at qualification time.
- **Classification Result** — final category, per-category outcomes, basis,
  gaps, exclusions, rule version, provisional flag.
- **Rule Version** — dated configuration: window, thresholds, lists, mapping
  table, boundary conventions.

## Success Criteria

- **SC-001**: On the golden dataset of at least 25 faculty cases hand-classified
  against the guideline, the engine agrees with the hand classification in
  **100%** of cases — including the administrator-events regression case
  (User Story 4, scenario 3).
- **SC-002**: 100% of results are reproducible from snapshot + rule version.
- **SC-003**: 100% of "not demonstrated" outcomes ship with at least one
  specific, actionable gap item.
- **SC-004**: 0 official classifications are ever produced from non-locked
  records (audited across all runs).
- **SC-005**: Every SA result's counted articles carry a recorded quality basis
  (ranking or CCOR approval) in 100% of cases.

## Assumptions and Dependencies

- Verified faculty records, contribution typing, and journal reference data
  (ABDC, SCImago, ABS, JCR lists, refreshed yearly) exist — provided by the
  data-capture and verification features (separate specifications).
- The guideline-to-type mapping table is maintained as part of each rule
  version; known ambiguity it must resolve: organizational leadership appears
  in the guideline's intellectual-contribution lists while association
  participation appears in the professional-engagement lists.
- Whether an AACSB-sponsored event attended by a *non-administrator* also counts
  as a professional-engagement item is governed by the FQ-2 list wording
  ("participation in professional events…") and the mapping table
  [NEEDS CLARIFICATION: confirm with the coordinator; record in mapping table].
- **Out of scope for this specification**: CV extraction; data-capture screens
  and the completeness loop; external verification against Crossref/OpenAlex;
  Table 3-1 / Table 3-2 computation and the 40% / 90% / 75% ratio checks
  (reporting specification, which consumes this engine's results);
  participating vs. supporting designation workflow (FQ-6; teaching/reporting
  specification).
