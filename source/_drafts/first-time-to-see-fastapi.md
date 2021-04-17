---
title: FastAPI 初體驗
categories: 學習紀錄
tags:
---

<style>
  section.compact {
    font-size: 150%  
  }
  img[alt~="center"] {
    display: block;
    margin: 0 auto;
  }
</style>

![](https://nijialin.com/images/2021/)

# 前言

- 適用於 Python 3.6 (含)以上的版本
- 支援非同步，使用 [Asyncio](https://docs.python.org/3/library/asyncio.html) 
- Pydantic 做型別檢查 (超讚)
<!-- more -->

# 介紹

```python
import uvicorn
from fastapi import FastAPI
app = FastAPI()

@app.get("/")
def root():
    return {"message": "Hello World!"}

if __name__ == "__main__":
    uvicorn.run("main:app", host="0.0.0.0", port=5000, reload=True)

```

跟 Flask 很像，只要把 Flask() 改成 **FastAPI()** 就可以啟動一個 sample server，

FastAPI 推薦使用 [Uvicorn](https://www.uvicorn.org/) 作為跑服務的工具，支援 [ASGI](https://asgi.readthedocs.io/en/latest/specs/main.html)，跑非同步相關的 Python 應用程式。

- [Uvicorn](https://www.uvicorn.org/) 可支援 HTTP/1.1 以及 WebSockets，但 HTTP/2.0 還不支援。
- 基於 [Starlette](https://github.com/encode/starlette) 實作的框架。
- 如果你的 Python app 有很大的吞吐量(throughput)，可以搭配 gunicorn 使用。([參考 startlette 的 Performance](https://github.com/encode/starlette#performance))

> WSGI 是單一且同步的介面，不適合有 long-lived connection 的場景，如 long-polling HTTP 或 Websocket。([參考](https://asgi.readthedocs.io/en/latest/introduction.html#what-s-wrong-with-wsgi))

# 引入函式庫

由於 Python 各個版本的用戶居多2.7~3.9，因此許多函式庫都還是以同步的方式去寫，才能向下相容，這邊我就使用 [line-bot-sdk-python](https://github.com/line/line-bot-sdk-python) 作為本次引入的範例


decode('UTF-8')
# 結論
