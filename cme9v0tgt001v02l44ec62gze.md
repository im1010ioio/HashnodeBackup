---
title: "#57 CSS @property：變數的再進化！輕易製作純 CSS 漸層動畫、圓餅圖動畫"
datePublished: Wed Aug 13 2025 11:01:04 GMT+0000 (Coordinated Universal Time)
cuid: cme9v0tgt001v02l44ec62gze
slug: css-houdini-property
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766491860511/9a663172-9433-4965-954a-b0cfd3ddccd5.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766491849285/37991b0c-6eb3-4442-96d8-a57ea5d7e9e2.png
tags: css3, css, css-animation, houdini, property, css-houdini

---

CSS 除了變數外，還可以額外新增自訂屬性—— `@property`，現已全面支援了！

`@property` 規則是 API 的 [CSS Houdini](https://developer.mozilla.org/zh-CN/docs/Web/API/Houdini_APIs) 系列的一部分：

> 「Houdini」這個詞源自美國著名的魔術師哈利・胡迪尼（Harry Houdini）。胡迪尼以其驚人的逃脫術和幻術聞名於世，他可以從看似不可能的困境中神奇地脫身，因此他的名字常被用來形容某種神秘或不可思議的能力。
> 
> 在 CSS Houdini 的背景下，「Houdini」暗指這個 API 集合能讓開發者做出一些以前在 CSS 中無法實現的效果，就像魔術一樣擴張和自訂 CSS 的行為，使你可以「逃脫」傳統 CSS 的限制。這名字隱喻了開發者可以用 Houdini API 自定義並控制 CSS，創造出更神奇和複雜的效果。

那麼 `@property` 到底能做到什麼以前做不到的事呢？讓我們來看看。

---

## 一、基本用法

### 1\. 基本語法

還記得 CSS 變數如何使用嗎？其實 `@property` 與它類似。

> 延伸閱讀：[#09 原生的 CSS 變數，基本與進階應用](https://ithelp.ithome.com.tw/articles/10327133)

首先，我們需要定義一組資訊，其中要包含：

* `syntax` **類型**：如 `<color>`、`<length>`、`<angle>` 等等（[查看全部可用的值](https://developer.mozilla.org/zh-CN/docs/Web/CSS/@property/syntax)）；
    
* `inherits` **是否要繼承父層**，為 `true` 或 `false`（布林值）；
    
* `initial-value` **實際的數值。**
    

例如，以下的 code 定義了一組顏色資訊：

```css
@property --myColor {
    syntax: '<color>';
    inherits: false;
    initial-value: pink;
}
```

接著，使用方法就和變數一樣，使用 `var()` 使用這組資訊；並且，在已經使用過 `@property` 的情況下，可以直接改變 `@property` 的數值：

```css
p {
    color: var(--myColor);
    &:hover {
        --myColor: blue;
    }
}
```

### 2\. 這改變了什麼呢？

過去我們在介紹 CSS `transition` 動畫時，有提到過：「`transition` 是兩個狀態之間的過渡效果，但這個過渡效果只適用於『**可以計算的數值型屬性**』。」

所以在前幾篇繪製漸層時，因為漸層是屬於 `background-image` 屬性，`image` 不算是「數值」，所以無法從 `image` 過渡動畫到另一個 `image` 上。

但是有了 `@property` 後，我們可以就可以把漸層顏色的「數值」使用 `@property` 存放，就繞過了 `background-image` 無法有漸變動畫的規則了。

過去的 CSS 無法做到的事，現在已經可以了。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728315422340/f1896ecf-d038-4edd-8bde-60e64a754217.png align="center")

> [Can I Use](https://caniuse.com/?search=%40property)

---

## 二、DEMO: 漸層動畫

讓我們實際使用 `@property` 製作一個 `transition` 漸層動畫，這邊值得注意的是：`transition` 必須指定是使用哪一個 `@property` ：

```css
@property --color-start {
    syntax: "<color>";
    inherits: false;
    initial-value: rgba(255,182,193,1);
}

body{
    background: linear-gradient(in oklch, var(--color-start), rgba(104,133,244,1));
    transition: 1s --color-start;
    &:hover{
        --color-start: rgba(75,188,213,1);
    }
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728313690836/acf0613a-55f2-4e9c-ba6a-b0b8e1f14d60.gif align="center")

> DEMO: [CSS Gradient Transition with @property](https://codepen.io/im1010ioio/pen/NWQRWQM)

---

## 三、DEMO: 圓餅圖動畫

有了圓錐漸層 `conic-gradient` 後，繪製圓餅圖變得很輕易，首先我們先畫出一個圓餅圖：

```css
div{
    background: 
        conic-gradient(from 0turn at center,
                       #73a4df 0.25turn, #eee 0);
    width: 200px;
    height: 200px;
    border-radius: 50%;
}
```

這邊用了個漸層小技巧：把第二個顏色的位置設為 0，瀏覽器會把它的位置調整成前面顏色停止點的位置。

> 延伸閱讀：
> 
> * [#37 CSS 基本漸層：線性/放射/圓錐漸層 (CSS linear-gradient, radial-gradient, conic-gradient)](https://ithelp.ithome.com.tw/articles/10352603)
>     
> * [#39 CSS 幾何背景：條紋、格子、點點、棋盤格子背景 (CSS background)](https://ithelp.ithome.com.tw/articles/10354663)
>     

然後，我們用變數、`@property` 換掉裡面的顏色、角度，就可以製作出圓餅圖動畫了：

```css
:root{
    --main-color: #73a4df;
    --bg-color: #eee;
}

@property --percentage {
    syntax: "<angle>";
    inherits: false;
    initial-value: 0turn;
}

@keyframes animate-percentage {
    from {
        --percentage: 0turn;
    }
    to {
        --percentage: 0.8turn;
    }
}

div{
    background: 
        conic-gradient(from 0turn at center,
                       var(--main-color) var(--percentage), var(--bg-color) 0);
    width: 200px;
    height: 200px;
    border-radius: 50%;
    animation: animate-percentage 3s 1 ease-in-out forwards;
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728313677425/249d3ece-85df-4492-bd35-fee39792d29b.gif align="center")

> DEMO: [CSS Pie Charts Animation with @property](https://codepen.io/im1010ioio/pen/zYgByOO)

過去，用 CSS 製作圓餅圖動畫很麻煩，而且動畫行進的速率只能為 `linear`，現在想要 `ease`、`ease-in` 等等都可以了，不僅彈性更高，而且輕輕鬆鬆就做到了。

---

> **延伸閱讀：**
> 
> * [CSS @property，讓不可能變可能 | IT人](https://iter01.com/594993.html)
>     
> * [@property：現在支援通用瀏覽器的新一代 CSS 變數](https://web.dev/blog/at-property-baseline?hl=zh-tw)
>     
> * [【Day28】改變CSS的遊戲規則 - 自定義屬性CSS @property](https://ithelp.ithome.com.tw/articles/10335660)
>