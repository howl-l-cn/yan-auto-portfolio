# n8n — AI Brief Automation System

## Overview
This project is a self-hosted n8n automation system that turns AI industry news into structured email briefs.

It is designed to reduce manual information sorting by connecting news ingestion, deduplication, conditional processing, model summarization, and email delivery into one repeatable workflow.

## What It Does
- Reads AI industry news from RSS sources
- Deduplicates processed items with Google Sheets
- Checks whether there are new items before calling the model
- Uses DeepSeek to generate a structured brief
- Sends the result as an HTML email through Gmail
- Records workflow runs for observability and tracking

## Workflow Highlights
- RSS ingestion
- Google Sheets state management with `seen_items`
- Conditional branching with `new_count > 0`
- DeepSeek summary generation
- Gmail auto delivery
- `run_log` for workflow observability
- Self-hosted deployment with Docker on personal server

## Why I Designed It This Way
This workflow is designed to avoid unnecessary model calls and repeated notifications.

Key design choices:
- only call the model when new items exist
- keep processed items in `seen_items`
- keep execution records in `run_log`
- separate state tracking from content generation
- make the workflow easy to inspect and demonstrate

## Engineering Work
I independently handled the workflow design, deployment, debugging, and delivery logic.

Key engineering points:
- n8n workflow design and node orchestration
- self-hosted deployment on personal server with Docker
- Google Sheets integration for deduplication and logging
- conditional branching to reduce repeated execution
- HTML email formatting for readable output
- practical debugging of node logic, field mapping, and API responses

## Problems I Solved
During implementation, I solved several practical issues:

- Google Sheets OAuth connection setup
- deduplication logic with `seen_items`
- splitting `new_items[]` into appendable rows
- ensuring only new items trigger model generation
- fixing Gmail HTML body rendering
- making the workflow produce observable run records

These issues helped me turn a simple workflow idea into a working automation loop that can actually be shown and reused.

## Why This Project Matters
This project shows that I can connect information sources, state management, model calls, and delivery into one working automation system.

It is not just an RSS reader or a prompt demo — it is a self-hosted workflow with clear logic, persistent state, and visible output.

## Stack
- n8n
- DeepSeek API
- Gmail
- Google Sheets
- RSS
- Docker
- Personal server

## Proof / Materials
The following materials will be added here:
- workflow overview screenshot
- email brief screenshot
- `seen_items` screenshot
- `run_log` screenshot
- notes on design choices
