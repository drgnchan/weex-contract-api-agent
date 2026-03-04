# WEEX Contract API Endpoint Index

Source scope:
- Contract docs root: <https://www.weex.com/api-doc/contract/log/changelog>
- Seed page (EN): <https://www.weex.com/api-doc/contract/Transaction_API/PlaceOrder>
- Sitemap used for coverage: <https://www.weex.com/api-doc/sitemap.xml>

This index covers contract Market, Account, Transaction, and WebSocket pages present in WEEX docs as of 2026-03-04.

## Market APIs

| Key | Method | Path | Doc |
|---|---|---|---|
| `market.get_server_time` | GET | `/capi/v2/market/time` | <https://www.weex.com/api-doc/contract/Market_API/GetServerTime> |
| `market.get_contract_info` | GET | `/capi/v2/market/contracts` | <https://www.weex.com/api-doc/contract/Market_API/GetContractInfo> |
| `market.get_ticker` | GET | `/capi/v2/market/ticker` | <https://www.weex.com/api-doc/contract/Market_API/GetTickerInfo> |
| `market.get_all_tickers` | GET | `/capi/v2/market/tickers` | <https://www.weex.com/api-doc/contract/Market_API/GetAllTickerInfo> |
| `market.get_depth` | GET | `/capi/v2/market/depth` | <https://www.weex.com/api-doc/contract/Market_API/GetDepthData> |
| `market.get_trades` | GET | `/capi/v2/market/trades` | <https://www.weex.com/api-doc/contract/Market_API/GetTradeData> |
| `market.get_candles` | GET | `/capi/v2/market/candles` | <https://www.weex.com/api-doc/contract/Market_API/GetKLineData> |
| `market.get_history_candles` | GET | `/capi/v2/market/historyCandles` | <https://www.weex.com/api-doc/contract/Market_API/GetHistoryKLineData> |
| `market.get_current_fund_rate` | GET | `/capi/v2/market/currentFundRate` | <https://www.weex.com/api-doc/contract/Market_API/GetCurrentFundRate> |
| `market.get_funding_history` | GET | `/capi/v2/market/getHistoryFundRate` | <https://www.weex.com/api-doc/contract/Market_API/GetContractFundingHistory> |
| `market.get_next_funding_time` | GET | `/capi/v2/market/funding_time` | <https://www.weex.com/api-doc/contract/Market_API/GetNextContractSettlementTime> |
| `market.get_open_interest` | GET | `/capi/v2/market/open_interest` | <https://www.weex.com/api-doc/contract/Market_API/GetTotalPlatformOpenInterest> |
| `market.get_currency_index` | GET | `/capi/v2/market/index` | <https://www.weex.com/api-doc/contract/Market_API/GetCurrencyIndex> |

## Account APIs

| Key | Method | Path | Doc |
|---|---|---|---|
| `account.get_accounts` | GET | `/capi/v2/account/getAccounts` | <https://www.weex.com/api-doc/contract/Account_API/AllContractAccountsInfo> |
| `account.get_account` | GET | `/capi/v2/account/getAccount` | <https://www.weex.com/api-doc/contract/Account_API/GetUserSingleAssetInfo> |
| `account.get_assets` | GET | `/capi/v2/account/assets` | <https://www.weex.com/api-doc/contract/Account_API/GetAccountBalance> |
| `account.get_all_positions` | GET | `/capi/v2/account/position/allPosition` | <https://www.weex.com/api-doc/contract/Account_API/GetAllContractPositions> |
| `account.get_single_position` | GET | `/capi/v2/account/position/singlePosition` | <https://www.weex.com/api-doc/contract/Account_API/GetSingleContractPosition> |
| `account.get_settings` | GET | `/capi/v2/account/settings` | <https://www.weex.com/api-doc/contract/Account_API/GetSingleContractUserConfig> |
| `account.get_bills` | POST | `/capi/v2/account/bills` | <https://www.weex.com/api-doc/contract/Account_API/GetContractBills> |
| `account.adjust_leverage` | POST | `/capi/v2/account/leverage` | <https://www.weex.com/api-doc/contract/Account_API/AdjustLeverage> |
| `account.adjust_margin` | POST | `/capi/v2/account/adjustMargin` | <https://www.weex.com/api-doc/contract/Account_API/AdjustMargin> |
| `account.auto_add_margin` | POST | `/capi/v2/account/modifyAutoAppendMargin` | <https://www.weex.com/api-doc/contract/Account_API/AutoAddMargin> |
| `account.change_hold_mode` | POST | `/capi/v2/account/position/changeHoldModel` | <https://www.weex.com/api-doc/contract/Account_API/ModifyUserAccountMode> |

