---
title: "Flask Web"
weight: 10
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
## 最小应用

```python
from flask import Flask

app = Flask(__name__)
 
@app.route('/')
def index():
    return 'Hello World!'
 
if __name__ == '__main__':
    app.run(host = '0.0.0.0', port = '5000')
```


