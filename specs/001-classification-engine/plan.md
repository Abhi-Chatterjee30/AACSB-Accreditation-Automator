# Implementation Plan: 001-Classification-Engine

**Status**: Proposed
**Context**: Translating `spec.md` and `system-in-one-page.md` into a sequence of technical milestones. Consistent with Architecture Document v1.2 and Constitution v1.0.

## 1. Architectural Approach
Consistent with the neuro-symbolic design (Principle II) and simplicity constraint (Principle VIII), the engine will be implemented as a **standalone, pure-Python, deterministic package**.
- **No LLMs/AI in the engine**: The engine strictly executes defined rules. 
- **No I/O dependencies**: The engine takes pure data structures (e.g., Pydantic models representing verified records) and returns structured outputs. It does not query the database directly. This makes it 100% independently testable.
- **Rule Configuration**: Thresholds and lists are separated from execution logic into a versioned configuration file strictly formatted as **JSON**, satisfying Principle I.

## 2. Component Design

### 2.1 Data Models (Pydantic)
- **Inputs**:
  - `FacultyRecord`: Core demographics, degree type, teaching field, doctorate year, degree relatedness flags, initial-qualification experience record (for SP/IP, absence yields not-demonstrated and a gap), a Dean-approval flag (for the adjunct IP exception), administrator status, and return-to-faculty date. 
  - `Contribution`: An item with a type, date, and quality flags (e.g., ABDC/SJR ranking, CCOR approval, AACSB-sponsored tag).
  - `RuleVersion`: The JSON schema representing thresholds, review window length, boundary convention (switchable), and lists of valid contribution types for each category.
- **Outputs**:
  - `CategoryResult`: The outcome for a single category (met / not demonstrated), counted evidence, specific missing gaps, and citations to FQ-x.
  - `ClassificationResult`: The final decision (SA, PA, SP, IP, A, or **UNDETERMINED** when degree relatedness is "unclear"), basis statement citing FQ-x for counted/excluded items, provisional flag, and rule version identifier.

### 2.2 Shared Logic and Rule Evaluators
- **Shared Counting/Filtering Logic**: Functions to filter contributions based on the window (using the switchable boundary convention from `RuleVersion`) and quality evidence (ensuring every counted SA article has a quality basis).
- **Independent Modules** for evaluating each qualification category:
  - `evaluate_sa()`: Handles initial qualification (6 years) and the 2+3 (or 1+3 for admins) contribution threshold.
  - `evaluate_pa()`: Handles the 4-contribution rule, the admin AACSB-sponsored exception, and the 3-year transition rule.
  - `evaluate_sp()`: Checks initial professional qualification and the 3-contribution rule (including 1 peer-reviewed).
  - `evaluate_ip()`: Checks initial professional qualification and the 3-contribution rule (2 professional).

### 2.3 The Orchestrator
- A main entry point (e.g., `classify(record: FacultyRecord, rules: RuleVersion) -> ClassificationResult`).
- Evaluates in order: SA → PA → SP → IP. Returns the highest met category (or UNDETERMINED if unclear relatedness).
- Formats plain-language basis statements and actionable gap lists (citing the guideline section FQ-x for counted and excluded items).

## 3. Phased Implementation Plan

**Package Layout**:
```
classification_engine/
├── models/
├── evaluators/
├── rules/
│   └── v1.json
├── orchestrator.py
└── tests/
```

### Phase 1: Scaffolding and Data Models
1. Initialize the Python package structure (`classification_engine/`).
2. Define Pydantic models for inputs and outputs.
3. Define the first rule configuration JSON matching the FQ-1 to FQ-6 Fall 2026 guidelines.

### Phase 2: Category Evaluators and Filtering
1. Implement the shared window and quality filtering logic used across evaluators.
2. Implement the evaluators (SA, PA, SP, IP) leveraging the shared filtering logic.
3. Write supplementary mock-data unit tests for each evaluator (mock-data unit tests are supplementary only).

### Phase 3: Engine Orchestration and Formatting
1. Implement the overarching `classify()` function that runs the evaluators in precedence order.
2. Build the formatting logic for basis statements, citing the guideline sections (FQ-x), and actionable gap lists.

### Phase 4: Golden Dataset and Compliance (SC-001)
1. **Transcribe**: The golden dataset already exists and is approved (`specs/001-classification-engine/golden-dataset.md`, 25 cases). The task is to transcribe those cases and their expected outcomes into `tests/golden_dataset.json` exactly — never author or alter expected outcomes.
2. Write a Pytest suite that iterates over the golden dataset, asserting 100% agreement between the engine and the manual classification.

## 4. Open Clarifications
- **(a) FR-003 — six-year window boundary**: Calendar years vs exact dates, undecided; the convention stays switchable in `RuleVersion`.
- **(b) AACSB-sponsored events**: Whether AACSB-sponsored events attended by non-administrators count as professional engagements — undecided.

## 5. Definition of Done
- [ ] Code passes Ruff (linting/formatting), Bandit (security), and pip-audit.
- [ ] Golden dataset tests pass at 100% (SC-001).
- [ ] Outputs are fully deterministic and reproducible (SC-002).
- [ ] Unmet categories explicitly yield actionable gap strings (SC-003).
- [ ] **SC-004**: The engine's input contract accepts verified records only.
- [ ] **SC-005**: Every article counted toward SA carries a recorded quality basis in the output.
- [ ] Code is ready to be merged to the main branch after review.

*(No code is written yet. Ready for review and conversion into `tasks.md`.)*
