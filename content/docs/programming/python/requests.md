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

