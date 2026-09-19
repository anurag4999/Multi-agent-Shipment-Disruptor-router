# AI-Powered Shipment Disruption Router

An AI-powered, multi-agent workflow that detects shipment disruptions, classifies severity, and recommends policy-grounded actions (reroute, expedite, escalate). Built-in self-review and safety guardrails ensure accurate, auditable decisions — reducing manual work while keeping humans in the loop for critical cases.

## The Business Problem

When shipments run into trouble — weather delays, carrier failures, customs holds, capacity breaches — someone has to notice, judge severity, and decide what to do next. Done manually, this is slow, inconsistent, and pulls dispatchers away from the cases that actually need their judgment. Routine delays get the same attention as critical ones, and decisions aren't always traceable back to policy.

This workflow automates that triage and decision-making end-to-end, while keeping humans firmly in control of anything high-stakes.

## How It Works

The workflow uses a team of specialized AI agents that check each other's work, rather than a single model making an unchecked call:

1. **Classifier Agent** — reviews the disruption and determines its type (weather, carrier failure, capacity breach, customs hold, or standard delay) and severity (low to critical).
2. **Router Agent** — recommends an action (reroute, expedite, hold, monitor, or escalate to a human), searching the company's logistics policy rulebook and citing the specific policies behind every recommendation.
3. **Auditor Agent** — independently reviews the Router Agent's recommendation for accuracy, policy alignment, and safety before it's finalized. If something doesn't hold up, it sends the case back for revision (up to a limit) or escalates it to a human.

Two safeguards run before any of this:
- **Noise filter** — shipments that are on-time and healthy are filtered out immediately, so the AI agents only spend effort on genuine disruptions.
- **Prompt-injection guardrail** — screens incoming data for attempts to manipulate the AI's instructions, protecting the integrity of every downstream decision.

## Key Benefits

- **Faster response** to disruptions, with less manual triage
- **Consistent, policy-grounded decisions** — every recommendation cites the rule it's based on
- **Built-in quality control** — a second AI agent checks the first before anything is finalized
- **Human oversight where it matters** — critical, ambiguous, or high-value cases are escalated, not auto-resolved
- **Auditable by design** — decisions, rationale, and policy citations are captured for every case

## Tech Stack

- **[n8n](https://n8n.io/)** — workflow orchestration
- **OpenAI GPT models** (via n8n's LangChain integration) — reasoning agents
- **Retrieval-Augmented Generation (RAG)** — grounds every routing decision in the company's actual policy rulebook rather than model guesswork

## Status

This is a demonstration/reference workflow. File paths and instance identifiers have been sanitized for public sharing — connect your own OpenAI credentials and policy/data files before running it in n8n.
