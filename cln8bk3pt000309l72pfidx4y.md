---
title: "#16 CSS 數學函式 calc()、max()、min()、clamp()"
datePublished: Mon Oct 02 2023 03:16:22 GMT+0000 (Coordinated Universal Time)
cuid: cln8bk3pt000309l72pfidx4y
slug: css-calc-max-min-clamp
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1764906058341/357c0621-da92-4a22-8424-71a853e2a836.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1764906067503/d445f0fb-a4ae-4676-bf2b-ce47eb8b586e.png
tags: css3, css

---

CSS 的數值可以做簡單的運算，今天我們要介紹 CSS 的數學函式，數學函式可以讓你在設計網頁時更靈活操控元素的尺寸和位置。

實用的 CSS 數學函式共用四個：`calc()`、`max()`、`min()`、和 `clamp()`。數學函式另外還有很多種，例如三角函數等等，不過還是以這四個最實用，其他的有空我再去研究。

> #### ↓ 今日學習重點 ↓
> 
> * 了解四個實用的 CSS 數學函式：`calc()`、`max()`、`min()`、和 `clamp()`
>     

---

## 1\. calc()

`calc()` 可以做基本數學運算，例如加法、減法、乘法和除法。而且，它可以組合不同的單位和數值，非常好用！我們之前在講解變數時，其實已經有偷跑用過了。語法如下：

```css
/* 屬性: calc(加減乘除算式); */
div {
    width: calc(50% - 20px);
}
```

## 2\. max()

`max()` 定義了最大值，可以寫多個數值，使用逗號隔開，用這個方法可以確定內容至少要多大。在下面例子中，div 的寬度設為 300px 或父層寬度的 50％，以較大的那個值為準。

```css
/* 屬性: max(數值, 數值); */
div {
    width: max(300px, 50%);
}

/* 等同於：
div {
    width: 50%;
    min-width: 300px;
}
*/
```

## 3\. min 函式

`min()` 與 `max()` 相反，它定義了最小值，用這個方法可以確定內容至少要多小。在下面例子中，div 的寬度設為 100px 或父層高度的 30％，以較小的那個值為準。

```css
/* 屬性: min(數值, 數值); */
div {
    height: min(100px, 30%);
}

/* 等同於：
div {
    height: 30%;
    max-height: 300px;
}
*/
```

## 4\. clamp 函式

`clamp()` 函式結合了 `min()` 與 `max()`，它讓你指定一個範圍，並在這個範圍內自由變化。以下面的例子來說，div 的寬度設為 20vw，但最大不超過 400px，最小不小於 20px。

```css
/* 屬性: clamp(最小值, 中間值, 最大值); */
div {
    width: clamp(20px, 20vw, 400px);
}

/* 等同於：
div {
    width: 20vw;
    min-width: 20px;
    max-width: 400px;
}
*/
```

---

以上的例子都是以寬高為主，但是其實這些數學函式也可以應用在其他 CSS 屬性上。

CSS 的寬與高有最大、最小屬性可以替代（`max-width`、`min-width`...），但是其他屬性並沒有，例如：`font-size` 就沒有辦法設定所謂的最大最小值，過去可能要寫好幾段 `@media` 設定，但現在一行就能搞定了。

有了數學函式後，我們的 CSS 可以寫得更靈活，大家也來試試看吧！  
希望這篇文章對你有所幫助！

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")