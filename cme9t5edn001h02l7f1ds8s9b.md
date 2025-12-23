---
title: "#53 CSS Animation"
datePublished: Wed Aug 13 2025 10:08:39 GMT+0000 (Coordinated Universal Time)
cuid: cme9t5edn001h02l7f1ds8s9b
slug: css-animation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766490100467/4939b838-48ff-4ac8-91fc-45288b961ab0.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766490105519/e13025a6-1e5b-4905-8779-11344d90a519.png
tags: css3, css, animation, css-animation, web-animation

---

在網頁設計中，**CSS 動畫** 可以讓你的網站更具互動性和吸引力。過去，我們可能需要透過 JavaScript 才能實現動畫效果，但隨著 CSS3 的發展，現在只需要簡單的 CSS 就能輕鬆實現各種動畫效果！

這篇文章將帶你了解 CSS Animation 的基本語法，並示範如何讓元素進行簡單的動態變化。

---

#### 1\. 什麼是 CSS Animation？

CSS Animation 是一組用來控制 HTML 元素在特定時間內進行動態變化的屬性。透過它，你可以讓元素的位置、大小、顏色等屬性在頁面載入或事件觸發時自動變化。

CSS Animation 通常包含兩個核心屬性：

* `@keyframes`：定義動畫的關鍵幀（keyframe），即動畫從哪裡開始，怎麼變化，以及怎麼結束。
    
* `animation`：將 `@keyframes` 作用於元素，並控制動畫的執行方式，例如時長、循環次數等。
    

#### 2\. 基本語法

首先，我們先來看一個簡單的範例，讓一個方塊隨著動畫從紅色變成藍色：

```css
/* 定義動畫關鍵幀 */
@keyframes changeColor {
  0% {
    background-color: red;
  }
  100% {
    background-color: blue;
  }
}

/* 套用動畫至元素 */
.box {
  width: 100px;
  height: 100px;
  background-color: red;
  animation: changeColor 2s ease-in-out;
}
```

在這個範例中，`@keyframes` 定義了從 0% 到 100% 的變化，從紅色變到藍色。我們接著透過 `animation` 屬性，將這個動畫套用到 `.box` 元素上，並讓這個變化在 2 秒內發生。

#### 3\. `@keyframes` 詳解

`@keyframes` 是動畫的基礎，負責定義動畫每一個時間點的狀態。你可以用百分比表示動畫進行到特定階段時，元素應該是什麼狀態：

```css
@keyframes example {
  0% {
    transform: translateX(0);
  }
  50% {
    transform: translateX(100px);
  }
  100% {
    transform: translateX(0);
  }
}
```

這個範例中，元素會先移動 100 像素，然後再回到原位。我們將其應用到元素上，並調整一些其他的動畫屬性：

```css
.box {
  animation: example 3s infinite;
}
```

這裡的 `3s` 表示動畫持續時間為 3 秒，而 `infinite` 則表示動畫會無限次循環。

#### 4\. 常用的 `animation` 屬性

除了 `animation` 屬性之外，還有一些相關的屬性可以進一步控制動畫的效果：

* `animation-duration`：動畫持續的時間。
    
* `animation-timing-function`：動畫的速度曲線，如 `linear`（均勻速度）、`ease`（緩入緩出）、`ease-in`（緩入）、`ease-out`（緩出）。
    
* `animation-delay`：動畫開始前的延遲時間。
    
* `animation-iteration-count`：動畫播放的次數，可以是數字或 `infinite`。
    
* `animation-direction`：動畫的方向，可以是 `normal`（正常播放）、`reverse`（反向播放）、`alternate`（正反交替播放）。
    

#### 5\. 實際範例：彈跳效果

接下來我們來做一個彈跳動畫，模擬一個方塊上下跳動的效果：

```css
@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-50px);
  }
}

.box {
  width: 100px;
  height: 100px;
  background-color: orange;
  animation: bounce 1s ease infinite;
}
```

在這個範例中，我們透過 `@keyframes bounce` 讓方塊上下移動，並將動畫時間設為 1 秒，並且讓它無限次循環，呈現持續跳動的效果。

#### 6\. 小結

CSS Animation 是讓你的網頁更具吸引力的重要工具。透過 `@keyframes` 定義動畫過程，再使用 `animation` 屬性將其應用到元素上，你可以輕鬆實現動態效果。掌握這些技巧後，你可以創造出更豐富的視覺體驗，讓使用者對你設計的網站印象深刻！

---

#### 7\. 練習時間

試試看自己創造一個動畫吧！可以從簡單的顏色變化開始，然後試著加入移動、旋轉、縮放等效果，挑戰一下自己的創意！

---

希望這篇教學文章對你有所幫助！有任何問題，歡迎留言討論。

---

0% 和 100% 可以用逗號寫在一起

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720589119637/3a0f7bfb-50ac-494c-883f-d53e086d5a90.png align="center")

* 除了 infinity 也可以寫次數(數字)
    
* 可使用 reverse 共用一個 keyframes，做成兩種不同的動畫
    
* 可以用逗號跑兩個 keyframes，但會有優先順序，也可以包兩層以上做
    

CSS matrix()???

animation-timeline: scroll()