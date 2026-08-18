# Templates

Fill-in structures for every artifact in the pipeline. Copy the ones the current
lane needs; delete rows that carry no information rather than padding them.

---

## design/problem.md

```markdown
# Problem statement

## Statement
[User] needs [need] in order to accomplish [goal].

## How Might We
How might we [reframed question]?

## Five Ws
- **Who** is experiencing this:
- **What** are they trying to accomplish:
- **Where** does it occur:
- **When** does it take place:
- **Why** does it matter:

## Cause and effect
| Root cause | Visible effect |
|---|---|
|  |  |

## Success metrics
| Metric | Baseline | Target |
|---|---|---|
| Time on task |  |  |
| Steps to complete |  |  |
| Error moments |  |  |
| First-time success rate |  |  |

## Non-goals
- This design does NOT address …

## Assumptions
| Assumption | Confidence | If wrong, what breaks | Cheapest way to test |
|---|---|---|---|
|  |  |  |  |
```

---

## design/personas.md

```markdown
# Personas

## Primary: [Name]

> "[A quote capturing their attitude in one line]"

**Age / Occupation / Location:**
**Context:** where and when they use this, on what device, in what state

### Goals
-

### Frustrations
-

### Narrative
[A paragraph: their situation, what they already know, what they've tried,
what they're working around.]

### Design-relevant attributes
| Attribute | Value | Design consequence |
|---|---|---|
| Digital literacy |  |  |
| Language |  |  |
| Accessibility needs |  |  |
| Device / connectivity |  |  |
| Time pressure |  |  |
| Environment |  |  |

### Evidence
Based on: [research / assumed — say which]

---

## Secondary: [Name]
[Only include if this persona changes a design decision. Say which one.]
```

---

## design/journey.md

```markdown
# User journey — [persona] × [scenario]

|  | Stage 1 | Stage 2 | Stage 3 | Stage 4 |
|---|---|---|---|---|
| **Touchpoints** |  |  |  |  |
| **Actions** |  |  |  |  |
| **Thoughts** |  |  |  |  |
| **Emotion** | 😟 | 😌 | 😀 | 😄 |
| **Pain points** |  |  |  |  |
| **Opportunities** |  |  |  |  |

## Emotional curve
Lowest point: [stage] — [why]
Peak: [stage] — [why]
Ending: [stage] — [how it leaves them]

## Ranked pain points
1. [most severe] — severity, frequency, who it affects
2.
```

---

## Current-state user story (the problem)

```markdown
# [Persona name]'s day — current experience

1. [Opening context — who they are, where they are, what they need] 😐
2. [First attempt] 🙂
3. [First obstacle] 😕
4. [Escalation] 😟
5. [Failure or workaround] 😞
6. [Aftermath — how they feel about it] 😐

## Where the design fails them
| # | Failure | Type | Principle violated |
|---|---|---|---|
| 1 |  | language / context / knowledge / support |  |

## Baseline metrics
| Metric | Value |
|---|---|
| Time to complete |  |
| Number of steps |  |
| Error moments |  |
| Positive emotional moments |  |
| Negative emotional moments |  |
| Likelihood to reuse |  |
```

---

## Concrete scenario (the solution)

```markdown
# [Persona name] using [product]

Same persona, same triggering situation. Narrated in the vocabulary of the
actual interface.

1. [Same opening context] 😐
2. [First interaction with the new design] 🙂
3. [The moment the design helps] 😀
4. [Task completed] 😌
5. [Goal actually met — beyond the transaction] 😄

## Metrics after
| Metric | Before | After |
|---|---|---|
| Time to complete |  |  |
| Number of steps |  |  |
| Error moments |  |  |
| Positive emotional moments |  |  |
| Negative emotional moments |  |  |
```

---

## design/flows.md

```markdown
# User flows

## Key path: [primary task]

Node types: [action] · <decision> · (system response) · {system decision}

```
[Entry point]
   ↓
[User action]
   ↓
(System response)
   ↓
<User decision> ──no──> [Alternative path]
   ↓ yes
(System response)
   ↓
[Goal achieved]
```

### Failure branches
| Step | What can go wrong | How the design handles it |
|---|---|---|
|  |  |  |

## Validation scenarios
- **Alternative:**
- **Necessary-use:**
- **Edge case:**
- **Empty state:**
- **Error state:**
- **Offline / slow:**
```

---

## design/framework.md

```markdown
# Interaction framework

## 1. Form factor, posture, input
- **Form factor:**
- **Posture:** sovereign / transient / daemonic / satellite / standalone / kiosk
- **Why this posture:**
- **Input methods:**

## 2. Data elements (the nouns)
| Object | Key attributes | Matches mental model? | Relationships |
|---|---|---|---|
|  |  |  |  |

## 3. Functional elements (the verbs)
| Action | On object | How it's surfaced | What would a helpful human do? |
|---|---|---|---|
|  |  |  |  |

## 4. Views and hierarchy
| View | Goal it serves | Contains | Space needed |
|---|---|---|---|
|  |  |  |  |

## 5. Navigation model
Model: step-by-step / hub / connected / tree / pan-and-zoom / pyramid
Why:

At every screen, the user can answer:
- Where am I? →
- Where did I come from? →
- Where can I go next? →

## 6. Key path narration
[Narrate the persona completing the primary task through this framework.
If any step reads awkwardly, the framework is wrong — fix it here, not later.]
```

---

## design/evaluation.md

```markdown
# Evaluation

Method: heuristic evaluation / cognitive walkthrough / usability test
Evaluated by: [who] as [persona]
Artifact: [what was evaluated — sketch, prototype, build]

## Cognitive walkthrough
| Step | Knows the goal? | Notices the control? | Connects control to goal? | Sees progress? | Defect |
|---|---|---|---|---|---|
| 1 | ✓ | ✓ | ✗ | ✓ | Label "Sync" doesn't read as "save my work" |

## Heuristic findings
| # | Finding | Where | Heuristic violated | Severity | Recommendation | Status |
|---|---|---|---|---|---|---|
| 1 |  |  |  | 3 |  | fixed / deferred |

Severity: 3 = blocks task or loses data · 2 = significant friction · 1 = cosmetic

## Heuristic checklist
| # | Heuristic | Pass | Note |
|---|---|---|---|
| 1 | Visibility of system status |  |  |
| 2 | Match with the real world |  |  |
| 3 | User control and freedom |  |  |
| 4 | Consistency and standards |  |  |
| 5 | Error prevention |  |  |
| 6 | Recognition over recall |  |  |
| 7 | Flexibility and efficiency |  |  |
| 8 | Aesthetic and minimalist design |  |  |
| 9 | Error recognition and recovery |  |  |
| 10 | Help and documentation |  |  |

## Deferred findings and why
- [Finding] — deferred because [reason]. Revisit when [condition].

## Metrics
| Metric | Target | Measured |
|---|---|---|
|  |  |  |
```

---

## Concept selection — Pugh matrix

```markdown
# Concept selection

Datum (baseline): [current solution or Concept A]

| Criterion | Weight | A (datum) | B | C |
|---|---|---|---|---|
| Solves primary pain point | 3 | 0 | + | + |
| Effort to build | 2 | 0 | − | + |
| Fits persona's literacy | 3 | 0 | + | 0 |
| Accessible | 2 | 0 | 0 | + |
| **Weighted total** |  | 0 |  |  |

Winner:
Hybrid opportunity: [take the "+" columns from several concepts]
Selection criteria were declared before scoring: yes / no
```
