# 01 — Design DNA Extraction

Goal: after this step you could delete the site and redraw any section of it from the worksheet
alone. Fill `templates/design-dna.md` with **exact values from the file** — never approximations,
never "standard" values from your training. If the site uses `letter-spacing: -0.03em`, the
worksheet says `-0.03em`, not "slightly tight."

Work through every category below. For each, cite where in the file the value comes from
(a class name, a CSS variable, a section name) so build decisions are traceable.

## 1. Typography (the single biggest tell)

- **Families:** every `font-family` stack in the file, and how fonts load (Framer CDN
  `https://framerusercontent.com/...` woff2? Google Fonts? `@font-face` inline?). Record the
  exact `@font-face` sources and `font-display` values. New text must use these fonts via the
  same mechanism — never add a new font or a new loading method.
- **Scale:** the complete set of font-sizes in use (e.g. 12/14/16/18/24/40/64px). This is a
  closed set. A new heading uses an existing size from the correct tier, never 22px because it
  "felt right."
- **Weights:** which weights are actually loaded and used per role (headings vs body vs labels).
  Using a 500 weight when the file only loads 400 and 700 will render fake-bold — instant tell.
- **Line-heights & letter-spacing:** per tier, exact values (em/px/unitless — keep the unit
  style too).
- **Casing & punctuation habits:** ALL-CAPS labels? Sentence case headings vs Title Case?
  Periods at the end of card blurbs or not? Ampersands or "and"? Em-dash use? These are
  designer fingerprints — copy them.
- **Text wrapping habits:** `<br>` forced line breaks in headings? `max-width` on paragraphs
  (record the exact ch/px value)? `text-wrap: balance`?

## 2. Color

- Full palette as used: backgrounds, text tiers (primary/secondary/muted), accent(s), borders,
  overlays — exact hex/rgb/oklch strings AND the format used (if the file writes
  `rgb(255, 255, 255)` don't write `#fff`).
- CSS variables / Framer tokens (`--token-...`): map each variable to its value and its role.
  **If the file uses tokens, new code uses the tokens, not the resolved values.**
- Gradients: exact stops, angles, and where they're used.
- Opacity conventions: does the designer make secondary text `#888` or `rgba(0,0,0,0.6)`?
  Which pattern — copy it.

## 3. Spacing & Layout

- **Spacing scale:** the set of paddings/gaps/margins actually used (e.g. 8/12/16/24/40/80/120).
  Closed set, same rule as font sizes.
- **Section rhythm:** vertical padding of each major section (top and bottom, desktop and
  mobile). Is it constant (every section 120px) or varied? New sections must land on the rhythm.
- **Container:** max-width value(s), horizontal padding at each breakpoint, centered how.
- **Grid habits:** flex vs grid, column counts, gap values, how cards stretch/align.
- **Alignment character:** is this a center-aligned site, left-aligned, mixed with a rule
  (e.g. hero centered, everything else left)? Identify the rule, don't guess per-section.

## 4. Shape & Surface

- Border-radius set (buttons vs cards vs images vs pills — each exact value).
- Borders: width, color, where they appear (all cards? only inputs?).
- Shadows: exact `box-shadow` strings and which elevation tier gets which shadow.
- Backdrop effects: blur values, glassmorphism, noise/grain overlays, background patterns.

## 5. Imagery & Iconography

- Icon system: inline SVG? Which set (stroke width, corner style, filled/outline)? Sizes?
- Image treatment: radius, aspect ratios, object-fit, overlays/tints, alt-text style.
- Illustration/photo style so any new asset request can be described consistently.

## 6. Components (atoms)

For buttons, links, inputs, badges/pills, cards: the complete recipe — padding, radius, font,
default + hover + active states (including transition properties and durations). There are
usually exactly 1–3 button variants; record each and never create a fourth.

## 7. Copy voice

- Heading style: short & punchy ("Ship faster.") vs descriptive ("Everything you need to ship").
  Word length patterns, use of "you/we", questions vs statements.
- Subheading/body register, CTA verb style ("Get started" vs "Start free trial" vs "Book a call").
- Any recurring rhetorical patterns (number-led stats, "No X. No Y. Just Z." constructions).
New copy must read like the same person wrote it on the same day.

## 8. Motion (summary — full treatment in 05)

- Appear/scroll-in animations: exact transform distances, opacity ranges, durations, delays,
  easing curves, stagger patterns.
- Hover transitions: properties animated, durations, easings.
- Any scroll-linked effects, marquees, parallax, looping animations.

## 9. Breakpoints & Responsive behavior

- Exact breakpoint values (Framer commonly: desktop / ≤1199 tablet / ≤809 mobile — but read the
  file, don't assume).
- The mechanism: media queries? Framer's duplicated variant DOM (`ssr-variant`, `hidden-*`
  classes)? Both? New content must implement responsiveness the same way — see 03.
- What changes at each breakpoint per section type (font size drops, column collapses, hidden
  elements) — record the pattern.

## 10. Meta & plumbing

- How `id` anchors, nav links, and smooth scrolling work.
- SEO/meta/OG patterns if a new page/section affects them.
- Any inline `<script>` behaviors (menu toggles, tabs, accordions) and their conventions.

---

**Output check:** the worksheet is done when every field has an exact value + source citation,
and the "closed sets" (fonts sizes, colors, spacing, radii, shadows, easings, durations) are
explicitly listed. These sets are the law during BUILD: if a value isn't in a set, it doesn't
go in the file.
