---
title:
  "[object Object]": null
categories: 學習紀錄
tags:
---

# 前言

以前在寫 Rails 時管理資料庫都是透過 ActiveRecord 來幫我處理 Database Schema 的事情，隨著年紀的增長以及語言的切換後，開始要自己手動建立 Database，只是過往都是憑著自己的印象去建立表格，抑或是遷移(migration)時開兩個視窗一個一個比對，但這樣的舉動實在是很費時。

之後被教了 DDL 這個方法，讓我對於這個費時的工作有了新的見解，以下就介紹我學到的部分囉！

# What is DDL?

<!-- more -->

資料定義語言（Data Definition Language，DDL）屬於 DBMS 語言的一種，用於定義 DB schemas，且 DBMS 內有 DDL 編譯器 (complier) 能夠處理 DDL，由 CREATE、ALTER 與 DROP 三個語法所組成。

> 參考來自 [wiki](https://zh.wikipedia.org/wiki/%E8%B3%87%E6%96%99%E5%AE%9A%E7%BE%A9%E8%AA%9E%E8%A8%80)

# 操作環境

- MacOS
- Docker
- PgAdmin
- PostgreSQL
- [參考範例](https://github.com/louis70109/postgresql-pgadmin)

# 介紹

## 建立範例 Table

首先先到 pgadmin 中，建立一個新的 Table
![](https://i.imgur.com/5lq8eip.png)

建立一個範例的 Item table
![](https://i.imgur.com/NvDIicH.png)

再來是 Book table
![](https://i.imgur.com/qdmIQCE.png)

簡單加個 Item 的外鍵 (Foreign Key)
![](https://i.imgur.com/XoQai7x.png)

## 找 DDL

接著就要開始找 DDL 啦！透過 `CREATE SCRIPT` 來找我們要的 DDL 腳本
![](https://i.imgur.com/kYoWCTgl.png)

儲存 `Item` & `Book` 的內容 (存成`.sql` 或是任一文字檔案)
![](https://i.imgur.com/5Br3HkM.png)

### 注意事項

在前面的範例中 id 使用 流水號(`serial`)，它存在於 `Sequences` 的地方，要記得將它一併帶出後複製起來：
![](https://i.imgur.com/d9jRfBil.png)

否則會遇到以下問題:

```
ERROR:  relation "Book_id_seq" does not exist
SQL state: 42P01
```

---

## 將範例 Item & Book 刪除

接著就把它刪除來做測試吧！
![](https://i.imgur.com/phQ8AYvl.png)
![](https://i.imgur.com/F6kVuYwl.png)

## 將 Table 放回去

在 `Public` 這個下拉式選單中`右鍵`就會看到 `CREATE SCRIPT` 的選項
![](https://i.imgur.com/BS6wNXxl.png)

把剛剛的 DDL 複製過來，記得要先讓 Sequence 先進去接著才是 Table

抑或是可以將兩個組裝在一起，先把 Sequence 放在前面，如下:

```
-- SEQUENCE: public.Item_id_seq

CREATE SEQUENCE public."Item_id_seq"
    INCREMENT 1
    START 1
    MINVALUE 1
    MAXVALUE 2147483647
    CACHE 1;

ALTER SEQUENCE public."Item_id_seq"
    OWNER TO postgres;


-- Table: public.Item

CREATE TABLE public."Item"
(
    id integer NOT NULL DEFAULT nextval('"Item_id_seq1"'::regclass),
    title character varying(100) COLLATE pg_catalog."default",
    description text COLLATE pg_catalog."default",
    CONSTRAINT "Item_pkey" PRIMARY KEY (id)
)
WITH (
    OIDS = FALSE
)
TABLESPACE pg_default;

ALTER TABLE public."Item"
    OWNER to postgres;
```

這樣就能省掉一個步驟並且不用一直記得順序，儲存時也建議這樣儲存避免失誤。

# 結論

在建置初期也許只有一個 staging，但隨著專案規模變大之後就會分 production、develop、beta、QA 等等的環境，而在建置環境時使用 DDL 這樣的功能也能避免部署人員失誤出錯，例如將欄位長度輸入錯(長度 100 -> 199)，當然如果連複製都能錯那就...😅，總之在專案中放入一個 schema 的資料夾放入這些 DDL 在部署到其他環境時能夠更快速處理這部分。
