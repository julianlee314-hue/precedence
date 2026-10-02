# Precedence — full levels inventory

*Source inventory: 3 October 2026 (ICT). Cross-checked against `engine.js`, `app.html`, `levels.js`, all `levels-*.js` extension files, `README.md`, `docs/STRUCTURE.md`, and `docs/PRECEDENCE_ERA_UNLOCK_MAP.md`.*

This document separates the **Precedence core** (the order-of-operations racer) from the older/larger **Algebra Licenses** ladder that still ships in the same engine and is hidden from the MVP home.

## 1. Recommended nomenclature

Use **Eras** for the ten large Precedence garage cards: an Era carries a math title, a rule progression, a world, and an earned visual travel reward. Use **Levels** for the individual problem bands inside the order-of-operations core; a level produces the clean runs/stamps that help clear an Era. Use **Licenses** for the separate Algebra Licenses wing, where each license contains its own named level ladder (for example, Powers 2.1–2.12 and Quadratics 9.1–9.15). Within a playable level, call a single generated problem a **run** or **challenge**, and call each tap/collapse a **step**. This keeps transport as art and progression language, while math remains the visible title system.

## 2. Precedence core — order-of-ops racer

**Status key:** *Playable* means wired in the current garage. *Stub* means the card exists but has no Era-specific generator yet. “Engine mapping” is the current `PrecEngine.LEVELS` number; a dash means the future Era is not mapped yet.

| # | Math title | Playable? | Engine mapping | Operations / rule focus | Example | Mathera skill IDs | Visual vehicle (development note only) |
|---:|---|---|---:|---|---|---|---|
| 1 | **Sums** | Yes | L1 — Sums | `+` and `−`; brackets are part of the rule set | `9 − 4 + 3` | `II.8.01`, `III.4.03`; bracket rule also `III.1.08` | On foot; Mesa Verde cliffs |
| 2 | **Products** | Yes | L3 — Products | Adds `×`; multiplication before addition/subtraction | `2 + 3 × 4` | `II.8.01`, `II.8.03`, `III.4.03` | Royal litter / Cleopatra likeness; Alexandria. Visual only; no transport label copy |
| 3 | **Differences** | Yes | L2 — Differences | `+ −` mix with bracket-order traps; brackets change order | `(2 + 3) × 4` | `II.8.01`, `III.1.08`, `III.4.03` | Horseback; desert West |
| 4 | **Quotients** | Yes | L4 — Quotients | Adds `÷`; `×` and `÷` resolve left-to-right | `12 ÷ 3 × 2` | `II.8.01`, `II.8.03`, `III.4.03` | Horse-drawn carriage; gaslit Boston |
| 5 | **Mixed operations** | No — stub card | Future mix / no current mapping | All four operations in one road test; precedence and left-to-right review | `18 − 6 ÷ 2 + 1` | Current family: `II.8.01`, `II.8.03`, `III.4.03`; add/confirm any mixed-review IDs during content pass | Early car / Model T; Detroit |
| 6 | **Powers** | No — stub card | L5 — Powers exists, but `POWERS = false` globally | Adds powers; powers outrank multiplication/division | `2 + 3²` | Current engine metadata: `II.8.01`, `II.8.03`, `III.4.03`; bracket rule `III.1.08` where relevant | Streamliner; Art Deco New York |
| 7 | **Long chains** | No — stub card | L6 — Long chains exists, but is not mapped to the garage | Longer expressions combining brackets and powers | `(1 + 2)² × 2` | Current engine metadata: `II.8.01`, `II.8.03`, `III.4.03`; bracket rule `III.1.08` | 1950s cruiser; Route 66 |
| 8 | **Nested** | No — stub card | Future nested generator | Nested brackets; deeper tree/order traps | `2 × (3 + (4 − 1))` | Current family: `II.8.01`, `II.8.03`, `III.1.08`, `III.4.03` | Wedge sports car / Miami Burnout; reserved for 1.0 |
| 9 | **Negatives** | No — stub card | No current core mapping | Negative numbers inside precedence expressions | `−3 + 4 × (−2)` | Extend the current order-of-operations family with the integer/negative skill IDs during content pass | Electric vehicle; San Francisco fog |
| 10 | **Fraction bars** | No — stub card / elite | No current core mapping; sister Fractions app exists | Fraction bars plus the full precedence rule set | Compound fraction-bar expression | Extend with fraction-operation IDs; hand-off to Fractions app is an option | Robotaxi; 2040 neon city |

