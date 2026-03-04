# Authentication and Signing

## Base domains

- Contract REST base URL: `https://api-contract.weex.com`
- Contract docs sample (Place Order): <https://www.weex.com/api-doc/contract/Transaction_API/PlaceOrder>

## REST headers

Private endpoints require these headers:

- `ACCESS-KEY`
- `ACCESS-SIGN`
- `ACCESS-PASSPHRASE`
- `ACCESS-TIMESTAMP` (Unix epoch milliseconds)
- `Content-Type: application/json`
- `locale` (optional, for example `en-US`)

## Signature formula

WEEX spot quick-start explicitly documents the signing string. Contract endpoint examples use the same header scheme and path-based signing style.

Reference page: <https://www.weex.com/api-doc/spot/QuickStart/Signature>

Signing message:

- if query string is empty:
  - `timestamp + method.toUpperCase() + requestPath + body`
- if query string exists:
  - `timestamp + method.toUpperCase() + requestPath + "?" + queryString + body`

Then:

1. `digest = HMAC_SHA256(secretKey, message)`
2. `ACCESS-SIGN = Base64(digest)`

Notes:

- `timestamp` must match `ACCESS-TIMESTAMP`.
- `requestPath` is only the path part (for example `/capi/v2/order/placeOrder`), not full URL.
- For GET requests, body is usually empty string.
- The timestamp window is short; ensure local clock is synced.

## Environment variables used by this skill script

- `WEEX_API_KEY`
- `WEEX_API_SECRET`
- `WEEX_API_PASSPHRASE`
- `WEEX_API_BASE` (optional override, default `https://api-contract.weex.com`)
- `WEEX_LOCALE` (optional, default `en-US`)
- `WEEX_API_TIMEOUT` (optional, default `15` seconds)

## Safety rules in this skill

- All mutating POST operations (order placement/cancel, leverage/margin changes, etc.) require explicit `--confirm-live`.
- Use `--dry-run` to inspect signed request shape without sending.
- Market data GET endpoints are safe by default and sent immediately.
