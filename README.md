# Salt Pool Chemistry Calculator

A single-page web app for tracking and managing the water chemistry of a salt water generator (SWG) pool. Enter test results, get instant status badges and chemical dosing recommendations, and track trends over time — all client-side, no server or account required.

The app is hardcoded for a 19,800 gallon pool.

## Features

- **Readings tab** — enter Free Chlorine (FC), Combined Chlorine (CC), pH, Total Alkalinity (TA), Calcium/Total Hardness (CH/TH), Salt, Cyanuric Acid (CYA), and water temperature. Each field shows an instant in-range / out-of-range / action-needed status badge against SWG target ranges.
- **Langelier Saturation Index (LSI)** — automatically calculated from pH, TA, calcium hardness, and temperature to indicate whether the water is corrosive, balanced, or scaling.
- **Hardness toggle** — switch the hardness input between Calcium Hardness (CH) and Total Hardness (TH); TH is converted to an estimated CH value for calculations.
- **Dosing tab** — chemical dose recommendations calculated from current readings, including:
  - Liquid chlorine (sodium hypochlorite) to raise FC, with selectable product concentration (6%, 8.25%, 10%, 12.5%)
  - SLAM shock dosing when Combined Chlorine is too high (shock level = CYA × 0.4), using liquid chlorine at the selected concentration
  - Muriatic acid to lower pH or Total Alkalinity, with selectable concentration (14.5%, 31.45%, 34%)
  - Soda ash to raise pH, baking soda to raise TA, calcium chloride to raise CH, pool salt to raise salt level, and stabilizer (CYA) additions
  - Guidance to partially drain/refill when salt, CH, or CYA are too high
  - Dosing results persist ("held") until new readings are entered
- **Trends tab** — logs each reading with a timestamp to browser `localStorage` and charts historical values (via Chart.js) for any tracked parameter, with the SWG target range shown as a shaded band. Includes a log history table with per-entry delete and a clear-all option.
- **Reference tab** — a quick-reference table of SWG target ranges plus notes on FC/CYA relationship, salt cell efficiency, pH drift, SLAM shock threshold, muriatic acid safety, and salt cell maintenance.
- **Units** — toggle displayed units between ppm and mg/L.
- **Dark mode** — follows the OS `prefers-color-scheme` setting.

## Usage

Open `pool-calculator.html` in a browser (no build step or server needed). All data (logged readings, last dosing recommendation, unit/concentration preferences within a session) is stored in the browser's `localStorage`, so it persists locally across visits but is not synced anywhere.

## Tech stack

- Plain HTML/CSS/JavaScript (no framework, no build tools)
- [Chart.js](https://www.chartjs.org/) (loaded via CDN) for the trends chart
- [Tabler Icons](https://tabler.io/icons) webfont (loaded via CDN) for icons
- Browser `localStorage` for persistence
- A strict Content-Security-Policy meta tag restricting scripts/styles/fonts to `self` and the specific CDNs used

## Files

- `pool-calculator.html` — markup, styles, and CSP
- `pool-calculator.js` — all application logic (state, dosing calculations, LSI, charting, history)
