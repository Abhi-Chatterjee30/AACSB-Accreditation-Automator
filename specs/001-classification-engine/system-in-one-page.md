# Faculty classification — the whole system in one page

Three things, three different places. They never swap jobs.

## 1. The engine — code that contains the rules

- The CBPM guideline (FQ-1 to FQ-6) turned into code, followed step by step like a checklist.
- Takes facts in, calculates one answer out: SA, PA, SP, IP, or A.
- Same facts in → same answer out, every time. It can show its working.
- No AI inside it. An accreditation decision cannot be an AI opinion that changes tomorrow.

## 2. The dataset file — sits next to the code, never in the database

- 25 test professors with answers decided by hand from the guideline, before any software runs.
- Its only job: prove the engine follows the guideline.
  Test professor goes in → engine calculates → we compare with the hand-decided answer.
- Pass = 25 out of 25. If a case fails, we fix the rules in the code — never the dataset.
- After every future change, the same 25 run again, so an old mistake cannot return quietly.
- It does not teach the engine, no AI looks it up, and it is never used on a real person.
  If it were in the database, the 24 invented professors would be counted as real Kean faculty and the ratios would be wrong.
- Status: drafted, not binding yet. It becomes the binding answer key (SC-001) only when Abhi reviews and signs off the expected answers.

## 3. The database — Supabase, not in the project folder

- Holds only real faculty facts: degrees, publications, dates, engagements — after they are verified.
- When a real person is classified, the engine takes that person's facts from here and applies the rules.

## What about a messy CV?

A messy CV makes a messy draft — never a confident wrong answer.

1. The reader (AI) pulls candidate facts from the CV into fixed fields. Unclear = marked uncertain. Absent = marked missing. It must not guess.
2. The faculty member corrects the draft form and answers specific questions ("This publication has no year — add the year").
3. Publications are checked against Crossref/OpenAlex; journal quality comes from the ABDC/SJR lists.
4. Only the verified record goes to the engine.

That is Case 001: a strong career, no dates at all → A — Needs Info, with questions, not a guessed IP.

## One line to keep

**The AI reads, the engine decides, the dataset proves the engine is right, and the database holds only real faculty.**
