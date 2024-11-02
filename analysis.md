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

<details>
  <summary>📘 What is EMA?</summary>

  The Exponential Moving Average (EMA) is a type of moving average that places a greater weight and significance on the most recent data points. This makes it more responsive to recent price changes compared to the Simple Moving Average (SMA), which assigns equal weight to all data points.

</details>


<details>
  <summary>📐 How is EMA Calculated?</summary>

  The EMA is calculated with the following formula:

  **EMA<sub>current</sub> = [(Price<sub>current</sub> - EMA<sub>previous</sub>) × Multiplier] + EMA<sub>previous</sub>**

  Where:
  - **Multiplier** = 2 ÷ (N + 1), with **N** being the EMA period (e.g., 20 or 200 days).
  - **Price<sub>current</sub>** is the current closing price.
  - **EMA<sub>previous</sub>** is the EMA value calculated for the previous period.

  This formula smooths out price fluctuations by adjusting the average more heavily based on recent data points, which helps to identify trends more effectively.

</details>


### 📌 Positioning and EMA Trend Alignment

- **Positioning for Long Recommendations**: Stocks with a **closing price below both EMA20 and EMA200** are considered potential long recommendations. This positioning suggests that the stock might be undervalued or approaching a support level, which could lead to upward movement if other indicators align.
  - **EMA Trend Support**: The recommendation is strengthened if EMA200 shows an upward trend, as this suggests a positive longer-term trajectory despite the current undervaluation. This trend alignment is confirmed through `_is_ema200_rising`, which contributes to the long score multiplier.

- **Positioning for Short Recommendations**: Stocks with a **closing price above both EMA20 and EMA200** are considered potential short recommendations. This configuration indicates the stock may be overvalued or nearing resistance, making it more likely to experience a price correction.
  - **EMA Trend Support**: The recommendation is reinforced if EMA200 shows a downward trend, which signifies a declining longer-term trend that supports a potential short position. This is evaluated through `_is_ema200_falling`, which adjusts the short score multiplier accordingly.

- **Normalizing Effect**: When the stock price is **above both EMA indicators with a rising EMA200** or **below both EMA indicators with a falling EMA200**, it is assumed that the price may be temporarily diverging from the trend. This divergence suggests that the price may normalize, aligning more closely with EMA200 over time. This normalization effect is factored into the recommendation, as it implies potential price reversion toward the prevailing EMA trend direction.

- **Between EMA20 and EMA200**: Stocks trading **between EMA20 and EMA200** are often the most volatile, with no clear directional positioning based solely on EMA alignment. This region is harder to interpret with pure positioning alone, as it may indicate transitional price behavior. In these cases, a slight edge is given to the **direction of the EMA trend** (upward or downward) to help guide the recommendation. However, this edge has a minimal effect on the final forecast since volatility and uncertain positioning limit the reliability of trend-based predictions in this range.


### 📊 Volume Analysis
- **Volume Multiplier**: The volume multiplier is assessed using the `_score_volume` function, which evaluates the current trading volume relative to historical averages. This multiplier influences both **long** and **short recommendation scores**, amplifying or moderating the impact of other indicators depending on the volume levels. High volume generally increases the weight of the recommendation score, while low volume dampens it, as movements with low volume are often less reliable.

- **Influence on Recommendations**: 
  - In **long recommendations**, a strong volume multiplier enhances indicators suggesting upward momentum (e.g., trends, price positioning). This makes the long recommendation more robust, as high volume on upward indicators suggests that institutional investors may be supporting the price increase.
  - For **short recommendations**, high volume strengthens signals of potential overvaluation or resistance, making the short recommendation more compelling. This is because increased selling activity with high volume often signals that large players anticipate a downward trend.

- **Significance of High Volume**: In financial markets, a surge in trading volume typically indicates the involvement of major institutional players, such as **hedge funds, pension funds, mutual funds, and proprietary trading desks at large banks**. These large players have the capital and influence to shift market trends significantly, as they often execute substantial trades based on deep analysis and strategic positioning.

  > **Why Volume Matters**: Unlike individual investors, whose trades are unlikely to shift the overall market trend, these "big players" have the power to influence price direction. When a price movement is accompanied by high volume, it signals that major players are actively trading the instrument and possibly initiating or reinforcing a trend. Respecting these volume-supported price movements is crucial, as they reflect the collective weight and intentions of influential market participants.


### 📏 Candle Patterns
Candle patterns are critical in assessing market sentiment and predicting potential reversals or continuations in price trends. By analyzing specific candle formations, the model can interpret buying and selling pressure and infer where significant support or resistance levels may lie.