### Current core wiring

The live `app.html` maps the first four garage cards deliberately as **Sums → engine L1**, **Products → L3**, **Differences → L2**, **Quotients → L4**. Products comes before Differences in the garage because the current fantasy ladder introduces `×` before the dedicated `+ −` bracket-drill band; this is a progression choice, not a claim that the original engine numbering changed. Eras 5–10 are present as locked cards only. The road currently has theme/color packs, not the final foot, litter, horse, carriage, or later vehicle sprites.

The engine does support `^`, and engine levels 5–6 are named **Powers** and **Long chains**, but `const POWERS = false` currently prevents powers from appearing in generated core expressions. The future content pass should turn that on deliberately per Era rather than silently treating the six engine levels as ten finished Eras.

## 3. Original order-of-operations engine levels 1–6

These are the names and generator definitions in `engine.js`; they are the crosswalk for the current Precedence core.

| Engine level | Original display name | Operators / generator intent | Current state |
|---:|---|---|---|
| 1 | **Sums** | `+`; bracket-aware expression trees | Wired to Era 1; playable |
| 2 | **Differences** | `+`, `−`; mixed plus/minus and bracket traps | Wired to Era 3; playable |
| 3 | **Products** | `+`, `−`, `×`; multiplication precedence | Wired to Era 2; playable |
| 4 | **Quotients** | `+`, `−`, `×`, `÷`; exact whole-number division and `×÷` order | Wired to Era 4; playable |
| 5 | **Powers** | Same four base operators plus `^` when enabled | Exists in engine; not garage-wired; powers globally off |
| 6 | **Long chains** | Longer trees (`extra: 2`) plus powers when enabled | Exists in engine; not garage-wired |

Every engine level currently carries the core metadata IDs `II.8.01` and `III.4.03`; levels 3–6 also carry `II.8.03`. The UI rule board adds `III.1.08` for the brackets-first rule. The exact future ID set for negatives and fraction bars should be confirmed against the Mathera skill tree when those generators are written.

## 4. Algebra Licenses wing — hidden from the Precedence MVP home

This is the compact crosswalk of `LIC` in `levels.js`. The number before the dot is the license; the number after the dot is the level’s position in that license. The IDs are stable save keys, so they should not be renumbered casually. “Mixed review” is a review level, not a new topic. Levels marked **comeback** wait for a later license; they remain part of the inventory even when not initially available.

### License 2 — Powers

| Level ID | Display name |
|---|---|
| `2.1` · `2.mul` | Same base, multiply |
| `2.2` · `2.div` | Same base, divide |
| `2.3` · `2.pow` | Power of a power |
| `2.4` · `2.neg` | Zero and negative exponents |
| `2.5` · `2.frac` | Fractional exponents |
| `2.6` · `2.laws` | All the laws at once |
| `2.7` · `2.negbase` | Negatives and fractions as bases |
| `2.8` · `2.negfrac` | Negative exponents in fractions |
| `2.9` · `2.sci` | Scientific notation |
| `2.10` · `2.mix` | Mixed review |
| `2.11` · `2.rad` | Radicals and fractional exponents — comeback after 11 |
| `2.12` · `2.calc` | Rewrite for the power rule — comeback after 13 |

### License 3 — Simplify

