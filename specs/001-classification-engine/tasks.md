# Tasks: 001-Classification-Engine

**Status**: Draft
**Context**: Breaking down the approved `plan.md` into small, testable tasks for implementation. Governed by the Project Constitution v1.0 and Architecture Document v1.2. 

**Rule**: After every task, run linting (Ruff), security scans (Bandit, pip-audit), and tests before proceeding. Do not proceed to the next task until the current one passes its checks.

## Phase 1: Scaffolding and Data Models

- [ ] **Task 1.1**: Initialize the Python package structure.
  - Create the folder structure: `classification_engine/` containing `models/`, `evaluators/`, `rules/`, and `tests/`.
  - Add `__init__.py` files to make it a package.
- [ ] **Task 1.2**: Define Pydantic Input Models.
  - Create `FacultyRecord` (demographics, degree type, teaching field, doctorate year, degree relatedness flags, initial-qualification experience record, Dean-approval flag, administrator status, return-to-faculty date, record status).
  - Create `Contribution` (type, date, ABDC/SJR ranking, CCOR approval, AACSB-sponsored tag).
  - Create `RuleVersion` (thresholds, window length, boundary convention switch, lists of valid types).
- [ ] **Task 1.3**: Define Pydantic Output Models.
  - Create `CategoryResult` (met/not demonstrated, counted evidence, missing gaps, FQ-x citations).
  - Create `ClassificationResult` (final decision: SA/PA/SP/IP/A/UNDETERMINED, basis statement, provisional flag, rule version ID).
- [ ] **Task 1.4**: Define Rule Configuration JSON (`rules/v1.json`).
  - Draft the initial JSON configuration containing thresholds, review window limits, and contribution lists as specified in FQ-1 to FQ-6 of the CBPM Fall 2026 guideline.

## Phase 2: Shared Logic and Rule Evaluators

- [ ] **Task 2.1**: Implement Shared Filtering Logic.
  - Create functions to filter contributions based on the window (using the switchable boundary convention from `RuleVersion`).
  - Create functions to filter quality evidence (ensuring every counted SA article has a quality basis).
- [ ] **Task 2.2**: Implement `evaluate_sa()` (Scholarly Academic).
  - Logic: Handles initial qualification (6 years) OR the 2+3 (or 1+3 for admins) contribution threshold.
  - Write supplementary mock-data unit tests for this evaluator.
- [ ] **Task 2.3**: Implement `evaluate_pa()` (Practice Academic).
  - Logic: Handles the 4-contribution rule, the admin AACSB-sponsored exception, and the 3-year transition rule.
  - Write supplementary mock-data unit tests for this evaluator.
- [ ] **Task 2.4**: Implement `evaluate_sp()` (Scholarly Practitioner) and `evaluate_ip()` (Instructional Practitioner).
  - Logic: Check initial professional qualification. For SP, check 3 contributions (1 peer-reviewed). For IP, check 3 contributions (2 professional) and handle the adjunct Dean-approval exception.
  - Write supplementary mock-data unit tests for both evaluators.

## Phase 3: Engine Orchestration and Formatting

- [ ] **Task 3.1**: Implement Input Validation (SC-004).
  - In the main entry point, assert that `FacultyRecord.status` is strictly verified or locked. Reject drafts and unverified records (SC-004).
- [ ] **Task 3.2**: Implement `classify()` Orchestrator.
  - Create the main function `classify(record: FacultyRecord, rules: RuleVersion) -> ClassificationResult`.
  - Evaluate in order: SA → PA → SP → IP. Return the highest met category.
  - Handle the "unclear" degree relatedness by yielding an explicit `UNDETERMINED` outcome.
- [ ] **Task 3.3**: Implement Formatting Logic.
  - Generate plain-language basis statements citing the guideline sections (FQ-x) for counted and excluded items.
  - Ensure every article counted toward SA clearly records its quality basis in the output (SC-005).

## Phase 4: Golden Dataset and Compliance (SC-001)

- [ ] **Task 4.1**: Transcribe the Golden Dataset.
  - Transcribe the 25 approved cases from `specs/001-classification-engine/golden-dataset.md` into `tests/golden_dataset.json` exactly.
  - **Constraint**: Never author or alter expected outcomes.
- [ ] **Task 4.2**: Implement the Pytest Golden Suite.
  - Write a Pytest suite that iterates over `tests/golden_dataset.json`, runs each case through `classify()`, and asserts 100% agreement with the expected classification.
- [ ] **Task 4.3**: Final Verification and Linting.
  - Run the full suite: `pytest`, `ruff check .`, `ruff format --check .`, `bandit -r .`, and `pip-audit`.
  - Confirm SC-001 through SC-005 are explicitly met.
