---
title: "#14 Reset CSS！用 Reset.css 或 Normalize.css 變回你該有的樣子"
datePublished: Sat Sep 30 2023 05:34:01 GMT+0000 (Coordinated Universal Time)
cuid: cln5llepz000b09jr4gtp69ww
slug: reset-css
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1764831462030/690494ef-b064-4ecb-a3f1-7bd9f0654fe6.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1764831472797/5af4f1c1-6f61-4f71-b6f9-45b0f6b1fa98.png
tags: css3, css

---

> #### ↓ 今日學習重點 ↓
> 
> * 了解 CSS 為什麼需要 Reset？
>     
> * 了解 CSS 有哪些 Reset 的方法？
>     

## CSS 為什麼需要 Reset？

不同的瀏覽器會有不同的預設樣式，可能包含字體大小、邊距、填充、行高等等。

這會導致網頁的外觀不一致，所以通常我們在最一開始開發時，就會需要 Reset CSS。將所有瀏覽器的預設樣式歸零，從頭開始設計自己的網頁樣式，就不用擔心寫出來的東西受到預設風格影響。

---

## 寫個簡單粗暴的 Reset

如果今天只是要簡單 Demo 或練習排版，我們可以快速寫這段 Reset 樣式。

```css
*, *::before, *::after {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
```

只不過這樣寫當然還不夠周全，通常會推薦使用下面受大家受歡迎的 CSS Reset。

---

## 常見的 CSS Reset

最受歡迎的選擇 Reset 有以下兩種，只要載下來，在 HTML 中引用就可以了。

CSS Reset 要引用在最開頭，而自己寫的 CSS 則是放在後面，因為它的目的就是要在「一開始」幫你調整好各瀏覽器之間的差異。

### 1\. Eric Meyer's Reset CSS

> 連結：[CSS Tools: Reset CSS](https://meyerweb.com/eric/tools/css/reset/)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695724446520/2c50a4c1-99f9-4a42-ab93-bac813bf6463.png align="center")

這是最早的 CSS Reset 方法之一，是由網頁設計師 Eric Meyer 所寫的。它的目標是將所有 HTML 元素的樣式歸零，把所有 HTML 的樣式都清空了，包含所有外邊距、內邊距、列表樣式等都強制歸零。

---

### 2\. Normalize.css

> 連結：[Normalize.css: Make browsers render all elements more consistently.](http://necolas.github.io/normalize.css/)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695724434661/e5b5aeca-aa8b-48b2-b6d1-fab9aa9e2699.png align="center")

Normalize.css 較上一個完全歸零的概念不太一樣，它的目標是保留有用的預設值，讓開發者不需要針對每一個標籤重新寫樣式，並且統一瀏覽器之間不一致的地方、修正瀏覽器的 Bug。

---

### 小結

Reset.css 與 Normalize.css 各有優缺，兩個目前都很多人使用，可以依據需求擇一使用即可。另外，這兩個在 `box-sizing` 方面，都沒有幫你把所有元素變為 `border-box`，所以這個部分要自己加喔！

---

## 使用框架時

如果你有使用 CSS 框架，框架通常都已經有包含 CSS Reset，例如：Bootstrap 使用的就是 Normalize.css（[Reboot · Bootstrap v5.3](https://getbootstrap.com/docs/5.3/content/reboot/)）；而 Tailwind 使用的是由 Normalize.css 改良的 [modern-normalize](https://github.com/sindresorhus/modern-normalize)（[Preflight - Tailwind CSS](https://tailwindcss.com/docs/preflight)）。

各個框架實際是如何實作 CSS Reset，還需要去詳讀各自的文件。

---

好的，今天就先到這邊了。  
你可以依據需求或個人喜好選擇其中一個 CSS Reset 方法來試試看。

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")