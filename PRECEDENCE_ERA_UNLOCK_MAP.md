# Precedence — Era Unlock Map (design lock draft)

*Math Sensei · 3 Oct 2026 · for Julius before build*

Working title: **Precedence**. Scope of this doc: the **order-of-operations racer** only (ten eras of getting around). Algebra Licenses 2–11 stay a later wing unless noted.

---

## 1. Design thesis

**Vehicle = rank. Math = the gate. Road world = the souvenir.**

You never buy a car. You earn how you move. New players always start **on foot**. The Miami wedge / 80s burnout is **Era 8**, not the default skin and not the attract-screen spoiler on a fresh install.

Each era adds **one new rule** (or one sharp combination). Clearing the era unlocks:

1. the next vehicle sprite on the road  
2. that era’s vista / lamps / sky pack  
3. that era’s “engine” sound (footsteps → hooves → clatter → rumble → neon whine)  
4. the garage postcard stamped **CLEARED**

Practice has no clock. Rally / Race is where speed and the vehicle fantasy matter. A miss costs time (and a hubcap once cars exist), never a game-over scare.

---

## 2. The ten eras (unlock table)

| Era | Vehicle | Place / vibe | New math rule | Example | Suggested Mathera skills | Earn condition (MVP proposal) |
|---:|---|---|---|---|---|---|
| **1** | On foot | c. 1200 · Mesa Verde cliffs | `+` and `−` only; brackets from day one | `9 − 4 + 3`, `8 + (5 + 2)` | II.8.01, III.4.03 | Stamp Practice ×10 clean **or** clear Rally checkpoint pack |
| **2** | Royal litter | 40 BC · Cleopatra / Alexandria | adds `×` (× before +−) | `2 + 3 × 4` | II.8.01, II.8.03, III.4.03 | Same |
| **3** | Horseback | 1860s · desert West | brackets change order | `(2 + 3) × 4` | II.8.01, II.8.03, III.4.03 | Same |
| **4** | Carriage | 1850s · gaslit Boston | adds `÷`; `×÷` left to right | `12 ÷ 3 × 2` | II.8.01, II.8.03, III.4.03 | Same |
| **5** | Model T | 1913 · Detroit line | mixes all four freely | `18 − 6 ÷ 2 + 1` | II.8.01, II.8.03, III.4.03 | Same + short **road test** (12 mixed, 1 slip OK) → unlock Era 6 |
| **6** | Streamliner | 1935 · Art Deco NY | adds powers | `2 + 3²` | II.8.01, II.8.03, III.1.08?, III.4.03 | Same |
| **7** | Fifties cruiser | 1957 · Route 66 diner | brackets with powers | `(1 + 2)² × 2` | same family | Same |
| **8** | **Wedge sports car** | 1986 · Miami sunset | nested brackets | `2 × (3 + (4 − 1))` | same family | **Burnout unlock** — feel this as the fantasy payoff |
| **9** | Electric | Today · SF fog | negatives | `−3 + 4 × (−2)` | extend Ops / integers | Same |
| **10** | Robotaxi | 2040 · neon city | fraction bars + everything | compound | hand-off toward Fractions app / III fraction ops | Elite plate; optional Pro ★ |

**Notes on chronology:** eras are ordered by *how you travel*, not strict history. Horse (1860s) before Carriage (1850s) is intentional fantasy rank, not a textbook timeline. Keep the postcard copy playful, not a museum lecture.

**Notes on engines today:** `engine.js` only has levels 1–6 (Sums → Long chains) and `POWERS = false` in the live generator. This map **stretches** that into 10 eras by splitting “same ops, harder structure” (eras 3, 5, 7, 8) and adding negatives / fraction bars late. Build work = remap levels + turn powers on per era + new sprites/worlds.

---

## 3. Progression model (detail)

### 3.1 What “clearing an era” means
- **Practice:** earn stamps on that era’s level(s). Proposal: **10 clean problems → 1 stamp; 5 stamps → era cleared** (reuse Algebra Licenses stamp math so one save format works).
- **Rally:** optional for clearing; required for **best km** and for feeling the vehicle. Streaks raise speed; miss = −10 s (or −5 s if we keep v3.1 pacing).
- **Road test (eras 5 and 10):** mixed problems at top tier; pass unlocks the next *band* (pre-car → cars; cars → elite).

### 3.2 What unlocks visually
| Band | Eras | Road fantasy |
|---|---|---|
| Pre-car | 1–4 | Dirt / stone / sand paths; camera still “pseudo-3D road” but vehicle is walker / litter / horse / carriage |
| Early car | 5–7 | Real car silhouette evolves: boxy T → deco streamliner → chrome cruiser |
| Fantasy car | **8** | Miami wedge — neon, hubcaps, burnout audio sting on streak ≥5 |
| Future | 9–10 | Quiet EV hum → robotaxi HUD lanes |

**Important:** on a fresh profile, attract / title can show a **generic dusk road** or Era 1 footpath — **not** Miami. Garage shows locked silhouettes as outlines (“???”) until earned.

