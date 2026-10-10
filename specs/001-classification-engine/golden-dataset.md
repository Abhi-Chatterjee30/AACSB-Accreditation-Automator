# Faculty classification

## Case 001 — Adjunct, management/marketing, deep industry career, undated resume

**Source:** Real colleague resume, anonymized. Hand-classified 2026-10-02.
**Why this case exists:** It tests the project's core design principle — the system must NOT depend on the CV alone. This resume is experience-rich but evidence-poor: it contains **no dates at all**, so the six-year window cannot be applied to a single item. The correct behavior is "not demonstrated + specific questions," not a confident classification.

### Facts as encoded (exactly what the resume supports — nothing added)

| Field | Value |
|---|---|
| Role | Adjunct Professor (part-time) |
| Teaching fields | Global/International Management, Organizational Management, International Marketing, Small Business Management (undergraduate) |
| Doctorate | None |
| Master's | M.A.L.S. — interdisciplinary (Economics, Psychology, Sociology, Political Science). Relatedness to management/marketing teaching: **not designated** (human decision pending) |
| Other degrees | B.S. Management Science; associate degrees. One further credential listed by abbreviation only ("P.B.M. — Economics"), level unclear |
| Professional experience | 47+ years; senior global business leadership role (operations, marketing/promotion, corporate communications, team of five, corporate training design) at a large multinational. **No start or end dates given** |
| Publications (any date) | **None listed** |
| Presentations (any date) | **None listed** |
| Certifications | Six Sigma Green Belt; Lean Thinking. **No dates** |
| Association / leadership items (all **undated**) | President of a professional exhibitors association; exhibit committee member for two national associations; member of a networking professionals association; vice president of a university part-time student council (historical) |
| Board-type service (undated) | Municipal planning official / board of adjustments commissioner (relevance to business teaching not established) |
| Student engagement | Mentors students on internships, contracts, and career decisions (undated, presented as current role activity) |

### Expected evaluation, category by category

**SA (FQ-1) — Not demonstrated.**
No doctorate. No JD/terminal law degree, no taxation graduate degree, so no exception applies.

**PA (FQ-2) — Not demonstrated.**
No doctorate. No exception applies.

**SP (FQ-3) — Not demonstrated.**
- Significant and substantive professional experience: **met on substance** (47+ years, senior global role).
- Related master's: not designated.
- Decisive failure: SP requires **one refereed publication (article / book chapter / case)** plus two further intellectual contributions within six years. The resume lists **zero publications at any date**, and zero dated intellectual contributions. SP cannot be met on this evidence, regardless of the window question.

**IP (FQ-4) — Not demonstrated on current evidence. This is the person's realistic path.**
- Significant and substantive professional experience: **met on substance**.
- Contribution test **cannot yet be passed**: IP requires at least 3 contributions within six years, at least 2 from the Professional Engagement list. Candidate items exist — Six Sigma Green Belt certification (the IP list names Six Sigma explicitly), professional association participation and leadership, sustained professional work — but **every one is undated**, so none can be counted yet.
- Degree test unresolved, with two possible routes: (a) the master's is designated related to the teaching field by the chair/coordinator; or (b) the FQ-4 adjunct exception — depth, duration, sophistication, and complexity of experience (47+ years, senior global role) outweighing the degree question, **subject to a recorded Dean approval**, which does not exist in the resume.

**A (FQ-5) — Expected final category on the evidence in the resume.**
FQ-5 applies to faculty who do not meet any of the four categories. As *demonstrated*, that is the case here.

### Expected system behavior for this case

- **Final output:** A — with record status **Needs Info**, NOT a locked A. The distinction matters: this is "not yet demonstrated," with a documented path to IP.
- **The engine must produce these follow-up questions** (completeness checker):
  1. Dates for the industry career: when did the senior role end? Any professional activity within the past six years (consulting, board work, association work)?
  2. Six Sigma Green Belt: year obtained, and is it maintained/current?
  3. Association presidency and exhibit committee service: which years? Any within the past six years?
  4. Any publications, book chapters, cases, or presentations in the past six years that are not on this resume? (A "yes" with a refereed item reopens the SP evaluation.)
  5. Credential listed as "P.B.M.": what is this credential and its level?
