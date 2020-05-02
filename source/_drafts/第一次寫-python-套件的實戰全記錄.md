---
title:
  "[object Object]": null
tags:
---

![](https://i.imgur.com/Rms5ZNG.png)

# 前言

對於 LINE Notify 其實早早就一直有在使用，不管是 server 健康檢查、空汙通知、直播主開台通知...等，都一直使用著，也是因為一直在用時有個困擾，就是每次都要找 [API 文件](https://notify-bot.line.me/doc/en/)並且看對應的參數...這在開發流程上浪費了不少時間，也因為到 Pypi 套件庫裡找 LINE Notify 相關套件時大多都只有推送功能，幾乎沒有對於認證流程的操作的 function ，文件也不齊全，在此同時也看到卡米哥的 GitHub 在此時上傳了一個 [Notify SDK](https://github.com/etrex/lotify)，畢竟我對 Ruby 還不算陌生，就直接參考卡米哥的架構並加上單元測試來完成本篇要介紹的 - [Lotify](https://github.com/louis70109/lotify)

<!-- more -->

# [Lotify](https://github.com/louis70109/line-notify) 介紹

先簡單列幾點以下會提到的部分：

1. tests/ 是 mock 住 server 而不是 mock 請求函式
2. requirements 分層用意
3. SDK function init 設計用途

使用 flask 框架的範例程式碼 - [flask-line-notify](https://github.com/louis70109/flask-line-notify)

這是 Lotify 的展開圖:
![目錄架構](https://i.imgur.com/uXo7jA8.png)

架構上參考許多 [line-bot-sdk-python](https://github.com/line/line-bot-sdk-python) 的使用方式，包括 `tests` 的寫法、`Travis`、`requirements`的環境分層、`tox`支援多版本的寫法...

> 因為 python 有多版本支援的問題，雖然最後我沒支援到 2.7，不過寫法上其實已經可以支援，只差設定檔搞不清楚是哪邊的問題，這邊的優先權就排後面點～

## 測試是如何 mock LINE server

```python
import responses

@responses.activate
def test_get_access_token(self):
    responses.add(
        responses.POST,
        '{url}/oauth/token'.format(url=self.bot_origin),
        json={ 'access_token': self.token },
        status=200
    )

    result = self.tested.get_access_token('foo')
    request = responses.calls[0]
    response = json.loads(request.response.content.decode())
    self.assertEqual('POST', request.request.method)
    self.assertEqual(self.token, response.get('access_token'))
    self.assertEqual(result, response.get('access_token'))
```

## Client 設計原則

<script src="https://gist.github.com/louis70109/e39302e76c66a450991fb2aea5838a35.js"></script>

### 預設環境變數

有設定三個是可以讓使用者只要在`環境變數`中引入這三個參數，SDK 預設就會去載入至 Instance 中，而使用者也可以手動輸入，原因是因為可能這個 key 被占走抑或是不想寫出來被看到，而在`初始化`階段才引入也是可行的。

### 網址設計

因為 Notify 有分 Oauth 以及 push 兩種不同 api 網址，這邊我設計是參考 bottender 其中一個設計原理，為了滿足使用者想做負載測試時可以切回自己的 api，而不需要對著第三方服務去做壓力測試，一方面可以更正確的測試問題，二方面不寫死也較有彈性。

## Setup

```python

import re
from os import path

from setuptools import setup, find_packages

version_file = path.join(
    path.dirname(__file__),
    'line-notify',
    '__version__.py'
)
with open(version_file, 'r') as fp:
    m = re.search(
        r"^__version__ = ['\"]([^'\"]*)['\"]",
        fp.read(),
        re.M
    )
    version = m.groups(1)[0]


setup(
    name='line-notify-nijia.lin',
    version=version,
    description='Using Line Notify more easily',
    url='https://github.com/louis70109/line-notify',
    author='NiJia Lin',
    long_description=open('README.rst').read().strip(),
    long_description_content_type="text/x-rst",
    author_email='louis70109@gmail.com',
    keywords='line notify python',
    license='MIT',
    platforms='any',
    packages=find_packages(exclude=['tests']),
    install_requires=[
        'requests==2.22.0'
    ],
    python_requires='>=2.7, !=3.0.*, !=3.1.*, !=3.2.*, !=3.3.*',
    zip_safe=False,
    project_urls={
        'Bug Reports': 'https://github.com/louis70109/line-notify/issues',
        'Source': 'https://github.com/louis70109/line-notify',
    },
    classifiers=[
        'License :: OSI Approved :: MIT License',
        'Programming Language :: Python :: 3.5',
        'Programming Language :: Python :: 3.6',
        'Programming Language :: Python :: 3.7',
        'Programming Language :: Python :: 3.8'
    ],
)
```

### 奇怪的地方

[官方](https://packaging.python.org/tutorials/packaging-projects/#creating-setup-py)說 name 後面要接 USERNAME，目前測起來是也要這樣子，還需要找一下要怎麼去除那個名字。

## Markdown to RST

使用這個 [Converter](https://cloudconvert.com/md-to-rst) 把寫好的 markdown 轉成 RST 的格式

## upload package to pypi

check -r -s [references](https://stackoverflow.com/questions/46682793/how-to-ensure-that-readme-rst-is-valid/46687472#46687472)

```shell script
python setup.py check -r -s  #  lint your RST
python setup.py bdist_wheel  # build dist/
python -m twine check dist/* # check and lint your static files
python setup.py sdist upload -r pypi # upload package
```

# 結論
