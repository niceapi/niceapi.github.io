---
title: "Requests"
weight: 8
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---

## 发送请求
```python
req = requests.get(url)
req = requests.post(url,data={'key':'value'})
req = requests.put(url,data={'key':'value'})
req = requests.delete(url)
req = requests.head(url)
req = requests.options(url)
```

响应内容
```python
req.url
req.txet
req.json()
req.status_code
req.history
```

### get请求参数格式化
```python
import requests
import json

r=requests.get("https://api-testnet.bybit.com/public/linear/kline?symbol=BTCUSDT&interval=1&limit=2&from=1581231260")
print(json.dumps(json.loads(r.text)['result'],indent=4,sort_keys=True))

kline="https://api-testnet.bybit.com/public/linear/kline"
params={
        'symbol':'BTCUSDT',
        'interval':1,
        'limit':2,
        'from':1581231260
        }
r1=requests.get(kline,params=params)
data=json.loads(r1.text)
data=json.dumps(data['result'],indent=4,sort_keys=True)
print(data)
```