- **Candle Types**:
  - **Elephant Candles**: These are large candles that signal strong price movement in either direction, typically resulting from a surge in buying or selling activity. 
    - **Green Elephant Candle**: Indicates strong bullish momentum, suggesting that buyers are actively pushing the price up.
    - **Red Elephant Candle**: Signals strong bearish momentum, suggesting that sellers are driving the price downward. 
    - Elephant candles are considered significant as they often mark key shifts in market sentiment or the beginning of new trends. When they appear with high volume, they carry additional weight, as they likely reflect the influence of institutional investors.
    
  - **Wicks**: Long upper or lower wicks (shadows) represent areas where price was rejected, showing that the market attempted to move higher or lower but faced resistance.
    - **Lower Wick**: Indicates that while the price fell to a certain level, buyers stepped in to push it back up. This suggests a possible support level where demand may increase.
    - **Upper Wick**: Indicates that although the price rose to a certain point, selling pressure pushed it back down. This suggests a potential resistance level where supply may increase.

- **Indicators**:
  - `_is_candle_elephant_green` and `_is_candle_elephant_red`: These functions detect large bullish (green) or bearish (red) elephant candles, helping to identify strong directional trends. 
    - **Bullish Elephant Candle**: Contributes to long recommendation scores by indicating a strong upward movement.
    - **Bearish Elephant Candle**: Adds weight to short recommendation scores, suggesting downward momentum.
  - `_is_candle_wick_lower` and `_is_candle_wick_upper`: These functions detect long lower or upper wicks, signaling potential support or resistance levels. 
    - **Lower Wick**: Adds to the long recommendation score, as it suggests buying interest at a certain level, indicating support.
    - **Upper Wick**: Contributes to the short recommendation score, as it signals selling pressure at a higher price, suggesting resistance.

### 📉 Trend Analysis
Trend analysis evaluates the overall direction of the stock's price movement, indicating whether it is moving in an upward or downward direction. By scoring the trend strength, the model can gauge the likelihood of continued price movement in that direction.

- **Trend Scores**: Calculated using the functions `_score_trend_up` and `_score_trend_down`, trend scores provide insight into whether a stock's price is currently in an uptrend or downtrend. These scores factor into the recommendation process by either reinforcing or weakening the case for long or short positions.
  - **Upward Trend (`_score_trend_up`)**: This score increases the long recommendation score if the stock is exhibiting upward momentum. A positive trend score suggests that the stock is moving in a direction aligned with a long recommendation, indicating potential for continued gains.
  - **Downward Trend (`_score_trend_down`)**: This score enhances the short recommendation score if the stock is in a downtrend. A negative trend score suggests that the stock's price is moving in alignment with a short recommendation, indicating a potential for further declines.

> **Interpreting Trend Scores**: Strong trend scores (either upward or downward) serve as additional confirmation for the recommendation. For example, a high upward trend score paired with a low closing price relative to EMA20 and EMA200 would create a compelling case for a long recommendation. Conversely, a high downward trend score combined with a high closing price relative to both EMAs would strengthen the case for a short recommendation.


---

## 🧮 Scoring System

### 📍 Overview
The scoring system is designed to weigh multiple technical indicators to calculate a recommendation score for each stock. This score helps determine whether a stock qualifies for a long or short recommendation. Each indicator in the scoring process adds points or modifies existing points in specific ways, either by direct addition, using multipliers, or through conditional contributions based on trend or candle patterns.

### 📝 Score Calculation

The scoring process is broken down into specific components for **long** and **short** recommendations, with each indicator playing a role in adjusting the final score. Here's how the score calculation unfolds:

1. **Long Recommendation Score**:
   - **Proximity to EMA200**:
     - This initial score, calculated using `_score_proximity_to_ema200`, evaluates the stock's closing price in relation to EMA200, reflecting whether it’s positioned near a support level. The closer the stock is to this moving average, the higher the initial score is likely to be.
   
   - **Volume Adjustment**:
     - Calculated by `_score_volume`, the **volume multiplier** reflects trading activity in comparison to historical volume levels. Higher trading volume increases the weight of other scores, signaling stronger market activity. The volume multiplier enhances both long and short indicators, such as price movements and trends.
   
   - **Candle Indicators**:
     - **Jump Up**: Checked with `_jump_up`, this is a **binary score** (1 if true, 0 otherwise) added to the long score if the price shows a significant upward movement.
     - **Bullish Candle Patterns**: 
       - `_is_candle_elephant_green` checks for a large bullish (green) candle.
       - `_is_candle_wick_lower` detects a lower wick, indicating potential support.
     - If either bullish condition is met, an additional **1 point is added** to the score, which is also adjusted by the volume multiplier.

   - **Trend and Position**:
     - **Trend Score**: Evaluated through `_score_trend_up`, this score assesses the stock’s upward trend strength and adds additional points if the price is in an upward trend. This score is **multiplied by volume** to emphasize stronger trends in high-activity stocks.
     - **Price Position**: `_score_price_position_long` checks the stock’s price relative to EMA levels to assess whether it is positioned to rise. If true, this adds directly to the final long score.

   - **Overall Adjustment**:
     - **EMA200 Trend Multiplier**: `_is_ema200_rising` checks whether the EMA200 is in an upward trend. If true, a **multiplier of 1** is applied to the long score; if false, the score is **reduced by half (0.5 multiplier)**. This condition ensures that long recommendations align with a longer-term upward trend, reducing weight if the overall trend is downward.

