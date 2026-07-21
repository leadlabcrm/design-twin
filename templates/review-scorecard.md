# Review Scorecard — pass [n]

> HARD items: any fail → fix → re-run ENTIRE gate. Deliver after two consecutive all-green
> passes. Every verdict needs evidence (a value comparison, a search result, a screenshot),
> not "looks fine". Unverifiable → mark ⚠ UNVERIFIED with reason, never ✅.

## A. Value fidelity (HARD)
| # | Check | Evidence | ✅/❌ |
|---|-------|----------|------|
| A1 | Every font-size/weight/line-height/letter-spacing in new code ∈ DNA type sets | | |
| A2 | Every color ∈ palette, correct format, tokens used where file uses tokens | | |
| A3 | Every padding/margin/gap ∈ spacing set; section padding on rhythm | | |
| A4 | Radius/border/shadow strings exact matches to surface sets | | |
| A5 | Zero values in new code that exist nowhere else in file (searched & proven) | | |

## B. Structure fidelity (HARD)
| B1 | New markup skeleton diffed against clone source — divergences all justified | | |
| B2 | Class dialect matches (hash-style classes; no semantic/BEM/tailwind names) | | |
| B3 | data-framer-name naming matches designer's naming style | | |
| B4 | Attribute order / indentation / formatting matches file style | | |
| B5 | No HTML comments, TODOs, or annotations introduced | | |

## C. Responsive (HARD)
| C1 | New content present & correct in EVERY breakpoint variant/media query | | |
| C2 | Visibility/hidden-class wiring verified against same-breakpoint neighbors | | |
| C3 | Per-breakpoint value changes follow neighbors' patterns | | |

## D. Motion (HARD)
| D1 | Entrance animation param-equal to nearest sibling (duration/easing/transform/delay) | | |
| D2 | New animated nodes registered in file's mechanism; appear-ids unique | | |
| D3 | No orphaned opacity-0 / stuck states if runtime skips new nodes | | |
| D4 | Hover/active/focus states match cloned component exactly | | |
| D5 | Stagger pattern matches siblings | | |

## E. Integrity (HARD)
| E1 | File parses; tags balanced; scripts & JSON blobs valid | | |
| E2 | No duplicate ids; anchors/nav links resolve | | |
| E3 | Untouched regions byte-identical to input | | |
| E4 | No placeholder hrefs/copy beyond flagged list | | |

## F. Voice (HARD)
| F1 | New copy read alongside 3 existing sections — same author verdict | | |
| F2 | Casing, punctuation, CTA verbs, sentence lengths consistent | | |

## G. Optical (browser available? else mark ⚠ UNVERIFIED)
| G1 | Screenshot desktop: alignment edges, rhythm, type sizes match neighbors | | |
| G2 | Screenshot mobile: same | | |
| G3 | Entrance animation observed firing correctly; neighbors unaffected | | |
| G4 | Console: no new errors | | |

## Five killer questions (written answers required)
1. Would the designer stop scrolling at this section? —
2. Any value in new code that exists nowhere else in the file? —
3. Correct at every breakpoint? —
4. Entrance matches neighbors parameter-for-parameter? —
5. Can the raw-HTML reader spot the author change? —

## Parameter Matrix (protocol/06 — every row, every pass)
| P | Parameter | ✅/❌/⚠ | Evidence (measured value / count / screenshot ref) |
|---|-----------|--------|------------------------------------------------|
| P1 | Typography fidelity | | |
| P2 | Color discipline | | |
| P3 | Spacing & rhythm | | |
| P4 | Surface | | |
| P5 | Motion fidelity | | |
| P6 | Voice & copy | | |
| P7 | Archetype: diversity / novelty / model | | |
| P8 | Responsive integrity (375/810/1200) | | |
| P9 | Hydration integrity (all copies + survives re-render) | | |
| P10 | Links & wiring | | |
| P11 | Assets | | |
| P12 | Meta & brand sweep | | |
| P13 | Untouched-region stability | | |
| P14 | Optical parity vs Reference Capture | | |
| P15 | Weight & console vs baseline | | |

**Verdict:** PASS / FAIL → [if fail: list fixes, then re-run full gate]
**Consecutive clean passes:** [n]/2
