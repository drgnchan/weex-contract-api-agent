---
name: weex-contract-api-agent
description: Use when the user wants WEEX futures (contract) API automation via REST, including direct order execution from natural language, order cancel/query, and market/account data retrieval.
---

# WEEX Contract API Agent

Use `scripts/weex_contract_api.py`.

For private endpoints:

```bash
export WEEX_API_KEY="..."
export WEEX_API_SECRET="..."
export WEEX_API_PASSPHRASE="..."
export WEEX_API_BASE="https://api-contract.weex.com"
export WEEX_LOCALE="en-US"
```

`WEEX_API_KEY`, `WEEX_API_SECRET`, and `WEEX_API_PASSPHRASE` are read from environment variables only.
If any is missing, stop immediately and tell the user to set env vars. Do not try alternatives.

## Fast Path

```bash
python3 scripts/weex_contract_api.py list-endpoints --pretty
python3 scripts/weex_contract_api.py ticker --symbol cmt_btcusdt --pretty
python3 scripts/weex_contract_api.py poll-ticker --symbol cmt_btcusdt --interval 2 --count 30 --pretty
```

## Natural Language Order

Example user instruction: `Place ETHUSDT short, limit 10000, size 0.001`

Preview parse:

```bash
python3 scripts/weex_contract_api.py place-order-from-text --text "<original user text>" --dry-run --pretty
```

Submit live:

```bash
python3 scripts/weex_contract_api.py place-order-from-text --text "<original user text>" --confirm-live --pretty
```

## Safety Policy

- Never send mutating requests without `--confirm-live`.
- Use `--dry-run` first.
- If instruction is ambiguous or missing fields, ask only for missing fields.

## References

- `references/contract-endpoints.md`
- `references/auth-and-signing.md`
- `references/websocket.md`
