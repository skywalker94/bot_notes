# 🤖 Analysis Guide for Stock Recommendation System
*How the system evaluates and recommends stock actions*

---

## 📑 Table of Contents
1. [📋 Introduction](#introduction)
2. [🔍 Technical Indicators Used](#technical-indicators-used)
   - [📈 Exponential Moving Averages](#exponential-moving-averages)
   - [📊 Volume Analysis](#volume-analysis)
   - [📏 Candle Patterns](#candle-patterns)
   - [📉 Trend Analysis](#trend-analysis)
3. [🧮 Scoring System](#scoring-system)
   - [📍 Overview](#overview)
   - [📝 Score Calculation](#score-calculation)
4. [📋 Recommendation Categories](#recommendation-categories)
   - [💰 Long Recommendation](#long-recommendation)
   - [❌ Short Recommendation](#short-recommendation)
5. [⚠️ Risk Factors & Caveats](#risk-factors--caveats)
6. [📚 Conclusion](#conclusion)

---

## 📋 Introduction
The purpose of this document is to provide insight into how the stock recommendation system analyzes market data and generates recommendations for buying (long) or selling (short) stocks. The system uses a variety of technical indicators to assess market conditions and stock performance.

## 🔍 Technical Indicators Used

### 📈 Exponential Moving Averages
- **EMA 20**: Exponential Moving Average of the stock's closing price over the last 20 days.
- **EMA 200**: Exponential Moving Average of the stock's closing price over the last 200 days.
- **Positioning**: Stocks below EMA20 and EMA200 are considered for long recommendations, while those above both are considered for short recommendations, as long as the EMA trend supports it.

### 📊 Volume Analysis
- **Volume Multiplier**: Evaluated through `_score_volume`, this indicator assesses the trading volume relative to historical averages, enhancing the weight of the recommendation scores.

### 📏 Candle Patterns
- **Candle Types**:
  - **Elephant Candles**: Large candles indicating strong price movement.
  - **Wicks**: Long upper or lower wicks that suggest resistance or support levels.
- **Indicators**:
  - `_is_candle_elephant_green` and `_is_candle_elephant_red` identify bullish and bearish trends, respectively.
  - `_is_candle_wick_lower` and `_is_candle_wick_upper` indicate potential support and resistance.

### 📉 Trend Analysis
- **Trend Scores**: Evaluated using `_score_trend_up` and `_score_trend_down`, these scores indicate whether a stock is currently trending upward or downward, influencing the recommendation process.

---

## 🧮 Scoring System

### 📍 Overview
The scoring system weighs multiple technical indicators to generate a comprehensive recommendation score for each stock. The final score is used to determine if a stock qualifies for long or short recommendations.

### 📝 Score Calculation
1. **Long Recommendation Score**:
   - Proximity to EMA200: Based on the score from `_score_proximity_to_ema200`.
   - Volume Adjustment: Influenced by `_score_volume`.
   - Candle Indicators: Positive scores from `_jump_up`, `_is_candle_elephant_green`, and `_is_candle_wick_lower`.
   - Trend and Position: Additional points from `_score_trend_up` and `_score_price_position_long`.
   - Overall Adjustment: Multiplier based on the trend of EMA200 using `_is_ema200_rising`.

2. **Short Recommendation Score**:
   - Similar to long scores but uses bearish indicators:
   - Proximity to EMA200, volume, candle indicators (`_jump_down`, `_is_candle_elephant_red`, `_is_candle_wick_upper`), and downward trend scoring from `_score_trend_down` and `_score_price_position_short`.
   - Overall Adjustment: Based on the trend of EMA200 with `_is_ema200_falling`.

---

## 📋 Recommendation Categories

### 💰 Long Recommendation
- **Criteria**: Stocks where the closing price is below EMA20 and EMA200 with a score above the threshold.
- **Typical Score**: Must meet the `RECOMMENDATION_SCORE_THRESHOLD`.

### ❌ Short Recommendation
- **Criteria**: Stocks where the closing price is above EMA20 and EMA200 with a score above the threshold.
- **Typical Score**: Must meet the `RECOMMENDATION_SCORE_THRESHOLD`.

---

## ⚠️ Risk Factors & Caveats
While the system employs various technical indicators for analysis, it is important to note that no analysis method guarantees success. Market conditions, news, and economic factors can all impact stock performance.

---

## 📚 Conclusion
The stock recommendation system leverages technical analysis to evaluate potential trading opportunities. By integrating multiple indicators and a scoring system, the function aims to provide well-informed recommendations for traders.

---

*Remember: All recommendations are based on historical data and technical analysis. Always conduct your own research before making trading decisions.*
