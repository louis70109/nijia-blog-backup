---
title: TypeScript 學習筆記
tags: ["TypeScript"]
categories: TypeScript
---

## 可選屬性

```js
interface Person{
  name: string;
  age?: number;
}

let tom: Person{
  name: "Tom"
} // true
```

加個`?`可以讓這個參數可有可無，以我 Ruby 的理解來說應該會像是這樣：

```ruby
Person.first&.name
```

Ruby 當中有 `&.` 的一個判斷運算子，他主要是來自於 try 這個函式，詳細內容可以[參考](http://mitrev.net/ruby/2015/11/13/the-operator-in-ruby/)。

### 小結

透過這些運算符號讓我們在定義某些東西或是要判斷可以更加有彈性，而不會在寫程式時被介面的邏輯卡住而無法繼續往下寫。

## declare

https://ithelp.ithome.com.tw/articles/10224070
