# Golden Dataset — Review Guide (for Abhi's sign-off)

**Purpose:** Make the 25-case review one sitting, not twenty-five separate decisions.
**The dataset itself:** `golden-dataset.md` in this same folder. This guide does not change any expected answer — it only tells you where to look closely and where a quick pass is enough.
**How to use it:** For each case, read only the **Expected** line in the dataset. Mark Agree or Flag below. When you are done, your sign-off (last section) makes the dataset the binding answer key (SC-001).

---

## 1. The three cases that need your closest eye

These are the only cases where the expected answer rests on a *reading* of FQ-1 to FQ-6, not on simple counting. If you disagree with any of these three readings, flag that case — the others do not depend on it except where noted.

**Case 013 — PA through AACSB events alone**
- Reading used: FQ-2 gives administrators a PA path of 2 AACSB-sponsored events in the window, with **no extra contribution total added**. The case has those 2 events + 1 other contribution, and the answer is PA.
- If you read FQ-2 as also requiring the standard 4-total, this answer flips to A — and **Case 010** (Dean who lands on PA through the same events path) flips with it.
- ☐ Agree  ☐ Flag

**Case 003 — Articles count differently for SA and for PA**
- Reading used: a journal article with **no quality basis** (not on ABDC / SJR / ABS / JCR, no CCOR approval) does **not** count toward SA's 2 quality articles — but the same article **does** count on PA's contribution list, where journal quality is not the test. Answer is still A, because PA fails separately on 0 of 2 professional engagements.
- If you read quality as required for PA counting too, the final answer (A) does not change, but the stated PA total (5) would be wrong.
- ☐ Agree  ☐ Flag

**Case 023 — No category until a human decides relatedness**
- Reading used: a PhD in Chemistry teaching Marketing, with SA-level counts, gets **Undetermined — Needs Human Decision**, not SA and not A, and is excluded from Tables 3-1 / 3-2 and the ratios until a chair/coordinator records the relatedness decision.
- The principle behind it: when a required human designation (here, degree relatedness) is missing, the record is held as Undetermined rather than forced into a category — the engine requests the decision instead of making it. If you would rather default to A, flag it — that changes how every undesignated record in the real system is reported.
- ☐ Agree  ☐ Flag

## 2. Quick-pass groups — one idea per group

If the group's idea matches the guideline as you read it, every case in it can be agreed together.

**Clean awards — the engine says yes, in full**
002 SA standard · 004 SA recent doctorate · 006 SA via JD (business law) · 008 SA via taxation degree · 009 SA administrator path (1 PRJ + 3 ICs) · 011 PA standard (4 total, 2 engagements) · 016 SP (related master's + experience + refereed item) · 019 IP (3 contributions, 2 engagements) · 020 IP adjunct exception *with* Dean approval recorded · 024 SA wins over PA when both are met
☐ Agree all  ☐ Flag case(s): ______

**Refusals — a strong-looking record that must NOT get the category**
001 A / Needs Info (real resume, everything undated) · 005 A (automatic SA expired, 2019 doctorate) · 007 A (JD exception does not travel to Marketing) · 012 A — **the permanent regression case: administrator with 2 consulting jobs and 0 AACSB events; if any build ever calls this PA, the build is wrong** · 017 A (SP missing its refereed item; IP missing one engagement) · 022 A (2019 article outside the six-year window) · 025 A (PA total is 4, but only 1 engagement)
☐ Agree all  ☐ Flag case(s): ______

**One missing record flips the case — the engine must ask, not guess**
018 A / Needs Info (SP counts met, but no experience record on file → flips to SP once recorded) · 021 A / Needs Info (adjunct IP, everything present except the Dean approval → flips to IP once recorded) · 014 PA / 015 A pair (transition designation: returned 2024 = still live; returned 2021 = expired in 2024)
☐ Agree all  ☐ Flag case(s): ______

**Cascade**
010 PA (SA fails by one IC as Dean, PA met through AACSB events — depends on the Case 013 reading above)
☐ Agree  ☐ Flag

## 3. Totals check

Final answers: **SA 6** (002, 004, 006, 008, 009, 024) · **PA 4** (010, 011, 013, 014) · **SP 1** (016) · **IP 2** (019, 020) · **A 11** (001, 003, 005, 007, 012, 015, 017, 018, 021, 022, 025) · **Undetermined 1** (023) = **25 cases.**
Heavy on A on purpose: most real errors are wrong *awards*, so the sheet tests refusal as much as award.

**Deliberately not in the sheet yet:** a contribution dated at exactly six years. That waits on the open FR-003 question — calendar years vs. exact dates — to be settled with the accreditation coordinator. Signing off does not settle FR-003.

## 4. Sign-off

- ☑ **Approved** — Abhi approved the dataset on 2026-10-07 (whole-dataset approval, given in chat). The dataset is now the binding SC-001 answer key, and the constitution and spec approval fold into this same sign-off.
- ☐ **Approved except:** case(s) ______ — those get corrected and re-checked before anything is built on them.

Next step after sign-off, and only after it: create the GitHub repository (~20 min, walked through step by step); constitution, spec, and this dataset become the first commit.