| Level ID | Display name |
|---|---|
| `3.1` · `3.like` | Like terms |
| `3.2` · `3.dist` | Distribute |
| `3.3` · `3.minus` | Minus before a bracket |
| `3.4` · `3.nest` | Nested brackets |
| `3.5` · `3.pow` | Like terms with powers |
| `3.6` · `3.fraccoef` | Fractions as coefficients |
| `3.7` · `3.twolet` | Two letters |
| `3.8` · `3.dec` | Decimals |
| `3.9` · `3.mix` | Mixed review |
| `3.10` · `3.rat` | Cancel factors in fractions — comeback after 10 |
| `3.11` · `3.radlog` | Radicals and log laws — comeback after 11 |
| `3.12` · `3.calc` | Tidy a derivative — comeback after 13 |

### License 4 — Expand

| Level ID | Display name |
|---|---|
| `4.1` · `4.mono` | Monomial times polynomial |
| `4.2` · `4.foil` | Two binomials |
| `4.3` · `4.spec` | Special products |
| `4.4` · `4.tri` | Binomial times trinomial |
| `4.5` · `4.three` | Three factors |
| `4.6` · `4.twolet` | Two letters |
| `4.7` · `4.expsimp` | Expand and simplify |
| `4.8` · `4.cube` | Cube a binomial |
| `4.9` · `4.mix` | Mixed review |
| `4.10` · `4.conj` | Conjugates — comeback after 11 |
| `4.11` · `4.dq` | Difference quotients — comeback after 12 |

### License 5 — Factor

| Level ID | Display name |
|---|---|
| `5.1` · `5.gcf` | Common factor |
| `5.2` · `5.gcfpow` | Common factor with powers |
| `5.3` · `5.group` | Grouping |
| `5.4` · `5.tri1` | x² + bx + c |
| `5.5` · `5.tria` | ax² + bx + c |
| `5.6` · `5.spec` | Special patterns |
| `5.7` · `5.gcfthen` | Common factor first, then factor |
| `5.8` · `5.twolet` | Two letters |
| `5.9` · `5.cubes` | Cubes |
| `5.10` · `5.qtype` | Quadratic type |
| `5.11` · `5.twice` | Factor twice |
| `5.12` · `5.mix` | Factor completely |
| `5.13` · `5.divthm` | Long division and the factor theorem — comeback after 10 |
| `5.14` · `5.fracexp` | Negative and fractional exponents — comeback after 11 |
| `5.15` · `5.calc` | Tidy a derivative — comeback after 13 |

### License 6 — Isolate

| Level ID | Display name |
|---|---|
| `6.1` · `6.one` | One step |
| `6.2` · `6.two` | Two steps |
| `6.3` · `6.brack` | Brackets first |
| `6.4` · `6.both` | x on both sides |
| `6.5` · `6.frac` | Fractions and decimals |
| `6.6` · `6.prop` | Proportions |
| `6.7` · `6.none` | No solution or every number |
| `6.8` · `6.abs` | Absolute value |
| `6.9` · `6.form` | Formulas |
| `6.10` · `6.twice` | The letter shows up twice |
| `6.11` · `6.bottom` | x on the bottom |
| `6.12` · `6.mix` | Mixed review |
| `6.13` · `6.ratq` | Rational equations that turn quadratic — comeback after 10 |
| `6.14` · `6.rad` | Radical equations and false roots — comeback after 11 |
| `6.15` · `6.explog` | Exponential and log equations — comeback after 11 |
| `6.16` · `6.calc` | Where the slope is zero — comeback after 13 |

### License 7 — Inequalities

