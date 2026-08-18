# Develop — ideation, TRIZ, and choosing a concept

Read this when generating solution candidates, when stuck on a trade-off, or when
selecting between competing concepts.

## Contents

- [Ground rules for ideation](#ground-rules-for-ideation)
- [Ideation techniques](#ideation-techniques)
- [TRIZ](#triz)
- [Envisioning](#envisioning)
- [Selecting a concept](#selecting-a-concept)

## Ground rules for ideation

- **No judgment, no criticism.** Evaluation and generation cannot share a room.
  The instant someone says "that won't work," the flow of ideas stops.
- **Quantity over quality.** Outlandish and provocative ideas are the point —
  they mark the boundaries of the space, and the usable idea often sits next door
  to an absurd one.
- **Don't linger.** A minute per idea, maximum. Detail is convergent thinking in
  disguise.
- **Make everything visible.** Ideas on a shared surface cross-pollinate.
- **Timebox.** Thirty minutes minimum, two hours maximum with breaks.

Sources of inspiration, when the well runs dry:

- Pain points and opportunities from the journey map
- Goals and frustrations from the personas
- **Metaphors** — what is this product like? What is it emphatically *not* like?
  ("What if a phone were a musical instrument?")

## Ideation techniques

### Crazy 8s

Fold a sheet into eight panels. Eight minutes, one idea per panel, one minute
each. The constraint is the mechanism: your first two ideas are things you have
already seen, ideas three through five are variations, and six through eight are
where you finally have to think. Do not stop at four.

### Mind mapping

Central concept, radiating branches. Good for exploring a domain's structure
before deciding what to build in it.

### SCAMPER

Apply each lens to the current solution or the closest existing product:

- **S**ubstitute — what if a component were something else?
- **C**ombine — what if two features merged?
- **A**dapt — what solves this in a different industry?
- **M**odify / magnify / minify — what if a dimension were 10× or 1/10?
- **P**ut to other use — who else could use this, for what?
- **E**liminate — what if we removed the thing everyone assumes is essential?
- **R**everse — what if the order, or the roles, flipped?

Eliminate and Reverse are the two that most often produce something genuinely
new. "What if the user never opened the app at all?" is a real design direction.

### Worst possible idea

Deliberately design the worst version. It is liberating, it is fast, and
inverting the results frequently produces something good. It also surfaces
assumptions you didn't know you had.

### Bizarro world / break the rules

Pick a constraint everyone treats as fixed — a login, a save button, a homepage,
a settings screen — and remove it. Then see what the design must become.

### Brainwriting

Everyone writes ideas silently, then passes them on for others to build upon.
Beats verbal brainstorming when there is a status gradient in the room, because
the loudest voice stops setting the agenda.

### Six Thinking Hats — generating

1. **Blue** frames the user need and goal
2. **White** reviews existing solutions to similar problems, factually
3. **Green** proposes changes and improvements
4. **Blue** decides whether this concept advances

### Analogies

Find a structurally similar problem in another domain and import its solution.
"How does an emergency room triage?" is a real answer to a queueing problem.

## TRIZ

*Theory of Inventive Problem Solving* — developed by Genrich Altshuller, born in
Tashkent, from an analysis of 400,000 patents. Two founding premises:

1. Somebody, somewhere, has already solved your problem or one very like it.
2. Creativity is finding that solution and adapting it.

And one instruction that changes how you design: **do not accept contradictions —
resolve them.**

### Ideality

> Systems evolve toward delivering more benefit with fewer inputs and fewer
> harms.

$$\text{Ideality} = \frac{\sum \text{benefits}}{\sum \text{costs} + \sum \text{harms}}$$

The **Ideal Final Result** is the outcome achieved with no cost and no harm —
usually impossible, but naming it reframes the problem productively.

The classic illustration: a soap factory occasionally ships empty boxes. The
engineered answer is an X-ray scanner on the line — expensive. The IFR answer is
a fan at the end of the conveyor that blows the empty boxes off. Asking "what
resource do we already have?" beat asking "what machine should we buy?"

When stuck, ask: *what already present in this system could solve this for free?*
In software the free resources are usually data you already collect, a moment the
user is already idle, or a step they are already taking.

### Trends of technical evolution

Useful for predicting where a product should go next:

- **Simplicity → complexity → simplicity.** Systems start simple, accrete
  features, then re-integrate into something simple again. If your product is
  mid-bloat, the next winning move is consolidation, not another feature.
- **Increasing segmentation.** Monolith → components → services → fields. In
  software: monolith → modules → microservices → serverless functions.
- **Increasing dynamization and controllability.** Rigid → jointed → flexible →
  fluid. In interfaces: fixed layouts → responsive → adaptive → personalized.

### Technical contradictions

A technical contradiction is: *improving parameter A makes parameter B worse.*

The conventional response is a compromise. TRIZ's response is to find the
solution where both improve, by consulting what worked for the same contradiction
elsewhere. Classically this means mapping A and B onto 39 standard engineering
parameters, reading the 39×39 contradiction matrix, and applying the inventive
principles it suggests.

The 40 inventive principles, which transfer surprisingly well to software:

| # | Principle | # | Principle |
|---|---|---|---|
| 1 | Segmentation | 21 | Skipping (rush through) |
| 2 | Separation / taking out | 22 | Blessing in disguise |
| 3 | Local quality | 23 | Feedback |
| 4 | Asymmetry | 24 | Intermediary |
| 5 | Merging | 25 | Self-service |
| 6 | Multi-functionality | 26 | Copying |
| 7 | Nested doll | 27 | Cheap disposables |
| 8 | Weight compensation | 28 | Substitute mechanical means |
| 9 | Preliminary anti-action | 29 | Pneumatics and hydraulics |
| 10 | Preliminary action | 30 | Flexible shells, thin films |
| 11 | Beforehand cushioning | 31 | Porous materials |
| 12 | Equipotentiality | 32 | Color changes |
| 13 | The other way around | 33 | Homogeneity |
| 14 | Curvature / spheroidality | 34 | Discarding and recovering |
| 15 | Dynamics | 35 | Parameter changes |
| 16 | Partial or excessive action | 36 | Phase transitions |
| 17 | Another dimension | 37 | Thermal expansion |
| 18 | Mechanical vibration | 38 | Strong oxidants |
| 19 | Periodic action | 39 | Inert atmosphere |
| 20 | Continuity of useful action | 40 | Composite materials |

Software readings of the ones that carry over best:

- **1 Segmentation** — split a monolithic flow into steps; split a big form into
  a wizard; chunk a long list.
- **2 Separation** — extract the harmful part rather than fixing the whole.
- **3 Local quality** — different parts of the UI get different treatment rather
  than uniform styling; per-user configuration.
- **10 Preliminary action** — do the work before it is needed. Prefetch,
  precompute, pre-fill.
- **13 The other way around** — invert the interaction. Instead of the user
  searching, the system suggests. Instead of opt-in, opt-out.
- **15 Dynamics** — the interface adapts to context, usage, or expertise.
- **17 Another dimension** — use a layer, a modal, a timeline, a second axis.
- **23 Feedback** — add a feedback loop where there was open-loop guessing.
- **24 Intermediary** — insert a translating layer between two things that don't
  fit.
- **25 Self-service** — the system heals or configures itself.
- **22 Blessing in disguise** — turn the harm into the resource (the fan and the
  empty soap box).

### Physical contradictions

A physical contradiction is sharper: *one thing must be both A and not-A.*

- The filling must be hot to pour and cold to not melt the chocolate.
- The aircraft must be streamlined to fly fast and have protrusions to maneuver
  on the ground.
- **Software must be simple to use and rich in features.**

Resolve by **separation** — the single most useful TRIZ idea for interface work:

| Separation | Statement | Software examples |
|---|---|---|
| **In time** | +C at time 1, −C at time 2 | Progressive disclosure; onboarding simple then advanced; retractable landing gear |
| **In space** | +C in region 1, −C in region 2 | Simple main view, dense side panel; basic tab vs advanced tab; bifocal lens |
| **In condition** | +C under condition 1, −C under condition 2 | Beginner vs expert mode; responsive breakpoints; photochromic sunglasses |
| **Whole vs parts** | +C partially, −C as a whole | Bicycle chain: rigid links, flexible chain. Simple components composing a powerful system; plugin architectures |

The habit worth building: whenever you catch yourself proposing a compromise
("somewhat simple, somewhat powerful"), stop and write the contradiction down
explicitly. Then ask which of the four separations applies. A compromise satisfies
nobody; a separation satisfies both.

## Envisioning

Making ideas visible so they can be examined — by you and by others. The medium
should match the stage: rough early, refined late.

**Sketches.** Quick, cheap, disposable, plentiful. That is the entire value
proposition — you should be willing to throw them away. More sketches means more
options. Polished mockups produced too early get defended instead of tested.

**User flows.** Map the steps to complete a task. Four node types, kept visually
distinct:

- User action
- User decision
- System response
- System decision

Draw the happy path first, then add every branch where something can go wrong.
The branches are where the design work actually is.

**Wireframes.** Layout, navigation, and information architecture — no color, no
typography, no imagery. Hand-drawn is genuinely preferable early: it signals
"unfinished, argue with the structure" in a way that a clean Figma frame does not.

## Selecting a concept

Now switch to convergent thinking. Name your criteria before you look at the
options, or you will rationalize whichever one you already liked.

**Dot voting.** Each participant gets N dots to place. Fast, but anchors on
whoever votes first — use **secret voting** when there is a status gradient.

**Benefit/effort matrix.** Two axes, four quadrants. High benefit + low effort
first; high benefit + high effort becomes roadmap; low benefit + low effort is a
distraction that feels productive; low benefit + high effort dies now.

**Pros/cons (force field).** For each concept, forces driving toward it and
forces resisting. Good when the resistance is organizational rather than
technical.

**Pugh matrix.** The most rigorous option. Pick one concept as the datum. Score
every other concept against it per criterion as **+ / 0 / −**. Sum. Weight
criteria if some genuinely matter more. Its real value is not the total — it is
that the highest-scoring concept usually suggests a hybrid: take the "+" columns
from several concepts and build a new candidate.

**Six Thinking Hats — selecting.**

1. **Blue** restates the need and goal
2. **White** gives an objective account of the concept and its alternatives
3. **Yellow** argues the benefits
4. **Black** argues the limitations and risks
5. **Red** states gut feelings, without justification
6. **Blue** decides

The Red hat is not decoration. A concept everyone can defend logically but nobody
feels good about tends to fail in ways the logical analysis missed.
