# WIC AI Agent (2026–2027)

> **Status:** Research and design — no strategy validated for live competition deployment.

Joint project for the **World Investment Competition 2026–2027 — AI Agent Division**. We aim to design, test, document, and operate an autonomous trading agent that complies with the competition rules.

## Investment hypothesis

The starting research hypothesis is an **earnings-announcement premium (EAP)** in Nasdaq-listed equities. The candidate implementation takes positions around earnings, selects eligible events, and uses a QQQ hedge. The research explores concentrated portfolios and market-on-close (MOC) execution.

**The EAP parameters are not final.** Historic results are sensitive to survivorship bias, event timing, illiquid-name execution, transaction costs, and the assumptions used to simulate competing teams. Estimates in `FINDINGS_WIC_EAP.md` are research findings, **not forecasts**.

## Proposed architecture (to validate)

```text
Point-in-time event calendar / official issuer announcements
                        |
                Eligibility and data checks
                        |
             Quantitative EAP candidate signals
                        |
     LLM assessment of event timing and special situations
                        |
           Deterministic risk & compliance veto
                        |
            IBKR API execution and reconciliation
                        |
              Immutable logs and monitoring
```

- **Quantitative strategy:** earnings calendar, candidate selection, sizing and QQQ hedge. The current concentrated configuration (up to 10 names, R−1 to R) is a *research candidate*, not a committed deployment.
- **LLM agent:** participates throughout trading in actual investment decisions or predeclared strategy updates. Candidate uses include confirming earnings dates/times from issuer announcements and evaluating special situations. Its decisions and inputs must be logged.
- **Risk engine:** deterministic, independent veto over eligibility, exposure, margin, maximum drawdown, order sizing, data quality and emergency stops.
- **Execution:** IBKR TWS API / IB Gateway, with explicit checks for MOC cutoffs, order acknowledgements, fills, partial/rejected orders, hedge availability and reconciliation.
- **MarketPulse:** existing research on news relevance/sentiment; integrate only if testing shows it adds measurable value.

## Competition constraints (verify against latest official rules)

- AI Agent trading window: **1 February – 25 March 2027**; flatten all positions by **15:50 ET on 25 March**.
- Disqualification if end-of-day NAV falls **20% or more below the historical highest daily close**, including the initial NAV.
- Final outcome combines **70% performance rank** and **30% report rank** through weighted reciprocal rank fusion.
- Agent must make autonomous investment decisions; LLM must play an active role throughout live trading. Use the organizers' approved LLM access, log calls and costs, and respect the predeclared change policy.
- **Do not feed other teams' rankings or returns into the agent.**
- Nasdaq-listed equities/ETFs and permitted options only. Confirm all operational and eligibility details with the organizers before implementation.

Rules: https://jpsi-association.com/wic/rules

## Research and decisions

- [EAP research and findings](FINDINGS_WIC_EAP.md)
- [Issue #1 — Validate IBKR MOC execution](../../issues/1)
- [Issue #2 — Audit EAP strategy](../../issues/2)
- [Issue #3 — Define LLM decision architecture](../../issues/3)

### Immediate priorities

1. **Application:** agree on a truthful, specific 100–200-word investment approach before 15 November 2026.
2. **MOC execution:** verify IBKR paper order behavior, cutoff times, official auction prices, fill quality and liquidity assumptions. Do not treat paper fills as evidence of executable alpha.
3. **Point-in-time validation:** historical index constituents, delisted securities, announcement timestamps and corporate actions.
4. **Risk assessment:** run the proposed concentrated configuration with NAV peak-to-trough limits and overnight shock scenarios.
5. **Agent specification:** define exactly when the LLM intervenes and how the deterministic risk engine can reject decisions.

## Collaboration

Use **Issues** to track questions, experiments, evidence and decisions. Link each conclusion to code, data and a reproducible run. Prefer pull requests for implementation changes. Record why tests were accepted or rejected.

Keep **API keys, broker credentials, competition keys, private datasets, and account information** out of Git. Do not enable unattended live order placement until the agent, safeguards and logging have been validated.

## Important distinction

This repository documents a **research program**, not a promise of returns. A better backtest does not by itself establish a tradable edge after transaction costs and execution constraints.
