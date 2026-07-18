# 05 — Motion Fidelity

Motion is where clones get caught. A pixel-perfect static section that fades in with
`ease 0.3s` when every sibling uses a 0.8s spring with a 0.15s stagger reads as foreign in the
first scroll. Treat motion values with the same "closed set" law as colors.

## 1. Extract the motion system first (during DNA)

Catalog from the file, with exact strings:

- **Entrance animations:** per section — initial state (translateY(40px)? scale(0.95)?
  opacity 0.001?), final state, duration, delay, easing (cubic-bezier string or spring config
  JSON), and trigger (load vs scroll-into-view, threshold).
- **Stagger patterns:** how child elements offset (0.1s per card? heading→sub→CTA at
  0/0.1/0.2?). Direction of stagger.
- **Hover transitions:** which properties (transform? background? color? shadow?), duration,
  easing — per component type.
- **Continuous motion:** marquees (speed as duration-per-loop, direction, pause-on-hover?),
  floating elements, gradient animations, parallax factors.
- **Micro-interactions:** button press scale, accordion open curve, tab switches.

## 2. Application rules

1. **New section entrance = nearest sibling's entrance,** parameter-for-parameter, registered
   through the same mechanism (CSS keyframes, appear-id JSON, IntersectionObserver script —
   whatever this file uses; see 03-3).
2. **Stagger children the way siblings stagger** — same step, same order, same cap (some sites
   stop staggering after n items).
3. **Never substitute easings.** `cubic-bezier(0.44, 0, 0.56, 1)` is not `ease-in-out`. Springs
   (`data-framer-spring`, JSON spring params) are copied as config, not approximated by beziers.
4. **Durations come from the file's duration set.** No 300ms defaults in a 600/800ms site.
5. **Respect what's absent:** if the site has no scroll animations, a new section doesn't get
   one. Static is a motion choice too.
6. **`will-change` / transform hygiene:** mirror sibling usage exactly — Framer sets these
   deliberately; missing ones cause visible jank differences, extra ones are a code tell.
7. **Reduced motion:** if the file honors `prefers-reduced-motion`, extend that handling to new
   nodes; if it doesn't, don't add it (note it instead).

## 3. Verification (feeds the review gate)

Simulate the first-load and first-scroll experience in your head, then — if a browser is
available — actually load the file and watch:

- Does the new section's entrance fire at the same scroll offset behavior as neighbors?
- Is anything stuck at opacity 0 (unregistered appear-id — the classic failure)?
- Do hovers on new elements feel identical to hovers on cloned-from elements?
- Does the page still animate correctly ABOVE and BELOW the new section (no broken stagger
  chains, no duplicate appear-ids hijacking each other)?
