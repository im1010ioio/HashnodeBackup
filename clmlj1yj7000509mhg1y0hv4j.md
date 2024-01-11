---
title: "#00 參賽前言 / 文章目錄 | Super Easy CSS"
datePublished: Sat Sep 16 2023 04:27:31 GMT+0000 (Coordinated Universal Time)
cuid: clmlj1yj7000509mhg1y0hv4j
slug: super-easy-css-contents
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694417958400/77ae1fab-6b90-47e7-92ea-12dd57311262.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691479658522/b689fe48-2289-4109-b424-110ac62728dd.png
tags: css3, css, html, html5

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683705571380/284e9ba0-04c8-43bd-a093-784c330bd862.png align="left")

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

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1683705560504/15822e35-b6be-4cbc-b2e7-b7b5f55a8555.png align="left")

## 文章目錄

（這 30 天內持續更新中）

### 基礎知識 / 共用觀念

* `#00` 參賽前言 / 文章目錄
    
* `#01` [網頁的基本名詞：UI/UX？切版&切圖？前端&後端？靜態&動態？RWD or Mobile First？](https://im1010ioio.hashnode.dev/glossary-of-web-development)
    
* `#02` [關於各家瀏覽器，前端必備的小知識：支援度、市佔率、CSS 實驗語法 -webkit-, -moz-... PostCSS Autoprefixer](https://im1010ioio.hashnode.dev/about-browsers)
    
* `#03` [人在江湖，版控要有：了解 GIT / GitHub / GitLab / Git Flow](https://im1010ioio.hashnode.dev/git-github-gitlab-git-flow)
    
* `#04` [GIT 實戰練習：GitHub Desktop、GitHub Page 基礎教學](https://im1010ioio.hashnode.dev/git-github-gitpage-practice)
    
* `#05` [HTML 基礎語法](https://im1010ioio.hashnode.dev/html-basics)
    
* `#06` [寫一份簡單的 HTML，常用 HTML Tag 總整理](https://im1010ioio.hashnode.dev/html-strugtrue)
    
* `#06補充` [網頁的根、絕對路徑、相對路徑，那些關於路徑的小知識](https://im1010ioio.hashnode.dev/html-file-paths)
    
* `#07` [CSS 基本語法 & 權重介紹](https://im1010ioio.hashnode.dev/css-basics)
    
* `#08` [CSS 選擇器總整理！id、class、:nth-child(n)、:not、:where、:is、:has 都難不倒我](https://im1010ioio.hashnode.dev/css-selectors)
    
* `#09` [原生的 CSS 變數，基本與進階應用](https://im1010ioio.hashnode.dev/css-variables)
    
* `#10` [原生的 CSS 巢狀 (CSS Nesting) 終於支援啦！](https://im1010ioio.hashnode.dev/pure-css-nesting)
    
* `#11` [開始寫 CSS 或程式必須知道的幾個原則：DRY & KISS & YAGNI](https://im1010ioio.hashnode.dev/css-dry-kiss-yagni)
    
* `#12` [CSS 設計方法與命名建議：OOCSS、SMACSS、BEM、RSCSS](https://im1010ioio.hashnode.dev/oocss-smacss-bem-rscss)
    

### 版面編排

* `#13` [CSS 盒子模型 (Box Model)：border-box & content-box](https://im1010ioio.hashnode.dev/css-box-model)
    
* `#14` [Reset CSS！變回你該有的樣子](https://im1010ioio.hashnode.dev/reset-css)
    
* `#15` [網頁使用的單位大解析：px、rem、em、%、vw、vh (dvh, lvh, svh)、vmin、vmax](https://im1010ioio.hashnode.dev/css-units)
    
* `#16` [CSS 數學函式 calc()、max()、min()、clamp()](https://im1010ioio.hashnode.dev/css-calc-max-min-clamp)
    
* `#17` [CSS block、inline、inline-block：網頁排版的御三家](https://im1010ioio.hashnode.dev/css-block-inline-inline-block)
    
* `#18` [CSS Flex：網頁排版的超級寵兒](https://im1010ioio.hashnode.dev/css-flex)
    
* `#19` [CSS Grid：網頁排版的神奇格子，來排個照片牆與雞腿便當吧！](https://im1010ioio.hashnode.dev/css-grid)
    
* `#20` [CSS 內部尺寸 (Intrinsic Sizing)：min-content、max-content、fit-content](https://im1010ioio.hashnode.dev/css-intrinsic-sizing)
    
* `#21` [CSS Position：relative、absolute、fixed、sticky 找到適合的定位](https://im1010ioio.hashnode.dev/css-position)
    
* `#22` [CSS display: contents：製作 JS Components 時的好東西！](https://im1010ioio.hashnode.dev/css-display-contents)
    
* `#23` [CSS 邏輯屬性 Logical properties 與 Writing modes](https://im1010ioio.hashnode.dev/css-logical-properties)
    

### 響應式 RWD

* `#24` [RWD & CSS Media Queries & iOS Safari 上的經驗談](https://im1010ioio.hashnode.dev/css-media-queries)
    
* `#25` [CSS 列印的小技巧：@media print、break-before/after/inside、@page](https://im1010ioio.hashnode.dev/css-media-print)
    
* `#26` [CSS Container Queries 容器查詢：隨著自己變大變小變畫面](https://im1010ioio.hashnode.dev/css-container-queries)
    

### 文字

* `#27` [網頁載入字體、Icon Font 與 CSS font-family、font-weight](https://im1010ioio.hashnode.dev/css-font-family-font-weight)
    
* `#28` [CSS 文字過長、行數過多顯示點點點、文字自動折行、強制換行：white-space、word-break、-webkit-line-clamp 的妙用](https://im1010ioio.hashnode.dev/css-white-space-word-breakline-clamp)
    
* `#29` [CSS 立體字、霓虹字、外框字、漸層字：text-shadow、-webkit-text-stroke、-webkit-background-clip](https://im1010ioio.hashnode.dev/css-text-effect)
    

### 雜記

* `#30` [iT 鐵人賽心路歷程 & 我的寫作方法](https://im1010ioio.hashnode.dev/thoughts-about-30-days)
    

### 顏色

* `#31` [CSS 顏色設定：基本的 hex、rgb()、cmyk()、hsl()、hsb() 、hwb() 與明日之星的 lch()、oklch()](https://im1010ioio.hashnode.dev/css-colors-hex-rgb-hsl-lch-oklch)
    
* `#32` [CSS currentcolor、accent-color 與混色的 color-mix() 讓規劃色彩系統好方便！](https://im1010ioio.hashnode.dev/css-currentcolor-accent-color-color-mix)
    
* `#33` [CSS 切換淺色/深色模式：Media Queries 的 prefers-color-scheme 搭配 CSS 變數](https://im1010ioio.hashnode.dev/css-prefers-color-scheme)
    

### 形狀 & 圖形

* `#34` CSS 讓圖片填滿容器的各種方法，以圓形大頭貼為例：object-fit 與 background-size，搭配 aspect-ratio
    
* `#35` 圖片的 1x, 2x, 3x 是什麼？關於網頁上圖片解析度的處理：HTML srcset、CSS image-set() 與 @media resolution
    
* `#36` CSS Background： (漸層, 偽視差捲動, 格子背景)
    
* `#37` CSS 邊框 Border 與其他製作邊框的小技巧：outline、box-shadow、半透明邊框、內邊框 (css secret)
    
* `#38` 用 CSS 畫各種形狀：三角形、多邊形、雞蛋、水滴、愛心、星芒、金牛角
    
* `#39` CSS Transform
    
* `#40` CSS 特效：濾鏡 filter backdrop-filter/ 混色 blend mode
    

### 互動

* `#41` CSS Transition
    
* `#42` CSS Animation
    
* `#43` 網頁渲染動畫的建議 & will-change 的使用時機
    
* `#44` CSS Overflow 及捲軸設定 scroll 行為 (scroll-behavior / scroll snap)
    
* `#45` 利用radio, checkbox製作click toggle 行為
    
* `#46` CSS @property（CSS Houdini）
    

### SEO 與其他實用工具

* `#47` SEO 基本概念，多種 SEO 檢測工具
    
* `#48` 多種實用前端工具總整理，任務完成，打開百寶箱！
    

### 雜記

* `#49` 真結局，感言
    
* `#50` 本系列文章的更新補充紀錄
    

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![送杯珍奶鼓勵我 (Eva Chen)](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="left")