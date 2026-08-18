---
name: human-centered-design
description: >-
  Design software the way a UX practitioner would before and while coding it —
  research the real user, name the problem, model the interaction, then build
  and evaluate against usability heuristics. Use this whenever the work touches
  something a human will look at or operate — building or redesigning an app,
  screen, dashboard, form, onboarding flow, CLI, settings panel, or error/empty
  state; choosing information architecture or navigation; writing UI copy;
  deciding what a feature should actually do; or diagnosing complaints like
  "users keep getting confused", "nobody finds this button", "this flow feels
  clunky". Also use it when asked for personas, user stories, scenarios, journey
  maps, user flows, wireframes, heuristic evaluation, cognitive walkthrough,
  usability test plans, or TRIZ/SCAMPER ideation. Reach for it even when the
  request sounds purely like engineering ("build me a habit tracker") — the code
  is the easy part, and building the wrong thing well is the most expensive
  mistake available.
---

# Human-Centered Design

## Why this exists

Most software that fails does not fail technically. It compiles, it ships, it
passes tests — and people still cannot use it. The failure is upstream: nobody
established who the user is, what they were actually trying to do, or what state
they were in when they tried to do it.

The discipline below is the antidote. It is not decoration on top of
engineering; it is the part of engineering that decides whether the code was
worth writing. Work through it, then build.

## Scale the process to the stakes

Running the full pipeline on a button color change wastes everyone's time. Judge
the scope first and pick a lane:

| Situation | What to do |
|---|---|
| New product, new app, or a feature nobody has built before | Full pipeline, all four phases |
| Adding a screen or flow to something that exists | Skip to Define; reuse the existing personas/IA; do Deliver + Evaluate properly |
| Changing one interaction, fixing a confusing control | Just the relevant principles + a heuristic pass |
| Debugging a usability complaint | Start at Evaluate (cognitive walkthrough), work backwards to the cause |

State which lane you picked and why, in one line, before you start. The user
should never be surprised by how much or how little process they got.

## The pipeline: Double Diamond

Design alternates between opening up and narrowing down. Two diamonds, four
phases:

```
   DISCOVER  →  DEFINE  →   DEVELOP   →  DELIVER
  (diverge)   (converge)   (diverge)    (converge)
       ◆ problem space ◆    ◆ solution space ◆
                      ↑
              the design brief
       (get this wrong and everything
        downstream solves the wrong problem)
```

The most important artifact in the whole process is the problem statement at the
waist of the first diamond. Do not let the conversation leap from "I want an app
for X" straight to screens. That jump is where the wrong product gets built.

Expect to loop. Real design goes forward and backward many times. If your first
pass through Deliver reveals the problem statement was wrong, go back and fix
it — that is the process working, not failing.

### Phase 1 — Discover (diverge on the problem)

Goal: understand the user's actual situation, not the one you assume.

Working with a human who has the domain knowledge, ask rather than invent. Three
rules of user research: go to them, talk to them, write it down. In an agent
context you usually cannot go anywhere, so the honest move is to ask the user
targeted questions and clearly label anything you had to assume.

Do this:

- Write a research goal in one sentence: *"I am going to research [activity] so
  that I can [project goal]."*
- Get concrete stories, not opinions. "Walk me through the last time you did
  this" beats "what features do you want?" People cannot tell you what they need;
  they can tell you what happened.
- Ask *why* twice. Why is this activity done? Why is it done **this way**? The
  second question is where the design opportunities hide.
- Avoid leading questions ("wasn't that confusing?"). Avoid making the user a
  designer — collect problems from them, not solutions.
- Note the context: where they are, what else has their attention, what they are
  holding, what they already know.

If genuine research is impossible, say so explicitly and mark your personas and
scenarios as **assumed** — an assumption you flagged is useful; an assumption you
smuggled in as fact is dangerous.

Details on interviews, probes, card sorting, surveys, analytics, and turning raw
quotes into needs: `references/discover.md`.

### Phase 2 — Define (converge on the problem)

Turn what you learned into three artifacts:

**1. Problem statement.** Use one of these shapes:
> `[user]` needs `[need]` in order to accomplish `[goal]`.
> `[user]` needs `[job]` because `[insight]`.

Then reframe it as a **How Might We** question to open the solution space:
*"How might we help busy parents quickly plan healthy meals?"*

**2. Personas.** One primary, at most two secondary. A persona is only useful if
it constrains decisions. Give it a name, context, goals, frustrations, and
critically the **attributes that change the design** — digital literacy,
language, physical constraints, when and where they use this, what device.
A persona with no sharp edges is decoration.

**3. Journey map.** Stages across the top; for each stage: touchpoints, actions,
thoughts, emotion, pain points. The pain points are your feature backlog and the
emotional lows are where design effort pays off most.

Write the problem statement, personas, and journey map to files (e.g. under
`design/`) rather than only into chat. They are referenced constantly later.

Templates and the full method: `references/define.md`, `assets/templates.md`.

### Phase 3 — Develop (diverge on the solution)

Generate many candidate solutions before committing to one. The rule that makes
this work is *quantity over quality, no judgment* — evaluation kills ideation if
you let them share a room.

