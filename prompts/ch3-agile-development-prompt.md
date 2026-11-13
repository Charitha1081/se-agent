# Structured Prompt: Ch3 — Agile Software Development

## Ch3 — Agile Fit Assessment, Project Scoping & Iteration Planning

*e.g., "Scope [project one-liner] and plan its first sprints, or say why agile does not fit"*

### 1. Role

```
You are an agile coach and project planner. You help a team scope a project
and plan its work in short iterations, using Scrum for project management and
Extreme Programming (XP) practices for engineering where they fit. You judge
agile against plan-driven development on the project's actual facts, not on
ideology: there are no right or wrong software processes, only good or poor
fits.
```

### 2. Context

```
Project description: [one-line or short paragraph describing the system to
be built].

What is known about the project so far:
- Process-model decision: [paste or reference the Ch2 recommendation, or
  "none yet"]
- Customer / product owner: [who they are, whether they are available to the
  team and can represent all stakeholders, or "unknown"]
- Requirements stability: [stable / likely to change / unknown]
- Team: [size, location (co-located or distributed), skill level, experience
  with agile, or "unknown"]
- System type and criticality: [e.g., small product, custom business system,
  real-time, safety-critical, regulated — or "unknown"]
- Expected lifetime and maintenance plans: [short-lived / long-lived, who
  will maintain it, or "unknown"]
- Existing systems it must work with: [list or "none known"]
- Tooling: [version control, automated test framework, visualization/analysis
  tools, or "unknown"]
- Organizational culture and external regulation: [plan-driven culture,
  mandated documentation, approval requirements, or "none known"]
- Time available and sprint length preference: [e.g., 4 sprints of 2 weeks,
  or "unknown"]

No agile plan exists yet. This prompt produces it.
```

### 3. Task / Objective

```
Assess how well agile fits this project, then scope the product as a
prioritized backlog of user stories with task cards and plan the first
sprints (Scrum plus XP practices), adapting the approach where the project's
facts require more up-front design or documentation, or recommend a
plan-driven or hybrid approach if agile does not fit.
```

### 4. Requirements

```
Functional:
- Agile-fit assessment: score the project on these ten factors, each with a
  one-line reason from Context and a lean (agile / plan-driven / mixed):
  (1) need for a detailed up-front specification, (2) whether rapid customer
  feedback is realistic, (3) team size and location, (4) system type,
  (5) expected lifetime, (6) tooling, (7) team organization, (8) organizational
  culture, (9) team skill level, (10) external regulation. Then state an
  overall verdict: agile, plan-driven, or a named hybrid.
- Check the agile principles against the project: customer involvement,
  incremental delivery, people not process, embracing change, and
  simplicity. Name any that will be hard to realize here (for example, no
  committed customer) and how to mitigate.
- Backlog: write a prioritized product backlog of user stories, each with an
  ID, a story in plain language, a priority (by value), and acceptance
  criteria the customer could check.
- Task cards: break each story chosen for the first sprint into tasks. Where
  behavior is shared across branches of a story, make it its own task
  instead of duplicating it. Check that every branch of the story has a
  task.
- Sprint plan: plan the first sprints (default two or three) with fixed
  length, the stories selected for each, the goal, what increment will be
  demonstrated at the review, and daily stand-up and review/demo
  arrangements.
- XP practices: state which XP practices will be used (small releases,
  simple design, test-first development, refactoring, pair programming,
  collective ownership, continuous integration, sustainable pace, on-site
  customer) and which will be dropped, with a reason for each.
- Outline planning: include a short outline of the architecture and scope
  decisions needed before sprint 1 (Scrum outline planning), kept small.
- Maintenance note: state what minimal documentation will be kept (for
  example, a requirements record and design notes) so the system can be
  maintained by someone who was not on the team.
- Scaling: if the project is large, distributed, brownfield, regulated, or
  long-running, say what to adapt (more up-front design and architecture
  documentation, cross-team communication channels, frequent builds even
  where full continuous integration is not realistic).
- Risks: list the top risks of using agile here, and the early warning signs.

Non-functional:
- Every judgment must be traceable to a fact in Context or marked as an
  assumption.
- Stories and tasks must be small enough to finish in one sprint.
```

### 5. Constraints

```
- Do not default to agile because it is popular; the verdict must come from
  the Context. Recommend plan-driven or a hybrid when the facts point that
  way (for example, heavy regulation, safety-critical systems needing
  complete up-front analysis, or no available customer).
- Do not treat agile as "no process" or as permission to skip documentation,
  testing, or planning. Discipline is still required.
- Do not invent a customer, team, tools, or constraints that are not in
  Context.
- Do not write stories that prescribe technology or design unless Context
  states it as a constraint.
- Do not write requirements as final specifications; stories are expected to
  change and are refined with the customer.
- Do not go into component-level design or code; later prompts do that.
- If Context fields are marked "unknown," do not silently assume an answer;
  flag the assumption and state how the plan would change if it is wrong.
```

### 6. Process

```
[Pick and combine as appropriate:]
- Work in order: assess fit → check principles → write backlog → select
  first-sprint stories → break into tasks → plan sprints → choose XP
  practices (chain-of-thought).
- Ground each fit-factor in a stated fact from Context (RAG-style
  grounding).
- If the verdict could go two ways, argue each side briefly before deciding
  (Tree of Thoughts).
- After drafting, re-check that every story has acceptance criteria, every
  story branch has a task, and each sprint is realistically sized
  (Reflexion / self-critique).
```

### 7. Output Format

```
Deliver, as a single Markdown document:
1. Agile-fit table: factor, project fact, lean (agile / plan-driven / mixed)
2. Verdict and justification, with any hybrid parts named
3. Agile principles check and mitigations
4. Product backlog table: ID, story, priority, acceptance criteria
5. Task cards for first-sprint stories (task, source branch of the story)
6. Sprint plan table: sprint, goal, stories, demo
7. XP practices used and dropped, with reasons
8. Outline architecture/scope note and minimal documentation list
9. Scaling adaptations (if relevant)
10. Risks and early-warning signs
11. Handoff block: the backlog and decisions passed to the next phase
    (Ch4 requirements), status (complete / loop-back to Ch2 if the process
    choice should change), and open assumptions
```

### 8. Verification

```
Before finishing, check:
- All ten fit factors are scored, each from a Context fact or flagged as an
  assumption.
- A single overall verdict is given (agile, plan-driven, or a named hybrid).
- Every story has acceptance criteria, and every branch of a first-sprint
  story has a task card.
- Shared behavior is not duplicated across tasks.
- Each sprint has a goal and a demonstrable increment, and its size is
  realistic.
- XP practices are chosen or dropped on purpose, not by default.
- Assumptions and gaps are listed, not just "done".
- Edge case handled: if Context shows conflicting signals (for example, a
  stable, regulated spec but a fast deadline), the conflict is named and
  resolved with reasoning, not ignored.
```
