# Last Bet (`Madras_Race_Club.html`)

**Last Bet** is an interactive, single-file browser game that teaches **multiple linear regression** through a 6-race horse-betting challenge. Built with vanilla HTML/CSS/JavaScript and **Three.js**, it lets players buy racing features ("clues"), tune a regression model by hand or via Ordinary Least Squares (OLS), bet on an 8-horse field, and watch the race unfold in a 3D oval stadium.

---

## Story & Objective

The game opens with a 4-panel comic introducing **Ravi**, a bettor on a 47-race losing streak who turns to regression modeling to beat the odds.

- **Starting Bankroll:** ₹25,000  
- **Campaign Length:** 6 races  
- **Win / End Conditions (after Race 6):**
  - **₹60,000+:** Legend!
  - **Above ₹25,000:** You beat the track.
  - **₹25,000 or below:** Below your starting bankroll.
  - **Below ₹1,000 at any point:** Out of coins (early game over).

---

## How to Play (5-Step Race Loop)

Each of the 6 races follows a 5-stage workflow tracked in the top header:

1. **🛒 Pick Your Clues**
   - Select up to **5 clues** from 12 available racing features.
   - New clues cost **₹500 × Race Number** (e.g., ₹500 in Race 1, ₹3,000 in Race 6).
   - Previously purchased clues remain **free** in later races.
2. **📈 Build Your Model (Regression Lab)**
   - Adjust the **Baseline** (`0–160s`) and clue weight sliders (`-2.0` to `+2.0`) to make the actual vs. predicted scatter plot hug the gold diagonal line (`y = x`).
   - Toggle **👁 Misses** to inspect vertical residual error bars.
   - Click **✨ Auto-fit** to compute the exact Ordinary Least Squares (OLS) solution.
   - Track **Your miss** (training RMSE), **Best** (OLS RMSE), and **New races** (RMSE on 40 held-out test races).
3. **🎟️ Place Your Bet**
   - Review the 8-horse field ranked by your model's predicted finish time (`⭐ model's pick` marks #1).
   - Toggle **📊 Stats** to inspect each horse's clue values.
   - Choose a stake (minimum ₹100; quick presets for `500`, `1,000`, `2,500`, and `ALL IN`).
4. **🏁 Watch the 3D Race**
   - A live **Three.js** stadium renders one full oval lap with animated horses, jockeys, cheering grandstands, track mud conditions (`0–10`), and a live leaderboard.
5. **🏆 Result & Debrief**
   - **Payouts:** 🥇 1st = **2×**, 🥈 2nd = **1.25×**, 🥉 3rd = **1× (money back)**, 4th–8th = **₹0**.
   - Expand **📋 Full results** to compare predicted vs. actual times, or **🛠️ Behind the scenes** to view the underlying ground-truth formula, PRNG seed, and a 3,000-run Monte Carlo win-probability table (also logged to the browser DevTools console).
   - All 8 finished horses are appended to your training dataset for the next race.

---

## Available Clues (Features)

| Clue | Description | Impact per 1 SD (Ground Truth) |
| :--- | :--- | :--- |
| `🏃 Speed 5` | Average speed over the last 5 races (km/h) | 1.21 s |
| `🫀 Stamina` | Fitness rating from the vet | 0.72 s |
| `⚡ Speed 3` | Average speed over the last 3 races (km/h) | 0.55 s |
| `⚖️ Jockey kg` | Weight carried by the horse (kg) | 0.42 s |
| `🎓 Jockey yrs` | Jockey's professional experience (years) | 0.35 s |
| `🐴 Horse kg` | Horse body weight (kg) | 0.35 s |
| `🚦 Lane` | Starting lane (1 = inside, 8 = outside) | 0.28 s |
| `🧑‍🏫 Trainer %` | Trainer win rate (%) | 0.25 s |
| `😴 Rest days` | Days since the horse's last race | 0.21 s |
| `🏅 Dist. wins` | Past wins at this distance | 0.20 s |
| `🎂 Age` | Horse age (3–10 years) | 0.18 s |
| `🌧️ Mud` | Track mud level (`0–10`, shared by all horses in a race) | 1.42 s (race-wide) |

---

## Running Locally

1. Download or keep `Madras_Race_Club.html` in a local folder.
2. Open `Madras_Race_Club.html` directly in any modern browser (Chrome, Edge, Firefox, or Safari).
3. **Note:** An active internet connection is required on load to fetch **Three.js (`r128`)** from `cdnjs.cloudflare.com` for the 3D race view.

---

## Technical Highlights

- **Single-File Architecture:** Zero build tools or backend required; all HTML, CSS, SVG sprites, comic panels, 2D Canvas plotting, and Three.js 3D rendering live in `Madras_Race_Club.html`.
- **In-Browser OLS Solver:** Solves the normal equations via Gaussian elimination with partial pivoting and a `1e-6` ridge term for numerical stability.
- **Responsive & Accessible:** Supports light/dark mode (`prefers-color-scheme`), mobile viewports, keyboard focus rings, and `prefers-reduced-motion`.