- **Human decisions this case requires (software must request, never make):**
  1. Chair/coordinator designation: is the interdisciplinary master's (with Economics) related to management/marketing teaching?
  2. If route (b) is used instead: Dean approval under the FQ-4 adjunct exception, recorded with date.
- **Participating vs. supporting (FQ-6):** Not decided by this case. The resume shows one candidate basis activity (mentoring students on internships and careers, beyond teaching). A participating designation, if made, must be recorded separately with its basis activity.

### What this case proves if the engine passes it

- The engine does not award IP on undated evidence, however strong the career looks.
- The engine does not award SP without a refereed publication.
- The engine returns A as *Needs Info* with the five specific questions above — it asks for what the CV is missing instead of guessing.

---

## Cases 002–025 — Invented cases

**Drafted 2026-10-06, pending owner review and sign-off.** Each case was worked out by hand from FQ-1 to FQ-6. Dates use clear margins — contributions dated 2021 or later are inside the six-year window, 2019 or earlier are outside it — so no case depends on the still-open boundary question (calendar years vs. exact dates, Spec FR-003). Boundary-exact cases will be added when the accreditation coordinator settles that question.

---

## Case 002 — Clean SA, standard path

**Source:** Invented. **Tests:** SA standard path (FQ-1); journal quality recorded per article (FR-009).

### Facts

- Role: full-time faculty. Teaching field: Management.
- Doctorate: PhD in Management, 2015. Relatedness: **designated related** by the chair.
- Peer-reviewed journal articles in window: 2022, journal on the ABDC list (rating A) — quality basis recorded; 2024, journal ranked SJR Q1 — quality basis recorded.
- Additional intellectual contributions in window: peer-reviewed conference proceeding paper (2023); editorial board member of a relevant journal (2024); mentor for a student research project (2025).

### Expected

- **SA — Met.** Related doctorate + 2 quality PRJs in window + 3 additional ICs.
- **PA / SP / IP — Not demonstrated** (not needed; precedence applies — and on these facts PA also fails: 0 professional engagements).
- **Final: SA.** Basis must cite the two quality bases (ABDC, SJR) individually, per FR-009 / SC-005.

---

## Case 003 — SA fails on journal quality alone

**Source:** Invented. **Tests:** journal quality is classification-critical (FR-009); an off-list journal without CCOR approval must not count toward the SA minimum; PA professional-engagement minimum.

### Facts

- Role: full-time faculty. Teaching field: Finance.
- Doctorate: PhD in Finance, 2014. Relatedness: **designated related**.
- Peer-reviewed journal articles in window: 2022 and 2023 — both journals appear on **none** of the ABDC, SJR, ABS, or JCR lists, and **no CCOR approval** is recorded for either.
- Additional intellectual contributions in window: conference presentation (2022); published book chapter (2023); documented journal reviewer (2024).
- Professional engagements in window: none.

### Expected

