# Evaluate — testing designs against reality

Read this when reviewing a design, diagnosing a usability complaint, planning a
test, or reporting on your own work.

## Contents

- [Formative vs summative](#formative-vs-summative)
- [Heuristic evaluation](#heuristic-evaluation)
- [Cognitive walkthrough](#cognitive-walkthrough)
- [Usability testing with participants](#usability-testing-with-participants)
- [Usability metrics](#usability-metrics)
- [Reporting findings](#reporting-findings)
- [Deceptive patterns to avoid](#deceptive-patterns-to-avoid)

## Formative vs summative

**Formative** evaluation happens *during* design, before or while coding. Its
purpose is to find problems while changing them is still cheap. This is where
almost all the value is.

**Summative** evaluation happens on a finished product, usually to compare
against a competitor or a previous version before a redesign. Necessary, but by
then every finding is expensive.

The practical implication: evaluate at every stage, on whatever exists — sketch,
wireframe, prototype, staging build. A defect found on paper costs a pencil
stroke; the same defect found after launch costs a release cycle and some
goodwill.

## Heuristic evaluation

Experts walk representative tasks as a persona and judge each step against
established principles, assigning severity.

### Nielsen's ten heuristics

**1. Visibility of system status.** Keep users informed about what is happening
through timely feedback. Show current state, location, and available actions.
*Like a "You are here" marker on a mall map.*

**2. Match between system and the real world.** Speak the user's language. Use
familiar words, phrases, and concepts rather than internal jargon. Follow
real-world conventions; present information in a natural order. *Like stovetop
controls arranged to match the burners.*

**3. User control and freedom.** Users act by mistake. Give a clearly marked
emergency exit — undo, cancel, back — without a lengthy process. *Like a clearly
marked fire exit.*

**4. Consistency and standards.** Users should never wonder whether different
words, situations, or actions mean the same thing. Follow platform and industry
convention. *Like hotel check-in desks always being near the entrance.*

**5. Error prevention.** Good error messages matter, but preventing the error
matters more. Either eliminate error-prone conditions, or check for them and ask
for confirmation before the user commits. *Like guard rails on a mountain road.*

**6. Recognition rather than recall.** Minimize memory load. Make elements,
actions, and options visible. Users should not have to remember information from
one part of the interface to another. *"Is Lisbon the capital of Portugal?" is
much easier than "What is the capital of Portugal?"*

**7. Flexibility and efficiency of use.** Shortcuts, hidden from novices, speed
up experts. Let users tailor frequent actions. *Like locals taking a shortcut off
the marked route.*

**8. Aesthetic and minimalist design.** Interfaces should not contain irrelevant
or rarely needed information. Every extra unit of information competes with the
relevant ones and reduces their visibility. *Like an ornate teapot whose
decoration makes it hard to hold and hard to wash.*

**9. Help users recognize, diagnose, and recover from errors.** Plain language,
no error codes, precise about the problem, constructive about the solution.

**10. Help and documentation.** Ideally unnecessary; realistically, provide it —
searchable, task-focused, concrete, and available in context. *Like an
information kiosk at an airport.*

### Severity scale

| Rating | Meaning | Action |
|---|---|---|
| 3 | Critical — blocks task completion or causes data loss | Fix before ship |
| 2 | Major — significant delay, frustration, or repeated error | Fix this cycle |
| 1 | Minor — cosmetic or occasional annoyance | Backlog |

### Compressed version

When there is no time for the full ten, five overarching principles cover most of
the ground:

1. Ease of learning
2. Ease of remembering
3. Effectiveness in use
4. Error prevention and recovery
5. Satisfaction

### Running one on your own work

Self-evaluation is worth doing even though it is weaker than independent review.
To keep it honest:

- Walk the flow *as the persona*, not as yourself. You know where everything is;
  they don't.
- Go step by step through the actual built artifact, not your memory of the plan.
- Write findings before writing fixes — deciding what to do changes what you see.
- Report the findings you chose not to fix, with the reason. This is the part
  that makes the review credible.
- Zero findings means the review did not happen.

## Cognitive walkthrough

A systematic, paper-based technique. Step through the interaction using a
concrete scenario and a detailed description of the interface. At each step, ask
four questions:

1. **Intent clarity** — will the user understand what goal they need to achieve
   at this step?
2. **Visibility of action** — will the user notice that the correct control is
   available?
3. **Association between action and goal** — will the user correctly connect that
   control with the outcome they want?
4. **Feedback clarity** — after acting, will the user see that progress was made?

Any "no" flags a usability problem. Deliberately do **not** prescribe the solution
during the walkthrough — recording the defect and fixing it are separate
activities, and mixing them causes you to stop looking once you've found
something fixable.

The mapping back to theory is exact: questions 1–3 are the gulf of execution;
question 4 is the gulf of evaluation.

This is the right first tool when someone reports "users keep getting confused"
without being able to say where.

## Usability testing with participants

Users complete a predetermined set of tasks while you measure performance.

**A usability test evaluates; it does not create.** Do not ask participants how
to improve the product. Ask them to use it and watch what happens. Users are
excellent at revealing problems and unreliable at proposing solutions.

### What to test for

- **Naming** — do section and button labels make sense? Do certain words land
  better than others?
- **Organization** — is information grouped meaningfully? Are things where users
  look for them?
- **First-time use and discoverability** — can new users find common items? Are
  instructions clear? Are they even necessary?
- **Effectiveness** — can users complete tasks efficiently? Where do missteps
  happen, and how often?

### Protocol

1. Draft tasks from your scenarios.
2. Try the tasks yourself and estimate how long each should take.
3. Prepare a task sheet and the prototype.
4. Tell participants **the system is under test, not them.** Say it plainly; it
   changes what people are willing to report.
5. Ask for a running commentary — what they're doing, why, and what is confusing.
6. Encourage them to keep talking when they go quiet (silence usually means
   difficulty).
7. Afterwards, interview briefly about usability and about the session itself.
   Thank them.
8. Write up notes immediately, while the session is fresh, into a usability
   report.

### Questions during the session

- What do you want to do?
- What were you expecting to happen?
- What is the system telling you?
- Why do you think it did that?
- What are you doing now?

### Questions after

- What was the best/worst thing about it?
- What most needs changing?
- How easy were the tasks?
- How realistic were the tasks?
- Did giving a commentary distract you?

### How many participants

Five participants surface the large majority of usability problems in a given
design. More than that has sharply diminishing returns — better to run three
rounds of five across three iterations than one round of fifteen.

## Usability metrics

### By aspect

| Easy to learn | Easy to remember | Effective in use | Error-resistant | Satisfying |
|---|---|---|---|---|
| Time to complete (first attempt) | Time to re-learn after a break | Time to complete (after learning) | Error frequency per task | Satisfaction rating (Likert) |
| Errors during initial use | Steps forgotten | Actions per task (clicks, keystrokes, navigation) | Error severity (minor vs critical) | SUS score |
| Help requests during first use | Errors on return | Mental workload (NASA-TLX) | Recovery rate after errors | UEQ |
| First-time success rate | Returning-user success rate | Regular-user success rate | Time to recover | Net likelihood to recommend |

### Emotional metrics

Underused and powerful, especially for consumer products:

- Count of positive emotional moments
- Count of negative emotional moments
- Where the peak occurs and how the experience ends (Peak-End Rule)

### Using metrics honestly

- Record baseline numbers **before** redesigning, or you will have no argument
  afterwards, only a preference.
- Always state the target alongside the metric. "Time on task: 45s" means nothing;
  "45s against a 30s target" means something.
- Pair every quantitative result with a qualitative reason. Analytics tell you
  where users fail; only observation tells you why.

## Reporting findings

A useful finding has five parts:

1. **What** — the observed problem, stated concretely
2. **Where** — the specific step, screen, or control
3. **Why** — which heuristic or principle it violates, and what the user's mental
   model was doing
4. **Severity** — 1–3, with justification
5. **Recommendation** — the fix, or the options if there is a real trade-off

Rank by severity, not by ease of fixing. Easy fixes cluster at the bottom of the
severity scale, and a report sorted by convenience quietly buries the important
problems.

## Deceptive patterns to avoid

These are manipulative, frequently illegal, and always corrosive to trust. Never
implement them, and name them if asked to.

- **Disguised ads** — deliberately blurring content and advertising
- **Fake scarcity** — manufactured "only 2 left!" or countdown urgency
- **Fake social proof** — fabricated or exaggerated endorsements and activity
- **Forced action** — withholding something the user wants until they surrender
  something unrelated
- **Roach motel** — easy to sign up, deliberately hard to cancel
- **Confirmshaming** — guilt-loaded decline options ("No thanks, I don't want to
  save money")
- **Preselected opt-ins** — consent boxes ticked by default
- **Misdirection** — visual hierarchy steering users to the choice that benefits
  the business over the one that benefits them
- **Hidden costs** — fees appearing only at the final checkout step

If a stakeholder requests one of these, say what it is, note the legal exposure
where it exists (many jurisdictions now regulate them explicitly), and offer the
honest alternative that serves the same business goal. Real urgency communicated
truthfully still works.
