# order-flow-signal
Order flow vs price dislocation signal (TSLA intraday)

## Overview
This project studies the relationship between short-term order flow and price movement.
The goal is to detect situations where aggressive buying or selling pressure is not yet reflected in price.

## Research Question
Can signed order flow predict short-horizon future returns when price has not yet adjusted?

## Intuition
When there is strong aggressive buying but price barely moves up, this may indicate latent upward pressure.
Similarly, strong selling pressure without price decline may indicate latent downward pressure.

## Data
- Instrument: TSLA
- Frequency: Intraday (1-minute bars)
- Source: Yahoo Finance (yfinance)
- Fields used:
  - Open, High, Low, Close
  - Volume
  - Mid price (constructed)

## Methodology
- Signed order flow over rolling window
- Midprice log return
- Z-score normalization
- Signal = Flow Z-score – Price Move Z-score

### Trade Classification
Trades are classified using a tick-rule proxy for the Lee–Ready algorithm:
- Buy-initiated if price increases
- Sell-initiated if price decreases

### Signal Construction
We construct:
- Net Order Flow
- Realized Price Movement

Final signal:
Sₜ = Normalized(Flowₜ) − Normalized(ΔPₜ)

## Results
Key findings:
- The signal shows weak but non-zero predictive power (IC ≈ -0.007 over 10-minute horizon)
- Return monotonicity across signal deciles is observed
- A toy long/short strategy suggests the signal is not directly tradable but contains information

## Repository Structure