### 3.3 Garage UI (replace dense plate strip for Precedence MVP)
Horizontal or 2×5 postcard garage (from concept art):
- Locked: grey outline + math tease (“adds ×”)
- Current: cyan pulse
- Cleared: vehicle filled + CLEARED stamp
- Elite (10): neon frame

License-plate UI can remain for the **Algebra Licenses wing** later; Precedence home = garage.

### 3.4 Modes
| Mode | Clock | Vehicle uses | Purpose |
|---|---|---|---|
| Practice | No | Cosmetic only (idle pose) | Learn the new rule |
| Rally | Yes | Full: speed, hubcaps, engine | Earn km + feel rank |
| Forks / Race signs | Yes | Same | Later polish; 2→4→8 lanes |

---

## 4. Mapping to the current codebase

| Concept-art era | Closest `engine.js` level today | Gap to close |
|---|---|---|
| 1 On foot | L1 Sums (+, brackets) | Rename; foot sprite + mesa world |
| 2 Litter | L3 Products (adds ×) — *order differs* | Reorder so × comes before “hard +− drills”, or keep L2 as Differences *without* calling it a new vehicle era |
| 3 Horse | L2-ish brackets emphasis | Dedicated bracket-trap generator |
| 4 Carriage | L4 Quotients | ÷ world |
| 5 Model T | L4 hard mix / long | Road test gate |
| 6 Streamliner | L5 Powers (`POWERS` off) | Turn powers on for era ≥6 |
| 7 Cruiser | L5/L6 power+bracket | Templates |
| 8 Wedge | L6 nested | Fantasy world pack |
| 9 EV | *missing* | Negatives in tree + generator |
| 10 Robotaxi | *missing* / Fractions app | Fraction bars **or** deep-link to Fractions “Bakery Lane” as sister app |

**Recommended MVP build order**
1. Remap 4 live levels → Eras 1–4 vehicles + 4 world packs (foot → carriage).  
2. Garage UI + unlock saves.  
3. Eras 5–8 (powers on, nested, Miami).  
4. Eras 9–10 (negatives, fraction bars / elite).  
5. GitHub Pages ship anytime after step 2 (even with later eras “Coming soon”).

---

## 5. Product thoughts (Sensei’s take)

**What’s strong**
- Fantasy ladder is memorable and maps cleanly onto “one new rule per era.”
- Starting on foot fixes the current “you’re already in an 80s car” disconnect.
- Miami as Era 8 is the right dopamine spike — same role as a mid-game legendary weapon.
- Equivalence-friendly engine already matches “drive well, don’t grind arithmetic.”

**What to watch**
- **Ten eras vs six engine levels:** don’t fake ten by only swapping skins. Each era needs a *felt* rule change or trap set.
- **Cleopatra litter:** concept art is fun; keep it classy (royal procession, not costume joke). Audience was locked 16+ for Algebra Licenses; if Precedence also aims younger later, litter copy may need a softer “palanquin / royal ride” label.
- **Scope creep into Algebra Licenses:** plates 2–11 are a whole second game. For MVP, **Precedence = eras 1–10 only**. Fractions stays its own Bakery app; robotaxi can *tease* fractions without swallowing that ladder.
- **Chronology pedants:** shrug in the About blurb (“travel rank, not a history exam”). Math History 101 is the museum; Precedence is the arcade.

**GitHub**
Still trivial: static `index.html`, `localStorage`, Pages. Title/rename Algebra Licenses → Precedence when we push.

---

## 6. Open questions for Julius

1. **Scope of v1 Pages ship:** Eras 1–4 playable + 5–10 locked postcards, or wait until Miami (Era 8) exists?  
2. **Stamp rule:** keep 10 clean → stamp, 5 stamps → clear? Or lighter for Precedence (e.g. 3 stamps)?  
3. **Must Rally be required to unlock the next vehicle, or can Practice alone clear eras?** (I lean Practice-can-clear, Rally-for-glory.)  
4. **Litter naming:** keep “Cleopatra / royal litter,” or neutral “Royal litter” only?  
5. **Era 10:** build fraction bars inside Precedence, or end at Era 9 and deep-link “Continue in Fractions”?  
6. **Algebra Licenses wing:** hide entirely from Precedence MVP home, or show greyed “Coming soon” garage door?  
7. **Attract screen:** dusk footpath vs silent garage fly-through of *unlocked* vehicles only?  
8. **Dojo gating:** originally Sums/Differences/Products/Quotients apps unlocked levels — still required, or Precedence self-contained?  
9. **Age tone:** keep 16+ arcade voice, or soften for 8+ once foot eras exist?  
10. **Repo name:** `precedence` on GitHub now?

---

## 7. Proposed lock (if you say “ship it”)

- Precedence MVP = **ten eras, vehicle = rank, Miami = Era 8.**  
- Practice can clear; Rally is the showcase.  
- Algebra Licenses + Fractions = sister apps, not on the Precedence home strip.  
- First Pages build after Eras 1–4 + garage shell; Miami before calling it “1.0.”