## Transaction APIs

| Key | Method | Path | Doc |
|---|---|---|---|
| `transaction.place_order` | POST | `/capi/v2/order/placeOrder` | <https://www.weex.com/api-doc/contract/Transaction_API/PlaceOrder> |
| `transaction.batch_orders` | POST | `/capi/v2/order/batchOrders` | <https://www.weex.com/api-doc/contract/Transaction_API/PlaceOrdersBatch> |
| `transaction.cancel_order` | POST | `/capi/v2/order/cancel_order` | <https://www.weex.com/api-doc/contract/Transaction_API/CancelOrder> |
| `transaction.cancel_batch_orders` | POST | `/capi/v2/order/cancel_batch_orders` | <https://www.weex.com/api-doc/contract/Transaction_API/CancelOrdersBatch> |
| `transaction.get_order_info` | GET | `/capi/v2/order/detail` | <https://www.weex.com/api-doc/contract/Transaction_API/GetSingleOrderInfo> |
| `transaction.get_history_orders` | GET | `/capi/v2/order/history` | <https://www.weex.com/api-doc/contract/Transaction_API/GetOrderHistory> |
| `transaction.get_current_orders` | GET | `/capi/v2/order/current` | <https://www.weex.com/api-doc/contract/Transaction_API/GetCurrentOrderStatus> |
| `transaction.get_fills` | GET | `/capi/v2/order/fills` | <https://www.weex.com/api-doc/contract/Transaction_API/GetTradeDetails> |
| `transaction.place_plan_order` | POST | `/capi/v2/order/plan_order` | <https://www.weex.com/api-doc/contract/Transaction_API/PlacePendingOrder> |
| `transaction.cancel_plan_order` | POST | `/capi/v2/order/cancel_plan` | <https://www.weex.com/api-doc/contract/Transaction_API/CancelPendingOrder> |
| `transaction.get_current_plan_orders` | GET | `/capi/v2/order/currentPlan` | <https://www.weex.com/api-doc/contract/Transaction_API/GetCurrentPendingOrders> |
| `transaction.get_history_plan_orders` | GET | `/capi/v2/order/historyPlan` | <https://www.weex.com/api-doc/contract/Transaction_API/GetHistoricalPendingOrders> |
| `transaction.close_positions` | POST | `/capi/v2/order/closePositions` | <https://www.weex.com/api-doc/contract/Transaction_API/ClosePositions> |
| `transaction.cancel_all_orders` | POST | `/capi/v2/order/cancelAllOrders` | <https://www.weex.com/api-doc/contract/Transaction_API/CancelAllOrders> |
| `transaction.place_tpsl_order` | POST | `/capi/v2/order/placeTpSlOrder` | <https://www.weex.com/api-doc/contract/Transaction_API/PlaceTpSlOrder> |
| `transaction.modify_tpsl_order` | POST | `/capi/v2/order/modifyTpSlOrder` | <https://www.weex.com/api-doc/contract/Transaction_API/ModifyTpSlOrder> |

## WebSocket pages

| Topic | Doc |
|---|---|
| Intro | <https://www.weex.com/api-doc/contract/Websocket/websocket-intro> |
| Public ticker channel | <https://www.weex.com/api-doc/contract/Websocket/public/Tickers-Channel> |
| Public depth channel | <https://www.weex.com/api-doc/contract/Websocket/public/Depth-Channel> |
| Public trades channel | <https://www.weex.com/api-doc/contract/Websocket/public/Trades-Channel> |
| Public candles channel | <https://www.weex.com/api-doc/contract/Websocket/public/Candlesticks-Channel> |
| Private account channel | <https://www.weex.com/api-doc/contract/Websocket/private/Account-Channel> |
| Private order channel | <https://www.weex.com/api-doc/contract/Websocket/private/Order-Channel> |
| Private fill channel | <https://www.weex.com/api-doc/contract/Websocket/private/Fill-Channel> |
| Private positions channel | <https://www.weex.com/api-doc/contract/Websocket/private/Positions-Channel> |

## Common parameter docs

- Margin mode: <https://www.weex.com/api-doc/contract/API_Common_Params/MarginMode>
- Position mode: <https://www.weex.com/api-doc/contract/API_Common_Params/PositionMode>
- Split position mode: <https://www.weex.com/api-doc/contract/API_Common_Params/SplitPositionMode>
- Error codes: <https://www.weex.com/api-doc/contract/ErrorCodes/ExampleOfErrorCode>
