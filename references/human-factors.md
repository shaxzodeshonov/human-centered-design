# Human factors — the constraints you are designing against

Read this when you need to justify a design decision from how people actually
perceive, remember, and act — or when something "feels wrong" and you need to
name why.

## Contents

- [Human information processing](#human-information-processing)
- [Vision](#vision)
- [Gestalt principles](#gestalt-principles)
- [Reading](#reading)
- [Hearing and touch](#hearing-and-touch)
- [Movement and reaction time](#movement-and-reaction-time)
- [Memory](#memory)
- [Attention](#attention)
- [Errors](#errors)
- [Laws of UX](#laws-of-ux)

## Human information processing

The mind modeled as a system that takes input, processes it through memory, and
produces output:

**Attention** → **Encoding** → **Storage** → **Retrieval**

- **Attention** selects which stimuli get through
- **Encoding** converts stimuli into a storable form
- **Storage** retains it over time
- **Retrieval** accesses it when needed

Every interface competes for attention, imposes an encoding cost, and depends on
retrieval. Design that ignores any of the four generates a predictable class of
failure.

Three levels of processing, from Norman:

- **Visceral** — immediate, automatic, universal. First impressions, fear
  responses, aesthetic reaction. Fast and unconscious.
- **Behavioral** — learned skill triggered by pattern recognition. Largely
  subconscious. This is where fluent tool use lives — and where slips happen.
- **Reflective** — conscious reasoning, deliberation, meaning-making. Slow. This
  is where mistakes originate, and where brand and satisfaction are formed after
  the fact.

Different levels need different design. Visceral responds to aesthetics and
motion; behavioral to feedback and consistency; reflective to a coherent
conceptual model and a good story about what the product is for.

## Vision

Perception is not passive reception — it is an active search for the best
interpretation of ambiguous data. That is why context resolves ambiguity, and why
optical illusions exist at all (over-compensation by a system that is usually
right).

**Perceptual constancy** — we perceive shape, color, and size as stable despite
changing retinal images. Useful: a button that scales still reads as the same
button.

### Color

- Retina: **rods** for low-light, **cones** for color
- Ganglion cells: **P-cells** detect pattern, **M-cells** detect movement
- Visible range roughly 380 nm (blue) to 770 nm (red)
- Color has three components: **hue** (wavelength), **intensity** (brightness),
  **saturation** (amount of white)
- Untrained people reliably name ~10 colors but can *perceive* millions —
  so color is excellent for grouping and terrible for encoding many values
- **Blue acuity is lowest** — only 3–4% of the fovea has blue-sensitive cones.
  Never use blue for fine detail or thin text.
- Around **8% of men and 0.5% of women** have color vision deficiency, most
  commonly red-green

Implications: avoid saturated colors for large areas (they fatigue), and always
make color coding **redundant** — pair it with shape, position, icon, or label.

### Brightness and contrast

Brightness is the subjective response to luminance. Contrast is a function of the
luminances of object and background. Visual acuity increases with luminance — but
so does perceived flicker.

**Negative contrast** (dark text on light background) improves reading from
screens, though high luminance introduces flicker. This is why light mode
generally reads faster and dark mode generally fatigues less in dim rooms; the
right default depends on the environment your persona is actually in.

### Size and depth

**Visual angle** determines whether something is perceivable at all. The same
object at different distances subtends different angles; different objects at
different distances can subtend the same one. Practical consequence: text size
must be specified against *viewing distance*, which differs enormously between a
phone (~30 cm), a monitor (~60 cm), a TV (~3 m), and a kiosk (~50 cm, standing,
possibly with a queue behind).

Depth cues, if you are designing anything spatial or using elevation/shadow:

- **Binocular**: disparity, stereopsis, accommodation, convergence
- **Monocular**: light and shade, linear perspective, height in visual field,
  motion parallax, occlusion, relative size, relative density

Material Design's elevation system is essentially light-and-shade plus occlusion,
which is why it reads as depth on a flat screen.

### Saccades

Eye movement is not smooth. It jumps (**saccades**, 20–50 ms) between
**fixations** (200–300 ms). Information is gathered only during fixations; during
saccades the brain suppresses visual input entirely.

Consequence: every additional fixation costs roughly a quarter second and some
cognitive effort. Layouts that require scanning back and forth between related
pieces of information are measurably slower — which is the mechanical reason
behind "keep related information together."

## Gestalt principles

How the visual system organizes elements into groups. These operate before
conscious attention, which is why they beat labels and borders.

- **Proximity** — close objects are seen as a group. The strongest and cheapest
  grouping tool available. Use whitespace before dividers.
- **Similarity** — objects sharing color, shape, or size are seen as related.
- **Closure** — the mind completes incomplete shapes. Lets you imply containers
  without drawing them.
- **Good continuation** — elements on a line or curve are seen as related. Why
  aligned form fields read as one form.
- **Common fate** — objects moving together are grouped. Why animating related
  elements in unison communicates relationship.
- **Figure-ground** — distinguishing object from background. Modal overlays work
  by forcing a figure-ground split.
- **Prägnanz (simplicity)** — complex images are interpreted in the simplest way
  available. If your layout has a simpler wrong reading, users will find it.

A **Gestalt shift** is the flip between two valid interpretations of the same
elements. Its lesson for design: perception is construction, and the same pixels
can mean two things. If a layout has an ambiguous reading, some fraction of users
will lock onto the wrong one and stay there.

## Reading

Stages: visual pattern perceived → decoded via internal language representation →
interpreted using syntax, semantics, pragmatics.

Facts with design consequences:

- Adults read ~250 words per minute
- 94% of reading time is fixations; perception occurs only during them
- **Word shape matters for recognition** — which is precisely why
  ALL CAPS IS SLOWER TO READ. It flattens every word into the same rectangle,
  destroying the shape cue. It also reads as shouting.
- Screen reading is slower than paper: longer line lengths, fewer words per page,
  orientation, and familiarity all contribute
- Negative contrast (dark on light) improves screen reading

Applied to a control panel someone glances at while doing something else: use
dark text on light background, keep labels short (they are processed in
fixations), use mixed case for distinctive word shapes, size text for the actual
viewing distance, and group related information to minimize the number of
fixations required.

### Read flow

Action items should follow the direction of reading, and the last action should
be the most likely one, so the user does not backtrack. In left-to-right
languages:

- **Left** — back, cancel, quit, previous
- **Right** — next, continue, submit

Reverse for right-to-left languages. Getting this backwards produces an interface
that feels subtly wrong in a way users cannot articulate.

## Hearing and touch

**Hearing.** Humans hear roughly 20 Hz to 20 kHz, distinguishing changes of about
1.5 Hz at low frequencies and less accurately at high ones. Loudness spans about
30–100 dB in normal use (whisper ~15 dB, conversation ~60 dB, car horn ~110 dB).
Sound carries pitch (frequency), loudness (amplitude), and timbre (quality).

Audio feedback is powerful because it does not compete for visual attention — and
dangerous for the same reason: it cannot be ignored, and it is frequently
unavailable (muted, noisy environment, deaf or hard-of-hearing users). Never make
sound the only channel for important information.

**Touch / haptics.** Receptors: thermoreceptors (heat/cold), nociceptors (pain),
mechanoreceptors (pressure — some responding instantly, some continuously).
Sensitivity varies enormously by body region; fingertips are among the most
sensitive. Unlike vision and hearing, haptic perception is not localized to one
organ.

Haptic feedback is the third channel and the least contested — it can confirm an
action without stealing eyes or ears. It may be the *primary* channel for
visually impaired users.

## Movement and reaction time

Response time = **reaction time + movement time**.

Reaction time by stimulus type:

| Stimulus | Reaction time |
|---|---|
| Auditory | ~150 ms |
| Visual | ~200 ms |
| Pain | ~700 ms |

Movement time depends on age and fitness. Rushing an unskilled operator reduces
accuracy; rushing a skilled one largely does not — which is why expert shortcuts
can be fast and dangerous simultaneously.

### Fitts's Law

$$MT = a + b \log_2\left(\frac{D}{S} + 1\right)$$

where *MT* is movement time, *D* is distance to target, *S* is target size, and
*a*, *b* are empirical constants.

The index of difficulty is $\log_2(D/S + 1)$, in bits. Index of performance by
input device:

| Device | Bits/s |
|---|---|
| Hand (direct) | 10.6 |
| Mouse | 10.4 |
| Joystick | 5.0 |
| Touchpad | 1.6 |

Two consequences: **make targets as large as possible** and **distances as small
as possible.** Also note the touchpad number — a laptop user is roughly six times
slower at acquiring targets than a mouse user. Design generous targets accordingly.

Corollaries worth knowing: screen edges and corners have effectively infinite
size in one dimension (the pointer stops there), which is why menu bars and docks
live at edges. And destructive actions should be *far* from frequent ones, since
proximity plus habit is exactly how a slip becomes a deleted file.

## Memory

### Sensory memory

- **Iconic** (visual) — high-fidelity, ~250–500 ms
- **Echoic** (auditory) — ~2–4 seconds, which is why you can replay the last few
  words of something you weren't listening to

Large capacity, near-instant decay. Design implication: anything displayed for
less than about 250 ms may never enter cognition at all. Flash messages, frame
rates, and alert timing all live against this limit.

### Working memory (short-term)

- Access is fast (~70 ms) but contents decay in about **30 seconds** without
  rehearsal
- Capacity is roughly **3–4 chunks** for realistic material (the popular "7±2"
  figure comes from ideal laboratory conditions and overstates real capacity)
- A **chunk** is a high-level abstraction bundling lower-level ones — which is why
  `998 97 456 45 45` is far easier than `9989745645 45`
- Components: **central executive** (decisions among few options), **articulatory
  loop** (~2–3 seconds of speech, maintained by rehearsal), **visuo-spatial
  sketchpad** (a few visual elements)
- Contents are lost by **decay** (unrehearsed ~30 s) or **displacement** (pushed
  out by new content)

Design implications, and these are among the highest-value rules in this file:

- **Never require carrying information across screens.** If step 3 needs a value
  from step 1, display it in step 3.
- **Prefer recognition over recall.** Show the options.
- Chunk long strings, IDs, and numbers.
- Any interruption — a modal, a notification, a page load — risks displacing
  everything the user was holding. Design so that returning is cheap.

### Serial position effect

Recall is best for the **first** items (primacy) and the **last** items
(recency), and worst in the middle. So: put the most important items at the
beginning and end of any list, menu, or sequence. The middle of a long list is
where information goes to be forgotten.

## Attention

**Selective attention** (focus) — concentrating on one stimulus while filtering
others. This is what your interface is competing for, and what a well-designed
interface protects.

**Divided attention** (multitasking) — splitting across stimuli. Performance
degrades on all of them; people are much worse at it than they believe. Assume
your user is also doing something else, especially on mobile, in a car, or at a
kiosk.

Practical: minimize the number of things demanding attention simultaneously. An
interface with three competing animations has effectively none, because attention
that is contested is attention that is lost.

## Errors

### Mistakes vs slips

**Mistakes** — the wrong goal was formed. Wrong intention, incorrect mental
model, novice behavior. They occur at the **conscious** level, and are in
principle avoidable through better design.

- **Rule-based mistake** — the wrong rule was applied ("I wanted voicemail and
  dialed the police")
- **Knowledge-based mistake** — the situation was misdiagnosed (fuel weight
  computed in pounds instead of kilograms)
- **Memory-lapse mistake** — a step in the plan was forgotten (a mechanic
  abandons troubleshooting after being distracted)

**Slips** — the goal was right, the execution was wrong. Skilled behavior at the
**subconscious** level. Slips are *unavoidable* — the price of fluency. Experts
slip more than novices, precisely because they are running on automatic.

Types of slip:

- **Capture** — a frequently-performed action hijacks the intended one when both
  start the same way. *Confirming a deletion instead of cancelling.*
- **Description similarity** — the intended action closely resembles a nearby
  alternative. *Pressing Caps Lock instead of Shift.*
- **Data-driven** — incoming sensory information intrudes into the action.
  *Calling to give someone a number and dialing that number instead.*
- **Loss of activation** — forgetting the goal partway through the sequence.
  *Walking into a room and forgetting why.*
- **Associative activation** — internal associations trigger the wrong action.
  *The phone rings and you shout "come in!"*
- **Mode error** — acting in one mode while believing you are in another. The
  most preventable and most common in software. **Every mode you add creates a
  class of error that did not previously exist.**

### The design consequence

Mistakes and slips need **different fixes**:

- Mistakes → clearer conceptual model, better information, better labels, better
  match to real-world concepts
- Slips → constraints, spatial separation of similar controls, confirmation on
  destructive actions, undo, and eliminating modes

Confirmation dialogs are a poor defense against slips, because the slip that
clicked "delete" will click "yes" for the same reason. Undo is a much better
defense.

### Three considerations for errors

1. **Avoiding and preventing** — design them out
2. **Identifying and understanding** — detect and explain them
3. **Handling and recovering** — make recovery easy and complete

### Prevention guidelines

- Create a clear, consistent conceptual model aligning designer, system, and user
- Simplify tasks to minimize memory and planning burden
- Make actions and effects visible, so users know what to do and what will happen
- Use natural mappings between intention, action, system response, and state
- Employ constraints to guide toward appropriate actions
- Design *for* errors: easy undo, hard-to-reach irreversibility, wizards for
  complex sequences
- Standardize only as a last resort — it works, but it forecloses improvement

### Error message guidelines

- Take care with wording and presentation
- Avoid threatening language: *fatal error*, *run aborted*, *kill job*,
  *catastrophic error*
- Never use all uppercase — it reads as shouting and is slower to read
- Avoid double negatives; they are ambiguous
- Be specific and constructive: "please enter your name", not "invalid entry"
- Make the system take the blame: "unrecognized command", not "illegal command"
- Use attention-grabbing techniques sparingly — no flashing, no more than four
  font sizes per screen, minimal audio and video
- Use color conventionally (red = danger, green = ok) and never as the sole cue

### Recovery guidelines

- Undo, always
- Cancel for anything in progress
- Confirmation for genuinely destructive commands only — overuse trains people to
  click through
- Reasonableness checks on input ("did you mean to order 5,000?")
- Return focus to the field that needs fixing
- Guess helpfully when you can
- Context-sensitive help within reach

Response types, from least to most intrusive: **nothing** (user must notice —
risky), **self-correct** (guess and act, like spellcheck), **warn** (an alert),
**dialog** (system opens a conversation), **gag** (prevent continuing). Match the
intrusiveness to the actual stakes.

## Laws of UX

Quick-reference psychology-derived heuristics. Full catalogue at
<https://lawsofux.com/>.

**Jakob's Law.** Users spend most of their time on *other* sites and prefer yours
to work the same way. They transfer expectations from familiar products. Leverage
existing mental models so users can spend effort on their task rather than on
learning your model. When you must change something, let people keep the familiar
version for a while. (The QWERTY layout survives on phones despite having zero
mechanical justification — that is Jakob's Law at full strength.)

**Fitts's Law.** Time to acquire a target is a function of distance and size.
Targets should be large enough to hit accurately, spaced enough not to be
confused, and placed where they are easy to reach.

**Hick's Law.** Decision time increases with the number and complexity of
choices. Minimize choices when speed matters; break complex tasks into steps to
reduce cognitive load; highlight a recommended option; use progressive
onboarding. But do not simplify to the point of abstraction — a menu of three
vague categories is worse than ten clear ones.

**Miller's Law.** People hold about 7±2 items in working memory (realistically
3–4 for meaningful material). Do not use the number to justify arbitrary limits;
do chunk content into digestible groups. Capacity varies with prior knowledge and
context.

**Peak-End Rule.** People judge an experience by its most intense point and its
end, not the average of all moments. Find where your product is most valuable and
invest there. Design the ending deliberately. And remember negative experiences
are recalled more vividly than positive ones — one bad peak outweighs several
good moments.

**Doherty Threshold.** Productivity soars when system and user interact at a pace
under **400 ms**, so neither waits on the other. Past that, use optimistic UI,
skeleton screens, and progress indication — perceived performance is a design
variable, not just an engineering one.

**Aesthetic-Usability Effect.** Users perceive attractive designs as more usable,
and tolerate more minor problems in them. Polish buys goodwill — but it also
masks usability problems during testing, so watch behavior rather than sentiment.

**Von Restorff (Isolation) Effect.** Among similar objects, the one that differs
is best remembered. This is the mechanism behind a single primary button per
screen — and the reason that making everything prominent makes nothing prominent.

**Postel's Law.** Be conservative in what you do, liberal in what you accept from
others. In interface terms: accept input in whatever form the user offers it
(phone numbers with or without spaces, dates in any reasonable format) and
normalize it yourself. Every format restriction you impose is work you have moved
from your parser to your user.

**Tesler's Law (conservation of complexity).** Every system has an irreducible
amount of complexity. The only question is who absorbs it — the developer or the
user. Choosing the developer is almost always correct, and is what separates
products that feel effortless from products that feel like paperwork.
