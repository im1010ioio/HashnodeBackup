---
title: "#62 使用 CSS overflow 自訂捲動範圍"
datePublished: Wed Aug 13 2025 11:39:22 GMT+0000 (Coordinated Universal Time)
cuid: cme9we2ql000q02l54kxb9orz
slug: css-overflow
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766575139449/6b0bda74-8cb8-4e18-b131-e942fddd3720.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766575144179/cf770c0f-d68a-4f12-a86a-258815d3ecac.png
tags: css3, css, overflow, overflow-property, css-scroll, scrollable

---

當我們在進行網頁設計時，常常要處理當內容超出容器範圍時的情況，這就是使用到 `overflow` 屬性的時候了！`overflow` 最常用在自訂捲動範圍，尤其是系統後台網頁常見的雙欄設計上。

---

### `overflow` 基本語法

當一個 HTML 元素的內容超出它的容器大小時，預設情況下，這些超出的內容可能會溢出容器。`overflow` 屬性則可以幫助我們控制這些「溢出」內容該如何處理。

語法如下：

```css
overflow: visible | hidden | scroll | auto;
```

* **visible**（預設值）：內容會超出容器，且完全顯示出來，不會被遮蓋。
    
* **hidden**：超出的內容會被隱藏，僅顯示容器範圍內的內容。
    
* **scroll**：即使內容沒有超出容器範圍，容器也會顯示捲軸，允許用戶捲動瀏覽。
    
* **auto**：當內容超出容器範圍時，容器才會顯示捲軸。
    

---

### 控制 X 軸和 Y 軸

有時候，我們只需要控制水平或垂直方向的 `overflow`，這時可以使用 `overflow-x` 和 `overflow-y` 屬性來分別控制。

```css
/* 水平溢出時隱藏，垂直顯示捲軸 */
overflow-x: hidden;
overflow-y: scroll;
```

---

### DEMO 1

以下的 DEMO，使用了 `overflow: auto;` ，能讓放了許多文字的區塊滾動：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728662787409/3a4599f6-18d8-45d0-b13a-260bd749e955.gif align="center")

> DEMO: [CSS overflow auto](https://codepen.io/im1010ioio/pen/gOVgMgV)

---

### DEMO 2

修改前幾天的 DEMO，加上 `overflow: auto` ，這樣當內容超出畫面時，就可以滾動了！

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728663635322/33dae899-c9d8-44b8-9a19-d8d0192c6309.gif align="center")

> DEMO: [Pure CSS toggle aside + overflow auto](https://codepen.io/im1010ioio/pen/RwXKRyX)

---

### iOS Safari 的陷阱

我們在第 #24 篇時提過好幾個 iOS Safari 的陷阱，其中一個就和 `overflow` 自訂捲動範圍有關，請大家在切版手機網頁時請多注意喔：

> 延伸閱讀：[#24 RWD & CSS Media Queries & iOS Safari 上的經驗談](https://ithelp.ithome.com.tw/articles/10337429)
> 
> 我們有時候會使用 `overflow: scroll/auto;` 來製作 body 內部客製的可滾動區域，然後整個網頁的 `<body>` 設為 `overflow: hidden;`。但是，這種做法在 iPhone Safari 上時常會怪怪的，導致整個網頁無法滑動。
> 
> 深究其原因，似乎是 Safari 在解析網頁時的渲染前後順序問題：「子元素的高度如果沒有在 ScrollView 建立之前確定，就不會觸發內部滑動，而會觸發外部滑動。」
> 
> 我的解法是在 CSS 規劃時，就盡量滾動 `<body>`，沒有任何 `overflow: hidden;` 設定在 `<body>` 上，給大家參考。