| Level ID | Display name |
|---|---|
| `7.1` · `7.one` | One step |
| `7.2` · `7.flip` | Negative flips |
| `7.3` · `7.two` | Two steps |
| `7.4` · `7.comp` | Compound |
| `7.5` · `7.abs` | Absolute value |
| `7.6` · `7.nl` | Number line |
| `7.7` · `7.int` | Interval notation |
| `7.8` · `7.xy` | Two variables |
| `7.9` · `7.both` | Where both are true |
| `7.10` · `7.frac` | Fractions in inequalities |
| `7.11` · `7.mix` | Mixed review |
| `7.12` · `7.rat` | Rational inequalities — comeback after 10 |
| `7.13` · `7.calc` | Where a function rises — comeback after 13 |

### License 8 — Systems

| Level ID | Display name |
|---|---|
| `8.1` · `8.sub` | Substitution |
| `8.2` · `8.add` | Add to eliminate |
| `8.3` · `8.scale` | Scale, then eliminate |
| `8.4` · `8.none` | None or infinitely many |
| `8.5` · `8.three` | Three unknowns |
| `8.6` · `8.line` | Pick the line |
| `8.7` · `8.graph` | Graph to solve |
| `8.8` · `8.slopes` | Slopes tell the story |
| `8.9` · `8.frac` | Fractions and decimals |
| `8.10` · `8.mix` | Mixed review |
| `8.11` · `8.parab` | Line meets parabola — comeback after 9 |
| `8.12` · `8.matrix` | Matrices and row reduction — comeback after 16 |

### License 9 — Quadratics

| Level ID | Display name |
|---|---|
| `9.1` · `9.sqrt` | Square roots |
| `9.2` · `9.fact` | Factoring |
| `9.3` · `9.rearr` | Move everything to one side first |
| `9.4` · `9.cts` | Complete the square |
| `9.5` · `9.formula` | The formula |
| `9.6` · `9.disc` | How many solutions? |
| `9.7` · `9.method` | Pick your method |
| `9.8` · `9.vertex` | Vertex form |
| `9.9` · `9.qtype` | Quadratic type |
| `9.10` · `9.build` | Build it from its roots |
| `9.11` · `9.read` | Read the parabola |
| `9.12` · `9.ineq` | Quadratic inequalities |
| `9.13` · `9.linepar` | Line meets parabola |
| `9.14` · `9.mix` | Mixed review |
| `9.15` · `9.disguise` | Quadratics in disguise — comeback after 11 |
| `9.16` · `9.calc` | Highest and lowest points — comeback after 13 |

### License 10 — Rationals

| Level ID | Display name |
|---|---|
| `10.1` · `10.cancel` | Cancel common factors |
| `10.2` · `10.muldiv` | Multiply and divide |
| `10.3` · `10.same` | Same bottom |
| `10.4` · `10.lcd` | Different bottoms |
| `10.5` · `10.complex` | Fraction over fraction |
| `10.6` · `10.eq` | Rational equations |
| `10.7` · `10.longdiv` | Long division |
| `10.8` · `10.remthm` | The remainder theorem |
| `10.9` · `10.graph` | Read the graph |
| `10.10` · `10.partial` | Split into partial fractions |
| `10.11` · `10.mix` | Mixed review |

### License 11 — Radicals & logs

| Level ID | Display name |
|---|---|
| `11.1` · `11.simp` | Simplify a root |
| `11.2` · `11.muldiv` | Multiply and divide roots |
| `11.3` · `11.add` | Add like roots |
| `11.4` · `11.ration` | Rationalize the bottom |
| `11.5` · `11.fracexp` | Roots and fractional exponents |
| `11.6` · `11.tolog` | Power to log and back |
| `11.7` · `11.eval` | Work out a log |
| `11.8` · `11.expand` | Expand with the log laws |
| `11.9` · `11.condense` | Condense into one log |
| `11.10` · `11.base` | Change of base |
| `11.11` · `11.graph` | Read the graph |
| `11.12` · `11.mix` | Mixed review |

### Sister app: `LIC[0]` — Fractions / Bakery Lane

`LIC[0]` is intentionally not an Algebra License. It is the separate Fractions app ladder (storage key `fractions-v1`, level codes `F1`–`F17`) and remains the intended sister app for the late Fraction bars Era.

