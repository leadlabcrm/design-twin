# 03 — Framer Export Conventions

Extracted Framer sites have a distinctive markup dialect. Breaking the dialect breaks both the
illusion and, often, the page itself. **Read what the actual file does first** — extractors
differ (some inline everything, some keep Framer's runtime, some strip it). This chapter lists
what to look for and the rules for each pattern *if present*.

## 1. Generated class names (`framer-XXXXXX`)

Framer emits hashed classes like `framer-1x2y3z4`, plus semantic-ish ones (`framer-text`,
`framer-styles-preset-...`). Rules:

- **Reusing an existing class = preferred.** If the hero heading's classes produce the exact
  style you need, use the same classes on the new heading.
- **Minting a new class:** generate a new plausible hash (5–7 lowercase alphanumerics, same
  format as the file's), define it in the same `<style>` block region where sibling classes are
  defined, and follow the same selector pattern the file uses (e.g. `.framer-abc12, .framer-abc12 *`
  or breakpoint-scoped variants). **Never** introduce BEM/tailwind/semantic class names
  (`.pricing-card`, `.flex`, `.btn-primary`) into a Framer file — instant tell.
- **Never rename existing classes.**

## 2. `data-framer-name` attributes

Framer labels nodes with human names (`data-framer-name="Hero"`, `"Card"`, `"Desktop"`). New
sections/components get names in the designer's naming style (check: Title Case? short nouns?
numbered variants like "Card 2"?). This is also how you'll identify sections in the inventory.

## 3. Appear / scroll animations (`data-framer-appear-id`)

Framer's entrance animations typically work via `data-framer-appear-id` attributes paired with
generated `@keyframes` and a small runtime script, or via inline `animator` scripts with JSON
config (`__framer__appearAnimationsContent`, `__framer__spring` etc.). Rules:

- Find the mechanism in THIS file. If appear animations are driven by a JSON blob in a script
  tag, new animated elements must be registered in that blob the same way (new appear-id,
  same animation params as sibling sections).
- Copy exact params from the closest sibling: transform distance, opacity range, duration,
  delay/stagger step, and the exact easing (Framer loves springs and specific cubic-beziers —
  copy the string, don't substitute `ease-out`).
- If the extractor stripped the animation runtime and animations are plain CSS, match that CSS.
- **Test mentally for the no-JS case:** if elements start at `opacity:0` waiting for a runtime
  that might not fire for your new ids, verify the registration actually covers them —
  a permanently invisible section is the worst possible failure.

## 4. Responsive variants — the duplicated-DOM pattern

Framer often ships **separate DOM subtrees per breakpoint**, controlled by classes like
`hidden-72rtv7`, `ssr-variant`, media queries toggling `display`, or a top-level variant switch
(`data-framer-name="Desktop" / "Tablet" / "Phone"`). Critical rules:

- If the file duplicates sections per breakpoint, **your new section must be added to EVERY
  breakpoint variant**, with the correct per-breakpoint styles and the correct hidden-class
  wiring. Adding it only to desktop is the #1 real-world failure for this kind of edit.
- If the file instead uses normal media queries, write media queries in the same block/format.
- Verify the hidden/visible class combinations against neighbors at the same breakpoint.

## 5. Typography plumbing

- Rich text uses `.framer-text` on wrappers AND descendants; text styles come from
  `framer-styles-preset-*` classes or `--framer-font-*` CSS variables. Copy the full stack of
  classes/variables from an equivalent text node — a heading missing one preset class will
  render with fallback styles at a glance-visible level.
- Fonts load from `framerusercontent.com` via `@font-face`. New text uses loaded families and
  weights only (see 01).

## 6. Assets

- Images: `framerusercontent.com` URLs, often with `?scale-down-to=` size params and `srcset`.
  New images follow the same pattern (user must supply real assets; use an existing-style
  placeholder reference and flag it in delivery notes — never hotlink foreign stock URLs).
- SVG icons: usually inline. New icons must match the set's stroke width / corner radius /
  viewBox conventions; prefer copying and editing an existing path structure.

## 7. Links, anchors, and the runtime

- Internal anchors: Framer smooth-scrolls via ids/`data-framer-page-link` patterns — wire new
  nav items identically.
- Do not remove or reorder `<script>` tags, `data-framer-*` attributes, or seemingly redundant
  wrappers ("pointless" divs are often animation or layout targets).
- `style` attribute conventions: Framer inlines layout-critical styles (`transform`,
  `opacity`, `will-change`) — mirror what sibling nodes carry.

## 8. Hydration & runtime-dependent rendering — test, don't assume

Extracted Framer sites usually keep the React runtime, which re-renders the page from JS data:

- **DOM-only edits get reverted on load.** Text must be changed in the HTML AND every JS chunk /
  handover blob / search index that carries a copy. Always verify in a browser after editing.
- **New sections inserted into the React root get deleted during hydration.** Place added
  sections outside the root (e.g. the bodyEnd snippet area) and insert them post-hydration with
  a small placement script + MutationObserver. Anchor-chain the config so repeated placement is
  stable (never two nodes anchored "before X" — the second anchors on the first).
- **Fit-text svg variants (`<svg viewBox…><foreignObject class="framer-fit-text">`) are sized by
  the runtime.** In a static clone they collapse to 0 height — use the plain-div text variant
  (unhidden across breakpoints) and pick a font size from the DNA scale that fits the narrowest
  breakpoint.
- **Cross-page clones need their CSS.** Class rules live per-page; when cloning a section from
  another page, extract and carry over every rule (including @media blocks) that mentions its
  classes.

## 9. What the extractor may have broken — don't "fix" beyond scope

Extracted files sometimes carry dead scripts, unused preloads, or broken badge-removal hacks.
Leave them unless they block the requested change; note anything load-bearing you had to touch.
