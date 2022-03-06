---
title: "行情数据接口"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
## API

注意，本文档仅针对USDT合约交易对。

RESTful接口
 - 测试网 https://api-testnet.bybit.com
 - 主网1 https://api.bybit.com
 - 主网2 https://api.bytick.com

测试接口
```python
from pybit import HTTP
session = HTTP("https://api-testnet.bybit.com")
print(session.orderbook(symbol="BTCUSD"))
```

## 查询k线数据

请求参数

|参数|是否必须|类型|说明
|-|-|-|-|
|symbol|true|string|交易对|
|interval|true|string|K线周期|
|from|true|int|起始时间|
|limit|false|int|k线数量，最大200|

```python
from pybit import HTTP
session = HTTP("https://api-testnet.bybit.com")
print(session.query_kline(
    symbol="BTCUSD",
        interval="m",
	    from_time=1581231260
	    ))
```

返回参数
|参数|类型|说明|
|-|-|-|
|symbol|string|交易对|
|interval|string|k线周期|
|open_time|int|开始时间|
|open|string|开始价格|
|high|string|最高价格|
|low|string|最低价格|
|close|string|结束价格|
|volume|string|交易量|
|turnover|string|成交金额|

## 合约最新信息

请求示例
```python
from pybit import HTTP
session = HTTP("https://api-testnet.bybit.com")
print(session.latest_information_for_symbol(
    symbol="BTCUSD"
    ))
```

返回参数
|参数|类型|说明|
|-|-|-|
|symbol|string|交易对|
|bid_price|string|第一笔挂单买入价|
|ask_price|string|第一笔挂单卖出价|
|last_price|string|最新成交价|
|tick_direction|string|价格变换方向|
|prev_price_24h|string|24小时前的整点市价|
|prev_24h_pcnt|string|市价相对24小时变化百分比|
|high_price_24h|string|24小时最高价|
|low_price_24h|string|24小时最低价|
|prev_price_1h|string|1小时前的整点市价|
|prev_1h_pcnt|string|市价相对一小时前变化百分比|
|mark_price|string|标记价格|
|index_price|string|指数价格|
|open_interest|number|未平仓合约数量|
|volume_24h|number|24小时成交量|
|funding_rate|string|资金费率|
|predicted_funding_rate|string|预测资金费率|
|next_funding_time|string|下次结算资金费用时间|
|countdown_hour|number|结算资金费用剩余时间|
|delivery_fee_rate|string|交割费率（仅交割合约）|
|predicted_delivery_price|string|预期交割价（仅交割合约）|
|delivery_time|string|交割时间|

## 平仓交易历史数据

```python
from pybit import HTTP
session = HTTP("https://api-testnet.bybit.com")
print(session.public_trading_records(
    symbol="BTCUSDT",
    limit=500
))
```

## 查询合约信息

```python
from pybit import HTTP
session = HTTP("https://api-testnet.bybit.com")
print(session.query_symbol())
```

## 查询上个周期的资金费率

```python
from pybit import HTTP
session = HTTP("https://api-testnet.bybit.com")
print(session.get_the_last_funding_rate(
    symbol="BTCUSDT"
))
```

## 标记价格K线

```python
from pybit import HTTP
session = HTTP("https://api-testnet.bybit.com",
               api_key="", api_secret="")
print(session.query_mark_price_kline(
    symbol="BTCUSDT",
    interval=1,
    limit=2,
    from_time=1581231260
)
```

