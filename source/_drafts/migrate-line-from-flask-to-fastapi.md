---
title: 【標題】題目
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

<!-- more -->

list workflow https://docs.github.com/en/rest/reference/actions#list-repository-workflows

# Query Parameter

一般在定義 GET API 時都會先確認好近來的參數是什麼([官網](https://fastapi.tiangolo.com/tutorial/query-params/))，

```python
@router.get("/liff/share", response_class=HTMLResponse)
async def read_item(request: Request):
    print(request.query_params['liff.state'])
    ...
```

# 結論
