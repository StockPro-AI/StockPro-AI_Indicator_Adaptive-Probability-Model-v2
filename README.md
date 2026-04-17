# StockPro-AI - Adaptive Probability Model v2

A self-calibrating Pine Script v6 indicator that estimates bullish and bearish bias using a compact online-learning model with anti-overfit safeguards.

## Overview

This repository contains the TradingView Pine Script implementation of the **StockPro-AI - Adaptive Probability Model v2** indicator.

The indicator is designed to provide a live probability-style output for market direction based on a small, controlled feature set:
- RSI
- EMA spread
- MACD spread
- ATR-based normalization

It is intended as a decision-support tool, not as a guarantee of future price movement.

## Features

- Adaptive probability output for UP and DOWN bias
- Online learning with delayed feedback
- Warmup protection to avoid invalid early values
- Confidence and accuracy tracking
- Trend / range regime awareness
- Adjustable table size
- Adjustable table position
- Anti-overfit safeguards through bounded buffers and weight clipping

## Files

- `StockPro-AI - Adaptive Probability Model v2.pine` — main Pine Script source
- `LICENSE` — project license

## How it works

The model combines three normalized inputs:

1. **RSI** for momentum balance
2. **EMA spread** for trend direction
3. **MACD spread** for momentum confirmation

A lightweight online logistic-regression style update is used. A prediction is stored first and evaluated only after the selected prediction horizon. The model then updates its weights from delayed feedback.

## Interpretation

- **UP %**: estimated bullish probability
- **DOWN %**: estimated bearish probability
- **Confidence**: quality score based on coverage and recent accuracy
- **Accuracy**: smoothed hit rate of the model
- **Status**: indicates whether the model is warming up or ready

## Recommended usage

- Test on multiple symbols and timeframes
- Start with the default settings
- Compare trend regimes and range regimes separately
- Do not use the output as standalone financial advice

## Installation

1. Open TradingView.
2. Create a new Pine Script.
3. Paste the contents of `StockPro-AI - Adaptive Probability Model v2.pine`.
4. Add the indicator to the chart.
5. Adjust the settings for your market and timeframe.

## License

This project is licensed under the MIT License.
See the `LICENSE` file for details.

## Roadmap

- Higher-timeframe regime filter
- Separate trend and range models
- Better calibration metrics
- Strategy version based on the indicator logic

## Author

StockPro-AI