2. **Short Recommendation Score**:
   - **Proximity to EMA200**:
     - Similar to the long score, proximity to EMA200 contributes to the initial short score, signifying that the price is approaching a resistance level.
   
   - **Volume Adjustment**:
     - The same volume multiplier applies here, amplifying the score for strong trading volume, which indicates higher market interest in the current price action. It emphasizes short signals when big players are likely active.
   
   - **Candle Indicators**:
     - **Jump Down**: Checked with `_jump_down`, this binary score (1 if true, 0 otherwise) is added to the short score if there is a sharp downward price movement.
     - **Bearish Candle Patterns**:
       - `_is_candle_elephant_red` identifies a large bearish (red) candle.
       - `_is_candle_wick_upper` detects a long upper wick, hinting at resistance.
     - Either of these conditions adds **1 point to the short score**, enhanced by the volume multiplier, as a signal of downward price pressure.

   - **Trend and Position**:
     - **Trend Score**: `_score_trend_down` assesses the downward momentum and contributes points if the stock is trending lower, signaling alignment with a short position. This score is also **amplified by the volume multiplier** for stocks with significant activity.
     - **Price Position**: `_score_price_position_short` checks if the price is positioned to fall based on EMA and other indicators, adding directly to the short score if true.

   - **Overall Adjustment**:
     - **EMA200 Trend Multiplier**: `_is_ema200_falling` checks if EMA200 is in a downward trend. If true, the short score is **multiplied by 1**; if false, it is **reduced by half (0.5 multiplier)**. This adjustment ensures alignment with a sustained downward trend for short recommendations, minimizing risk if the broader trend is upward.

### Confidence Levels
At the end of the scoring process:
   - **Long Score**: If the score exceeds 9, it has a “High” confidence level; between 6-9, “Moderate”; below 6, “Low.”
   - **Short Score**: Similar thresholds are applied, with high confidence above 9, moderate between 6 and 9, and low below 6.

> Only scores equal to and above 5 are recommended for either long and short category.

### Summary
The scoring system integrates these indicators and adjustments to form a final score that guides the recommendation:
   - High-volume stocks and strong trend alignment enhance the score and confidence level.
   - EMA200 trend adjustments ensure recommendations align with broader market movements, reducing risk in counter-trend scenarios.
   
This weighted approach allows the model to balance short-term signals with broader trends for more accurate recommendations.


---

## 📋 Recommendation Categories

### 💰 Long Recommendation
- **Criteria**: Stocks that display favorable technical conditions for a long (buy) position based on the overall score. Long recommendations are generated when a stock demonstrates sufficient alignment across various indicators, suggesting a likely upward price movement. The system evaluates conditions such as:
   - Relative position to EMA levels, generally looking for prices that align with anticipated support or rising momentum.
   - A combined score from volume, trend, and position indicators that surpasses a **minimum threshold** (currently set at `5`).
   - Indicators suggest support or strength within the price trend, and trends point to likely price increases.

- **Typical Score**: Must meet the **`RECOMMENDATION_SCORE_THRESHOLD` of 5** or higher for a stock to qualify as a long recommendation.

### ❌ Short Recommendation
- **Criteria**: Stocks that demonstrate conditions favorable for a short (sell) recommendation are flagged if they show trends indicating potential downward movement. Short recommendations consider:
   - Positioning relative to EMA levels that suggest resistance or overvaluation.
   - Alignment of bearish indicators, such as declining trends and the presence of significant selling pressure.
   - Scores that meet or exceed the **`RECOMMENDATION_SCORE_THRESHOLD` of 5**, indicating strong alignment with indicators supporting a decline.

- **Typical Score**: Must meet the **`RECOMMENDATION_SCORE_THRESHOLD` of 5** or higher for a stock to qualify as a short recommendation.

---

### 📬 Notifications
The system sends out recommendation notifications **three times daily**, with updates delivered approximately every **8 hours**. This schedule ensures timely recommendations aligned with market activity and helps traders respond promptly to new signals. 

---

## ⚠️ Risk Factors & Caveats
While the recommendation system employs technical indicators to provide data-driven insights, it’s crucial to understand the limitations inherent to technical analysis:
- **Market Sensitivity**: External factors, including economic data, news events, and global economic conditions, can significantly influence stock movements outside of technical predictions.
- **Risk of Over-Reliance**: The scoring system, while comprehensive, should not replace a well-rounded investment strategy. It is advisable to consider multiple perspectives and additional fundamental analysis alongside the provided recommendations.
- **No Guaranteed Outcomes**: Despite leveraging historical data, no analytical model can ensure success in all market conditions.

## 📚 Conclusion
The stock recommendation system is designed to support traders by integrating multiple technical indicators, producing a thorough analysis to guide long and short trading decisions. By combining scores from various indicators with a structured threshold, the function generates objective recommendations that can assist with identifying potentially profitable trades. 

**Remember**: All recommendations are generated using historical data and technical analysis. Always conduct your own research and consider additional factors when making trading decisions.

