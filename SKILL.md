---
name: weex-contract-api-agent
description: Use when the user wants WEEX futures (contract) API automation instead of browser clicks, including natural-language order execution (for example “place an ETHUSDT short limit order at 10000 with size 0.001”), auto placing/canceling orders, fetching market data, querying account/positions, adjusting leverage/margin, handling plan TP/SL orders, or building bot-style workflows on WEEX contract REST/WebSocket interfaces.
---

# WEEX Contract API Agent

## Overview

This skill provides a ready-to-run WEEX contract API CLI with signed private requests, market data retrieval, and guarded live trading actions.

When the user gives a direct trading instruction with complete fields, execute it directly through this skill.

## Prerequisites

1. Python 3.9+
2. Network access to WEEX API domains
3. For private endpoints, set credentials:

```bash
export WEEX_API_KEY="..."
export WEEX_API_SECRET="..."
export WEEX_API_PASSPHRASE="..."
# optional
export WEEX_API_BASE="https://api-contract.weex.com"
export WEEX_LOCALE="en-US"
```

## Core Script

Primary script:

- `scripts/weex_contract_api.py`

It supports:

- full contract REST endpoint catalog (market/account/transaction)
- generic endpoint invocation with JSON body/query
- convenience commands for `place-order`, `cancel-order`, `ticker`, and `poll-ticker`
- signing private requests with HMAC SHA256 + Base64
- live-trading guard (`--confirm-live`) for mutating endpoints

## Standard Workflow

1. Discover endpoint key:

```bash
python3 scripts/weex_contract_api.py list-endpoints --pretty
```

2. Read market data (no private creds needed):

```bash
python3 scripts/weex_contract_api.py ticker --symbol cmt_btcusdt --pretty
python3 scripts/weex_contract_api.py call --endpoint market.get_depth --query '{"symbol":"cmt_btcusdt","limit":"20"}' --pretty
```

3. Preview a private call before sending:

```bash
python3 scripts/weex_contract_api.py call \
  --endpoint transaction.place_order \
  --body '{"symbol":"cmt_btcusdt","client_oid":"demo-1","size":"0.001","type":"1","order_type":"0","match_price":"0","price":"100000"}' \
  --dry-run --pretty
```

4. Send a live mutating request only when explicitly required:

```bash
python3 scripts/weex_contract_api.py place-order \
  --symbol cmt_btcusdt \
  --size 0.001 \
  --type 1 \
  --order-type 0 \
  --match-price 0 \
  --price 100000 \
  --confirm-live --pretty
```

## Natural Language Auto-Order Workflow

Use this workflow when user messages are explicit live order commands (for example: `Place ETHUSDT short, limit 10000, size 0.001`).

1. Parse user text using:

```bash
python3 scripts/weex_contract_api.py place-order-from-text --text "<original user text>" --dry-run --pretty
```

2. Validate parsed fields:
- symbol normalized to WEEX contract format (for example `ETHUSDT -> cmt_ethusdt`)
- side mapping: `open long=1`, `open short=2`, `close long=3`, `close short=4`
- `limit` maps to `match_price=0` with required `price`
- `market` maps to `match_price=1`
- `size/qty/amount` maps to `size`

3. If user intent is clearly to execute now and fields are complete, send live order:

```bash
python3 scripts/weex_contract_api.py place-order-from-text --text "<original user text>" --confirm-live --pretty
```

4. Return execution response including `order_id`/error payload.

If any required field is missing or ambiguous, stop and ask only for the missing field.

## High-Frequency or Automated Pulls

Use polling mode for simple automated quote collection:

```bash
python3 scripts/weex_contract_api.py poll-ticker --symbol cmt_btcusdt --interval 2 --count 30 --pretty
```

For strategy loops, call the script from your scheduler/worker and parse the JSON output.

## Safety Policy

- Do not send mutating requests without `--confirm-live`.
- Use `--dry-run` first for any order/leverage/margin/account-changing operation.
- Keep symbols and numeric precision aligned with contract metadata (`market.get_contract_info`).
- If API returns timestamp/signature errors, sync local clock and re-check signing input order.

## References

Load these only when needed:

- `references/contract-endpoints.md` for full interface coverage (not only place order)
- `references/auth-and-signing.md` for headers/signature/env contract
- `references/websocket.md` for WS domains, auth notes, and channel docs
