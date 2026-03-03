# Project 2 — Reporting / Reconciliation-style Automation (Batch + Alerts)

## Goal
Build a reliable reporting workflow that:
ingests data (CSV / API / Google Sheets) → cleans & validates → aggregates → outputs a report  
with anomaly detection, alerts, and replay for failed batches.

## Tech Stack
- n8n (self-hosted)
- Batch processing (Split in Batches / controlled concurrency)
- Data validation & mapping (Code/Function node)
- Google Sheets (report output)
- Slack alerts
- Optional: SQLite/Postgres for audit trail (later)

## Architecture (WIP)
- Input: daily/weekly dataset (sanitized sample)
- Processing: normalize → validate → aggregate → detect anomalies
- Output: summary report + anomaly list
- Failure path: alert + dead-letter + replay

## Acceptance Criteria (L2)
- Data quality: missing/invalid rows are captured (not silently dropped)
- Batch safety: reruns do not duplicate final outputs (idempotency at report level)
- Observability: run_id / batch_id recorded for tracing
- Anomaly alerts: threshold-based alerts to Slack
- Replay: failed batch can be reprocessed deterministically
- Handoff pack: export JSON + setup guide + runbook + Loom demo

## Deliverables (to be added)
- [ ] architecture.png
- [ ] workflow.json
- [ ] setup.md
- [ ] runbook.md
- [ ] sample-data.csv
- [ ] loom-link.md

## Status
WIP — skeleton created.
