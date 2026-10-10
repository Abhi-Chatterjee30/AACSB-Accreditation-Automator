# AACSB Accreditation Automator — Technology Links

All official websites for the technologies in this project, grouped by the job each one does. Compiled 2026-10-06. Everything below is free or has a free tier used by this project; Snyk is the single exception and is marked optional.

## 1. Build with — AI builder, language, app screens

- **Google Antigravity** (the AI builder Abhi directs) — https://antigravity.google/
- **Gemini API / Google AI for Developers** (the AI model family behind Antigravity) — https://ai.google.dev/
- **Python** (the programming language everything is written in) — https://www.python.org/downloads/
- **Streamlit** (builds the web app screens) — https://streamlit.io/ · Docs: https://docs.streamlit.io
- **Pydantic** (defines the record shapes and validates data) — https://docs.pydantic.dev/
- **Groq** (fast AI service used by the prototype for CV extraction) — https://console.groq.com
- **Ollama** (runs AI models locally on our own machine — the on-campus fallback) — https://ollama.com

## 2. Store and host — database and packaging

- **Supabase** (database + login + file storage for Stages 1–2) — https://supabase.com
- **PostgreSQL** (the database underneath Supabase; also the Stage 3 database) — https://www.postgresql.org/docs
- **Docker** (packages the app for Kean IT hosting at Stage 3) — https://docs.docker.com · Docker Desktop: https://www.docker.com/products/docker-desktop/

## 3. Project control — memory, history, and the build method

- **Git** (version control on the laptop) — https://git-scm.com/downloads
- **GitHub** (the repository's online home; Streamlit Cloud publishes from here) — https://github.com
- **GitHub Spec Kit** (the spec-driven build method) — Repository: https://github.com/github/spec-kit · Docs: https://github.github.io/spec-kit/
- **Spec Kit article** (Microsoft Developer Blog — the article that introduced the method to this project) — https://developer.microsoft.com/blog/spec-driven-development-spec-kit/

## 4. Inspection — scanners and tests that check the code

- **Ruff** (code quality) — https://docs.astral.sh/ruff/
- **Bandit** (Python security flaws) — https://bandit.readthedocs.io/
- **Semgrep** (security flaws, wider patterns) — https://semgrep.dev
- **pip-audit** (vulnerable packages) — https://pypi.org/project/pip-audit/
- **pytest** (runs the tests, including the answer-sheet / golden-dataset cases) — https://docs.pytest.org/en/stable/
- **Snyk** (OPTIONAL extra scanner only — commercial product, capped free tier; never a required gate) — https://snyk.io/lp/snyk-code-checker/

## 5. Verification sources — free, used to check facts from outside

- **Crossref** (checks a publication / DOI is real) — https://www.crossref.org/ · API: https://api.crossref.org/
- **OpenAlex** (free scholarly database: works, authors, journals) — https://openalex.org/ · Docs: https://docs.openalex.org/
- **ORCID** (researcher IDs and publication records) — https://orcid.org/
- **Tavily** (web search for the advisory chat — not on the critical path) — https://tavily.com

## 6. Rules and journal-quality references — the authorities the engine follows

- **AACSB** (the accrediting body; Standard 3 and Tables 3-1 / 3-2) — https://www.aacsb.edu
- **ABDC Journal Quality List** — https://abdc.edu.au/abdc-journal-quality-list/
- **SCImago Journal Rank (SJR)** — https://www.scimagojr.com
- **Chartered ABS — Academic Journal Guide** — https://charteredabs.org/academic-journal-guide
- **Clarivate — Journal Citation Reports (JCR)** — https://clarivate.com/academia-government/scientific-and-academic-research/research-funding-analytics/journal-citation-reports/

*Note: smaller Python libraries used inside the app (e.g., openpyxl for Excel reports, PyPDF2 and python-docx for reading CV files) live on PyPI, the Python package index, and are installed by name — they have no separate project website worth bookmarking.*
