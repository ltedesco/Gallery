---
description: Run the full stock-analysis team on a ticker and return a synthesized Buy / Hold / Sell recommendation.
argument-hint: <TICKER>
---

Spawn the `portfolio-orchestrator` subagent with ticker `$1`. The
orchestrator will fan out to the fundamentals, technicals, and
news/sentiment specialists in parallel and return a synthesized
recommendation.

Return the orchestrator's output verbatim — do not add commentary.
