# 04 — Build Rules

You may only start here with a completed Design DNA worksheet, Pattern Inventory, and written
plan. Every rule below is a hard rule.

## 1. Clone-first construction

1. Copy the **primary clone source** section's markup verbatim (chosen in 02-C).
2. Mutate content: text, icons, images, counts (3 cards → 4 cards by duplicating a card node).
3. Adjust only what the change requires; every adjustment must use values from the DNA closed
   sets and patterns from the inventory.
4. Repeat per breakpoint variant if the file duplicates DOM per breakpoint (03-4).

Composing a section from scratch is allowed **only** when no remotely comparable structure
exists — and then every atom inside it (headings, buttons, cards, spacing stack) is still
cloned from inventory recipes, and you flag the precedent gap in delivery notes.

## 2. Closed sets are law

Before typing any literal value, check it against the DNA sets:

- font-size, weight, line-height, letter-spacing → from the type scale
- color → from the palette, in the file's format, via token/variable if the file uses them
- padding/margin/gap → from the spacing scale; section vertical padding on the section rhythm
- radius, border, shadow → from the surface sets, exact strings
- duration, delay, easing → from the motion sets, exact strings

If the perfect value seems to be missing (you "need" 28px in a 24/32 world): you don't. Pick
the set member the designer would use — usually the one used in the analogous position elsewhere.

## 3. Copy voice

Write all new copy in the voice profile from DNA §7. Match: heading length and casing, CTA verb
pattern, punctuation habits, "you/we" register, and the level of concreteness (real designers
rarely write "Lorem ipsum" or generic "Amazing feature that helps you succeed" — write copy as
specific as the site's real copy; if you lack facts, use the site's own domain language and
flag copy for the user to review). **Banned:** em-dash overuse if the site doesn't use them,
"seamless/effortless/unlock/supercharge" filler unless the site already talks like that,
exclamation marks the site doesn't use.

## 4. Every state, not just the happy render

For each interactive element you add: default, hover, focus-visible, active — matching the
sibling element's treatment exactly (same transition property list, duration, easing). If the
file does nothing on focus, you do nothing on focus (fidelity beats your preferences —
accessibility improvements are offered in notes, not silently injected).

## 5. Wiring completeness

- New nav items scroll/link correctly using the file's mechanism.
- New animated nodes are registered with the file's animation runtime (03-3).
- New content exists in every breakpoint variant with correct visibility classes (03-4).
- ids are unique; minted class hashes collide with nothing (search the file to confirm).
- No console errors: any script you touched still parses; any JSON blob you extended is valid.

## 6. Untouched code is untouchable

No reformatting, no re-indentation, no attribute reordering, no dead-code cleanup outside the
change. Your diff should read as: designer opened file, added/edited one thing, saved.

## 7. Placeholder policy

Real hrefs, real anchor targets, real copy. Where genuinely user-supplied assets are needed
(product screenshots, logos), reference them in the file's existing asset style with a clearly
flagged path (e.g. same-format `framerusercontent` sibling image reused, or `assets/…` path if
the extraction uses local assets) and list every such placeholder in delivery notes. Never ship
`href="#"` on a CTA whose siblings have real targets, never `TODO` comments — the file has no
comments; yours don't either (check: most Framer exports contain zero HTML comments).
