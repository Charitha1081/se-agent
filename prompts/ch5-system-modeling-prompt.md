# Structured Prompt: Ch5 — System Modeling

## Ch5 — Multi-Perspective UML Modeling (Context, Interaction, Structure, Behavior)

*e.g., "Model [project one-liner] from context through behavior"*

### 1. Role

```
You are a systems analyst responsible for turning requirements into a set of
complementary models — context, interaction, structural, and behavioral —
that together document what the system is, what surrounds it, and how it
behaves. No single model shows everything; your job is to pick the right
model for each purpose and keep them consistent with each other.
```

### 2. Context

```
Project description: [one-line or short paragraph describing the system to
be built].

What is known about the system so far:
- Requirements summary, or a reference to the requirements document produced
  by the Ch4 prompt: [describe or paste]
- External systems, actors, or manual processes the system must interact
  with: [list, or state "unknown — to be derived from the requirements"]
- Key use cases / user-facing interactions to be modeled in detail: [list
  2-5, or state "select the most significant ones from the requirements"]
- Primary domain entities / data the system manages: [list, or state
  "unknown — to be derived"]
- System character: [data-driven (input flows through processing stages to
  an output, e.g. a billing system) / event-driven (reacts to discrete
  stimuli with a limited number of states, e.g. a real-time control system)
  / mixed / unknown]
- Intended use of these models: [to facilitate discussion (informal, can be
  incomplete) / as documentation (must be correct, need not be complete) /
  as a specification for code generation (must be complete and correct) —
  state which, since this changes how rigorous the output must be]
- Model-driven engineering is in scope: [yes / no / unknown — default to no
  unless the project explicitly calls for generating implementation from
  models]

No models have been produced yet. This prompt produces them.
```

### 3. Task / Objective

```
Produce a coherent set of UML models covering all four modeling perspectives
— context, interaction, structural, and behavioral — for this system, each
using the diagram type(s) best suited to what it needs to show, and keep
entities and names consistent across all of them.
```

### 4. Requirements

```
Functional:
- Context: produce a context model showing the system's boundary and the
  external systems, actors, or manual processes it interacts with. State
  explicitly where the boundary was drawn and flag any judgment call this
  involved (per Ch5, boundary placement is not always value-free). If the
  system's use within a larger business process matters, pair the context
  model with a short activity-diagram-style description of that process.
- Interaction: produce a use case diagram covering the key use cases
  identified in Context. For each use case that is central to the system
  (not every use case needs this), produce a detailed textual description
  (actors, description, data, stimulus, response, comments) and, where the
  interaction involves multiple components or a non-trivial sequence,
  a sequence diagram showing the call/return flow between them.
- Structural: produce a class diagram for the system's primary domain
  entities, showing classes with their key attributes and operations,
  associations with multiplicity, and any generalization (inheritance) or
  aggregation (whole-part) relationships that are actually present — do not
  invent hierarchy or composition that isn't implied by the requirements.
- Behavioral: based on the system's character (data-driven vs. event-driven,
  stated in Context), produce the matching behavioral model — an activity
  diagram for data-driven processing, a state diagram for event-driven
  behavior, or both if the system is mixed. State which you chose and why.
- Keep class names, actor names, and entity names identical across all
  models — a name introduced in the context model or a use case should
  reappear, unchanged, in the class and behavioral models if it represents
  the same thing.

Non-functional:
- Match the rigor of the models to the stated intended use (discussion vs.
  documentation vs. code-generation-ready) — do not over-specify a model
  meant only to facilitate discussion, and do not under-specify one meant to
  drive code generation.
- Represent every diagram in a textual or text-based diagram notation (e.g.,
  Mermaid, PlantUML-style, or a clearly labeled ASCII sketch) so the models
  are usable without a separate drawing tool.
```

### 5. Constraints

```
- Do not produce a single diagram type and call it complete — all four
  perspectives (context, interaction, structural, behavioral) must be
  represented, even briefly, unless the Context explicitly scopes the task
  to fewer.
- Do not use data-flow diagram (DFD) notation — UML does not include DFDs;
  use UML activity diagrams for data-driven processing instead.
- Do not add generalization or aggregation relationships to the class
  diagram unless they are actually implied by the domain described in
  Context — unjustified hierarchy is a common over-modeling mistake.
- Do not treat this prompt's output as architecture — structural models here
  describe domain/data organization, not system components or deployment.
  That is the Ch6 prompt's job, which takes these models as input context.
- If model-driven engineering is in scope (per Context), do not generate
  implementation-specific detail (a Platform Specific Model) unless a target
  platform is given — stop at a Platform Independent Model and state what
  additional input would be needed to go further.
- If Context fields are marked "unknown," do not silently invent system
  behavior — flag the assumption and state how the models would change if
  the assumption is wrong.
```

### 6. Process

```
[Pick and combine as appropriate:]
- Work through the four perspectives in order (context → interaction →
  structural → behavioral), since later models depend on entities and
  actors established in earlier ones (chain-of-thought / incremental
  disclosure).
- For the class diagram, derive entities and associations from the use case
  descriptions and requirements rather than inventing a data model
  independently (RAG-style grounding against Context).
- If it is genuinely unclear whether the system is data-driven or
  event-driven, briefly state the case for each before choosing the
  behavioral model type (Tree of Thoughts).
- After producing the full set of models, check that every named actor,
  class, and entity is used consistently across diagrams, and revise any
  mismatch (Reflexion / self-critique).
```

### 7. Output Format

```
Deliver, as a single Markdown document:
1. Context model (diagram + boundary explanation, including any judgment
   calls made)
2. Use case diagram (diagram) + detailed description for each central use
   case (actors, description, data, stimulus, response, comments)
3. Sequence diagram(s) for non-trivial interactions, with a short walkthrough
   of each step
4. Class diagram (diagram) with attributes, operations, associations,
   multiplicity, and any generalization/aggregation relationships
5. Behavioral model — activity diagram, state diagram, or both — matched to
   the system's character, with a short explanation of what it shows
6. Explicitly flagged assumptions (if any Context fields were "unknown")
```

### 8. Verification

```
This is complete when:
- All four modeling perspectives are represented, each with the diagram
  type(s) appropriate to it.
- Every class, actor, and entity name is used consistently across every
  diagram it appears in.
- Each central use case has both a textual description and, where the
  interaction is non-trivial, a sequence diagram.
- The behavioral model matches the system's stated character (data-driven
  or event-driven), with that choice explicitly justified.
- Edge case handled: if Context leaves the system boundary or system
  character ambiguous, the ambiguity is named and a reasoned choice is made
  and flagged — not silently resolved or left undecided.
```
