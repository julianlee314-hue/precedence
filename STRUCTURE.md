# Precedence — structure MVP notes

*Math Sensei · 3 Oct 2026 · scaffold before content polish*

Working title: **Precedence**. Algebra Licenses wing is **hidden** on the Precedence home. **Era labels are math titles; vehicles are visual-only rewards.** Fractions remains a separate build (`PREC_APP = 'fractions'`).

## What shipped in this scaffold

1. User-facing rename: title / brand → **Precedence** (“TEN ERAS OF GETTING AROUND”). The garage and HUD use **math titles**; transport is visual-only road art.
2. Home = **era garage postcards** (10 eras). Dense algebra plate strip removed from Precedence UI.
3. **Eras 1–4 playable** via existing `PrecEngine` generators. Eras 5–10 show **Coming soon** (locked).
4. Practice bumps era stamps (10 clean → 1 stamp; 5 stamps → CLEARED). Rally stores best km per era. Clearing does not yet gate eras 1–4 (all four open for playtesting).
5. Road worlds `mesa` / `alexandria` / `frontier` / `boston` added in `road.js` (color packs only).
6. Mistake “Garage” relabeled **Parts** so it doesn’t collide with the era garage.

Build: from `mathera-games/games/precedence/` run `python3 build.py` → `dist/precedence/index.html`.

## Era → engine mapping

| Era | Math title (UI) | Visual-only transport | Place tease | Engine level | Generator / math focus |
|---:|---|---|---|---:|---|
| 1 | **Sums** | on foot | Mesa Verde cliffs | **1** | `+` (+ brackets) |
| 2 | **Products** | royal litter / Cleopatra look | Alexandria | **3** | adds `×` |
| 3 | **Differences** | horseback | desert West | **2** | brackets / `+ −` mix (closest bracket drill) |
| 4 | **Quotients** | horse-drawn carriage | gaslit Boston | **4** | adds `÷`, `×÷` L→R |
| 5 | **Mixed operations** | early car | Detroit | — | mix all four + road test |
| 6 | **Powers** | streamliner | Art Deco NY | — | powers (`POWERS` still false globally) |
| 7 | **Long chains** | 1950s cruiser | Route 66 | — | brackets + powers |
| 8 | **Nested** | wedge sports car | neon coast | — | nested brackets — **1.0 fantasy** |
| 9 | **Negatives** | electric vehicle | SF fog | — | negatives |
| 10 | **Fraction bars** | robotaxi | 2040 | — | fraction bars / elite |

**Why Era 2 → L3 and Era 3 → L2?** Matches the unlock map: × arrives before a dedicated brackets-emphasis band. Engine L2 is the closest live “brackets change order” drill without writing new generators yet.

Cleopatra: Era 2 UI is titled **Products**. The royal litter and Cleopatra likeness are visual-only — **no transport label or name copy**. Pixel likeness for the litter ride is still TODO (see art list).

## Save shape (Precedence)

`localStorage` key `precedence-v1`, fields added:

- `era` (1–10 selected)
- `eraStamps[n] = { clean, stamps }`
- `eraClear[n] = true`
- `bestKm.rally|forks` length 10 (per era)

`S.lic` forced to `1` on Precedence. Algebra license progress code remains in the file for the Fractions build / future wing.

## What’s stubbed / TODO

| Area | Status |
|---|---|
| Era garage UI + lock/clear badges | Done (structure) |
| Eras 1–4 play Practice / Rally / Forks | Done (engine remap) |
| Eras 5–10 playable content | Stub postcards only |
| Per-era **vehicle sprites** (foot, litter w/ Cleopatra look, horse, carriage, …) | **Not done** — road still draws lamps-car or 8-bit car in era colors |
| Concept-art vistas as live postcard canvases | Not ported; CSS cards only |
| Engine reordering / bracket-trap generator for Era 3 | Deferred (content pass) |
| Powers on for Era 6+ | Deferred (`POWERS = false`) |
| Attract screen without Miami spoilers | Not touched |
| Gate eras 2–4 behind prior CLEARED | Optional; currently all of 1–4 open |
| GitHub Pages repo `precedence` | Live on Pages |
| Algebra Licenses sister wing on home | Hidden |

## Art still needed (vehicles)

Priority for “playable through the 4th” feeling finished:

1. **On foot** — walker sprite from behind on mesa path  
2. **Royal litter** — litter + carriers; Cleopatra silhouette **visual only** (no text)  
3. **Horseback** — horse + rider  
4. **Carriage** — horse-drawn carriage, gaslit Boston lamps (world pack started)

Concept-art reference: `games/racer/concept-art.html` (`VEH.foot|litter|horse|carriage` + vistas). Port those side-view drawers into `road.js` `car()` (or a `vehicle()` switch on `st.world` / era).

Later (pre–1.0): Mixed operations → Powers → Long chains → **Nested (Era 8)** → Negatives → Fraction bars. The transport visuals evolve separately, with the Era 8 neon sports-car treatment reserved for 1.0.

## Files touched

- `app.html` — eras, garage home, rename, stamp scaffolding  
- `road.js` — mesa / alexandria / frontier / boston worlds  
- `build.py` — title replace strings for Fractions twin  
- `docs/STRUCTURE.md` (this file)  
- Design lock: `docs/PRECEDENCE_ERA_UNLOCK_MAP.md`


## Flight / Hangar wing (Eras 11–20)

Shipped 3 Oct 2026 playtest: separate **Hangar** tab on home. Math titles only; craft SVG silhouettes are visual-only.

| Era | Math title | Craft (visual) | Content |
|---:|---|---|---|
| 11 | Grouping towers | Wright Flyer | Full protocol bank |
| 12 | Fraction architecture | Barnstormer | Full protocol bank |
| 13 | Composition order | Clipper | Full protocol bank |
| 14 | Trig reading | 1950s airliner | Full protocol bank |
| 15 | Exp–log stacks | Early jet | Full protocol bank |
| 16 | Limits structure | Concorde | Light stub bank |
| 17 | Derivative protocol | Glass cockpit | Light stub bank |
| 18 | Integral protocol | Fighter | Light stub bank |
| 19 | Series structure | Stealth | Light stub bank |
| 20 | Several variables | Drone swarm | Light stub bank |

Stages (6): Lexicon · Trap A · Trap B · Combine · Dense · Fluency. Loop: pick next legal structural move (card signs). Stamps: 8 clean → stamp, 4 stamps → cleared.

Unlock note: curriculum gate is Era 10 cleared; playtest opens Hangar eras. Road eras 1–10 unchanged (Cleopatra / Miami rules intact).
