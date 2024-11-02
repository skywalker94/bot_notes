# 🤖 Scribe Bot

### A Dynamic Tool for Swing Traders
**Scribe Bot** offers short-term trading insights, technical stock analysis, and market trend tracking, designed specifically to assist swing traders in making informed decisions.

---

## About the Bot
Scribe Bot is your powerful trading assistant, expertly engineered for stock traders who seek to navigate the complexities of the market with confidence. By integrating various financial APIs and analytical tools, Scribe Bot provides real-time insights into stock trends, forecasts, and actionable recommendations, empowering traders to seize opportunities as they arise.

---

## Key Features
- **📈 Real-time Stock Data**  
  Harnesses the power of the [yfinance](https://pypi.org/project/yfinance/) library to access both live and historical stock data, enabling in-depth analysis and informed trading decisions.

- **📰 Sentiment Analysis**  
  Utilizes a news API in conjunction with [TextBlob](https://textblob.readthedocs.io/en/dev/) for advanced polarity and sentiment analysis, allowing traders to gauge the market sentiment surrounding specific stocks based on recent news headlines.

- **📊 Google Sheets Integration**  
  Seamlessly communicates with the [Google Sheets API](https://developers.google.com/sheets/api) to retrieve and manage a list of tickers and exchanges for analysis, making it effortless to update and track your preferred stocks.

- **📬 Pushbullet Notifications**  
  Delivers regular updates regarding stock actions, highlighting promising buy (long) or sell (short) recommendations for swing trading directly to your devices via the [Pushbullet API](https://docs.pushbullet.com/).

- **💬 Discord Interface**  
  Easily accessible through Discord, Scribe Bot allows users to interact, request analyses, and receive timely updates directly in their chat environment.

- **⚡ Stay Alive Server**  
  Spawns a stay-alive server that can be monitored via [UptimeRobot](https://uptimerobot.com/) to ensure reliability and minimal downtime, keeping your trading assistant operational at all times.

- **🔄 Automated Deployment**  
  Deployed using the [PM2](https://pm2.keymetrics.io/) service, Scribe Bot is designed to automatically restart on failure and undergoes a complete reset every even day (approximately every 48 hours) to maintain peak performance.

---

## Integrations
- **📈 Financial APIs**: Integrates multiple financial data sources for comprehensive analysis, ensuring you have the most accurate and up-to-date information at your fingertips.
  
- **📰 News APIs**: Leverages news sentiment analysis to enhance decision-making, providing context to the stock data and helping you understand potential market movements.
  
- **📊 Google Sheets API**: Retrieves data from user-managed sheets for tailored stock analysis, making it customizable to your specific trading strategy.

---

## Getting Started
You can interact with the Scribe Bot by joining our Discord server: <a href="https://discord.gg/9AXMNBfPMF" target="_blank" rel="noopener noreferrer">Join the Bot Gallery Server</a>.

If you'd like to invite the Scribe Bot to your own server, you can do so using this link: <a href="https://discord.com/api/oauth2/authorize?client_id=899283955000414238&permissions=534794206272&scope=bot" target="_blank" rel="noopener noreferrer">Invite Scribe Bot</a>.

---

## Resources
- For detailed user instructions, refer to the <a href="https://github.com/skywalker94/scribe_bot_notes/blob/main/handbook.md" target="_blank" rel="noopener noreferrer">User Handbook</a>.
- Access the <a href="https://docs.google.com/spreadsheets/d/1dVZjD294f4IPGJIE9EKR47hygZmnB9AE6LBlZ3gLw-w" target="_blank" rel="noopener noreferrer">Input Sheet</a> that controls the instruments that the bot is tracking for streamlined management.
- For an in-depth analysis of the bot's functionality, visit the <a href="https://github.com/skywalker94/scribe_bot_notes/blob/main/analysis.md" target="_blank" rel="noopener noreferrer">Analysis Document</a>.

---

## Conclusion
Scribe Bot aims to empower traders with actionable insights and timely recommendations, leveraging the power of advanced financial analytics and community interaction. Whether you’re a seasoned trader or new to the stock market, Scribe Bot is your reliable partner in navigating the complexities of trading, ensuring you’re always a step ahead.

---

**Note:** Always conduct your own research and due diligence before making trading decisions. The Scribe Bot provides recommendations based on historical data and technical analysis.
