# Personal n8n Projects

## 1. Daily Market Brief (Yahoo_Finance and CNBC)

### Purpose

Automated daily market summary workflow that aggregates global stock indices and financial news in a unified brief.

### Features

- **Scheduled Execution**: Runs daily at 8:00 AM
- **Global Indices Tracking**: Monitors 8 major stock market indices:
  - S&P 500 (^GSPC)
  - Nasdaq Composite (^IXIC)
  - Dow Jones Industrial Average (^DJI)
  - Russell 2000 (^RUT)
  - FTSE 100 (^FTSE)
  - Nikkei 225 (^N225)
  - Hang Seng (^HSI)
  - Straits Times Index (STI) (^STI)

- **Market Data**: Fetches 5-day historical charts from Yahoo Finance API
- **Headlines**: Retrieves top financial news from CNBC RSS feed
- **Formatted Output**: Presents indices with current prices and percentage changes with directional indicators (▲ for gains, ▼ for losses)

### Data Sources

- Yahoo Finance API
- CNBC RSS Feed

### Workflow Components

1. Schedule trigger (daily at 8:00 AM)
2. Symbol list builder for major indices
3. Yahoo Finance HTTP requests to fetch chart data
4. Data formatting and aggregation
5. CNBC headline aggregation
6. Output formatting for presentation

---

## 2. Portfolio Sentiment Analysis Bot

### Purpose

AI-powered sentiment analysis tool that evaluates news articles' potential impact on specific stocks using LLM analysis.

### Features

- **Ticker-based Analysis**: Reads stock ticker symbols from a Google Sheet
- **News Aggregation**: Fetches recent news articles for each stock from EODHD API
- **AI Sentiment Evaluation**: Uses LangChain AI Agent to analyze articles
- **Scoring System**: Generates sentiment scores from -1 to +1:
  - -1 = Strongly negative impact
  - 0 = Neutral
  - +1 = Strongly positive impact

- **Contextual Analysis**: Considers whether information is new or already priced in
- **Rationale Output**: Provides reasoning for each sentiment assessment

### Data Sources

- Google Sheets (stock ticker list)
- EODHD API (news articles)
- LLM/AI Agent (sentiment analysis)

### Workflow Components

1. Google Sheets integration to read stock tickers
2. Batch loop processing over ticker symbols
3. EODHD API calls to retrieve recent news articles
4. Article aggregation and formatting
5. LangChain AI Agent for sentiment analysis
6. JSON output with sentiment scores and rationale

### Output Format

```json
{
  "symbol": "STOCK_SYMBOL",
  "sentiment_score": -1 to 1,
  "rationale": "Explanation of analysis"
}
```

---

## Summary

| Project                | Type             | Trigger          | Purpose                              |
| ---------------------- | ---------------- | ---------------- | ------------------------------------ |
| Daily Market Brief     | Scheduled        | 8:00 AM Daily    | Automated global market summary      |
| Sentiment Analysis Bot | Batch Processing | Manual/Scheduled | AI-driven stock sentiment evaluation |

Both workflows demonstrate data aggregation, API integration, and intelligent processing using n8n's capabilities for financial market analysis and monitoring.
