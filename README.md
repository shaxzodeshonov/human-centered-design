# human-centered-design

A [Claude Code](https://claude.com/claude-code) skill that makes Claude do
design work *before* and *while* it writes code — research the user, name the
problem, model the interaction, then build and evaluate against usability
heuristics.

Most software that fails does not fail technically. It compiles, it ships, it
passes tests, and people still cannot use it. The failure is upstream: nobody
established who the user is, what they were trying to do, or what state they were
in when they tried. This skill is the antidote.

## What it does

When a task touches something a human will look at or operate, the skill loads a
four-phase pipeline (the Double Diamond) and works through it at a scale matched
to the stakes:

| Phase | Output |
|---|---|
| **Discover** (diverge on the problem) | Research goal, user needs, named assumptions |
| **Define** (converge) | Problem statement, personas, journey map — the design brief |
| **Develop** (diverge on the solution) | Concepts, TRIZ contradiction resolution, user flows, wireframes |
| **Deliver** (converge) | Interaction framework, IA, navigation, then the implementation |

It closes with an evaluation pass — heuristic evaluation and cognitive
walkthrough — on its own work, and reports the findings it *didn't* fix along
with the reasons.

It also knows when not to bother. A lane table up front keeps it from running
full research ceremony on a button-colour change.

## What's in it

```
human-centered-design/
├── SKILL.md                        the pipeline, principles, and error model
├── references/
│   ├── discover.md                 interviews, observation, probes, card sorting,
│   │                               surveys, analytics, translating data into needs
│   ├── define.md                   problem statements, personas, scenarios,
│   │                               storyboards, journey maps, stakeholders
│   ├── develop.md                  ideation techniques, TRIZ contradictions and
│   │                               separation principles, concept selection
│   ├── deliver.md                  interaction framework, information architecture,
│   │                               navigation, platform postures, visual design
│   ├── evaluate.md                 heuristic evaluation, cognitive walkthrough,
│   │                               usability testing, metrics, deceptive patterns
│   └── human-factors.md            perception, memory, attention, reading, Gestalt,
│                                   reaction times, the Laws of UX
└── assets/
    └── templates.md                fill-in templates for every artifact
```

Progressive disclosure: `SKILL.md` loads when the skill triggers; the references
load only when the relevant phase calls for them.

## Installing

**Claude Code** — clone into your skills directory:

```bash
git clone https://github.com/<your-username>/human-centered-design.git \
  ~/.claude/skills/human-centered-design
```

For a single project instead, clone into `.claude/skills/` inside the repo.

**Claude Desktop / Cowork** — package it and upload:

```bash
zip -r human-centered-design.skill human-centered-design/
```

Then attach the `.skill` file in a conversation and click **Save skill**.

Verify it loaded by asking Claude to list its available skills.

## Using it

Usually you don't have to do anything — it triggers on UI, UX, and product-shaped
requests on its own. To force it:

```
/human-centered-design
```

Some things worth asking it for:

- *"Build me a habit tracker"* — it will ask who the user is before it opens an
  editor
- *"Users keep abandoning our signup flow"* — starts at cognitive walkthrough and
  works backwards to the cause
- *"Run a heuristic evaluation on the settings page"* — the ten heuristics with
  severity ratings
- *"This has to be simple but also powerful"* — names the contradiction and
  resolves it by separation rather than compromise

## Design decisions

A few things I chose deliberately, in case you want to change them:

- **It writes files.** Artifacts land in a `design/` directory rather than
  evaporating into chat.
- **It names assumptions.** When it can't reach real users, it says so and marks
  personas as assumed, with the blast radius if wrong. An assumption you named is
  a design decision; one you didn't notice is a landmine.
- **It self-reviews.** A heuristic pass that finds nothing means the pass didn't
  happen, and the skill says so.
- **TRIZ is translated for software.** Progressive disclosure is
  separation-in-time; responsive breakpoints are separation-in-condition; plugin
  architectures are whole-versus-parts. The habit it installs: when you catch
  yourself proposing a compromise, write the contradiction down and separate it
  instead.

## Provenance

Distilled from a Creative Engineering Design lecture series (Inha University in
Tashkent, Dr. Oybek Eraliev), which itself draws on:

- Donald Norman, *The Design of Everyday Things*
- Alan Cooper et al., *About Face*
- Jakob Nielsen, [10 Usability Heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/)
- David Benyon, *Designing Interactive Systems*
- Genrich Altshuller, TRIZ
- [Laws of UX](https://lawsofux.com/)

The prose here is original synthesis, not reproduced course material. The
underlying principles are from the published literature above; go read it.

## Licence

MIT — see [LICENSE](LICENSE).
