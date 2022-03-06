---
title: "钱包数据接口"
weight: 3
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 账户划转

### 合约、现货、理财账户资金划转

```python
from pybit import HTTP
from uuid import uuid4
session = HTTP("https://api-testnet.bybit.com",
               api_key="", api_secret="")
print(session.create_internal_transfer(
    transfer_id=str(uuid4()),
    coin="BTC",
    amount="0.1",
    from_account_type="SPOT",
    to_account_type="CONTRACT"
))
```

### 子母账户划转

```python
from pybit import HTTP
from uuid import uuid4
session = HTTP("https://api-testnet.bybit.com",
               api_key="", api_secret="")
print(session.create_subaccount_transfer(
    transfer_id=str(uuid4()), # UUID，全局唯一
    coin="BTC",
    amount="0.1",
    sub_user_id=251711, # 子账户id
    type="IN" # 转入转出类型
))
```

