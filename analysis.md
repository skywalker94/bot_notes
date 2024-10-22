# 📊 Analysis Guide for Scribe Bot
*How the bot evaluates and recommends stock actions*

---

## 📑 Table of Contents
1. [📋 Introduction](#introduction)
2. [🔍 Technical Indicators Used](#technical-indicators-used)
   - [📈 Moving Averages](#moving-averages)
   - [📊 Relative Strength Index (RSI)](#relative-strength-index-rsi)
   - [📉 MACD (Moving Average Convergence Divergence)](#macd-moving-average-convergence-divergence)
   - [📊 Volume Analysis](#volume-analysis)
   - [📏 Support and Resistance Levels](#support-and-resistance-levels)
3. [🧮 Scoring System](#scoring-system)
   - [📍 Overview](#overview)
   - [📝 Score Calculation](#score-calculation)
4. [📋 Recommendation Categories](#recommendation-categories)
   - [💰 Buy Recommendation](#buy-recommendation)
   - [❌ Sell Recommendation](#sell-recommendation)
   - [🕊️ Hold Recommendation](#hold-recommendation)
   - [📈 Upswings](#upswings)
   - [📉 Downswings](#downswings)
5. [⚠️ Risk Factors & Caveats](#risk-factors--caveats)
6. [📚 Conclusion](#conclusion)

---

## 📋 Introduction
The purpose of this document is to provide insight into how the Scribe bot performs stock analysis and generates recommendations for buying, selling, holding, or identifying market trends. It focuses on short-term swing trading using a variety of technical indicators.

## 🔍 Technical Indicators Used

### 📈 Moving Averages

> An instrument is a means by which something of value is transferred, held, or accomplished.

**Open**:
  Opening / Starting price of the instrument for the day.

**Close**:
  Closing / Last price of the instrument for the day.

**High**:
  Highest traded price of the instrument for the day.

**Low**:
  Lowest traded price of the instrument for the day.

**EMA 20**:
  Exponential Moving Average of the stock's closing value over the last 20 days.  

**EMA 200**:
  Exponential Moving Average of the stock's closing value over the last 200 days.

**Volume**:
  Number of times the instrument was traded for that day.

### 🗒️Derivate Indicators / Abstract Concepts 
**Differential movement of the Slopes**:
  Can be referred to as Increasing / Flat / Decreasing Trends.
  One can gain insight about whether the trends are bound to swing one way of another by checking the rate of change of the given indicators.

**Last Close Position**:
  The current price position in relation to the other price indicators.

**Candle Shape**:
  The type of candles seen in the past.
  - __Elephant__: A larger than average candle with it's close and open close to the daily min & max.
  - __Long wick candles__: Where a large price movement has taken place but the market resisted the change. Can be top, bottom or both.
  - __Full yet Flat__: A flat candle supported by higher than average volume indicates hidden volatility.
  - __Colour__: Whether the price action concluded with a higher / lower value.

**Price Action**:
  The type of candles seen in the past.
  - __Elephant__: A larger than average candle with it's close and open close to the daily min & max.
  - __Long wick candles__: Where a large price movement has taken place but the market resisted the change. Can be top, bottom or both.
  - __Full yet Flat__: A flat candle supported by higher than average volume indicates hidden volatility.

## 🧮 Scoring System

### 📍 Overview
The bot uses a scoring system to weigh multiple technical indicators and generate a recommendation. Each indicator contributes to a final score that informs the decision-making process.

### 📝 Score Calculation
- **Position Supported Trend Strength**: 1-3 points awarded based on how promising it seems.
- **Volume Confirmation**: 1-3 points based on relative spike magnitude of the trade volume.

## 📋 Recommendation Categories

### 💰 Buy Recommendation
- **Criteria**: <a>, <b>, <c>...
- **Typical Score**: Above 'X' points out of 'Total' threshold

### ❌ Sell Recommendation
- **Criteria**: <a>, <b>, <c>...
- **Typical Score**: Above 'X' points out of 'Total' threshold

### 🕊️ Hold Recommendation
- **Criteria**: <a>, <b>, <c>...
- **Typical Score**: Above 'X' points out of 'Total' threshold

### 📈 Upswings
- **Criteria**: <a>, <b>, <c>...
- **Typical Score**: Above 'X' points out of 'Total' threshold

### 📉 Downswings
- **Criteria**: <a>, <b>, <c>...
- **Typical Score**: Above 'X' points out of 'Total' threshold

## ⚠️ Risk Factors & Caveats
While the bot uses tried-and-true technical indicators, no analysis method is infallible.
Always consider additional market factors, including news, earnings reports, and economic conditions.

## 📚 Conclusion
The Scribe bot is designed to assist with short-term trading by analyzing trends using technical indicators.
However, users are encouraged to use this tool as one part of a larger strategy.

---

*Remember: All recommendations are generated automatically based on historical data and technical analysis. Always do your own research before making trading decisions.*
