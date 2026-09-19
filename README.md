# From Figma to Function

Materials for a hands-on workshop on taking a real Figma design to a working interface with Claude Code.

Berlin · three hours · in person · part of the Co-Work &amp; Code series.

---

## What the workshop argues

Most of the quality of an AI-assisted build is decided before anyone types a prompt.

A model reproduces the structure it is handed. Give it a screenshot and it has to guess: it invents names for things that had none, hardcodes every colour it can see, builds one static view because it was shown one static view, and rewrites half the file the moment you ask for a change. Give it a system and the guessing stops. Named components become named code, tokens become variables, and the states you drew get built because they exist.

Same model. Same prompt. Different file.

**Your design system is the prompt.** Everything in this repository follows from that.

Three consequences the workshop works through:

1. **Naming became functional.** A layer name used to be a note to a teammate. It is now an instruction, and an empty one if the layer is called `Frame 427`.
2. **The system is the leverage, not the screen.** Anyone can generate one screen. The test is the fiftieth, and what a change to one token costs you.
3. **Design judgement did not get automated.** Models produce work that looks finished. Holding a spacing scale, keeping hierarchy under real content, building the states nobody drew, leaving a focus ring where a keyboard user needs one: still yours.

## Who it is for

Practising UX, UI, product and design-system designers who are already fluent in Figma.

It is not an introduction to design, not an introduction to Figma, and it does not promise one-click production code.

## Prerequisites

| | |
|---|---|
| Claude account | A paid plan. Claude Code does not run on the free tier |
| Figma account | Free is fine |
| Laptop | With permission to install software. Check this early if it is managed by an employer |
| Node | Version 18 or higher |

The prep page below walks through all of it and ends with a single self-test that proves the whole chain works.

## What is here

| Path | What it is |
|---|---|
| `site/index.html` | The attendee prep page. Setup checklist, a primer, ten minutes of play, when to reach for Claude Code and when for a Figma prototype, the naming reference, and a glossary. About 40 minutes of preparation |
| `instructor/` | Presentation and facilitation material. **Contains spoilers.** See the warning below |
| `.github/workflows/pages.yml` | Publishes `site/` to GitHub Pages |

### Attendees start here

Open the prep page and work through it in order. Do it on the laptop you are bringing, and do it before the day rather than on the night. The setup section is the part that matters; everything after it saves you time in the room but will not leave you stranded.

### A warning about `instructor/`

The starter Figma file contains two faults placed there on purpose. Discovering them in your own build is one of the better moments of the evening, and `instructor/` documents exactly what they are and when to reveal them.

If you are attending, do not read that folder. Nothing in it will help you and it will cost you the good part.

## Running it yourself

The material is reusable. `instructor/starter-project-spec.md` is a complete build spec for the starter Figma file, including the token set, the nine components, the frames, the two deliberate faults and the change request that the whole evening turns on. The presentation is a single self-contained HTML file: open it in a browser, navigate with the arrow keys, press `N` for presenter notes and timings, `F` for fullscreen.

If you do run it, an attribution is appreciated and a note about how it went is more so.

## Credits

Created and taught by **Hooman Abbasi**, Design Lead and design strategist.

Co-hosted with **Vidushi Malhan**, who runs the Co-Work &amp; Code workshop series and covers the Claude Code setup and tooling in the room.
