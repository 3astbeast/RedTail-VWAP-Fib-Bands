<p align="center">
  <img src="https://avatars.githubusercontent.com/u/209633456?v=4" width="160" alt="RedTail Indicators Logo"/>
</p>

<h1 align="center">RedTail VWAP Fib Bands</h1>

<p align="center">
  <b>A MIDAS VWAP indicator for NinjaTrader 8 with standard deviation bands and Fibonacci sub-bands.</b><br>
  Frames the anchored VWAP within a volatility envelope for mean-reversion, trend extension, and statistical extreme identification.
</p>

<p align="center">
  <a href="https://buymeacoffee.com/dmwyzlxstj">
    <img src="https://img.shields.io/badge/☕_Buy_Me_a_Coffee-FFDD00?style=flat-square&logo=buy-me-a-coffee&logoColor=black" alt="Buy Me a Coffee"/>
  </a>
</p>

---

## Credit

[@_hawkeye_13](https://twitter.com/_hawkeye_13)** (RedTail Indicators).

---

## Overview

RedTail VWAP Fib Bands implements Paul Levine's MIDAS (Market Interpretation/Data Analysis System) methodology — an anchored VWAP surrounded by three standard deviation band pairs and configurable Fibonacci sub-bands interpolated between them. The result is a complete volatility framework around VWAP that identifies where price sits statistically relative to the volume-weighted mean.

RedTail VWAP Fib Bands adds structure around the VWAP anchor — mean-reversion zones near the center, extension zones further out, and statistical extremes at the edges.

---

## How It Differs From Standard VWAP

- **Three band pairs** (±1σ, ±2σ, ±3σ) that expand and contract based on the volume-weighted standard deviation from MIDAS
- **Fibonacci sub-bands** interpolated between MIDAS and the ±3σ extremes, providing intermediate reference levels at ratios you define
- **Multiple anchor methods** — Session, Timeframe, or fixed Date — so you're not limited to a single daily reset
- **Graduated fill zones** that create a visual heat map of volatility zones

---

## Anchor Methods

**Session** — Resets at a configurable hour each day (default: 6 PM ET, the standard futures session open). Bars before the session hour are attributed to the prior session. This is the most common mode for intraday futures trading.

**Timeframe** — Resets at the start of each new period: Daily, Weekly, Monthly, Quarterly, or Yearly. Useful for higher-timeframe VWAP anchoring.

**Date** — Anchors from a fixed UTC date and never resets. Use this to anchor from a specific swing high, swing low, or event in history and watch how the MIDAS curve develops from that point.

---

## Band Structure

**±1σ (Band 1)** — The inner mean-reversion zone. When price oscillates between +1σ and -1σ, the market is range-bound and trading around fair value. Look for long opportunities on bounces off -1σ and short opportunities on rejections from +1σ. Default multiplier: 1.0.

**±2σ (Band 2)** — The extension zone. A close beyond ±2σ signals that the market is trending and has moved meaningfully away from the volume-weighted mean. Default multiplier: 2.0.

**±3σ (Band 3)** — The extreme zone. A close beyond ±3σ is a statistically rare event — potential exhaustion or climax move. Default multiplier: 3.0.

All multipliers are independently configurable.

---

## Fibonacci Sub-Bands

In addition to the σ bands, the indicator plots Fibonacci-ratio levels interpolated between the MIDAS line and the ±3σ extremes. These give you intermediate reference levels between the standard deviation bands.

The default levels are 0.333, 0.5, 0.667, and 0.786, which correspond approximately to: ±1σ, the midpoint between ±1σ and ±2σ, ±2σ, and a deep extension toward ±3σ.

Enter any comma-separated ratios you want — add more, remove some, or change the values entirely. Each ratio is plotted symmetrically above and below MIDAS.

---

## Fill Zones

Three graduated fill zones between the band pairs create a visual heat map:

- **Inner zone** (MIDAS ↔ ±1σ) — Full opacity
- **Middle zone** (±1σ ↔ ±2σ) — 60% of base opacity
- **Outer zone** (±2σ ↔ ±3σ) — 35% of base opacity

Base fill opacity is configurable (default: 15%). The fills use polygon-traced geometry that follows the actual band lines bar by bar.

---

## Visual Settings

Each element has its own independent Stroke setting (color, dash style, width):

- **MIDAS Line** — Default: DodgerBlue, Solid, width 2
- **Band 1 (±1σ)** — Default: Red, Solid, width 2
- **Band 2 (±2σ)** — Default: Red, Dash, width 1
- **Band 3 (±3σ)** — Default: OrangeRed, Dash, width 1
- **Fibonacci Bands** — Default: Gray, Dot, width 1

Optional right-edge labels for every level — σ notation for bands (e.g., "+1.0σ", "-2.0σ") and decimal notation for fibs (e.g., "0.500", "0.786").

---

## Plot Outputs

All core values are exposed as plot outputs for use in the data box, crosshair readout, strategies, or other indicators: MIDAS, Upper1/Lower1, Upper2/Lower2, Upper3/Lower3, and all Fibonacci levels (up and down).

---

## Installation

1. Download the `.cs` file from this repository
2. Copy the `.cs` to `Documents\NinjaTrader 8\bin\Custom\Indicators`
3. Open NinjaTrader (if not already open)
4. In Control Center, go to **New → NinjaScript Editor**
5. Expand the Indicator tree, find your new indicator, double-click to open it
6. At the top of the Editor window, click the **Compile** button
7. That's it!

---

## Part of the RedTail Indicators Suite

This indicator is part of the [RedTail Indicators](https://github.com/3astbeast/RedTailIndicators) collection — free NinjaTrader 8 tools built for futures traders who demand precision.

---

<p align="center">
  <a href="https://buymeacoffee.com/dmwyzlxstj">
    <img src="https://img.shields.io/badge/☕_Buy_Me_a_Coffee-Support_My_Work-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black" alt="Buy Me a Coffee"/>
  </a>
</p>
