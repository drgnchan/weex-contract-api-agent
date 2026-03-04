# Contract WebSocket Notes

Main doc: <https://www.weex.com/api-doc/contract/Websocket/websocket-intro>

## Endpoints

- Public: `wss://ws-contract.weex.com/v2/ws/public`
- Private: `wss://ws-contract.weex.com/v2/ws/private`

## Common control messages

Subscribe:

```json
{
  "event": "subscribe",
  "channel": "channel_name"
}
```

Unsubscribe:

```json
{
  "event": "unsubscribe",
  "channel": "channel_name"
}
```

Heartbeat response:

- Server ping example: `{"event":"ping","time":"1693208170000"}`
- Client should reply pong with same `time`.

## Private channel auth (header-based)

The intro page documents private WS authentication in connection headers:

- `ACCESS-KEY`
- `ACCESS-PASSPHRASE`
- `ACCESS-TIMESTAMP`
- `ACCESS-SIGN`

For private WS, docs describe signing message as:

- `timestamp + requestPath`

Where requestPath is `/v2/ws/private`.

## Channel docs

Public:

- Tickers: <https://www.weex.com/api-doc/contract/Websocket/public/Tickers-Channel>
- Depth: <https://www.weex.com/api-doc/contract/Websocket/public/Depth-Channel>
- Trades: <https://www.weex.com/api-doc/contract/Websocket/public/Trades-Channel>
- Candles: <https://www.weex.com/api-doc/contract/Websocket/public/Candlesticks-Channel>

Private:

- Account: <https://www.weex.com/api-doc/contract/Websocket/private/Account-Channel>
- Order: <https://www.weex.com/api-doc/contract/Websocket/private/Order-Channel>
- Fill: <https://www.weex.com/api-doc/contract/Websocket/private/Fill-Channel>
- Positions: <https://www.weex.com/api-doc/contract/Websocket/private/Positions-Channel>
