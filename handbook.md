# 🤖 User Guide for Scribe Bot
*The Scribe Bot is a helpful tool for traders who buy and sell stocks frequently. It provides information about stock trends and suggests potential trading opportunities.*

---

## **Interact with the Scribe Bot on Discord**

You can interact with the Scribe Bot by joining our Discord server: [Join the Bot Gallery Server](https://discord.gg/9AXMNBfPMF).

If you'd like to invite the Scribe Bot to your own server, you can do so using this link: [Invite Scribe Bot](https://discord.com/api/oauth2/authorize?client_id=899283955000414238&permissions=534794206272&scope=bot).

---

## **Bot Commands**

### 📊 **General Stock Analysis**

- 📝 **`tracked`**  
  Retrieves a list of currently tracked tickers with details on their symbol, exchange, and name. This command is ideal for getting a quick overview of all monitored stocks. It helps you stay updated on the stocks you are currently following, including their market activity and essential identifiers.

<details>
  <summary>Example Response</summary>
  
  📝 **Currently tracked tickers:**
  - **VOO**, Exchange: NYSE: New York, Name: Vanguard S&P 500 ETF
  - **AAPL**, Exchange: NASDAQ: New York, Name: Apple Inc.
  - **NVDA**, Exchange: NASDAQ: New York, Name: Nvidia
  - **GOOG**, Exchange: NASDAQ: New York, Name: Alphabet 
  - **META**, Exchange: NASDAQ: New York, Name: Meta Platforms Inc
  - **PLTR**, Exchange: NYSE: New York, Name: Palantir Technologies Inc.
  - **ARM**, Exchange: NASDAQ: New York, Name: Arm Holdings
  - **MCD**, Exchange: NYSE: New York, Name: McDonald's
  - **MMM**, Exchange: NYSE: New York, Name: 3M Company
</details>

---

- 📝 **`overview` | `summary` | `status`**  
  Provides a general summary of the current stock market status, including recent trends and key movements. This command gives users insight into broader market conditions, highlighting notable trends that may impact trading strategies.

<details>
  <summary>Example Response</summary>
  
  📊 Market Overview
  - **Total Tickers Being Tracked**: 78
  - **Total Exchanges Being Tracked**: 17
  - **EMA200s Rising**: 56
  - **EMA200s Falling**: 4
  - **EMA200s Volatile**: 18
  - **Low Volume Tickers**: 26
  - **High Volume Tickers List**: AMZN, Z74, XOM, CVX, ABT, UBER
</details>

---

- 📝 **`forecast` | `swing` | `trade`**  
  Fetches a list of tickers that the bot thinks are at a critical juncture, showing: `buy`, `sell`, and `hold` recommendations along with a score. This feature allows traders to identify stocks that are currently poised for significant movement, helping them make informed decisions based on the bot's analysis.

<details>
  <summary>Example Response</summary>
  📝 **Long Recommendations:**
  
  - **MSFT**, Exchange: NASDAQ: New York, Confidence - Low
  - **XOM**, Exchange: NYSE: New York, Confidence - Low
  - **ABT**, Exchange: NYSE: New York, Confidence - Low
  - **QCOM**, Exchange: NASDAQ: New York, Confidence - Low
  - **UBER**, Exchange: NYSE: New York, Confidence - Low
  
  📝 **Short Recommendations:**
  😵 No tickers found for short recommendations.
</details>

---

### ⚙️ **Individual Stock Reports & Actions** 

- 🔍 **`news [ticker]`**  
  Check general sentiment about the specified ticker, based on news headlines. This command helps traders gauge the market sentiment surrounding a specific stock, allowing them to incorporate recent news into their trading strategies.

<details>
  <summary>Example Response</summary>

  📰 **News Sentiment for NVDA on Exchange: NASDAQ**  
  **Sentiment Score:** Positive
  
  **Top News Headlines:**
  - Which stocks are in the Magnificent 7?
  - Meet the Newest Artificial Intelligence (AI) Chip Stock to Join Nvidia in the $1 Trillion Club
  - Got $1,000 to Invest? This "Magnificent Seven" Stock Is a Great Option Heading Into 2025
  - Should You Forget Nvidia and Buy This Artificial Intelligence (AI) Stock Right Now?
  - Better Artificial Intelligence Stock: Nvidia vs. AMD
</details>
  
---

- 🔍 **`report [ticker]`**  
  Fetches a detailed report for the specified stock, including recent data points and basic analysis. This provides a deeper dive into the stock's performance metrics, historical data, and critical indicators, assisting users in making informed trading decisions.

<details>
  <summary>Example Response</summary>

  📊 **Report for AMZN on Exchange: NASDAQ**  

  |     Date       |   Open    |  Close    |  EMA200   |
  |----------------|-----------|-----------|-----------|
  |   2024-11-01   |   199.0   |  197.93   |  177.36   |
  |   2024-10-31   |  190.51   |   186.4   |  177.07   |
  |   2024-10-30   |   194.7   |  192.73   |  176.66   |
  
  **EMA200 Trend:** Rising
</details>

---

### 🧩 **Resources & Links**

- 🔗 **`link`**  
  Shares the URL for the spreadsheet containing tracked tickers and stock data. This resource is helpful for deeper analysis, allowing users to access raw data and conduct their own evaluations.

<details>
  <summary>Example Response</summary>

  **Spreadsheet containing tracked tickers:** 🔗 [View Spreadsheet](https://docs.google.com/spreadsheets/d/1dVZjD294f4IPGJIE9EKR47hygZmnB9AE6LBlZ3gLw-w/)
</details>

---

- 🔗 **`explain` | `analysis`**  
  Shares the URL for a markdown file containing an explanation of how the bot decides on its recommendations. This resource provides insights into the algorithms and indicators used by the bot, enhancing user understanding of its analytical processes.

<details>
  <summary>Example Response</summary>

  **Analysis Guide for Scribe Bot:** 🔗 [View Analysis Guide](https://github.com/skywalker94/scribe_bot_notes/blob/main/analysis.md)
</details>

---

- **`guide` | `help` | `info`**  
  Provides this guide for how to use the bot commands, ensuring that users have easy access to instructions and command details.

---

Want to understand how Scribe Bot analyzes instruments? Take a look at the [Analysis Guide for Scribe Bot](https://github.com/skywalker94/scribe_bot_notes/blob/main/analysis.md).

> **💡 Note:** Please do your own research before following bot recommendations. The Scribe Bot is a tool to assist traders but should not be the sole basis for making trading decisions.
