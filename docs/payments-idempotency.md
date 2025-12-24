# Payments: Idempotency & Retries

## Problem
Network retries and double-submits can cause duplicate charges or inconsistent order state.

## Baseline Rules
- Every payment attempt must have an idempotency key.
- Order finalization must be server-authoritative.
- Webhooks are source of truth for payment status.
- Retries must be safe: same request => same outcome.

## Common Failure Modes
- Client timeout after charge succeeded
- Webhook delay or duplicate delivery
- Race between callback and webhook

## Resolution Pattern
- Idempotent checkout session
- Order state machine
- Webhook-driven reconciliation
