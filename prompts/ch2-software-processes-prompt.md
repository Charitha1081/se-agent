# Structured Prompt: Ch2 — Software Processes

## Ch2 — Software Process Model Selection & Change Strategy

*e.g., "Select and justify a software process model for [project one-liner]"*

### 1. Role

```
You are a senior software engineer and technical lead responsible for choosing
how a project will be run before any requirements work begins. Prioritize a
defensible, well-reasoned process decision over a fast or fashionable one —
the choice you make here shapes every later phase (requirements, design,
testing, evolution).
```

### 2. Context

```
Project description: [one-line or short paragraph describing the system to be
built].

What is known about the project so far:
- Domain / criticality: [e.g., business system, safety-critical, embedded,
  consumer app — unknown if not yet determined]
- Requirements stability: [well-understood and stable / likely to change /
  unknown/exploratory]
- Availability of reusable components, COTS, or existing systems to build on:
  [describe or state "none known"]
- Team size, distribution, and experience level: [describe or state "unknown"]
- Regulatory, safety, or contractual constraints (e.g., fixed-scope contract,
  Sarbanes-Oxley-style compliance, safety case requirements): [describe or
  state "none known"]
- Timeline / delivery pressure: [describe or state "unknown"]

No process model has been chosen yet. This prompt produces that decision.
```

### 3. Task / Objective

```
Recommend and justify a software process model (or deliberate hybrid) for
this project, drawn from: the waterfall model, incremental development,
reuse-oriented software engineering, Boehm's spiral model, and the Rational
Unified Process (RUP) — and specify how the project will cope with change
(prototyping and/or incremental delivery strategy).
```

### 4. Requirements

```
Functional:
- Identify which of the four fundamental process activities (specification,
  design/implementation, validation, evolution) carry the most risk or
  uncertainty for this specific project, and state why.
- Recommend one generic process model as the primary backbone. If a hybrid is
  justified (e.g., waterfall for a stable architectural core + incremental for
  a volatile UI), name each part explicitly and which sub-system or activity
  it governs.
- Explicitly state whether the project is closer to plan-driven or agile, and
  where on that spectrum it sits, with reasoning tied to the project context
  above (not a generic definition of the terms).
- Recommend a change-coping strategy: system prototyping, incremental
  delivery, both, or neither — and justify against the project's requirements
  stability and delivery constraints.
- If risk is a dominant concern (safety, security, unproven technology,
  integration uncertainty), assess whether a risk-driven approach (Boehm's
  spiral model) is warranted, and identify the top 2-3 project risks it would
  need to manage.
- Identify roles, key products, and one pre-/post-condition pair for at least
  the first phase or activity of the recommended process, following the
  process-description concepts in Ch2 (products, roles, pre/post-conditions).

Non-functional:
- The justification must be traceable to specific facts stated in the Context
  section — do not justify the choice using generic textbook advantages that
  weren't established as true for this project.
- Keep the recommendation actionable: a team should be able to read the
  output and know what to do next, not just what model was chosen.
```

### 5. Constraints

```
- Do not default to "agile" or "incremental" without justification — this is
  the common failure mode and must be argued from the Context, not assumed.
- Do not recommend formal transformation-based development (e.g., B method)
  unless the context explicitly indicates safety- or security-critical
  requirements.
- Do not recommend reuse-oriented engineering unless the Context indicates
  reusable components, COTS, or existing systems are actually available or
  plausible — do not invent their existence.
- Do not treat this prompt's output as final requirements or architecture —
  it produces a process-model decision and change strategy only. Later
  chapter prompts (requirements, architecture, etc.) build on this decision.
- If critical information in Context is marked "unknown," do not silently
  assume an answer — flag the assumption explicitly and state how the
  recommendation would change if the assumption is wrong.
```

### 6. Process

```
[Pick and combine as appropriate:]
- If there are multiple viable process models for this project, briefly list
  the plausible candidates and justify the one you choose before finalizing
  (Tree of Thoughts) — this decision has real downstream cost if wrong.
- Reason step-by-step from the four fundamental activities (specification,
  design/implementation, validation, evolution) to the process model, rather
  than pattern-matching the project description to a familiar label.
- Reference only the facts given in Context above rather than assuming
  unstated project characteristics (RAG-style grounding).
- After producing a recommendation, check it against the Requirements above
  and revise if anything is missed — in particular, confirm the change-coping
  strategy and risk assessment are both present (Reflexion / self-critique).
```

### 7. Output Format

```
Deliver, as a single Markdown document:
1. Recommended process model (name it explicitly; state hybrid components if
   any)
2. One-paragraph justification tied to Context facts
3. Plan-driven vs. agile positioning, with reasoning
4. Change-coping strategy (prototyping / incremental delivery / both /
   neither) with justification
5. Risk assessment: top risks and whether a spiral/risk-driven approach is
   warranted
6. Roles, key products, and at least one pre-/post-condition pair for the
   first phase or activity
7. Explicitly flagged assumptions (if any Context fields were "unknown")
```

### 8. Verification

```
This is complete when:
- A single process model (or explicitly named hybrid) is recommended, not a
  menu of options with no decision made.
- Every claim in the justification traces back to a specific fact in the
  Context section, or is flagged as an assumption.
- A change-coping strategy is explicitly stated and justified — "none" is an
  acceptable answer only if explicitly justified.
- The plan-driven/agile positioning is stated as a reasoned judgment, not a
  restatement of the textbook definitions.
- Edge case handled: if Context contains conflicting signals (e.g., stable
  requirements but tight, uncertain timeline), the conflict is named and
  resolved with reasoning, not ignored.
```
