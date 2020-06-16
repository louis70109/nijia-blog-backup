---
title:
  "[object Object]": null
categories: 學習紀錄
tags:
---

![](https://i.imgur.com/0QAGPDc.png)

# 前言

曾經有一次在趕專案時寫了一段

<!-- more -->

# 介紹

接下來以我寫的 LINE Notify SDK - [Lotify](https://github.com/louis70109/lotify) 裡的[ code 做範例](https://github.com/louis70109/lotify/blob/master/lotify/client.py#L9)，如下：

```python
class Client:
    CLIENT_ID = os.environ.get('LINE_NOTIFY_CLIENT_ID')
    CLIENT_SECRET = os.environ.get('LINE_NOTIFY_CLIENT_SECRET')
    REDIRECT_URI = os.environ.get('LINE_NOTIFY_REDIRECT_URI')

    def __init__(self,
                 client_id=None,
                 client_secret=None,
                 redirect_uri=None):
        self.client_id = client_id or self.CLIENT_ID
        self.client_secret = client_secret or self.CLIENT_SECRET
        self.redirect_uri = redirect_uri or self.REDIRECT_URI
```

> 為了方便說明先刪除一些 code

在 Class 宣告完後會看到 CLIENT_ID、CLIENT_SECRET、REDIRECT_URI 這三個參數，在這層的變數就是 `"Class Level"`，而在 \_\_init\_\_ 下面三個變數 self.client_id、self.client_secret、self.redirect_url 就是待會會提到的 `"Instance Level"`。

## Class Level

CLIENT_ID、CLIENT_SECRET、REDIRECT_URI 這三個參數是被所有有初始化 Client 的 Instances 使用，也就是說當數值改變時其他的 Instance 裡的參數也會跟著改變，在這層操作參數時要特別小心，因為只要改動到值是大家一起改，所以說若有一個地方給錯就其他都會一起錯。

## Instance Level

# 範例

製作一個 Example 的類別，包含著 `class_variable` 以及 `instance_variable` 兩個變數，其中 `instance_variable` 首次附值若初始化沒定義 instance_variable 的話則為 class_variable 的值 `123`：

```python
class Example:
     class_variable = 123
     def __init__(self, instance_variable=None):
         self.instance_variable = instance_variable or type(self).class_variable
```

接著使用範例來實驗：

```
s1 = Example()
s2 = Example(456)

s1.class_variable     # 123
s1.instance_variable  # 123
s2.class_variable     # 123
s2.instance_variable  # 456

Example.class_variable = "I am CLASS !!"

s1.class_variable     # 'I am CLASS !!'
s1.instance_variable  # 123
s2.class_variable     # 'I am CLASS !!'
s2.instance_variable  # 456
```

# 結論