| ID | Display name |
|---|---|
| `f.1` · `f.name` | Name the shaded part |
| `f.2` · `f.line` | Fractions on a number line |
| `f.3` · `f.equiv` | Equivalent fractions |
| `f.4` · `f.simp` | Simplify |
| `f.5` · `f.cmp` | Compare and order |
| `f.6` · `f.mixed` | Mixed numbers |
| `f.7` · `f.same` | Add and subtract, same bottom |
| `f.8` · `f.diff` | Add and subtract, different bottoms |
| `f.9` · `f.mixop` | Mixed numbers with regrouping |
| `f.10` · `f.mul` | Multiply, cancel first |
| `f.11` · `f.div` | Divide |
| `f.12` · `f.of` | A fraction of an amount |
| `f.13` · `f.fdp` | Fractions, decimals, percents |
| `f.14` · `f.order` | Order of operations |
| `f.15` · `f.letter` | The same moves with a letter |
| `f.16` · `f.cancel` | Cancel factors, never terms |
| `f.17` · `f.mix` | Mixed review |

## 5. Gaps and mismatches to resolve in the content pass

1. **Garage order differs from engine order.** The current MVP intentionally shows Products before Differences (Era 2 uses engine L3; Era 3 uses L2). Keep the math titles, but document the progression choice in code so nobody “fixes” it back accidentally.
2. **Powers are implemented but switched off.** `engine.js` supports powers and names L5/L6, while `POWERS = false` means generated core play is still arithmetic-only. Era 6 should get an explicit powers-on test before being called playable.
3. **Ten Eras are not ten finished content bands yet.** Eras 5–10 are garage stubs; only 1–4 are currently wired to playable generators. Era 8 / Nested is the Miami Burnout 1.0 milestone, not a current feature.
4. **Current visual transport is placeholder art.** `road.js` has world/color packs, but foot, Cleopatra’s litter, horse, and carriage sprites still need to replace the car silhouettes. Cleopatra can remain a visual likeness with no explanatory transport copy.
5. **Skill coverage is thin in the core metadata.** Most engine levels point to `II.8.01`, `II.8.03`, and `III.4.03`; the UI’s brackets-first rule also names `III.1.08`. This is enough for the shell, not a complete map for mixed operations, negatives, powers, or fraction bars.
6. **Era 3 is a content mismatch.** Its current engine mapping is L2, but the live L2 generator is primarily `+ −` and does not yet constitute a dedicated bracket-trap band matching the design example. A focused generator/content pass is still needed.
7. **Era 4 has the right operator set but not a separate quotient curriculum.** L4 supplies exact division and `×÷` precedence; verify the question mix and avoid presenting every quotient as merely another generic tree.
8. **Fraction bars have an architectural boundary.** `LIC[0]` is a strong sister Fractions app, but no in-core Era 10 generator is present. Decide whether Era 10 is native, a showcase hand-off, or both.
9. **Algebra Licenses are much broader than Precedence.** The 122-level Algebra Licenses inventory and its comeback rules should stay hidden from the Precedence garage until the core progression is stable.
10. **Naming should remain stable in saves.** User-facing names can be refined, but stable IDs such as `5.gcf` and `11.fracexp` are save keys and migration inputs.

## Quick implementation checklist

- Keep the home cards titled **Sums, Products, Differences, Quotients, Mixed operations, Powers, Long chains, Nested, Negatives, Fraction bars**.
- Keep transport out of the math title and out of the explanatory UI copy where Julius requested visual-only treatment.
- Treat Eras 1–4 as the first playable structure build; do content refinement against the original demo after the shell is accepted.
- Turn on and test powers only when Era 6 content is ready; do not infer readiness from the existence of L5/L6 names.
- Reserve **Nested / Miami Burnout** for the 1.0 milestone.
