# 🤖 Scribe Bot
A tool offering short-term trading insights, technical stock analysis, and market trend tracking to assist swing traders.

## About the Bot
Scribe Bot is a powerful trading assistant designed for stock traders seeking to make informed decisions. It integrates various financial APIs and analytical tools to provide real-time insights into stock trends, forecasts, and recommendations for trading opportunities.

### Key Features
- **Real-time Stock Data**: Utilizes the [yfinance](https://pypi.org/project/yfinance/) library to access live and historical stock data for in-depth analysis.
- **Sentiment Analysis**: Incorporates a news API and employs [TextBlob](https://textblob.readthedocs.io/en/dev/) for polarity and sentiment analysis, allowing traders to gauge market sentiment based on news headlines.
- **Google Sheets Integration**: Communicates with the Google Sheets API to retrieve a list of tickers and exchanges for analysis, making it easy to manage and update tracking lists.
- **Pushbullet Notifications**: Sends regular updates about stock actions and highlights promising buy (long) or sell (short) recommendations for swing trading via the [Pushbullet API](https://docs.pushbullet.com/).
- **Discord Interface**: Easily accessible through Discord, enabling users to interact with the bot, request analyses, and receive updates directly in their chat.
- **Stay Alive Server**: Spawns a stay alive server that can be monitored via the [UptimeRobot](https://uptimerobot.com/) service to ensure reliability.
- **Automated Deployment**: Deployed using the [PM2](https://pm2.keymetrics.io/) service, ensuring the bot automatically restarts on failure and undergoes a full reset every even day (approximately every 48 hours).

## Integrations
- **Financial APIs**: Integrates multiple financial data sources for comprehensive analysis.
- **News APIs**: Leverages news sentiment analysis to enhance decision-making.
- **Google Sheets API**: Retrieves data from user-managed sheets for tailored stock analysis.

## Getting Started
You can interact with the Scribe Bot by joining our Discord server: [Join the Bot Gallery Server](https://discord.gg/9AXMNBfPMF).

If you'd like to invite the Scribe Bot to your own server, you can do so using this link: [Invite Scribe Bot](https://discord.com/api/oauth2/authorize?client_id=899283955000414238&permissions=534794206272&scope=bot).

## Resources
- For detailed user instructions, refer to the [User Handbook](https://github.com/skywalker94/scribe_bot_notes/blob/main/handbook.md).
- [Input sheet](https://docs.google.com/spreadsheets/d/1dVZjD294f4IPGJIE9EKR47hygZmnB9AE6LBlZ3gLw-w/) to control the instruments that the bot is tracking.
- For an in-depth analysis of the bot's functionality, visit the [Analysis Document](https://github.com/skywalker94/scribe_bot_notes/blob/main/analysis.md).

## Conclusion
Scribe Bot aims to empower traders with actionable insights and timely recommendations, leveraging the power of advanced financial analytics and community interaction. Whether you're a seasoned trader or new to the stock market, Scribe Bot is your reliable partner in navigating the complexities of trading.

---

*Note: Always conduct your own research and due diligence before making trading decisions. The Scribe Bot provides recommendations based on historical data and technical analysis.*
