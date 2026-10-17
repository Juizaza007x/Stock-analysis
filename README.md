# QuantDesk

A private stock-analysis dashboard I designed and built for my own use as a computer engineering student.
The source code and the live app are private. This page describes what it does and how I built it.

## What it does

- Interactive stock charts (candles or line) with moving averages, RSI and MACD, and quotes that refresh
  during US market hours, with a label showing how fresh each number is
- Watchlist with notes and target prices
- Portfolio tracker: purchase lots, cost basis with fees, unrealized P/L, day change, allocation chart
- News per stock with importance ranking and the tickers each story relates to
- An "analysis pack" that turns my data into a briefing I can paste into an AI chat for a second opinion
- Price, percent-move, RSI and moving-average-cross alerts, checked every 5 minutes during market hours and
  sent to my phone through LINE
- Mobile layout, one-click backup export

## How it is built

- Next.js (App Router) and TypeScript, deployed on Vercel
- Neon Postgres with Drizzle ORM
- Market data from Alpaca with an automatic fallback to a second provider
- Charts: Lightweight Charts and Recharts
- Scheduled checks through an external cron service, notifications through the LINE Messaging API
- Vitest unit tests for the indicator math, portfolio math, alert logic and security helpers

## Design decisions

- Single-user, password-protected: nothing is public, and every API route checks the login itself
- Security by design: signed session cookies, login rate limiting, same-origin checks, strict
  Content-Security-Policy and other response headers, validated input, secrets kept out of the code
- Alerts fire once when a condition becomes true (not on every check), with cooldowns and a cap on
  notifications
- Minimal interface in a green palette.


![alt text](<chart c.png>)
![alt text](<news c.png>)
![alt text](<port c.png>)
![alt text](<new s.png>)
![alt text](<ana c.png>)
![alt text](<alert c.png>)