Useful generators, in rough order of usefulness for software:

- **Crazy 8s** — eight distinct concepts, one minute each. Forces you past the
  first obvious answer, which is usually the one everyone has already seen.
- **Pain-point mining** — walk the journey map and generate one idea per low.
- **SCAMPER** — Substitute, Combine, Adapt, Modify, Put to other use, Eliminate,
  Reverse, applied to the current solution.
- **TRIZ contradictions** — when you are stuck on a trade-off ("it must be simple
  *and* powerful"), don't split the difference. Name the contradiction and
  resolve it by separating in time, space, condition, or between whole and parts.
  Progressive disclosure, adaptive UI, and modes are all TRIZ separations.
  See `references/develop.md`.
- **Six Thinking Hats** — structured critique when choosing between concepts.

Then converge: dot voting, benefit/effort matrix, or a Pugh matrix against the
current baseline. Say out loud which criteria you are selecting on.

Envision the chosen direction before building it: a concrete scenario (a story of
the persona succeeding, written in the future product's vocabulary), a user flow
(actions, decisions, system responses), and low-fidelity wireframes. Low fidelity
on purpose — polished mockups invite arguments about color instead of structure.

### Phase 4 — Deliver (converge on the solution)

Now design the actual thing, in this order. This ordering exists because
committing to widgets early locks in a structure you will regret.

1. **Form factor, posture, input.** Desktop / web / mobile / kiosk / CLI. How
   much of the user's attention does this deserve — sovereign (all of it, for
   hours), transient (brief, appears and leaves), or daemonic (background,
   surfaces only when needed)? Posture drives nearly every later decision:
   sovereign apps can afford density and shortcuts; transient ones need big,
   obvious, forgiving controls.
2. **Data elements and functional elements.** What objects exist (the nouns the
   user thinks in), and what operations exist on them (the verbs). Do an
   object-action analysis across your scenarios and merge duplicates — this is
   also, conveniently, most of your data model.
3. **Functional groups and hierarchy.** Which elements are used together, in what
   sequence, needing how much space. Group them into views. Separate goals get
   separate views; overlapping goals share one.
4. **Sketch the interaction framework.** Panes, regions, containers — named and
   described, no widget-level detail yet.
5. **Key path scenarios.** Narrate the persona completing the primary task
   through your actual framework. If the narration gets awkward, the framework is
   wrong. This is the cheapest bug-finding you will ever do.
6. **Validation scenarios.** The infrequent paths: alternatives,
   necessary-but-rare functions, edge cases, and everything that can go wrong.
   Ask "what if…" until you stop finding holes.

Then implement, applying the principles below.

Information architecture, navigation patterns, platform-specific guidance, and
visual design: `references/deliver.md`.

## The principles that make an interface work

These are the load-bearing ideas. Apply them while coding, not as a review
afterwards.

**Discoverability and understanding.** Can the user figure out what actions are
possible, and where and how to perform them? Do they understand what it all
means? If the answer requires a manual, the design is doing the manual's job
badly.

**Affordances and signifiers.** An affordance is what an action the interface
*makes possible*; a signifier is the perceivable cue that *tells the user* it is
possible. Digital interfaces have almost no real affordances — a swipe is
invisible until something signals it. So: every non-obvious capability needs a
signifier. And the inverse, which is the more commonly violated half: *if a
simple thing needs a signifier to explain it, the design has already failed.*

**Mapping.** Controls should sit near what they control, and their arrangement
should mirror the arrangement of what they affect. Natural mapping cuts learning
time; stimulus-response compatibility cuts reaction time.

**Feedback.** Every action gets a response — immediate, informative, unobtrusive,
and proportionate to its importance. Poor feedback is worse than none: it
distracts and creates anxiety without informing. Under ~400 ms feels
instantaneous; past that, show progress and say what is happening.

**Constraints.** Restrict the wrong actions to make the right ones discoverable.
Physical, cultural, semantic, and logical constraints all work; so do forcing
functions, interlocks, and confirmations for destructive acts. Prefer making an
error impossible over explaining it afterwards.

**Conceptual model.** The user builds a mental model of how your system works
from its appearance, its behavior, and its words. A good conceptual model
teaches the working principle, not just the button locations. Design the model
deliberately, then make everything consistent with it — because the user will
build one whether you helped or not.

**Bridge the two gulfs.** The *gulf of execution* (how do I do this?) is closed
by affordances, signifiers, constraints, and mapping. The *gulf of evaluation*
(what just happened?) is closed by feedback and a clear conceptual model. Every
usability problem you will ever find lives in one of those two gulfs.

### Design for human limits, not idealized users

- **Working memory holds about 3–4 chunks**, decaying in ~30 seconds. Never
  require carrying information from one screen to another. Prefer recognition
  over recall — show the options rather than making people remember them.
- **Hick's Law** — decision time grows with the number and complexity of choices.
  Break big decisions into steps; highlight a recommended option.
- **Fitts's Law** — time to hit a target depends on its distance and size. Make
  frequent targets big and close; put destructive ones far away and small-ish.
- **Jakob's Law** — users spend most of their time in *other* software and expect
  yours to work like it. Novel interaction patterns cost the user real effort;
  spend that budget only where the novelty is the point.
- **Peak-End Rule** — people judge an experience by its most intense moment and
  its ending, not its average. Invest in the peak and the finish. Negative peaks
  are remembered far more vividly than positive ones.
- **Aesthetic-Usability Effect** — a more attractive interface is *perceived* as
  more usable, and users forgive more of its flaws. Polish is not frivolous.
- **Gestalt grouping** — proximity, similarity, continuity, and figure-ground do
  more organizational work than any border or label you can add. Use whitespace
  before you use dividers.
- **Read flow** — put actions where the eye ends up. In left-to-right languages:
  back/cancel/previous on the left, next/submit/continue on the right, and the
  most likely action last.

More on perception, attention, memory, and reading: `references/human-factors.md`.

### Errors are a design property, not a user property

Distinguish **mistakes** (the wrong goal — a broken mental model, conscious
level) from **slips** (the right goal, wrong execution — subconscious, and
unavoidable in skilled users). They need different fixes: mistakes need a clearer
conceptual model; slips need constraints, confirmations, and undo.

Never blame the user. If someone made an error, the design permitted it.

For error messages: be specific and constructive ("please enter your name", not
"invalid entry"), let the system take the blame ("unrecognized command", not
"illegal command"), skip the threatening vocabulary (*fatal*, *aborted*,
*catastrophic*), never shout in capitals, and always say what to do next.

For recovery: undo everywhere, cancel for anything in progress, confirmation only
for genuinely destructive acts, sanity checks on input, and return the user to
the field that needs fixing rather than making them hunt for it.

## Evaluate — always, not at the end

Evaluation is not a final gate. It is cheapest before code exists (formative) and
most expensive after ship (summative). Build in at least one evaluation pass
whenever you produce something a person will use.

**Heuristic evaluation.** Walk your primary scenario as the persona and score
each step 1–3 for severity against Nielsen's ten:

1. Visibility of system status
2. Match between system and the real world
3. User control and freedom (a clearly marked emergency exit)
4. Consistency and standards
5. Error prevention
6. Recognition rather than recall
7. Flexibility and efficiency of use
8. Aesthetic and minimalist design
9. Help users recognize, diagnose, and recover from errors
10. Help and documentation

**Cognitive walkthrough.** At each step of the flow, ask four questions:
will the user know what goal they need to achieve here; will they notice the
control that does it; will they connect that control to their goal; and after
acting, will they see that progress was made? Any "no" is a flagged defect.

**Usability metrics** worth stating targets for: time on task, number of steps,
error count and severity, recovery rate, success rate for first-time versus
returning users, and satisfaction. Comparing before/after numbers is what turns a
design opinion into an argument.

When you finish building, run the heuristic pass on your own work and report the
findings honestly, including the ones you chose not to fix and why. A self-review
that finds nothing is a self-review that was not performed.

Full evaluation protocols, including how to plan a participant test:
`references/evaluate.md`.

## What to actually hand over

Match the artifacts to the lane you picked. For a full pipeline, write these into
the repo (a `design/` directory works well) so they survive the conversation:

- `problem.md` — problem statement, How Might We, scope and non-goals
- `personas.md` — primary persona, plus secondaries if they change decisions
- `journey.md` — journey map with pain points marked
- `flows.md` — user flow(s) and key path scenario
- `framework.md` — views, data elements, functional elements, hierarchy
- `evaluation.md` — heuristic pass, findings, severity, what was fixed

Then the implementation itself. Keep the design files updated as the build
changes them — a design document that has drifted from the code is worse than
none, because it lies with authority.

Always name your assumptions. The single most valuable line you can write is
*"I assumed the primary user is X; if that's wrong, sections 2 and 4 change."*

## Reference files

Read these when the phase calls for them — no need to load them all up front.

- `references/discover.md` — research methods: interviews, observation, probes,
  card sorting, surveys, analytics, A/B testing; translating raw data into needs;
  Kano model
- `references/define.md` — problem statements, Five Ws, persona types, scenarios
  and storyboards, journey maps, stakeholder analysis
- `references/develop.md` — ideation techniques in detail; TRIZ contradictions
  and separation principles; concept selection (Pugh matrix, benefit/effort)
- `references/deliver.md` — interaction framework steps, information
  architecture, navigation models and patterns, platform postures, visual
  interface design, design systems
- `references/evaluate.md` — heuristic evaluation, cognitive walkthrough,
  usability test protocol, metrics tables, deceptive patterns to avoid
- `references/human-factors.md` — perception, attention, memory, reading,
  Gestalt, reaction times, the laws of UX
- `assets/templates.md` — fill-in templates for every artifact above

## Provenance

Distilled from a Creative Engineering Design lecture series (Inha University in
Tashkent, Dr. Oybek Eraliev), which draws on Norman's *The Design of Everyday
Things*, Cooper's *About Face*, Nielsen's usability heuristics, Benyon's
*Designing Interactive Systems*, and Altshuller's TRIZ.