- **SA — Not demonstrated.** Two PRJs exist, but neither carries a quality basis, so neither counts toward the SA minimum. Gap: quality evidence or a recorded CCOR approval for each journal — either one flips this case to SA.
- **PA — Not demonstrated.** Countable contributions total 5 (2 PRJs + 3 ICs count on the PA intellectual list, where journal quality is not the test), but professional engagements = 0 of the required 2.
- **SP / IP — Not demonstrated** (no master's-based path in the case facts).
- **Final: A.** The engine must name the missing quality basis as the SA gap — not report a bare failure.

---

## Case 004 — SA automatically: doctorate within the past six years

**Source:** Invented. **Tests:** recent-doctorate SA (FQ-1).

### Facts

- Role: full-time faculty, hired 2025. Teaching field: Marketing.
- Doctorate: PhD in Marketing, 2025. Relatedness: **designated related**.
- Contributions in window: none yet.

### Expected

- **SA — Met, automatically.** FQ-1: a doctorate earned within the past six years qualifies as SA to allow time to build a research portfolio. Zero contributions do not block this.
- **Final: SA.** Basis recorded as "recent doctorate (2025)" — so a future reviewer can see the qualification expires into the normal maintenance test six years after the degree.

---

## Case 005 — Doctorate just outside the automatic window, empty portfolio

**Source:** Invented. **Tests:** the automatic SA of Case 004 expires; companion case to 004.

### Facts

- Role: full-time faculty. Teaching field: Management.
- Doctorate: PhD in Management, 2019 — seven years before the Fall 2026 review.
- Contributions in window: none.

### Expected

- **SA — Not demonstrated.** The degree is outside the past six years, so the automatic path no longer applies, and the maintenance test (2 quality PRJs + 3 ICs) is unmet at zero.
- **PA — Not demonstrated** (0 of 4 contributions). **SP / IP — Not demonstrated** (no master's-based path in the case facts).
- **Final: A.**

---

## Case 006 — SA through the JD exception (business law)

**Source:** Invented. **Tests:** FQ-1 exception (a) — JD qualifies for SA to teach business law / legal environment, with the normal maintenance standards.

### Facts

- Role: full-time faculty. Teaching fields: Business Law, Legal Environment of Business.
- Degree: JD, 2012. No research doctorate.
- Peer-reviewed journal articles in window: 2021 (ABS-listed journal, quality basis recorded); 2024 (JCR-listed journal, quality basis recorded).
- Additional intellectual contributions in window: keynote panelist at an academic event (2022); editorial board member (2023); published case study in an editorially reviewed book (2025).

### Expected

- **SA — Met, via the JD exception.** The exception replaces the doctorate requirement for this teaching field only; the maintenance counts (2 quality PRJs + 3 ICs) are met in full.
- **Final: SA.** Basis must record that the exception was used, and the teaching field it is tied to.

---

## Case 007 — JD exception does not travel to another teaching field

**Source:** Invented. **Tests:** the JD exception is field-bound; companion trap to Case 006.

### Facts

- Role: full-time faculty. Teaching field: **Marketing**.
- Degree: JD, 2012. No doctorate in a field related to marketing.
- Record identical in strength to Case 006: 2 quality PRJs in window (quality bases recorded) + 3 additional ICs in window.

### Expected

- **SA — Not demonstrated.** FQ-1 exception (a) covers JD holders teaching business law and the legal environment of business. It does not extend to marketing, and no related doctorate is present.
- **PA — Not demonstrated** (same exception limit, FQ-2). **SP / IP — Not demonstrated** (a JD is not a related master's for this teaching field on these facts).
- **Final: A.** The engine's basis must state *why* the exception does not apply — a strong publication record must not pull this case into SA.

---

## Case 008 — SA through the taxation exception (no doctorate)

**Source:** Invented. **Tests:** FQ-1 exception (b) — graduate degree in taxation qualifies for SA to teach taxation, with the normal maintenance standards.

### Facts

- Role: full-time faculty. Teaching field: Taxation.
- Degree: M.S. in Taxation, 2016. No doctorate.
- Peer-reviewed journal articles in window: 2022 (ABDC-listed, rating B — quality basis recorded); 2025 (SJR Q2 journal — quality basis recorded).
- Additional intellectual contributions in window: peer-reviewed conference paper (2023); article in an editorially reviewed professional publication (2024); academic research grant received (2025).

### Expected

- **SA — Met, via the taxation exception.**
- **Final: SA.** Basis records the exception and the taxation teaching field.

---

## Case 009 — SA through the administrator reduced path

**Source:** Invented. **Tests:** FQ-1 administrator path — Deans, administrators, and chairs with a related doctorate maintain SA with 1 quality PRJ + 3 additional ICs.

### Facts

- Role: Department Chair. Teaching field: Accounting.
- Doctorate: PhD in Accounting, 2010. Relatedness: **designated related**. Administrator status: current chair.
- Peer-reviewed journal articles in window: 1 — 2023, ABDC-listed (rating A), quality basis recorded.
- Additional intellectual contributions in window: article in an editorially reviewed academic journal (2022); leadership position in an academic organization (2024); new course developed (2025).

### Expected

- **SA — Met, via the administrator path** (1 quality PRJ + 3 ICs). The standard path would fail at 1 PRJ; the engine must apply the administrator threshold because the role and doctorate are on record.
- **Final: SA.** Basis records the administrator path.


---

## Case 010 — Administrator: SA fails by one contribution, PA met through AACSB events (cascade)

**Source:** Invented. **Tests:** category cascade — when SA fails, PA is evaluated on its own paths, including the administrator AACSB-events path (FQ-2, FR-012).

### Facts

- Role: Dean. Teaching field: Finance.
- Doctorate: PhD in Finance, 2011. Relatedness: **designated related**. Administrator status: current dean.
- Peer-reviewed journal articles in window: 1 — 2024, quality basis recorded.
- Additional intellectual contributions in window: only 2 — panelist at an academic event (2023); documented journal reviewer (2025).
- AACSB-sponsored events in window: 2, distinctly tagged as AACSB-sponsored — AACSB conference (2024); AACSB seminar (2025).

### Expected

- **SA — Not demonstrated.** The administrator path requires 1 quality PRJ + **3** additional ICs; only 2 ICs are present.
- **PA — Met, via the administrator path:** 2 AACSB-sponsored events within the window (FQ-2).
- **Final: PA.** This case proves the engine does not stop at the first failure, and that the AACSB-events path uses only events tagged AACSB-sponsored.

---

## Case 011 — Clean PA, standard path

**Source:** Invented. **Tests:** PA standard path (FQ-2) — 4 total contributions including at least 2 professional engagements; SA fails first on article count.

### Facts

- Role: full-time faculty (not an administrator). Teaching field: Operations Management.
- Doctorate: PhD in Operations Management, 2016. Relatedness: **designated related**.
- Contributions in window: peer-reviewed journal article (2023); peer-reviewed conference proceeding paper (2022); consulting engagement, material in time and substance (2024) — professional engagement; active service on a corporate board of directors (2023–2026) — professional engagement.

### Expected

- **SA — Not demonstrated.** Only 1 PRJ; the standard path requires 2 quality PRJs + 3 additional ICs.
- **PA — Met.** Total contributions = 4, of which 2 are professional engagements.
- **Final: PA.**

---

## Case 012 — The administrator trap (permanent regression case)

**Source:** Invented to encode Spec User Story 4, Scenario 3 — the 2026 prototype classified this profile as PA. **Tests:** ordinary professional engagements must NOT satisfy the administrator AACSB-events path (FR-012).

### Facts

- Role: Associate Dean (administrator). Teaching field: Management.
- Doctorate: PhD in Management, 2013. Relatedness: **designated related**.
- Contributions in window: consulting engagement (2023); consulting engagement (2025). **Total: 2.**
- AACSB-sponsored events in window: **0.**

### Expected

- **SA — Not demonstrated** (0 PRJs).
- **PA — Not demonstrated, on both paths.** Administrator path: requires 2 **AACSB-sponsored** events; consulting engagements are not AACSB-sponsored events, so the count is 0 of 2. Standard path: requires 4 total contributions; only 2 are present.
- **SP / IP — Not demonstrated** (no master's-based path in the case facts).
- **Final: A,** status Needs Info. Gaps must state both routes out: participate in 2 AACSB-sponsored events, or reach 4 total contributions including 2 professional engagements (already met on type, short on total).
- **If the engine ever returns PA for this case, the build has regressed to the prototype's bug. This case never leaves the dataset.**

---

## Case 013 — PA through the administrator AACSB-events path alone

**Source:** Invented. **Tests:** FQ-2 administrator path stands on its own — 2 AACSB-sponsored events within the window, for an administrator holding a related doctorate.

### Facts

- Role: Department Chair (administrator). Teaching field: Marketing.
- Doctorate: PhD in Marketing, 2012. Relatedness: **designated related**.
- AACSB-sponsored events in window: AACSB annual conference (2023); AACSB seminar (2025) — both tagged AACSB-sponsored.
- Other contributions in window: 1 — panelist at an academic event (2024).
- Peer-reviewed journal articles in window: none.

### Expected

- **SA — Not demonstrated** (0 PRJs; administrator SA path still requires 1 quality PRJ + 3 ICs).
- **PA — Met, via the administrator path.** FQ-2 sets the events requirement for administrators without an additional contribution total; the engine must not import the standard path's 4-total test into this path.
- **Final: PA.**

---

## Case 014 — PA by transition designation (administrator returned to faculty)

**Source:** Invented. **Tests:** FQ-2 — doctoral administrators returning to faculty are designated PA during their first three transition years (FR-013).

### Facts

- Role: full-time faculty; formerly Dean. Teaching field: Economics.
- Doctorate: PhD in Economics, 2009. Relatedness: **designated related**.
- Administrator history: served as Dean; **returned to a faculty position in 2024** — two years before the Fall 2026 review.
- Contributions in window: none since returning.

### Expected

- **PA — Met, by transition designation.** 2024 falls within the first three transition years (2024–2027). The designation applies regardless of the empty contribution record.
- **SA — Not demonstrated** (no PRJs or ICs).
- **Final: PA.** Basis must record "transition designation, from return-to-faculty date 2024," including its expiry — a designation without an end date would silently become permanent.

---

## Case 015 — Transition designation expired

**Source:** Invented. **Tests:** the three-year limit on the transition designation; companion case to 014.

### Facts

- Role: full-time faculty; formerly an administrator. Teaching field: Economics.
- Doctorate: PhD in Economics, 2008. Relatedness: **designated related**.
- Administrator history: **returned to a faculty position in 2021** — five years before the Fall 2026 review.
- Contributions in window: none.

### Expected

- **PA — Not demonstrated.** The transition designation covered the first three years after return (2021–2024) and has expired; the standard PA test is unmet at 0 contributions.
- **SA — Not demonstrated. SP / IP — Not demonstrated** (no master's-based path in the case facts).
- **Final: A.**

---

## Case 016 — Clean SP

**Source:** Invented. **Tests:** SP met in full (FQ-3) — related master's, documented significant experience, 3 intellectual contributions including 1 refereed item.

### Facts

- Role: full-time faculty. Teaching field: Finance.
- Master's: M.S. in Finance, 2015. Relatedness: **designated related**.
- Initial qualification record: **documented** — 12 years in senior banking roles before joining the faculty, recorded as significant and substantive professional experience.
- Intellectual contributions in window: refereed book chapter (2023) — the refereed item; peer-reviewed conference proceeding paper (2024); article in an editorially reviewed academic journal (2025).

### Expected

- **SA / PA — Not demonstrated** (no doctorate).
- **SP — Met.** 3 ICs in window, including 1 refereed publication, on top of the documented experience record.
- **Final: SP.**

---

## Case 017 — SP fails on the refereed requirement; IP fails on the engagement count

**Source:** Invented. **Tests:** FQ-3's refereed item is mandatory for SP, not interchangeable with other ICs; FQ-4's 2-professional-engagement minimum applies to IP independently.

### Facts

- Role: full-time faculty. Teaching field: Management.
- Master's: M.S. in Management, 2014. Relatedness: **designated related**.
- Initial qualification record: **documented** — 15 years of professional experience.
- Intellectual contributions in window: invited conference presentation (2022); published open educational resources (2024); new course developed (2025). **None is a refereed publication.**
- Professional engagements in window: 1 — professional certification obtained (2023).

### Expected

- **SP — Not demonstrated.** 3 ICs are present, but SP requires one of them to be a refereed article, book chapter, or case. Count alone does not pass.
- **IP — Not demonstrated.** Total contributions = 4, but professional engagements = 1 of the required 2.
- **Final: A.** Gaps must offer both routes: one refereed publication flips SP; one more professional engagement flips IP.


---

## Case 018 — SP blocked: no initial-qualification experience record

**Source:** Invented. **Tests:** SP cannot be awarded on contributions alone — the documented record of significant and substantive professional experience must exist first (FR-014). Companion to Case 001, where the experience existed but the dates did not.

### Facts

- Role: full-time faculty. Teaching field: Marketing.
- Master's: M.S. in Marketing, 2016. Relatedness: **designated related**.
- Initial qualification record: **none on file.** The person's professional history before academia is not documented anywhere in the record.
- Intellectual contributions in window: refereed journal article (2024); peer-reviewed conference paper (2023); mentor for a student research project (2025).

### Expected

- **SP — Not demonstrated.** The contribution test is fully met (3 ICs including a refereed article), but SP status *applies to* faculty with significant and substantive professional experience; with no experience record, the category cannot be awarded.
- **Final: A,** status Needs Info. Single gap: create the initial-qualification experience record (employer history, roles, depth, duration, with the coordinator's assessment). Once recorded, this case flips to SP with no other change.
- The engine must not infer experience from the contribution list, from seniority, or from years of teaching.

---

## Case 019 — Clean IP

**Source:** Invented. **Tests:** IP met in full (FQ-4) — related master's, documented experience, 3 contributions including at least 2 professional engagements.

### Facts

- Role: full-time faculty. Teaching field: Management.
- Master's: M.B.A. (Management), 2013. Relatedness: **designated related**.
- Initial qualification record: **documented** — 18 years in operations management.
- Contributions in window: consulting engagement, material in time and substance (2024) — professional engagement; professional certification maintained (PMP, 2025) — professional engagement; leadership position in a professional organization (2023).

### Expected

- **SA / PA — Not demonstrated** (no doctorate). **SP — Not demonstrated** (no refereed publication among the contributions).
- **IP — Met.** 3 contributions in window, 2 of them professional engagements, on a documented experience record.
- **Final: IP.**

---

## Case 020 — IP through the adjunct exception, Dean approval recorded

**Source:** Invented. **Tests:** FQ-4 adjunct exception — IP without a master's where the depth, duration, sophistication, and complexity of professional experience outweigh the missing degree, **subject to Dean approval**.

### Facts

- Role: Adjunct Professor. Teaching field: Management.
- Master's: **none.** Highest degree: bachelor's, 1998.
- Professional experience: 25 years as a senior executive, documented in an initial qualification record.
- Dean approval under the adjunct exception: **recorded, dated 2025.**
- Contributions in window: executive education program developed and presented (2024) — professional engagement; active service on a board of directors (2023–2026) — professional engagement; professional presentation at a practice-focused event (2025) — professional engagement.

### Expected

- **IP — Met, via the adjunct exception.** Contribution test passed (3, all professional engagements); the degree gap is covered by the documented experience and the recorded Dean approval.
- **SA / PA / SP — Not demonstrated.**
- **Final: IP.** Basis must record the exception and the Dean approval date.

---

## Case 021 — Adjunct exception claimed, Dean approval missing

**Source:** Invented. **Tests:** the Dean approval is a required record, not a formality the engine may assume; companion case to 020.

### Facts

- Role: Adjunct Professor. Teaching field: Management.
- Master's: **none.**
- Professional experience: 20 years in senior roles, documented.
- Dean approval under the adjunct exception: **not recorded.**
- Contributions in window: consulting engagement (2024) — professional engagement; significant participation in a business professional association (2025) — professional engagement; judge for a student event (2024).

### Expected

- **IP — Not demonstrated.** Every element is present except the Dean approval; without that record the exception does not apply.
- **Final: A,** status Needs Info. Single gap: the Dean's approval decision, recorded with a date. The engine requests the decision — it does not make it, predict it, or treat the strength of the experience as a substitute for it.

---

## Case 022 — The window removes the qualifying article

**Source:** Invented. **Tests:** the six-year window applies before counting (FQ-1, FR-003) — strong old work does not count.

### Facts

- Role: full-time faculty. Teaching field: Accounting.
- Doctorate: PhD in Accounting, 2013. Relatedness: **designated related**.
- Peer-reviewed journal articles: 2019 — quality basis recorded, but **seven years before** the Fall 2026 review (outside the window); 2023 — quality basis recorded (inside the window).
- Other contributions inside the window: 1 additional IC (conference paper, 2024); 1 professional engagement (consulting, 2025).
- Contributions outside the window: several, none countable.

### Expected

- **SA — Not demonstrated.** Only 1 quality PRJ falls inside the window; the 2019 article cannot be counted, however good it is.
- **PA — Not demonstrated.** Countable (in-window) total = 1 PRJ + 1 IC + 1 PE = 3 of the required 4.
- **Final: A.** The basis must show the 2019 article as *excluded — outside the review window*, with its date, not silently dropped: the faculty member is entitled to see what was excluded and why (FR-022).

---

## Case 023 — Relatedness unclear: no category, human decision required

**Source:** Invented. **Tests:** relatedness is a human designation (Spec edge case) — an undesignated record stays provisional and is excluded from ratio calculations until a human decides.

### Facts

- Role: full-time faculty. Teaching field: Marketing.
- Doctorate: PhD in Chemistry, 2014.
- Record on counts alone: 2 quality PRJs in window (2022, 2024 — quality bases recorded, journals in the marketing field); 3 additional ICs in window.
- Relatedness designation: **not recorded** — the doctorate field and the teaching field differ, and no chair/coordinator decision exists.

### Expected

- **No category is awarded.** The counts would meet SA *if* the degree were designated related, but the engine does not decide relatedness — not from the degree title, and not from the publication fields.
- **Final output: Undetermined — Needs Human Decision,** with the record flagged provisional and **excluded from Tables 3-1 / 3-2 and the 40 / 90 ratios** until the designation is recorded.
- The referral must show the human decision-maker the full counts, so the decision is quick: designate related (case becomes SA) or not related (case becomes A).

---

## Case 024 — Precedence: SA and PA both met, SA wins

**Source:** Invented. **Tests:** highest met category wins, SA → PA → SP → IP (FR-020); the basis reports the highest category, not every met category.

### Facts

- Role: full-time faculty. Teaching field: Management.
- Doctorate: PhD in Management, 2012. Relatedness: **designated related**.
- Peer-reviewed journal articles in window: 2, both quality (bases recorded, 2021 and 2025).
- Additional intellectual contributions in window: 3 (2022, 2023, 2024).
- Professional engagements in window: 2 (consulting, 2024; board service, 2025).

### Expected

- **SA — Met** (2 quality PRJs + 3 ICs). **PA — also met** on its own test (7 total contributions including 2 professional engagements).
- **Final: SA.** The classification, the snapshot, and the ratio counts record SA only. Reporting PA anywhere for this person double-counts them in Table 3-1.

---

## Case 025 — PA fails on the mix: total is enough, engagements are not

**Source:** Invented. **Tests:** FQ-2's two PA conditions are independent — 4 total contributions AND at least 2 professional engagements. Companion trap to Case 011.

### Facts

- Role: full-time faculty (not an administrator). Teaching field: Finance.
- Doctorate: PhD in Finance, 2015. Relatedness: **designated related**.
- Contributions in window: 1 quality PRJ (2022); article in an editorially reviewed journal (2023); peer-reviewed conference paper (2024); professional certification obtained (2023) — the **only** professional engagement.
- Additional intellectual contributions in window: as listed — total contributions = 4.

### Expected

- **SA — Not demonstrated** (only 1 quality PRJ, and fewer than 3 additional ICs).
- **PA — Not demonstrated.** Total = 4 passes the count test, but professional engagements = 1 of the required 2. The two conditions do not trade off against each other.
- **Final: A.** Single gap: one more professional engagement inside the window flips this case to PA.

