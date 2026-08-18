# Define — framing the problem

Read this when converging from research onto a problem statement, personas,
scenarios, and a journey map.

## Contents

- [Stakeholders](#stakeholders)
- [Problem statements](#problem-statements)
- [Personas](#personas)
- [User stories](#user-stories-the-problem-version)
- [Scenarios](#scenarios-the-solution-version)
- [Storyboards](#storyboards)
- [Journey maps](#journey-maps)
- [The design brief](#the-design-brief)

## Stakeholders

A stakeholder is anyone with a right, share, claim, or interest in the system.
Three rings:

- Those who **interact directly** with the product (users)
- Those who **influence** users
- Those who are **influenced by** users

For a shop point-of-sale system: cashiers (direct users), the shop
administrator, accountants, customers, the owner, tax officers. Each has
different success criteria and only one of them touches the screen. Missing a
ring is how a product ends up technically correct and organizationally rejected.

List stakeholders before personas. Then decide, explicitly, whose experience you
are optimizing — and say so, because you cannot optimize for everyone.

## Problem statements

### The two formulas

> **[A user]** needs **[need]** in order to accomplish **[goal]**.
>
> **[A user]** needs **[job to complete]** because **[insight]**.

Examples:

> A dog owner needs to spend more time playing with their dog in order to keep
> him engaged and happy.
>
> Small business owners need to easily create professional-looking marketing
> materials because they lack the design skills and resources to promote their
> businesses effectively.

### Five Ws

Interrogate the research insight before writing the statement:

- **Who** is experiencing the problem?
- **What** are they trying to accomplish?
- **Where** does the problem occur?
- **When** does it take place?
- **Why** is it important to solve?

*Insight: College students struggle to find affordable textbooks, causing
financial strain and academic fallback.*
→ Who: college students. What: acquire required textbooks. Where: campus and
online. When: start of each semester. Why: course access, financial burden,
academic success.

### Cause → effect

Separate root cause from visible effect so you fix the right one.

| Cause | Effect |
|---|---|
| Insufficient capacity, infrequent service | Frustration, missed appointments, lost trust |

Designing against the effect gives you an apology screen. Designing against the
cause gives you a product.

### How Might We

Reframe the statement as an open question to re-open the solution space:

> *Parents struggle to consistently plan healthy family meals due to lack of
> time.*
> → **How might we help busy parents quickly plan healthy meals?**

Calibrate the scope. Too narrow ("how might we add a meal calendar") pre-decides
the solution. Too broad ("how might we improve family life") gives no traction.

### Also write the non-goals

State what this design deliberately does not address. Non-goals prevent scope
creep more effectively than any prioritization framework, because they are
falsifiable.

## Personas

A persona is a concrete representation of a type of person the system is for. It
exists to make design decisions arguable: "would Nodira find this button?" is a
question a team can actually answer, where "would a user find this?" is not.

### Structure

- **Name and photo/sketch** — makes them memorable and stops the team saying "the
  user"
- **Demographics** that matter: age, education, occupation, location, family
- **A quote** capturing their attitude in one line
- **Goals** — what they are trying to achieve in life and in this domain
- **Frustrations** — what currently gets in the way
- **Narrative** — a paragraph of context: their situation, what they already know,
  what they have tried
- **Decision-relevant attributes** — digital literacy, language, accessibility
  needs, device, connectivity, time pressure, environment

That last group is what makes a persona operational. If removing an attribute
would change no design decision, delete it.

### Types

- **Goal-directed** — centered on what the user is trying to accomplish and how
  they get there. Default choice for consumer software.
- **Role** — centered on the user's role in an organization: purpose, business
  objectives, who else is affected. Default for B2B and internal tools.
- **Engaging** — combines goal and role and adds emotion, psychology, and
  background. Most persuasive to stakeholders; most effort.
- **Fictional** — derived from the designer's accumulated experience rather than
  fresh research. Fastest, weakest evidence; label it as such.

### How many

One primary persona whose goals the product must satisfy completely. Add a
secondary only if it would change a decision. Three or more usually means the
scope is too wide, and the design will end up satisfying nobody fully.

### Anti-patterns

- Demographics with no design consequence ("enjoys hiking")
- The persona who is secretly you
- A persona so average that every design passes its test
- Personas written after the design, to justify it

## User stories (the problem version)

A user story here is a **narrative of the current, broken experience** — first
person, concrete, emotionally honest. Not the agile "As a user I want…" template.
Its job is to make failure visible.

Write it in short numbered paragraphs, each one a moment. Then annotate: where
exactly does the design fail this person?

A worked example. A tradesman in his fifties, recently moved to a new city, tries
to order lunch on a phone a relative set up for him. The interface is in a
language he does not read. It demands a delivery address while he is on a moving
bus. Payment requires card entry he has never done. Nobody is available to ask.
He gives up and buys bread from a shop instead.

Four failures — and **none of them are technical**. The app worked perfectly from
an engineering perspective. Every failure was a design failure: language,
context, prior knowledge, support. That is the lesson worth internalizing, and
it generalizes far past food delivery — substitute any product where the team
tested only on people who already knew how it worked.

Score the current experience so you have a baseline to beat:

| Metric | Before |
|---|---|
| Time to complete | 15+ min |
| Number of steps | 12+ |
| Error moments | 4 |
| Positive emotional moments | 1 |
| Negative emotional moments | 5 |
| Likelihood to reuse | Low |

## Scenarios (the solution version)

A **concrete scenario** is the same story retold with your design in it. It
dictates a particular solution, sketches the rough interface, and allocates
functions between the person and the system.

Rules that keep scenarios useful:

- Same persona, same triggering situation as the problem story — otherwise you
  are comparing different worlds.
- Written in the vocabulary of the actual interface. If you cannot narrate the
  step, the interface does not support it.
- Show the emotional arc, not just the clicks.
- End where the user's real goal is met, not where the transaction completes.

Retelling the example: the app opens with large food images and a language
choice by flag. Instead of a map, three buttons — *I'm at home / I'm at work /
I'm on the move*. Payment offers three large options including cash. A courier
meets him at the bus stop. New score: 2 minutes, 5 steps, 0 errors, 7 positive
moments.

The numbers are the argument. Always produce the before/after pair.

### Scenario types to write

- **Key path** — the primary task, taken most frequently. Optimize hardest here.
- **Alternative** — optional, less-travelled routes to the same goal.
- **Necessary-use** — functions that must exist but are used rarely (account
  deletion, data export, admin overrides). Must work; must not clutter.
- **Edge case** — unusual situations. Must not corrupt anything; may be awkward.

## Storyboards

Six frames is usually right:

1. One opening scene establishing context
2. Two scenes developing the storyline
3. Two scenes for the climax — the moment the product changes the outcome
4. One closing scene showing the resolved state

Annotate each frame with the matching scenario step, plus any notes on imagery,
sound, or timing. Mark the emotional register of each frame (an emoji works
fine). The point of marking emotion is to find the peak, because the Peak-End
Rule says that peak is what the user will remember.

## Journey maps

A journey map covers the **whole relationship**, wider than a single task flow.

Stages: Awareness → Consideration → Acquisition → Onboarding → Engagement →
Retention → Advocacy. Trim to what is relevant.

Three zones:

- **Zone A (the lens)** — who (persona) and what (scenario). Without these the
  map is generic and useless.
- **Zone B (the experience)** — for each stage: touchpoints, actions, thoughts,
  emotions. Quotes from research go here.
- **Zone C (the output)** — insights, pain points, opportunities, and internal
  ownership for each.

Layout:

| | Stage 1 | Stage 2 | … |
|---|---|---|---|
| **Touchpoints** | | | |
| **Actions** | | | |
| **Thoughts** | | | |
| **Emotions** | | | |
| **Pain points** | | | |
| **Opportunities** | | | |

Read the emotion row as a curve. The troughs are where design effort has the
highest return, and the final stage disproportionately determines how the whole
experience is remembered.

## The design brief

The output of the Define phase, and the single most consequential artifact in
the project. It should contain:

- The problem statement and its How Might We
- Primary persona (and secondaries if any)
- The journey map with pain points ranked
- Prioritized user needs
- Success metrics with target values
- Explicit non-goals
- Named assumptions, each with its consequence if wrong

Everything downstream inherits this. If it is wrong, the team will build the
wrong thing competently — which is the most expensive failure mode there is.
