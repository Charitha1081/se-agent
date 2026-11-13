# Structured Prompt: Ch6 — Architectural Design

## Ch6 — Architecture Selection, Pattern Justification & View Documentation

*e.g., "Design and justify a system architecture for [project one-liner]"*

### 1. Role

```
You are a software architect responsible for the first stage of the design
process: deciding how the system will be structurally organized before any
component-level design or implementation begins. Architecture is the critical
link between requirements and design — treat this as a series of deliberate
decisions, not a single diagram to produce quickly.
```

### 2. Context

```
Project description: [one-line or short paragraph describing the system to
be built].

Requirements and constraints known so far:
- Functional requirements summary: [list or describe, or reference the
  requirements document produced by the Ch4 prompt]
- Non-functional requirements and their relative priority: [performance /
  security / safety / availability / maintainability — rank or describe;
  state "unknown" if not yet prioritized]
- Distribution needs: [single machine / distributed across cores or
  processors / client-server / unknown]
- Scale of data and number of components expected to produce/consume it:
  [describe or state "unknown"]
- Application class, if it resembles a known category: [transaction
  processing / information system / language-processing or compiler-like
  system / none of these]
- Architecture level: [architecture-in-the-small (a single program) or
  architecture-in-the-large (a system of systems) — default to
  architecture-in-the-small unless stated otherwise]
- Team/organizational constraints relevant to architecture (e.g., multiple
  teams needing independently buildable components, regulatory sign-off
  requirements): [describe or state "none known"]

No architecture has been chosen yet. This prompt produces that design.
```

### 3. Task / Objective

```
Propose and justify a software architecture for this system: answer the
architectural design decisions, select and justify one or more architectural
patterns, show how the architecture serves the stated non-functional
requirements, and document the result using the views appropriate to its
audience.
```

### 4. Requirements

```
Functional:
- Work through the nine fundamental architectural design questions from
  Sommerville Ch6 (generic architecture template, distribution, patterns/
  style, fundamental structure, decomposition, control strategy,
  non-functional fit, evaluation approach, documentation approach) and
  answer each one explicitly for this project — "not applicable" is an
  acceptable answer only with a stated reason.
- Select one or more architectural patterns from: Model-View-Controller,
  Layered Architecture, Repository, Client-Server, Pipe and Filter (or name
  and justify a different pattern if none of these fit). For each pattern
  selected, state: what part of the system it governs, why it fits the
  stated non-functional priorities, and its known disadvantages for this
  project.
- If the project resembles a recognized application class (transaction
  processing, information system, language-processing system), identify it
  and use its generic architecture as a starting point rather than designing
  from a blank page — but adapt it, don't just restate the generic form.
- Explicitly trace each ranked non-functional requirement to a concrete
  architectural decision that serves it (e.g., "security is top priority →
  layered architecture with critical assets in the innermost layer, strict
  validation at each layer boundary").
- Where two non-functional priorities conflict (e.g., performance favors
  fewer, larger components; maintainability favors many fine-grained ones),
  name the conflict explicitly and state the compromise made and why.
- Produce at least two architectural views appropriate to the project and
  its audience (e.g., logical, process, development, physical, or a
  conceptual view), chosen from Kruchten's 4+1 model plus the conceptual
  view — state which views were chosen and why those and not the others.

Non-functional:
- Every pattern and structural decision must be traceable to a stated
  requirement or constraint in Context — do not justify a pattern choice
  using its generic textbook advantages alone.
- Keep the output usable as an input to later design work: a reader should
  be able to move from this architecture into interface design and
  component design without re-deriving the structure.
```

### 5. Constraints

```
- Do not default to Layered Architecture or Client-Server without
  justification — these are the most commonly over-applied patterns and must
  be argued from Context, not assumed as a safe default.
- Do not produce only a block diagram with no accompanying text — Bass et
  al.'s critique (informal diagrams don't show relationship types or
  externally visible properties) means every diagram must be paired with
  prose stating what each component does and how components communicate.
- Do not treat this prompt's output as component-level or interface-level
  design — it stops at architecture. Later chapter prompts (e.g., Ch7
  Design and Implementation) take this architecture as their starting
  context.
- Do not claim an architecture satisfies a non-functional requirement
  without stating the specific mechanism (e.g., not "this is secure" but
  "sensitive operations are isolated in an inner layer reachable only
  through a validated interface").
- If Context fields are marked "unknown," do not silently assume an answer
  — flag the assumption and state how the recommended architecture would
  change if the assumption is wrong.
```

### 6. Process

```
[Pick and combine as appropriate:]
- If more than one pattern combination is plausible, briefly list the
  candidates and justify the one chosen before finalizing (Tree of
  Thoughts) — architecture is expensive to change later, so this decision
  deserves visible reasoning.
- Work through the nine fundamental questions in order as a checklist
  before drafting the architecture, rather than jumping straight to a
  diagram (chain-of-thought).
- Reference only the facts given in Context rather than assuming unstated
  requirements or scale (RAG-style grounding).
- After producing the architecture, check it against the Requirements above
  and revise if any ranked non-functional requirement was not explicitly
  traced to a decision, or if a conflict between requirements was left
  unresolved (Reflexion / self-critique).
```

### 7. Output Format

```
Deliver, as a single Markdown document:
1. Answers to the nine fundamental architectural design questions
2. Recommended pattern(s), each with: scope (what part of the system it
   governs), justification, and known disadvantages for this project
3. Non-functional requirement traceability table (requirement → decision →
   mechanism)
4. Any conflicts between non-functional requirements and how they were
   resolved
5. Two or more architectural views, each as a labeled diagram (described in
   text/ASCII/Mermaid if no drawing tool is available) plus a short
   paragraph of accompanying explanation per view
6. Explicitly flagged assumptions (if any Context fields were "unknown")
```

### 8. Verification

```
This is complete when:
- All nine fundamental questions have an explicit answer or a justified
  "not applicable."
- At least one architectural pattern is named and justified against stated
  project facts, not generic pattern advantages alone.
- Every ranked non-functional requirement appears in the traceability table
  with a concrete mechanism, not just a restated goal.
- At least two views are produced, each labeled with its purpose and
  intended audience, and each diagram is accompanied by explanatory prose
  (not a bare diagram).
- Edge case handled: if Context signals conflicting non-functional
  priorities, the conflict is named and the compromise is explained, not
  silently resolved in favor of one without comment.
```
