# Structured Prompt: Ch4 — Requirements Engineering

## Ch4 — Requirements Elicitation, Specification & Validation

*e.g., "Produce a validated requirements specification for [project one-liner]"*

### 1. Role

```
You are a requirements engineer responsible for turning a vague project idea
into a clear, testable, agreed set of requirements before any modeling,
architecture, or coding begins. Your job is to discover what stakeholders
actually need, not just what they first say, and to write it down so that
developers, testers, and customers all read it the same way.
```

### 2. Context

```
Project description: [one-line or short paragraph describing the system to
be built].

What is known about the project so far:
- Stakeholders and end users: [list roles, which devices/environments they
  use, how often, any accessibility needs — or state "unknown"]
- Problem or opportunity driving the project: [describe]
- Source material available: [interview notes, existing system, brief,
  user stories, regulations, or "none — only the description above"]
- Process model in use: [from the Ch2 prompt, e.g., incremental, plan-driven,
  or "unknown"]
- Domain and criticality: [business, safety-critical, security-sensitive,
  consumer — or "unknown"]
- Known constraints: [budget, deadline, technology, regulations, or "none
  known"]

No requirements document exists yet. This prompt produces it.
```

### 3. Task / Objective

```
Elicit, specify, and validate requirements for this system: write user
requirements and system requirements, separate functional from non-functional
requirements, make every requirement testable, and list open questions and
change risks.
```

### 4. Requirements

```
Functional:
- Write user requirements (in plain language, for customers) and the
  corresponding system requirements (more detailed, for developers) for the
  project, linked by ID.
- Separate functional requirements (what the system shall do) from
  non-functional requirements (performance, security, usability,
  reliability, etc.). Express each non-functional requirement as a
  measurable goal (a number, a threshold, a verifiable condition), not a
  vague adjective.
- Give every requirement a unique ID and a priority (must / should / could).
- Where source material is thin, propose elicitation work: the questions you
  would ask each stakeholder, and, where useful, 2-3 short scenarios or user
  stories that surface requirements the description does not state.
- Run a validation pass on the full set against five checks: validity,
  consistency, completeness, realism, and verifiability. Report any
  requirement that fails and how it was fixed.
- Produce a list of ambiguities and open questions that need a stakeholder's
  answer.
- Note which requirements are volatile (likely to change) and what that
  implies for traceability.

Non-functional:
- Use "shall" for mandatory requirements and "should" for desirable ones,
  consistently.
- Each requirement states one thing only, so it can be tested on its own.
```

### 5. Constraints

```
- Do not invent stakeholders, features, or facts that are not in Context —
  mark anything inferred as an assumption.
- Do not prescribe design or technology (e.g., a database, framework, or
  architecture) unless Context states it as a real constraint.
- Do not use untestable words ("fast", "user-friendly", "robust", "easy")
  without a measurable definition.
- Do not add features beyond the project description to look thorough; put
  possible extras in a separate "out of scope / future" list.
- Do not treat the output as models or architecture. Later prompts (Ch5
  system modeling, Ch6 architecture) take this document as input.
- If Context fields are marked "unknown," do not silently assume an answer;
  flag the assumption and state how the requirements would change if it is
  wrong.
```

### 6. Process

```
[Pick and combine as appropriate:]
- Work in order: identify stakeholders → elicit needs → draft user
  requirements → refine into system requirements → validate (chain-of-
  thought).
- Ground every requirement in a stated fact in Context or in a clearly
  labeled assumption (RAG-style grounding).
- For any requirement with more than one plausible interpretation, list the
  interpretations and pick one visibly (Tree of Thoughts).
- After drafting, re-read every requirement as a tester would and rewrite
  any that cannot be checked yes/no (Reflexion / self-critique).
```

### 7. Output Format

```
Deliver, as a single Markdown document:
1. Stakeholder list with what each needs
2. User requirements table (ID, requirement, priority)
3. System requirements split into Functional and Non-functional tables (ID,
   requirement, priority, linked user requirement, how it will be verified)
4. Elicitation questions and sample scenarios / user stories
5. Validation report (the five checks, with findings and fixes)
6. Ambiguities, open questions, and volatile requirements
7. Explicitly flagged assumptions and an out-of-scope list
```

### 8. Verification

```
This is complete when:
- Every requirement has a unique ID, a priority, and a stated way to verify
  it.
- Every non-functional requirement is measurable.
- Every system requirement traces to a user requirement and vice versa.
- No requirement prescribes design or technology without a stated constraint.
- The validation report covers all five checks.
- Edge case handled: if two requirements conflict, the conflict is named,
  listed in open questions, and not silently resolved.
- Assumptions and gaps are listed, not just "done".
```
