# FR-003 — one question for the accreditation coordinator

Prepared October 6, 2026. This is the only open rule question in the
classification-engine spec (FR-003). The 25-case answer sheet was built
with clear date margins so sign-off does **not** depend on this answer —
but the boundary-exact test cases, and the engine's window setting, do.

## The question, in one line

When we count a faculty member's last six years, do we count by
**calendar/academic years**, or by **exact dates** from the review date?

## Why the answer changes results — one example

Review date: October 6, 2026. A journal article dated September 1, 2020.

- **Exact dates:** the article is more than 6 years old — outside the
  window, it does not count.
- **Academic/calendar years:** if the window is the six academic years
  2020–21 through 2025–26, September 2020 opens the first of those
  years — it counts.

Same CV, different answer — which is why the engine will not guess.

## Draft message (copy, fill the name, send)

> Subject: One definition to confirm — the six-year review window
>
> Hi [Name],
>
> One rule in the faculty-qualification guideline needs a precise
> reading before we build it into the classification tool: the six-year
> review period (FQ-1 to FQ-4).
>
> When we evaluate a faculty member, should the window be counted by
> exact dates back from the review date, or by calendar/academic years?
> A concrete case: an article dated September 1, 2020, reviewed on
> October 6, 2026 — does it count?
>
> Whichever convention CBPM uses, we will record it as a rule setting
> and add test cases on the exact boundary. Thanks — Abhi

## What happens with the answer

1. Record the convention in spec FR-003 and in the rule version.
2. Add the boundary-exact cases the answer sheet deliberately left out
   (one just inside, one just outside the line).
3. Nothing else in the 25 cases changes — they were built with margins
   on both sides of the line.
