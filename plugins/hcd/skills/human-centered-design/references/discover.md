# Discover — user research and requirements

Read this when you are gathering requirements, planning research, or trying to
turn messy input (interview notes, support tickets, survey results) into
something a design can be built on.

## Contents

- [The three rules](#the-three-rules)
- [Setting a research goal](#setting-a-research-goal)
- [Finding and screening participants](#finding-and-screening-participants)
- [Qualitative methods](#qualitative-methods)
- [Quantitative methods](#quantitative-methods)
- [From raw data to user needs](#from-raw-data-to-user-needs)
- [Organizing and prioritizing needs](#organizing-and-prioritizing-needs)
- [Doing this without access to users](#doing-this-without-access-to-users)

## The three rules

1. **You go to them.** Research where the product is actually used. Context is
   half the finding. Calling users into a meeting room strips away the thing you
   came to see.
2. **You talk to them.** *How* a story is told carries information that a
   transcript loses — hesitation, irritation, the workaround they are slightly
   embarrassed about.
3. **You write it down.** During, not after. Memory is not reliable and it
   quietly edits toward whatever you already believed.

## Setting a research goal

One sentence, this shape:

> I am going to research **[activity]** so that I can **[project goal]**.

Example: *"I am going to research how doctors use laptops on the job so that I
can design a laptop for them."*

If you cannot fill in the activity, you are not ready to research — you are still
guessing at a topic.

## Finding and screening participants

Prepare two or three fast screening questions that separate the people you need
from everyone else. Good screeners are behavioral, not attitudinal:

- "Do you order food through an app? How often?"
- "What does this icon mean?" (tests actual literacy, not claimed literacy)
- "Which of these is a QR code?"

Ask them anywhere the target user actually is.

## Qualitative methods

Qualitative work answers **how** and **why**, and produces stories, sketches,
photos, and video.

### Interviews

**Directed storytelling.** Ask for a specific past episode: *"Tell me about the
last time you did X."* Specific memories are accurate; general opinions are
reconstructions.

**Ethnographic interview.** Immersive, in context, ideally with two people — one
moderating, one taking notes and watching for nonverbal signals.

**Unfocus group.** Instead of typical users, assemble extremists: domain experts,
hobbyists, artists, people with unusual constraints. Their edge cases reveal
structure that average users have already adapted around.

**Role playing.** Have participants act out a scenario. Surfaces emotion and
attitude that direct questioning flattens.

#### Interview technique

- Go with the flow — the interview guide is a safety net, not a script.
- Assume the role of apprentice, not expert. You are there to be taught.
- Suppress your hypotheses about the technology. Say them out loud only at the
  end, if at all.
- Ask for show-and-tell. Have them demonstrate a real task with their real tools.
- Bring props: your product, competitors' products, adjacent products.
- Ask about goals first, tasks second. Tasks are how they currently cope; goals
  are what they are actually after.
- Watch for surprises and latent needs — the things they have stopped noticing
  because they have worked around them for years.
- Never lead ("wasn't that confusing?", "so how good is this?").
- Never turn the user into a designer. Ask what went wrong, not what to build.
- Assure privacy; record only with permission.

#### Questions that reliably produce material

- Tell me about a typical day.
- When and why do you use this?
- Walk me through a typical session.
- What do you like about the tools you use now? Tell me a story about that.
- What do you dislike? Tell me a story about that.
- What do you consider when choosing a tool like this?
- What would you change?

### Observation

**Fly on the wall.** Observe from a distance without interacting. Good for
discovering what people do versus what they say they do.

**Shadowing.** Follow a participant through their routine. Good for discovering
context switches, interruptions, and the hidden work between tasks.

**Undercover / apprentice.** Work alongside them as a novice. Best for
understanding tacit skill.

### Card sorting

Participants group cards representing content, pages, or concepts. The result is
your information architecture, derived rather than imposed.

- **Open sort** — participants invent their own categories. Use when you don't
  yet know the structure.
- **Closed sort** — participants sort into your categories. Use to validate a
  structure you're considering.

### Probes

Ask participants to capture their own life on a prompt list over days: *first
person you saw today, first meal, worst experience, most boring moment*. Cheap
way to reach contexts you cannot observe directly.

### Artifact collection

Gather what users create, use, or leave behind — notes, spreadsheets, printouts,
screenshots, the sticky note on the monitor. Workarounds are documented
requirements. The homemade spreadsheet someone maintains beside your product is
the feature spec you failed to write.

### Five Whys

Ask "why?" up to five times to get from a stated request to an underlying goal.
Stop when the answer stops changing — that's the real driver.

## Quantitative methods

Quantitative work answers **what** and **how many**, and produces numbers you can
compare over time.

**Surveys.** Standard instruments save you from writing bad questions: SUS
(System Usability Scale), NASA-TLX (workload), QUIS, SUMI, UEQ.

Survey design rules that matter:

- Specific questions beat general ones.
- Closed questions usually beat open ones for analysis.
- Offer a "no opinion" option so people don't default to the middle.
- Vary rating scale orientation (some good→bad, some bad→good) to catch
  straight-lining.
- Order matters: easy questions first, hard ones in the middle, interesting ones
  last.
- Include an intro (purpose, confidentiality) and a close (deadline, offer to
  share results).
- Show progress; make submission trivial.

**Analytics.** Flows, drop-off, demographics, geography. Tells you *where* people
fail, never *why*. Always pair with qualitative follow-up.

**A/B testing.** Randomized comparison of two variants. Needs traffic and a
pre-declared metric, or you will find noise and call it a result.

**Eye tracking.** Expensive and lab-bound, but definitive about what was actually
looked at versus what people claim they saw.

## From raw data to user needs

Translate each observation into a need statement. Rules:

- Express **what the product must do**, not how it might do it.
- Be as specific as the raw data — no more, no less.
- Use positive phrasing.
- Express it as an attribute of the product.
- Avoid "must" and "should" (they smuggle in priority you haven't decided yet).

Examples:

| Raw statement | Bad translation | Good translation |
|---|---|---|
| "I don't want to lose a fortune on gas bills" | Add an energy-saving mode | The thermostat minimizes energy consumption |
| "I set it to 20°C and wake at night from the heat" | Add a night schedule | The thermostat maintains a comfortable temperature through the night |
| "My kids play with it and heat the room" | Add a PIN lock | The thermostat prevents unintended changes by unauthorized people |
| "I'm too old for these touchscreens" | Make the font bigger | The thermostat is operable by users unfamiliar with touch interfaces |

Note how the good column stays out of solution space. That is the whole point —
it keeps the Develop phase free to invent.

## Organizing and prioritizing needs

A real project produces 50–300 need statements. Handle them like this:

1. Put each on its own card or line.
2. Delete redundancies.
3. Group by similarity **from the user's perspective**, not by which component
   implements them.
4. Label each group with the need it represents.
5. Grade importance with stars; mark **latent** needs (things users never
   articulated but clearly have) with `!`. Latent needs are where differentiated
   products come from.

### Kano model

Classify each need by how satisfaction responds to fulfilment:

- **Must-be** — absent, users are furious; present, nobody notices. Table stakes.
- **Performance** — satisfaction scales linearly with how well you do it. Where
  you compete.
- **Attractive (delighters)** — absent, nobody complains; present, users are
  delighted. Where you differentiate. These decay into must-be over time as
  competitors copy them.
- **Indifferent** — no effect either way. Stop building these.
- **Reverse** — some users actively dislike it.

## Doing this without access to users

Often you are an agent with no way to interview anyone. Do not fake it. Instead:

1. Ask the requester the research questions directly — they usually know more
   than they've said, and specific questions unlock it.
2. Mine what exists: support tickets, reviews, competitor complaints, forum
   threads, existing analytics, the codebase's own error logs and workarounds.
3. Build **assumption personas** and label them clearly as assumptions.
4. Record each assumption with its blast radius: *"Assuming users are on mobile
   in poor connectivity — if wrong, the offline-first architecture is
   unnecessary."*
5. Propose the cheapest test that would validate the riskiest assumption.

An assumption you named and priced is a design decision. An assumption you didn't
notice is a landmine.
