# Deliver — interaction framework, IA, navigation, visual design

Read this when turning a chosen concept into an actual structure: views,
navigation, layout, and the platform decisions that shape all of it.

## Contents

- [Conceptual vs physical design](#conceptual-vs-physical-design)
- [The interaction framework, in six steps](#the-interaction-framework-in-six-steps)
- [Platform and posture](#platform-and-posture)
- [Information architecture](#information-architecture)
- [Navigation](#navigation)
- [Mobile specifics](#mobile-specifics)
- [Visual interface design](#visual-interface-design)
- [Service design](#service-design)

## Conceptual vs physical design

**Conceptual design** is abstract: the system's logic, functions, structure, and
content. **Physical design** is concrete: look and feel, medium, touchpoints.

Do conceptual first. The reason is *functional fixedness* — once you have seen a
concrete form, you struggle to imagine any other. The classic demonstration: two
strings hang too far apart to hold both at once, and you have pliers, scissors, a
hammer, and nails. Most people fail because they see the pliers as a gripping
tool. The answer is to tie the pliers to one string and swing it as a pendulum.
The tool's *usual* purpose blocked its *useful* property (mass).

In software, functional fixedness looks like: assuming the answer is a screen
with a list, because the answer is always a screen with a list.

## The interaction framework, in six steps

### Step 1 — Form factor, posture, input methods

**Form factor**: desktop app, web app, mobile app, kiosk, in-vehicle, TV, CLI,
watch, voice. Each brings hard constraints — display size, input precision,
connectivity, session length, ambient distraction.

**Posture**: how much of the user's attention and effort this deserves. See the
next section — this decision cascades into every later one.

**Input methods**: what the persona will actually use, and what they are good at.
A user wearing gloves, holding a phone one-handed on a bus, or typing at 90wpm
are three different design targets.

### Step 2 — Data elements and functional elements

**Data elements** are the objects the user thinks in: photos, messages, records,
orders, workouts. For each:

- What are its key attributes?
- Does it match the persona's mental model, or only the database schema?
- Which attributes matter most to the persona?
- How does it relate to other objects?

**Functional elements** are operations on those objects, and how those operations
appear in the interface. For each:

- How is this function surfaced?
- **What would a helpful human do instead?** (The best question in this document.
  A good assistant would not ask you to fill in a form you already answered last
  week.)
- How can the system minimize the user's effort toward their goal?
- Which known patterns apply?

**Object-action analysis** — the mechanical procedure:

1. Categorize your scenarios by action or higher-level activity.
2. Extract objects and actions from each scenario.
3. Compare across scenarios.
4. Merge identical ones and give each a single, consistent name.

That merged list is simultaneously your interface vocabulary and most of your
data model. Naming things once, consistently, is a large fraction of what makes
software feel coherent.

### Step 3 — Functional groups and hierarchy

Group elements into units that support the persona's flow, asking:

- Which elements need lots of screen space? Which need very little?
- Which are containers for others?
- How should containers be arranged to optimize flow?
- Which elements are used together? Which never co-occur?
- In what sequence will related elements be used?
- What information does the persona need visible **at each decision point**?

Then organize into top-level containers — screens, frames, panes, views:

- **Non-overlapping goals → separate views.** Don't force two unrelated jobs into
  one screen.
- **Overlapping goals → shared view.** Don't make users hop between screens to do
  one thing.

### Step 4 — Sketch the framework

Subdivide each view into panes, regions, and components. Name and describe each
container. **Do not do widget-level design yet** — choosing dropdowns and toggles
now locks in a structure before you know if the structure is right, and creates
consistency problems that are painful to unwind later.

### Step 5 — Key path scenarios

Narrate the persona completing the primary task using the vocabulary of the
framework you just sketched. Primary paths are those taken most frequently.

This is the highest-yield step in the whole phase. If narrating a step feels
awkward — "then she goes back to the dashboard, finds the item again, and opens
settings" — the framework is wrong, and you have found it for the cost of a
paragraph rather than a sprint.

**Verbal thinkers** may prefer: scenario → grouping → sketch.
**Visual thinkers** may prefer: sketch → scenario → check grouping.
Either order works. Doing only one of the two does not.

### Step 6 — Validation scenarios

Stress-test with the paths you did not optimize:

- **Alternative** — less-travelled routes to the same goal
- **Necessary-use** — must exist, used rarely (export, delete account, admin
  override). Must work correctly; must not clutter the primary path.
- **Edge case** — rare and strange. Must not corrupt state; may be inelegant.

Ask "what if…" repeatedly: no network, empty state, one item, ten thousand items,
permission denied, session expired, two tabs open, the user goes back.

Empty states and error states are not edge cases. They are the *first* thing
every new user sees. Design them at the same time as the happy path.

## Platform and posture

Posture is the product's behavioral stance — how it presents itself and how much
of the user's attention it claims. Posture can also differ per feature: writing
text in a word processor is sovereign; inserting a table is transient.

### Desktop postures

**Sovereign** — monopolizes attention and screen space for extended periods.
Optimize for full-screen. Rich, deep functionality. Document-centric. Restrained
visual style (users stare at it for hours), but *rich visual modeless feedback* —
status communicated continuously without dialogs. Target intermediates; help
novices graduate quickly. Examples: IDEs, Photoshop, spreadsheets.

**Transient** — appears, does one job, leaves. Limited functionality, ideally one
screen. Novice-friendly: bigger, clearer controls, and remember the user's last
choices so repeat use is instant. Respects any sovereign app it interrupts.
Examples: calculators, media controls, share sheets.

**Daemonic** — runs in the background with little or no UI. Surfaces only when
attention is genuinely required. The design challenge is choosing that moment
correctly; a daemon that interrupts too often gets disabled. Examples: sync
services, antivirus, backup.

### Web postures

**Informational site** — content consumption over interaction. Content-forward,
clear hierarchy, optimized reading, strong search and navigation.

**Transactional** — commercial exchange. Clear product presentation, streamlined
checkout, trust signals (security, reviews), account management.

**Web app** — heavily interactive, behaves like a sovereign desktop app.
Persistent navigation and clear IA, designed for long sessions (watch ergonomics
and eye strain), customization for power users, real onboarding and help.

### Mobile postures

**Satellite** — supplements a primary device. Information is mostly viewed, not
manipulated. Watches, e-readers, glanceable displays.

**Standalone** — full screen, functions via slide-in menus or fixed top/bottom
bars, popups for settings and destructive actions. Occupies the whole screen but
behaves transiently: sessions are short and interruptible.

### Kiosk

Public, self-service, walk-up-and-use. Assume 2–5 minutes, no training, standing
posture, environmental distraction, privacy concerns, and wildly varying height
and ability. Therefore: large targets (≥1 cm²), step-by-step flows with progress
indicators, simplified choices with visual emphasis, timeouts with warnings, and
an attraction screen when idle.

### Automotive and embedded

Kiosk-like but seated, often with hardware bezel buttons. Minimize distraction
above all else; transactions must be completable in glances. Same logic applies
to appliance panels, medical devices, and industrial controls.

### CLI and developer tools

Not in the original taxonomy but the same reasoning applies. A CLI is sovereign
for the expert and transient for everyone else. This is why `--help`, sensible
defaults, confirmation on destructive operations, and useful error messages that
name the next action are not niceties — they are the entire novice experience.

## Information architecture

IA is organizing and labeling an information space for understanding and use.
Using what you know about your users, design:

- Structures and categories for content and functionality
- Ways to navigate the experience
- Workflows for multi-step tasks
- Labels and language
- Search, browse, and filter tools
- A standardized system of screen types and templates so presentation is
  consistent

Card sorting (see `discover.md`) derives structure from users rather than
imposing yours.

### Common IA patterns

**Feature / search / browse** — the main screen carries a featured item, a search
box, and a browsable list of items or categories. Works when users arrive with
mixed intent: some know what they want, some don't.

**Streams and feeds** — a continuously updated, scrollable series of cards, each
with an image, headline, intro copy, and source. Works when content is
time-ordered and abundant. Be honest about the cost: feeds are excellent at
engagement and poor at letting someone find a specific thing again.

**Hierarchy / tree** — categories and subcategories. Works when the domain has
genuinely stable structure (catalogs, documentation, file systems).

**Dashboard** — a fixed set of at-a-glance summaries with drill-down. Works when
users need status before action.

## Navigation

Navigation must answer three questions at all times:

- **Where am I now?**
- **Where did I come from?**
- **Where should I go next?**

**Signposts** tell users about their immediate surroundings. **Wayfinding** is
what people do to move toward a goal — supported by unambiguous labels that
anticipate what the user is looking for, plus environmental and cultural cues in
expected places.

### Navigation models

- **Step by step** — wizards. Linear, one decision at a time. Good for infrequent,
  complex, high-stakes tasks.
- **Hub and spoke** — a central menu radiating to sections; users return to the
  hub between tasks. Phone home screens.
- **Fully connected** — global navigation bar, any section reachable from any
  other. Most websites and web apps.
- **Tree** — hierarchical drill-down. Catalogs, marketplaces.
- **Pan and zoom** — a continuous space navigated by movement and scale. Maps,
  canvases, timelines.
- **Pyramid** — sequential items within a section, with a parent to return to.
  Photo galleries, article series.

### Navigation patterns

**Clear entry points** — present only a few main ways in, so users know where to
start. A page with twenty equally weighted options offers no starting point at
all.

**Fat menus** — show a long list of options in a drop-down or fly-out, grouped
into labeled columns. Beats deep nesting: seeing everything at once is cheaper
than hunting through three levels.

**Progress indicator** — on each page of a sequence, show all steps in order with
a "you are here" marker. Directly serves Nielsen heuristic 1.

**Breadcrumbs** — the path from the entry point down the hierarchy to the current
screen. Cheap, and answers all three navigation questions at once.

## Mobile specifics

### Formats

- **Stacks** — vertically organized list or grid with navigation at top/bottom
- **Screen carousels** — dashboard variants swiped between; avoid circular
  wrapping, which destroys the user's sense of position
- **Direct access** — the first screen shows actionable information with no input
  required, by making assumptions from context (location, time). The best mobile
  pattern when it applies: the answer before the question.
- **Hardware-like** — the interface mimics physical controls via metaphor

### Navigation components

Lists, grids, content carousels, swimlanes, tab bars, toolbars, nav bars, drawers
(hamburger). Note that hidden navigation reduces discoverability considerably —
a tab bar beats a drawer for anything used frequently.

### Gestures

Tap (≈ click), tap-and-hold (≈ right-click), drag to scroll / move / control,
swipe up/down and left/right, pinch, rotate, multi-finger swipes.

Every gesture is an invisible affordance. It **needs a signifier** — a peeking
edge, a hint animation on first use, a visible handle — or most users will never
discover it. And never make a gesture the *only* route to an important action.

### Guidelines that generalize

- Focus on the primary task; elevate the content people care about
- Think top down; give people a logical path to follow
- Use user-centric terminology, not internal jargon
- Minimize input effort; downplay file-handling; de-emphasize settings
- Make targets fingertip-sized; use subtle animation to communicate change
- Handle orientation changes; start instantly; always be ready to stop
- Ask people to save only when necessary; make modal tasks occasional and simple
- Make search quick and rewarding
- Be succinct

## Visual interface design

Design the visual layer against the user's existing mental models. It must
communicate:

- What commands exist, and what they let the user do
- What content is available, in what form, and how to find it
- How to get an overview, and how to focus on a region

### GUI building blocks (WIMP)

- **Window** — a region under one application's control
- **Icon** — an object to act upon
- **Menu** — a representation of actions on objects
- **Pointing device** — selection of objects and actions

**Direct manipulation** — acting on objects continuously with a pointer — is
still the strongest interface idea available, because it collapses the gulf of
execution: the action and its object are the same thing.

Icons represent through three mechanisms: **metaphor** (transferring knowledge
from another domain), **direct mapping** (a picture of the thing), and
**convention** (arbitrary but learned — the floppy disk save icon). Convention
beats cleverness. Icons must be easy to *distinguish* as well as easy to
*understand*, and an icon alone with no label is a guess.

### Menus and grouping

Group commands into topics. Apply Miller's Law: no more than ~4 options if the
user must *remember* them, ~7 if they only need to *recognize* them. Beyond that,
chunk into labeled groups.

Use Gestalt principles to organize controls: **proximity** to group related
buttons, **similarity** to indicate same-kind objects, **continuity** to connect
elements that belong to one thing (a scrollbar track), **figure-ground** to
separate content from chrome. These do more work than borders and do it without
adding visual noise.

### Design systems and style guides

A **design system** is the standards needed to manage design at scale — color
palettes, typography, logos, imagery, tone and content rules. It contains a style
guide, a component library, and a pattern library. Examples: Material Design,
IBM Carbon, Apple HIG.

A **style guide** is the documentation: implementation guidance, visual
references, and principles.

Platform guidelines carry real constraints (e.g. Apple's minimum touch target).
Follow them — they encode Jakob's Law, which says users expect your app to behave
like the other apps on their device.

Color conventions: red = danger/stop, green = ok/go, yellow = caution. These are
culturally variable but strong where they hold. **Never encode information in
color alone** — around 8% of men have some form of color vision deficiency. Pair
color with shape, position, or text.

## Service design

When the experience extends beyond the screen — deliveries, support calls,
physical handoffs — map a **service blueprint**:

- **Customer journey** — what the customer does
- **Frontstage** — actions visible to the customer
- **Backstage** — actions supporting frontstage, invisible to the customer
- **Internal processes** — verification, procurement, quality checks
- **Evidence** — the props and places involved
- **Metrics** — time, cost, performance, emotion

The blueprint reveals which apparent UI problems are actually operations
problems. A checkout screen cannot fix a two-day fulfilment delay, and redesigning
it repeatedly is a common way to waste a year.
