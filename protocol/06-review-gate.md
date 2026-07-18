# 06 — The Review Gate

You are now the original designer, tired, protective of your craft, reviewing a PR from someone
claiming to have matched your style. You are looking for reasons to REJECT. Run the full
scorecard (`templates/review-scorecard.md`) — every item, evidence required, no "looks fine."

**Protocol:** any HARD item fails → fix → re-run the ENTIRE gate (fixes cause regressions).
Deliver only after two consecutive fully-green passes. Never show the user a version that has
not passed.

## How to review (method, not vibes)

For each check, do the comparison mechanically:

- **Side-by-side value diff:** for the new section and its clone source, extract and compare
  actual values from the code — font-size/weight/line-height per text tier, paddings, gaps,
  colors, radii, shadows, durations, easings. Any value not traceable to the DNA closed sets
  is a fail.
- **Structure diff:** compare DOM skeletons (tag nesting, class stacks, data attributes,
  wrapper depth) between new section and clone source. Unexplained divergence = fail.
- **Breakpoint sweep:** verify the new content at EVERY breakpoint the file supports —
  duplicated-DOM variants all updated, visibility classes correct, per-breakpoint values match
  the neighbors' per-breakpoint pattern.
- **Motion trace:** every new animated node registered in the file's mechanism; params equal to
  sibling params; no orphaned opacity-0 states; unique appear-ids.
- **Voice read-aloud:** read all new copy immediately after reading three existing sections'
  copy. Same author? Casing, punctuation, CTA verbs, sentence length all consistent?
- **Integrity pass:** file parses (balanced tags), scripts/JSON valid, no duplicate ids, no
  broken hrefs/anchors, untouched regions byte-identical, no comments/TODOs introduced.
- **Browser pass (when tools available):** load the file. Screenshot the new section between
  its neighbors at desktop AND mobile widths. Compare alignment edges, rhythm, type sizes
  optically. Watch the entrance animation fire. Check console for new errors.

- **Diversity pass (HARD, for added sections):** name each new section's layout archetype.
  Fail if a new section shares its archetype with an adjacent section, or if any archetype now
  appears more times on the page than the designer's own pages ever use it. "Same skeleton,
  different words" counts as the same archetype — check the DOM, not the copy.
- **Novelty pass (HARD, for added sections):** diff the new section's DOM skeleton against
  EVERY existing section. If it is ≥90% identical to any one of them, it is a re-skin, not a
  design — fail, return to the Design Studio (04 §0), and produce a real concept. Exception:
  the user explicitly asked for "another one like X".
- **Model-consistency pass (HARD, for added sections):** check the built section against the
  Designer Model: every applicable decision rule honored, zero "nevers" violated, tensions
  resolved the designer's way. Quote the specific rules checked and the evidence in the built
  markup.

## The five killer questions (answer in writing on the scorecard)

1. If the designer scrolled past this section tomorrow, would anything make them stop?
2. Is there any value in the new code that exists nowhere else in the file? (Search to prove.)
3. Does the section exist and behave correctly at every breakpoint?
4. Does the entrance animation match its neighbors parameter-for-parameter?
5. Could a reader of the raw HTML spot where the "different author" starts? (Naming, comment
   style, attribute order, indentation, class dialect.)

A confident "no issue" backed by evidence on all five → gate passes. Anything hedged
("should be fine", "probably") is a fail by definition — go verify it.
