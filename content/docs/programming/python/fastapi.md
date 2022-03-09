---
title: "Fastapi"
weight: 1
# bookFlatSection: false
# bookToc: true
# bookHidden: false
# bookCollapseSection: false
# bookComments: false
# bookSearchExclude: false
---
## 基础

### 最小程序

``` python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
async def root():
    return {"message": "Hello World"}
```
用uvicorn运行：
```bash
uvicorn main:app --reload
# --reload跟flask中的debug功能一样
```

### 路由

为了准确防止用户名为“me”的用户抢占个人信息，要把“me”先定义在前面。
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/users/me")
async def read_user_me():
    return {"user_id": "the current user"}

@app.get("/users/{user_id}")
async def read_user(user_id: str):
    return {"user_id": user_id}
```

### 路径包含

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/files/{file_path:path}")
async def read_file(file_path: str):
    return {"file_path": file_path}

```


### 线程池

```python
@router.get("/test")
async def test():
    loop = asyncio.get_event_loop()
    await loop.run_in_executor(None, time.sleep, 1)
    return {"message": "线程池中运行sleep函数"}
```

### 文档接口

默认接口：`/docs/`
可选接口：`/redoc`

## 安全

### 关闭文档接口

```python
app = FastAPI(docs_url=None, redoc_url=None)
```
在开发时开启文档，部署时关闭文档，在系统中添加环境变量`env=develop`，然后修改代码：
```python
import os
from fastapi import FastAPI

env = os.getenv('env')
if env != 'develop':
    app = FastAPI(docs_url=None, redoc_url=None)
else:
    app = FastAPI()
```
