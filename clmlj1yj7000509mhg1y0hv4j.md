---
title: "#00 參賽前言 / 文章目錄 | Super Easy CSS"
datePublished: Sat Sep 16 2023 04:27:31 GMT+0000 (Coordinated Universal Time)
cuid: clmlj1yj7000509mhg1y0hv4j
slug: super-easy-css-contents
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694417958400/77ae1fab-6b90-47e7-92ea-12dd57311262.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691479658522/b689fe48-2289-4109-b424-110ac62728dd.png
tags: css3, css, html, html5

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683705571380/284e9ba0-04c8-43bd-a093-784c330bd862.png align="right")

## 參賽前言

本系列文章目標是學習 CSS 基本知識，並且研究 The State of CSS 中值得令人期待新屬性，讓想要學習 CSS 的人也能一起學到新知識，不用再零零散散地去爬文搜尋。此外，還會提及一些前端基本知識、版本控制、開發經驗等必要概念，讓新手對於前端開發有全面的認識。

---

### 這 30 天我想做什麼？

這 30 天我的方向主要是：

* **自我挑戰：研究新穎的 CSS 屬性**
    
    每年都有的 [The State of CSS](https://stateofcss.com/) 統計，討論了許多新提出的 CSS 屬性（例如：`color-mix()`、`:has`、`max()`、`min()`、`clamp()`、`container query` 等等），我覺得很有趣，卻未曾實際深究，我想趁此機會加以了解。
    
* **作為筆記：供自己日後參考**  
    延續上一點，將這些新學到的東西統整起來。再來是，過去在學習的時候有些容易混淆的部分，我希望也能藉此機會一起釐清。
    
* #### 作為紀念：留下些什麼吧！
    
    工作了多年，我想留下個紀念，統整這些我所學到的知識，並且透過分享，在網路上留下一些痕跡。
    
* **幫助他人：讓人跨出學習網頁的第一步**  
    除了統整好基礎前端與 CSS 知識外，並且上述所說未來能變得實用，且目前瀏覽器支援度還不差的新屬性（支援的瀏覽器&gt;=3），一併整理在所有基礎知識中。這樣想學的人也能一起學到新知識，不用再零零散散地去爬文搜尋。
    

本系列文章會以 CSS 為主，HTML、Git 等網頁開發概念為輔。

---

### 這個主題適合誰閱讀？

* 主要目標族群是完全小白新手。無論你是想要學習網頁成為前端工程師，或是想要了解網頁如何運作的 PM 或設計師，都很適合。
    
    我會介紹基礎的前端知識，因為我發現有時在開發上，PM、設計師或是業主，容易因為不懂前端或網頁上的 Domain Knowledge，造成上工作上的溝通成本或重工，而這往往只是缺乏了幾個簡單的概念。
    
* 次要則是已經會了，但是想了解 CSS 新屬性的人。
    

就讓我們開始這 30 天的前端基礎之旅吧！

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683705560504/15822e35-b6be-4cbc-b2e7-b7b5f55a8555.png align="center")

## 文章目錄

（這 30 天內持續更新中）

### 基礎知識 / 共用觀念

* `#00` 參賽前言 / 文章目錄
    
* `#01` [網頁的基本名詞：UI/UX？切版&切圖？前端&後端？靜態&動態？RWD or Mobile First？](https://im1010ioio.hashnode.dev/glossary-of-web-development)
    
* `#02` [關於各家瀏覽器，前端必備的小知識：支援度、市佔率、CSS 實驗語法 -webkit-, -moz-... PostCSS Autoprefixer](https://im1010ioio.hashnode.dev/about-browsers)
    
* `#03` [人在江湖，版控要有：了解 GIT / GitHub / GitLab / Git Flow](https://im1010ioio.hashnode.dev/git-github-gitlab-git-flow)
    
* `#04` [GIT 實戰練習：GitHub Desktop、GitHub Page 基礎教學](https://im1010ioio.hashnode.dev/git-github-gitpage-practice)
    
* `#05` [HTML 基礎語法，常用 HTML Tag 總整理](https://im1010ioio.hashnode.dev/html-basics)
    
* `#06` [寫一份簡單的 HTML](https://im1010ioio.hashnode.dev/html-strugtrue)
    
* `#06補充` [網頁的根、絕對路徑、相對路徑，那些關於路徑的小知識](https://im1010ioio.hashnode.dev/html-file-paths)
    
* `#07` [CSS 基本語法 & 權重介紹](https://im1010ioio.hashnode.dev/css-basics)
    
* `#08` [CSS 選擇器總整理！id、class、:nth-child(n)、:not、:where、:is、:has 都難不倒我](https://im1010ioio.hashnode.dev/css-selectors)
    
* `#09` [原生的 CSS 變數](https://im1010ioio.hashnode.dev/css-variables)
    
* `#10` [原生的 CSS 巢狀 (CSS Nesting) 終於支援啦！](https://im1010ioio.hashnode.dev/pure-css-nesting)
    
* `#11` 開始寫 CSS 或程式必須知道的幾個原則：DRY & KISS & YAGNI
    
* `#12` CSS命名建議：OOCSS、SMACSS、BEM、RSCSS
    

### 版面編排

* `#13` CSS Box 概念：content-box、border-box、間距(padding margin)、aspect-ratio
    
* `#14` 網頁使用的單位大解析：px、rem、em、%、vw、vh (dvh, lvh, svh)、vmin、vmax
    
* `#15` CSS 數學函式 max、min、clamp、calc
    
* `#16` CSS Display：block、inline、inline-block（Flow流式布局介紹）
    
* `#17` CSS Display：FLEX
    
* `#18` CSS Display：Grid
    
* `#19` CSS Position
    
* `#20` CSS 邏輯屬性 Logical properties
    

### 文字

* 敬請期待
    

### 顏色

* 敬請期待
    

### 形狀 & 圖形

* 敬請期待
    

### 互動

* 敬請期待
    

### 響應式 RWD

* 敬請期待
    

### SEO 與其他實用工具

* 敬請期待
    

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")