---
name: alert-correlation
description: CISO function F5 — identify the correlation between alert data and threat-intelligence reports to determine the impact on infrastructure. Use when the SOC needs alerts de-duplicated, grouped into incidents, and cross-referenced against current threat intelligence with infrastructure-impact scoring.
license: CC-BY-NC-ND-4.0
---

# F5 — Alert / Threat-Intelligence Correlation

Correlate alerts with TI and produce an impact-scored mapping that the SOC can action.

## Function mapping (GAISO T3.1)

- **Domain**: Threat detection and response.
- **ISO/IEC 27002:2022 controls**: **O7** Threat intelligence, **O25** Assessment and decision on information security events; **T8** Management of technical vulnerabilities, **T15** Logging, **T16** Monitoring activities, **T23** Web filtering.
- **Regulations**: NIS2 Art. 21(2)(b), (h); Commission Implementing Regulation (EU) 2024/2690 Annex; AI Act Art. 15.

## Inputs you must demand

1. Alert batch. Required fields per alert: `alert_id, timestamp, source, signature, raw_iocs[]`.
2. Threat-intelligence entries. Required: `ti_id, indicator, type, confidence, source, first_seen`.
3. Asset inventory summary with criticality tiers.
4. Time window the correlation should respect (default 24h lookback).

## Correlation rules

- Share at least one indicator of the same type for a **hard match** (IP, domain, URL, file hash, email sender).
- Share a TTP (MITRE ATT&CK technique) for a **soft match**. Tag as `soft` in the output.
- Time proximity alone is **not** a correlation.
- Similar vendor/geography alone is **not** a correlation.

## Procedure

1. **Ingest** alerts and TI. Normalise indicator strings (lowercase, strip zeros in IPs, Punycode normalisation, SHA trims).
2. **Match** each alert against TI by the rules above.
3. **Score impact** on 0–10 = f(asset_criticality, confirmed_iocs, breadth_of_hosts_touched).
4. **Group** alerts that share an incident candidate (same actor TTP + same critical asset) into an `incident_hint`.
5. **Recommend action** per alert: `Suppress`, `Monitor`, `Investigate`, `Contain`, `Escalate`.
6. **Emit** JSON list (or table — follow `[FORMAT]`).
7. **Append** the OVB.

## Default output format

```json
[
  {
    "alert_id": "a-9001",
    "ti_match": {"ti_id": "ti-447", "type": "hard:domain"},
    "impact_score": 7,
    "affected_assets": ["<tier1 asset>"],
    "affected_controls": ["T15", "T16", "T23"],
    "incident_hint": "inc-h-12",
    "recommended_action": "Contain"
  }
]
```

## Pitfalls

- **Indicator casing**. An IOC that differs only by case, trailing slash or www. prefix is the same indicator. Normalise before comparing.
- **Match inflation**. Shared TLD or shared ASN is not a TTP. Do not claim correlation.
- **Feedback loops**. Do not use the output of one correlation cycle as TI for the next without human review.
- **Time skew**. Clocks drift. Flag an alert whose timestamp is outside the SIEM's synchronised window (T17 Clock synchronization).
- **Data-poisoning risk**. TI feeds can be attacked. If a feed produces a statistically abnormal match burst, flag the feed and downgrade confidence.

## Escalation

If any alert group crosses the NIS2 "significant incident" threshold (see Implementing Regulation 2024/2690 Annex), escalate immediately to the IR Lead and convert into an F6 triage task.

## Cross-references

- `threat-intelligence-analysis` (F1) — per-event risk scoring upstream.
- `incident-response-triage` (F6) — downstream when correlations fire an incident.
- `llm-threat-detection` (F8) — when correlated alerts suggest LLM-generated phishing.

## Output footer

Append the Output Verification Block. `Human review` = `SOC Tier-2` for impact < 7, `IR Lead + CISO` for impact ≥ 7.
