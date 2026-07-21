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
- **(v3.2 correction) The wireframe also governs each section's internal LAYOUT, literally:**
  column splits, image placement and presence, element counts (6 cards means 6 cards), card
  vs list, table vs line, buttons drawn means buttons built, a map drawn means a map
  rendered. If the author drew it, they want to SEE it.
- The Designer Model is STYLING ONLY: it skins the wireframe's skeleton (fonts, sizes,
  colors, spacing, radii, hovers, motion) and fills gaps the sketch leaves open. **Taste may
  propose, never override:** when a drawn layout collides with a Model rule ("never cards"),
  build the wireframe's version styled as tastefully as the system allows, and offer the
  designer's alternative in the delivery notes as an opt-in suggestion. Only the user's
  explicit words in the request outrank the drawing.
- Template mechanics that physically constrain section order (e.g. a scroll-choreographed
  opening that cannot be reordered) must be surfaced as a named constraint BEFORE building —
  never discovered by the user in the delivery.

**The failure this correction replaces:** a field build where drawn cards became text lists,
split layouts became centered stacks, and the map became a link — "in the designer's taste"
but not what was drawn. That is re-skinning the designer's habits onto the user's plan, and
it fails the wireframe author. Structure is the user's; skin is the designer's.

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
