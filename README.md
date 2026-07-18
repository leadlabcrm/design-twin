# Design Twin Protocol

**Make edits to an extracted website that are indistinguishable from the original designer's own work.**

This repo is an instruction set for an AI assistant (Claude). When given an extracted website
(usually a single HTML file exported from Framer) plus a change request, the assistant must follow
this protocol **in full, in order, with no steps skipped** — so the output looks like the original
designer opened their own file and made the change themselves.

## The core promise

> No one — including the original designer — should be able to point at the new/edited section and
> say "an AI did this" or "a different person did this." Typography, spacing, color, motion,
> markup structure, naming, and copy voice must all be native to the file.

## How to use (for the human)

1. Extract the site (e.g., via a Framer extractor) → you get an HTML file (plus maybe assets).
2. Open a Claude session, attach or point to the HTML file.
3. Paste the prompt from [PROMPT.md](PROMPT.md), filling in your change request.
4. Claude reads this protocol, studies the file, builds the change, runs the review gate, and only
   then returns the result.

## Pipeline (for the assistant)

| Step | File | What happens |
|------|------|--------------|
| 0 | [protocol/00-pipeline.md](protocol/00-pipeline.md) | Mandatory order of operations. Read first. |
| 1 | [protocol/01-design-dna.md](protocol/01-design-dna.md) | Extract the site's complete Design DNA before touching anything. |
| 2 | [protocol/02-pattern-inventory.md](protocol/02-pattern-inventory.md) | Catalog every existing section & component and how they're built. |
| 3 | [protocol/03-framer-conventions.md](protocol/03-framer-conventions.md) | Framer-export-specific markup rules you must preserve. |
| 4 | [protocol/04-build-rules.md](protocol/04-build-rules.md) | Hard rules for writing the new/changed code. |
| 5 | [protocol/05-motion-fidelity.md](protocol/05-motion-fidelity.md) | Animation & interaction fidelity rules. |
| 6 | [protocol/06-review-gate.md](protocol/06-review-gate.md) | The designer's-eye self-review. Failing = loop back, fix, re-review. |
| 7 | [protocol/07-output-rules.md](protocol/07-output-rules.md) | How to deliver the final result. |

Templates the assistant fills in while working:

- [templates/design-dna.md](templates/design-dna.md) — the Design DNA worksheet
- [templates/review-scorecard.md](templates/review-scorecard.md) — the review gate scorecard

## Non-negotiables (summary)

1. **Never write a line of new UI code before the Design DNA worksheet and Pattern Inventory are complete.**
2. **Never invent** a color, font, font-size, spacing value, radius, shadow, easing curve, or
   animation duration that does not already exist in the file. Reuse exact values.
3. **Clone atoms, compose sections.** Editing an existing section = keep its skeleton. Adding a
   NEW section = pick a layout archetype from the designer's own vocabulary that DIFFERS from
   the adjacent sections — never stamp the same skeleton back-to-back with different words.
   Recombine the designer's moves the way they would; invent nothing foreign.
4. **The review gate is mandatory** and must be passed at 100% (all hard checks green) before any
   output is shown to the user. Failures loop back to a fix pass — as many rounds as needed.
5. **Deliver the complete working file**, never fragments with "…rest unchanged" placeholders,
   unless the user explicitly asks for a diff only.
