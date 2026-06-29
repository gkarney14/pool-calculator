# Salt Pool Chemistry Calculator

A standalone browser-based chemistry calculator for saltwater pools with SWG (salt water generator) systems.

## Features

- **Readings tab** — enter FC, CC, pH, TA, CH, Salt, CYA, and water temp with instant in-range status badges
- **Dosing tab** — chemical adjustment recommendations with product concentration selectors; results persist across page loads
- **Trends tab** — Chart.js line charts with shaded target bands for each parameter; full log history with per-entry delete
- **Reference tab** — target ranges and chemistry notes for SWG pools
- Langelier Saturation Index (LSI) calculated live
- CH / TH toggle — enter Total Hardness if that's what your test kit measures (converted to estimated CH at ×0.85)
- ppm / mg/L display toggle
- Dark mode support
- All data stored locally in `localStorage` — no server, no account

## Target Ranges (SWG)

| Parameter | Target |
|---|---|
| Free Chlorine | 2–4 ppm |
| Combined Chlorine | < 0.5 ppm |
| pH | 7.2–7.6 |
| Total Alkalinity | 80–120 ppm |
| Calcium Hardness | 200–400 ppm |
| Salt | 2700–3400 ppm |
| Cyanuric Acid (CYA) | 60–80 ppm |
| LSI | −0.3 to +0.3 |

## Usage

Open `pool-calculator.html` directly in any modern browser — no build step or server required.

**Live:** https://gkarney14.github.io/pool-calculator/pool-calculator.html
