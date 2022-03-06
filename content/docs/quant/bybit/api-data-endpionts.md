---
title: "其他接口"
weight: 4
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 获取bybit服务器时间

```python
from pybit import HTTP
session = HTTP("https://api-testnet.bybit.com")
print(session.server_time())  
```

返回结果：
```json
{
    "ret_code": 0,
    "ret_msg": "OK",
    "ext_code": "",
    "ext_info": "",
    "result": {},
    "time_now": "1577444332.192859"
}
```
