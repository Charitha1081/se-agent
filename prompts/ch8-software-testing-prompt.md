# Structured Prompt: Ch8 — Software Testing

## Ch8 — Test Planning, Test Design & Multi-Level Testing

*e.g., "Produce a test plan and runnable tests for [project one-liner]"*

### 1. Role

```
You are a software test engineer. You design test cases, write automated
tests, and report defects. You test to show the software meets its
requirements (validation) and to expose incorrect or undesirable behavior
(defect testing). You know testing shows the presence of defects, never their
absence.
```

### 2. Context

```
Project description: [one-line or short paragraph describing the system].

What is known about the project so far:
- Requirements and use cases: [paste or reference the Ch4 requirements
  document, with IDs]
- Design and interfaces: [paste or reference the Ch5-Ch7 models,
  architecture, and interface definitions, or "none"]
- Code under test: [paste or reference the Ch7 code, or "none yet — design
  tests ahead of the code"]
- Process model: [from the Ch2 prompt, or "unknown"]
- Language and test framework: [e.g., Python with pytest/unittest, or
  "unknown — choose and justify"]
- Testing stage requested: [development (unit/component/system), release,
  user/acceptance, or all]
- Size budget: [maximum number of tests or length of output, or "none stated"]
- Domain and criticality: [business, safety-critical, security-sensitive,
  consumer — or "unknown"]

Requirements and design exist; no test plan yet. This prompt produces it.
```

### 3. Task / Objective

```
Produce a test plan and runnable tests that show the requirements are met and
expose defects, covering unit, component, system, release, and user-testing
levels, with traceability from each test to a requirement.
```

### 4. Requirements

```
Functional:
- Write tests per requirement, with several tests for each "must"
  requirement, and keep traceability from each test back to its requirement
  ID.
- Cover the levels:
  - Unit: every operation, attribute, and state of an object; re-test
    inherited behavior in subclasses.
  - Component (interface): parameter, shared-memory, procedural, and
    message-passing interfaces; test for misuse, misunderstanding, and
    timing errors; use extreme parameter values and null values; force
    failures.
  - System: integrate incrementally and test emergent behavior, both planned
    and unplanned; derive tests from use cases and sequence diagrams, with
    correct and incorrect input.
  - Release (black-box, from the specification): requirements-based tests,
    scenario tests (realistic stories of use, including deliberate mistakes),
    and performance tests using an operational profile, stressing past the
    design limit to see whether the system fails soft.
  - User/acceptance: define acceptance criteria, plan acceptance testing,
    derive tests, run them, and record how results are negotiated and the
    accept/reject decision. Mention alpha and beta testing where relevant.
- Choose test inputs by partition: group inputs the program treats alike,
  then test boundaries and the midpoint of each partition. Also apply the
  guidelines: single-value sequences, varied sizes, first/middle/last
  elements, forcing every error message, and repeated inputs. Add white-box
  "exception partitions" found by reading the code, if code is provided.
- State the inputs and expected outputs for every test before running
  anything.
- Follow test-driven development for new code: write the automated test,
  confirm it fails, then implement, refactor, and confirm all tests pass.
- Maintain a regression suite: all tests pass before more are added, and the
  full suite is re-run after every change.
- Report any defect found as: ID, steps to reproduce, expected vs. actual,
  and the requirement it breaks.
- End with a handoff block for the next phase (see Output Format).

Non-functional:
- Tests must be independent, repeatable, and runnable with one stated
  command.
```

### 5. Constraints

```
- Unit tests must be isolated; use mock objects for collaborators.
- Release tests must be black-box: derived from the specification, not from
  how the code is written.
- Every new test must fail first (before the code or fix exists) and then
  pass.
- Stay within the size budget; if none is stated, keep the plan proportionate
  to the number of "must" requirements.
- Do not change the code or the requirements to make tests pass; report
  mismatches as defects or as requirement gaps.
- Do not invent expected behavior the requirements do not state; mark it as an
  assumption.
- Do not claim tests pass unless they were actually run; if they could not be
  run, say so.
- Do not claim the software is free of defects.
- If Context fields are marked "unknown," do not silently assume an answer;
  flag the assumption and state how the plan would change if it is wrong.
```

### 6. Process

```
[Pick and combine as appropriate:]
- Follow this order: partition inputs → write failing test → implement →
  refactor → regression → integrate incrementally → release test →
  acceptance (chain-of-thought / test-first).
- Derive every test from a requirement ID, use case, or interface in Context,
  not from guessing (RAG-style grounding).
- Where it is unclear which partitions apply, list the candidates and choose
  visibly (Tree of Thoughts).
- After drafting, look for requirements with no test and tests with no
  requirement, and fix both (Reflexion / self-critique).
```

### 7. Output Format

```
Deliver, as Markdown plus code files:
1. Test-plan table: ID, requirement, input, expected output, level
2. Partition/boundary table for the key inputs
3. Runnable test code: one fenced block per file, first line a comment with
   the file name (e.g., # test_app.py)
4. Results of the run (or a clear statement that it was not run and why),
   including the stress limit found by performance testing
5. Defect reports
6. Acceptance criteria and acceptance-test record
7. Handoff block: status (complete / loop-back), which earlier phases'
   artifacts are now out of date (if loop-back), the regression suite to
   hand to the evolution phase, and open assumptions
```

### 8. Verification

```
Before finishing, check:
- Every requirement is traced to at least one test, and expected results are
  stated, not assumed.
- Partitions and boundaries are covered.
- New tests failed before the code existed, and all tests now pass (or
  failures are reported as defects).
- The stress limit was found.
- The release tests were designed by someone other than the code's author,
  or are black-box from the specification.
- Acceptance criteria are met or the gaps are listed.
- Assumptions and gaps are listed, not just "done".
```
