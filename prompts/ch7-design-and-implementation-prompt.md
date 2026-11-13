# Structured Prompt: Ch7 — Design and Implementation

## Ch7 — Object-Oriented Design, Design Patterns & Implementation

*e.g., "Design and implement [project one-liner] from a given architecture"*

### 1. Role

```
You are a senior software engineer responsible for turning an agreed
architecture and requirements into a working, understandable implementation.
You design before you code, reuse before you rewrite, and keep every design
decision traceable to a requirement.
```

### 2. Context

```
Project description: [one-line or short paragraph describing the system to
be built].

What is known about the project so far:
- Requirements: [paste or reference the Ch4 requirements document]
- System models: [paste or reference the Ch5 models, especially use cases
  and the class diagram, or "none"]
- Architecture: [paste or reference the Ch6 architecture, patterns, and
  views, or "none"]
- Language, framework, and platform: [e.g., Python 3.11 with no external
  libraries, or "unknown — choose and justify"]
- Reusable code, libraries, or services available: [list or "none known"]
- Development environment and constraints: [host/target setup, deadlines,
  team size, coding standards, or "unknown"]

Architecture exists but no component-level design or code yet. This prompt
produces them.
```

### 3. Task / Objective

```
Produce a component-level object-oriented design and a working
implementation for this system: define objects/classes and their interfaces,
apply design patterns only where they solve a real problem, decide what to
reuse, and deliver runnable code with tests mapped to requirements.
```

### 4. Requirements

```
Functional:
- Follow the object-oriented design steps: restate the system context and
  interactions, confirm the architecture, identify the key objects/classes,
  describe them with UML-style models (at least a class diagram and one
  sequence or state model for a non-trivial behavior), and specify each
  interface (operations, inputs, outputs, errors).
- Choose design patterns (e.g., Observer, Facade, Iterator, Decorator) only
  where a stated problem calls for one; for each pattern used, name the
  problem it solves and where it appears in the code.
- Make a reuse decision for each major component: build, reuse an existing
  library/component, or configure an existing system, with a reason.
- Implement the design as code. Every requirement marked "must" in the Ch4
  document must map to at least one function or class.
- Include configuration-management notes: file/module layout, naming, and
  how versions of the code would be tracked.
- Include tests: at least one test per "must" requirement, each labeled with
  the requirement ID it checks.
- Note implementation issues that need a decision (host-target environment,
  open-source or licensing issues if reuse is involved).

Non-functional:
- Code must run as delivered, with instructions to run it and its tests.
- Naming, structure, and comments must be consistent so a stranger can
  maintain the code from the documentation alone.
```

### 5. Constraints

```
- Do not change the architecture or requirements; if you find a conflict or
  gap, report it instead of silently redesigning.
- Do not add features not in the requirements.
- Do not use a design pattern just to look sophisticated; no pattern without
  a named problem.
- Do not use external libraries unless Context allows them or reuse of that
  library is justified.
- Do not claim code works without showing how it was checked.
- If Context fields are marked "unknown," do not silently assume an answer;
  flag the assumption and state how the design would change if it is wrong.
```

### 6. Process

```
[Pick and combine as appropriate:]
- Design first, then code: write the class/interface design, then implement
  one component at a time, smallest first (incremental).
- Write each test from its requirement before or alongside the code it checks
  (test-first).
- Derive every class from the Ch5 models and Ch4 requirements, not from
  imagination (RAG-style grounding).
- Where two designs are plausible, list both briefly and choose visibly (Tree
  of Thoughts).
- Before finishing, review the code against the requirements and the
  constraints, and fix any mismatch (Reflexion / self-critique).
```

### 7. Output Format

```
Deliver, as Markdown plus code files:
1. Design summary: key objects/classes, class diagram (Mermaid or ASCII), one
   behavior model, interface table
2. Design decisions log: patterns used (with problem solved) and reuse
   decisions
3. Code: one fenced block per file, first line a comment with the file name
   (e.g., // app.js or # app.py)
4. Tests: one fenced block per file, each test labeled with the requirement
   ID
5. Requirements traceability table (requirement ID → class/function → test)
6. How to run the code and tests
7. Explicitly flagged assumptions, gaps, and any requirement/architecture
   conflicts found
```

### 8. Verification

```
Before finishing, check:
- Every "must" requirement appears in the traceability table with code and a
  test.
- Every design pattern used names the problem it solves.
- The code matches the class diagram and interfaces (names and operations).
- Nothing was added outside the requirements.
- The run instructions are complete and the tests could be run as written.
- Edge case handled: if the requirements, models, or architecture conflict,
  the conflict is reported, not hidden.
- Assumptions and gaps are listed, not just "done".
```
