# Project 1 — Lead Intake + AI Classification + Google Sheets + Slack

## Goal
Build a production-ready lead intake workflow:
Webhook → validation → AI classification (JSON) → Google Sheets → Slack alerts  
with idempotency, retries/backoff, failure alerts, and replay.

## Tech Stack
- n8n (self-hosted)
- Webhook trigger
- LLM API (Gemini/OpenAI-compatible) for structured output
- Google Sheets
- Slack Incoming Webhook / Slack API
- Optional: PostgreSQL for idempotency keys (later)

## Architecture (WIP)
- Input: webhook payload (sanitized sample)
- Processing: validate → enrich → classify → route
- Output: sheets row + slack message
- Failure path: alert + dead-letter + replay

## Acceptance Criteria (L2)
- Idempotency: repeated webhook does NOT duplicate writes
- Rate limit handling: 429 → backoff retry
- Observability: correlation_id in logs + outputs
- Failure loop: alert + dead-letter record + replay workflow
- Handoff pack: export JSON + setup guide + runbook + Loom demo

## Deliverables (to be added)
- [ ] architecture.png
- [ ] workflow.json
- [ ] setup.md
- [ ] runbook.md
- [ ] sample-data.json
- [ ] loom-link.md

## Status
WIP — skeleton created.
