# financial-stock — Claude Code plugin

A team of specialized subagents that analyze a stock ticker and produce a
synthesized Buy / Hold / Sell recommendation. All data is fetched from
public web pages via `WebFetch` — no API keys, no paid data feeds.

## The team

| Agent | Role |
|---|---|
| `portfolio-orchestrator` | Top-level. Spawns the three specialists in parallel and synthesizes their reports. |
| `stock-fundamentals` | Valuation ratios, earnings, margins, balance sheet, cash flow. |
| `stock-technicals` | Trend, moving averages, RSI, MACD, support/resistance. |
| `stock-news-sentiment` | Recent headlines, aggregate sentiment, upcoming catalysts. |

## Slash command

```
/analyze-stock AAPL
```

This invokes the orchestrator, which fans out to the three specialists and
returns a single structured recommendation.

## Install

### Option 1 — Local user install

Copy this directory into your user-level Claude Code plugins folder:

```bash
cp -r financial-stock-plugin ~/.claude/plugins/financial-stock
```

Restart your Claude Code session and the `/analyze-stock` command plus the
four subagents will be available.

### Option 2 — Project-local install

Drop the directory inside a project's `.claude/plugins/` and it will be
available in sessions started from that project.

### Option 3 — Marketplace

Reference the directory from a Claude Code plugin marketplace manifest.
See the Claude Code plugin docs for marketplace format.

## Data sources

All agents fetch from public pages:

- Yahoo Finance (`finance.yahoo.com`)
- SEC EDGAR (`sec.gov`)
- StockAnalysis.com (`stockanalysis.com`)
- StockCharts.com (`stockcharts.com`)
- Reuters (`reuters.com`)
- MarketWatch (`marketwatch.com`)
- Google News (`news.google.com`)

If your Claude Code session runs in a sandboxed environment with a
restrictive network policy (e.g. Claude Code on the web), make sure these
domains are reachable. See
<https://code.claude.com/docs/en/claude-code-on-the-web> for the policy
options.

## Disclaimer

This plugin is for informational and educational purposes only. Its
output is **not financial advice**. Do your own research, and consult a
licensed advisor before making investment decisions.
