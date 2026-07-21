# 08 — Wireframe Translation

Input: a wireframe PHOTO (hand sketch, Figma frame, whiteboard shot) + a template whose taste
has been studied (Stages 0–1). Output: a site where every wireframe region is executed **the
way this template's designer would have executed that brief** — not a literal tracing of the
wireframe's boxes.

## The precedence rule (memorize this)

- The **wireframe governs**: what sections exist, their order, what content/elements each
  contains, relative emphasis (what's big vs small), and required functionality (form, map,
  gallery, CTA targets).
- The **Designer Model governs**: everything visual — type, color, spacing, alignment,
  density, motion, and the archetype used to realize each region.
- On conflict, taste wins over sketch geometry: if the wireframe draws a 4-column icon grid
  but the designer "never explains with icons," you deliver the designer's version of that
  intent and FLAG the deviation with the quoted rule. The wireframe author sketched intent,
  not art direction — your job is intent, executed in the designer's hand.
- Only the user's words outrank taste: if the request explicitly says "follow the wireframe
  literally here," do so and note the taste tension in delivery notes.

## Step 1 — Wireframe Read (written artifact, mandatory)

Study the photo top-to-bottom and write a numbered inventory:

```
W1 | region name        | contents drawn (headline? image? 3 cards? form?) | emphasis | annotations/labels legible in the photo
W2 | ...
```

- Transcribe every legible label/word in the sketch verbatim; mark illegible ones `[?]` and
  list them as questions, don't guess silently.
- Note drawn hierarchy signals: box sizes, thick vs thin strokes, "big text here" scribbles,
  arrows, numbering.
- If the photo is skewed/cropped/ambiguous, say what's unreadable and proceed only on the
  readable parts — flagged, never invented.

## Step 2 — Translation Table (written artifact, mandatory)

Map every W-row to the designer's vocabulary BEFORE building anything:

```
W# | intent | chosen archetype (from 02-D) | atoms used | content source (onboarding field) | precedent or Studio?
```

- A wireframe region matching an existing archetype → assign it (clone-in-place execution).
- A region with NO precedent in the template → route it through the Design Studio (04 §0):
  three concepts for how THIS designer would realize that intent, judged by the Model.
- Adjacent regions must not resolve to the same archetype back-to-back (04 diversity rule) —
  if the wireframe repeats a shape, vary the execution the way the designer varies it, and
  note it.
- Every content element in a region needs a source: onboarding data, template copy kept, or
  FLAGGED placeholder. Wireframes often contain lorem/dummy labels — never let sketch dummy
  text leak into the build.

## Step 3 — Build

Standard rules (03/04/05) apply unchanged. Section order = wireframe order. Page rhythm,
spacing between sections, and breakpoint behavior come from the template's system, not from
the sketch's proportions.

## Step 4 — Verify (adds P16 to the Parameter Matrix)

**P16 — Wireframe conformance (HARD):** walk the built page against the Wireframe Read:
every W-region present, in order, with all its drawn elements realized or explicitly flagged;
nothing added that the wireframe or request didn't ask for; every taste-over-sketch deviation
listed with the Designer Model rule that justified it. The Translation Table ships in the
delivery notes so the wireframe author can audit intent → execution line by line.
