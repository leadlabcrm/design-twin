# 00 — Pipeline & Order of Operations

You are not "an AI making a change to an HTML file." You are stepping into the original
designer's chair. Everything below exists to make that literally true in the output.

## Mandatory order

```
INGEST → DESIGN DNA → PATTERN INVENTORY → PLAN → BUILD → REVIEW GATE → (fix → REVIEW GATE)* → DELIVER
```

No step may be skipped, merged, or reordered. In particular:

- **BUILD may not start** until the Design DNA worksheet (01) and Pattern Inventory (02) are
  written out in full. Writing them "mentally" does not count — produce them as actual text in
  your working notes. This is what prevents "random changes": every build decision must cite a
  line from these two documents.
- **DELIVER may not happen** until the Review Gate (06) passes with every hard check green.
  There is no limit on fix→review loops. Two consecutive clean passes are required after any
  fix round (a fix can introduce a new defect; the second pass catches it).

## Step details

### INGEST
- Read the ENTIRE file. Not the first 500 lines — all of it, including the `<style>` blocks,
  font declarations, and any `<script>` at the bottom. Large files: read in chunks until
  exhausted. You cannot clone a voice you've only half heard.
- Note the generator (Framer exports have telltale markup — see 03). Note whether styles are
  inline, in `<style>` blocks, or external. Note the asset strategy (CDN URLs vs local files).

### INGEST from a live template link (Reference Capture)
When the input is a LIVE URL (with or without an extracted copy), capture a measured baseline
BEFORE any work — this baseline is what the checking parameters (06) compare against:

1. **Open the live site in a browser.** Screenshot the top of the page at desktop and mobile
   widths. (If below-the-fold screenshots render black — a known compositing artifact with
   scroll-choreographed sites — verify via DOM instead: `elementFromPoint`, computed styles,
   and glyph rects prove what actually paints.)
2. **Measured type table:** for one element of every text tier (display, heading, body, label,
   button), record COMPUTED font-family/size/weight/line-height/letter-spacing/transform/color
   via `getComputedStyle` — computed values catch runtime scaling (e.g. fit-text) that static
   markup hides.
3. **Section map with geometry:** every section's name, archetype, rendered height at desktop
   and mobile, and vertical gap to the next section.
4. **Motion log:** watch the load and one full scroll. Note which elements animate, trigger
   points, perceived durations, marquees/loops, hover states on each interactive element.
5. **Console + network baseline:** record pre-existing errors so later verification can
   distinguish inherited noise from regressions.
6. If working on an extracted copy, serve it locally and confirm it renders identically to
   the live link BEFORE editing — differences found later are otherwise unattributable.

### DESIGN DNA (protocol/01)
Fill `templates/design-dna.md` completely, with **exact values copied from the file** —
real hex codes, real px/rem values, real cubic-bezier strings. "Around 24px" is a protocol
violation; the file knows the answer.

### PATTERN INVENTORY (protocol/02)
List every section top-to-bottom and dissect how this designer builds. This is where taste
lives: the DNA is the palette, the inventory is the brushwork.

### PLAN
Write 3–6 sentences: which existing section(s) the change will be cloned from, which tokens it
will use, what the motion treatment will be, and where it slots into the DOM. Every choice must
reference the DNA/Inventory. If the change request requires something with **no precedent in the
file** (e.g., "add a video carousel" to a site that has no carousel and no video), pick the
nearest existing pattern to extend and note the gap — and say so to the user in the final
delivery notes rather than silently inventing a foreign pattern.

### BUILD (protocol/03, 04, 05)
Write the code. Clone-first, compose-second, invent-never.

### REVIEW GATE (protocol/06)
Full designer QA pass with the scorecard. Fail → fix → full re-review. Pass twice → deliver.

### DELIVER (protocol/07)
Complete file + scorecard + decision summary.

## Scope rule

Touch only what the change requires. Do not "improve," reformat, re-indent, prettify, dedupe,
or modernize any code you were not asked to change — byte-level stability of untouched regions
is itself a fidelity requirement (a designer editing their own file doesn't reformat the whole
thing). Whitespace style of new code must match the file's existing style, even if it's ugly
minified single-line markup — match it.
