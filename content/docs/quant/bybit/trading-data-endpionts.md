---
title: "交易数据接口"
weight: 2
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 活动单

### 创建活动委托单

```python
from pybit import HTTP
session = HTTP("https://api-testnet.bybit.com",
               api_key="", api_secret="")
print(session.place_active_order(
    symbol="BTCUSDT",
    side="Sell",
    order_type="Limit",
    qty=0.01,
    price=8083,
    time_in_force="GoodTillCancel",
    reduce_only=False,
    close_on_trigger=False
))
```

### 查询活动委托单

```python
from pybit import HTTP
session = HTTP("https://api-testnet.bybit.com",
               api_key="", api_secret="")
print(session.get_active_order(
    symbol="BTCUSDT"
))
```

### 撤销活动委托单

```python
from pybit import HTTP
session = HTTP("https://api-testnet.bybit.com",
               api_key="", api_secret="")
print(session.cancel_active_order(
    symbol="BTCUSDT",
    order_id=""
))
```

### 撤销所有活动委托单

```python
from pybit import HTTP
session = HTTP("https://api-testnet.bybit.com",
               api_key="", api_secret="")
print(session.cancel_all_active_orders(
    symbol="BTCUSDT"
))
```

### 修改活动单信息

### 实时查询活动委托

## 条件单

### 创建条件委托单
### 查询条件委托单
### 撤销条件委托单
### 撤销全部条件委托单
### 修改条件委托单
### 实时查询条件委托单

## 持仓
## 风险限制
## 资金费率
