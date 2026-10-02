# Precedence — structure MVP notes

*Math Sensei · 3 Oct 2026 · scaffold before content polish*

Working title: **Precedence**. Algebra Licenses wing is **hidden** on the Precedence home. Fractions remains a separate build (`PREC_APP = 'fractions'`).

## What shipped in this scaffold

1. User-facing rename: title / brand → **Precedence** (“TEN ERAS OF GETTING AROUND”).
2. Home = **era garage postcards** (10 eras). Dense algebra plate strip removed from Precedence UI.
3. **Eras 1–4 playable** via existing `PrecEngine` generators. Eras 5–10 show **Coming soon** (locked).
4. Practice bumps era stamps (10 clean → 1 stamp; 5 stamps → CLEARED). Rally stores best km per era. Clearing does not yet gate eras 1–4 (all four open for playtesting).
5. Road worlds `mesa` / `alexandria` / `frontier` / `boston` added in `road.js` (color packs only).
6. Mistake “Garage” relabeled **Parts** so it doesn’t collide with the era garage.

Build: from `mathera-games/games/precedence/` run `python3 build.py` → `dist/precedence/index.html`.

## Era → engine mapping

| Era | Vehicle (UI name) | Place tease | Engine level | Generator name | Ops focus |
|---:|---|---|---:|---|---|
| 1 | On foot | Mesa Verde cliffs | **1** | Sums | `+` (+ brackets) |
| 2 | Royal litter | Alexandria | **3** | Products | adds `×` |
| 3 | Horseback | desert West | **2** | Differences | brackets / `+ −` mix (closest bracket drill) |
| 4 | Carriage | gaslit Boston | **4** | Quotients | adds `÷`, `×÷` L→R |
| 5 | Model T | Detroit | — | *stub* | mix all four + road test |
| 6 | Streamliner | Art Deco NY | — | *stub* | powers (`POWERS` still false globally) |
| 7 | Fifties cruiser | Route 66 | — | *stub* | brackets + powers |
| 8 | Wedge sports car | Miami | — | *stub* | nested brackets — **1.0 fantasy** |
| 9 | Electric | SF fog | — | *stub* | negatives |
| 10 | Robotaxi | 2040 | — | *stub* | fraction bars / elite |

**Why Era 2 → L3 and Era 3 → L2?** Matches the unlock map: × arrives before a dedicated brackets-emphasis band. Engine L2 is the closest live “brackets change order” drill without writing new generators yet.

Cleopatra: Era 2 UI says **Royal litter** / Alexandria only — **no name label**. Pixel likeness for the litter ride is still TODO (see art list).

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
| GitHub Pages repo `precedence` | Not pushed (per Julius) |
| Algebra Licenses sister wing on home | Hidden |

## Art still needed (vehicles)

Priority for “playable through the 4th” feeling finished:

1. **On foot** — walker sprite from behind on mesa path  
2. **Royal litter** — litter + carriers; Cleopatra silhouette **visual only** (no text)  
3. **Horseback** — horse + rider  
4. **Carriage** — horse-drawn carriage, gaslit Boston lamps (world pack started)

Concept-art reference: `games/racer/concept-art.html` (`VEH.foot|litter|horse|carriage` + vistas). Port those side-view drawers into `road.js` `car()` (or a `vehicle()` switch on `st.world` / era).

Later (pre–1.0): Model T → Streamliner → Cruiser → **Miami wedge (Era 8)** → EV → Robotaxi.

## Files touched

- `app.html` — eras, garage home, rename, stamp scaffolding  
- `road.js` — mesa / alexandria / frontier / boston worlds  
- `build.py` — title replace strings for Fractions twin  
- `docs/STRUCTURE.md` (this file)  
- Design lock: `docs/PRECEDENCE_ERA_UNLOCK_MAP.md`
