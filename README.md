# 🤖 StockPro-AI - Adaptive Probability Model v2

> **KI-gestützter, adaptiver Wahrscheinlichkeits-Indikator für TradingView**  
> Self-calibrating Pine Script v6 model with delayed online learning, configurable signals, strategy support, and anti-overfit safeguards.

[![GitHub stars](https://img.shields.io/github/stars/StockPro-AI/StockPro-AI_Indicator_Adaptive-Probability-Model-v2?style=social)](https://github.com/StockPro-AI/StockPro-AI_Indicator_Adaptive-Probability-Model-v2)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Pine Script](https://img.shields.io/badge/pine%20script-v6-00c2ff.svg)](https://www.tradingview.com/pine-script-docs/)

---

## ✨ Features

- 🧠 **Adaptive Probability Engine** – live UP/DOWN estimation with online learning
- 🔄 **Delayed Self-Calibration** – predictions are evaluated only after the prediction horizon
- 🛡️ **Anti-Overfit Safeguards** – bounded buffers, weight clipping, warmup protection
- 📊 **Confidence & Accuracy Tracking** – separate quality metrics for better filtering
- 🌐 **Trend / Range Awareness** – regime detection to dampen weak conditions
- 🎛️ **Flexible UI Controls** – table size, table position, colors, and display options
- 🚨 **Optional Signal Engine** – arrows, alerts, direction filters, and configurable thresholds
- 📈 **Strategy Version** – entry/exit logic, SL/TP, session filter, and signal throttling

---

## 🚀 Quick Start

### 1) In TradingView einfügen

1. Öffne TradingView.
2. Erstelle ein neues Pine Script.
3. Füge den Inhalt der gewünschten Datei ein:
   - `StockPro-AI - Adaptive Probability Model v2.pine`
   - `StockPro-AI - Adaptive Probability Strategy v1.pine`
4. Speichere und füge den Indikator bzw. die Strategy dem Chart hinzu.

### 2) Standard-Einstellungen prüfen

Empfohlene Startwerte:
- **Prediction Horizon:** 10
- **Training Window:** 300
- **Learning Rate:** 0.03
- **Min Confidence:** 70%
- **Min Accuracy:** 55%
- **Signal Cooldown:** 5 Bars
- **Max Signals per Trade:** 3

### 3) Signale aktivieren

Im Input-Menü kannst du wählen:
- **Both**
- **Long only**
- **Short only**
- **None**

Zusätzlich lassen sich:
- Signal-Pfeile ein- / ausschalten
- Alerts ein- / ausschalten
- Farben individuell anpassen
- Signal nur auf Bar Close bestätigen
- Signal-Cooldown pro Richtung setzen
- Maximalzahl an Signalen pro Trade begrenzen

---

## 📚 How It Works

Der Indikator kombiniert drei normalisierte Kernsignale:

| Feature | Zweck |
|---|---|
| RSI | Momentum-Balance |
| EMA Spread | Trendrichtung |
| MACD Spread | Momentum-Bestätigung |
| ATR-Normalisierung | Stabilität über Volatilitätsregime hinweg |

Die Wahrscheinlichkeit entsteht über ein kleines **Online-Logit-Modell**. Eine Vorhersage wird gespeichert, später mit dem Marktverlauf verglichen und danach zur Gewichtsanpassung verwendet.

Die Strategy-Datei verwendet dieselbe Logik, ergänzt aber:
- Entry / Exit-Management
- Stop Loss / Take Profit auf ATR-Basis
- Session-Filter
- Signalbegrenzung je Trade und Richtung
- Reversal-Handling

---

## 🚦 Signal Logic

### Long Signal
Ein Long-Signal wird nur erzeugt, wenn alle Bedingungen erfüllt sind:

- Long/Short-Verhältnis mindestens **60 / 40**
- **Confidence** mindestens **70%**
- **Accuracy** mindestens **55%**
- Signalmodus erlaubt Long-Signale
- Optional: nur auf Bar Close bestätigt

### Short Signal
Ein Short-Signal wird nur erzeugt, wenn alle Bedingungen erfüllt sind:

- Short/Long-Verhältnis mindestens **60 / 40**
- **Confidence** mindestens **70%**
- **Accuracy** mindestens **55%**
- Signalmodus erlaubt Short-Signale
- Optional: nur auf Bar Close bestätigt

### Modes
- **Both**: Long und Short
- **Long only**: nur Long-Signale
- **Short only**: nur Short-Signale
- **None**: keine Handelssignale

---

## 🛠️ Configuration

### Table Settings
- **Table Position**: Top Left, Top Right, Bottom Left, Bottom Right, Top Center, Bottom Center
- **Table Size**: Small, Medium, Large
- **Show Table**: on / off

### Signal Settings
- **Show Signal Arrows**: on / off
- **Enable Alerts**: on / off
- **Signal Only On Bar Close**: on / off
- **Arrow Colors**: frei wählbar

### Strategy Settings
- **Trade Mode**: Both, Long only, Short only, None
- **Signal Behavior**: Single entry oder Scale-in
- **Min Bars Between Signals**
- **Max Long Signals per Trade**
- **Max Short Signals per Trade**
- **Use Session Filter**
- **Trading Session**
- **Stop Loss ATR Multiplier**
- **Take Profit ATR Multiplier**

---

## 🧱 Project Structure

```text
StockPro-AI_Indicator_Adaptive-Probability-Model-v2/
├── README.md
├── LICENSE
├── StockPro-AI - Adaptive Probability Model v2.pine
└── StockPro-AI - Adaptive Probability Strategy v1.pine
```

---

## 🎯 Interpretation

- **UP %**: aktuelle bullische Modellwahrscheinlichkeit
- **DOWN %**: aktuelle bärische Modellwahrscheinlichkeit
- **Confidence**: kombinierte Qualitätsmetrik aus Coverage und Accuracy
- **Accuracy**: geglättete Trefferquote des Modells
- **Status**: WARMUP, READY / TREND oder READY / RANGE

---

## 📝 Important Notes

- Der Indikator und die Strategy sind Analyse- und Entscheidungswerkzeuge, kein Garant für Marktbewegungen.
- Historische Trefferquoten sind keine Garantie für zukünftige Ergebnisse.
- Die Signal-Logik ist absichtlich konfigurierbar, damit du sie an Markt und Timeframe anpassen kannst.
- Die Strategy-Datei ist für Backtesting gedacht und sollte vor echtem Einsatz auf mehreren Symbolen geprüft werden.

---

## 🗺️ Roadmap

- Higher-timeframe regime filter
- Separate trend / range sub-models
- Better calibration scoring
- Signal cooldown pro Richtung dynamisch adaptiv
- Exportable signal logs for backtesting

---

## 🤝 Contributing

Änderungen und Verbesserungen sind willkommen. Für neue Funktionen ist es sinnvoll, erst einen Branch zu erstellen und dann per Pull Request zu arbeiten.

1. Fork das Projekt
2. Branch erstellen
3. Änderungen committen
4. Pull Request öffnen

---

## 📄 License

This project is licensed under the MIT License.  
See the `LICENSE` file for details.

---

## 👤 Author

**StockPro-AI**  
GitHub: [@StockPro-AI](https://github.com/StockPro-AI)

---

<div align="center">
  <sub>Built for systematic trading workflows with a clean, modern setup.</sub>
</div>
