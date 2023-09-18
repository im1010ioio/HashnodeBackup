---
title: "#02  關於各家瀏覽器，前端必備的小知識：支援度、市佔率、CSS 實驗語法 -webkit-, -moz-... PostCSS  Autoprefixer | Super Easy CSS"
datePublished: Mon Sep 18 2023 12:43:53 GMT+0000 (Coordinated Universal Time)
cuid: clmovnzz600090aig3i8tge4o
slug: about-browsers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693192714283/e3591286-f553-4ed5-bfcf-ca51d43a6f4b.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695041017567/d518af91-d238-4f34-bbc0-14ffc4019fbe.png
tags: browser, browsers, web-development, chrome-cj73auo4o0012c3wted1yb7a1

---

> #### ↓ 今日學習重點 ↓
> 
> * 理解關於瀏覽器支援度的重要性
>     
> * 理解各家瀏覽器的開發注意事項
>     
> * 理解瀏覽器的 CSS 實驗性語法是什麼
>     

## 如何查詢 CSS 在各個瀏覽器的支援度？

不同的瀏覽器，如：Chrome、Safari、Edge、Firefox 等等，也是製作網頁需要考量的部分。因為就算是同樣的語法，不同的瀏覽器對它解讀的方式有可能會不一樣，或是不支援，最終導致破版。

因此，製作完網頁，可以的話，建議盡量使用各個瀏覽器跑過一遍做測試，看看有沒有因為相容性而產生的問題。我們製作網頁的目標就是為了讓大家都可以看，所以理論上各個常見的瀏覽器都要能正常運行。如果遇到真的不能正常運作的時候，就要有替代方案，或是改用別的方式做。

### 查詢各種語法的支援度：Can I Use

如果要查詢各個屬性瀏覽器能不能支援，我們一般會到「[Can I use](https://caniuse.com/)」這個網站查詢，HTML、CSS、JS 都可以查詢。

![Can I use :is() CSS pseudo-class](https://cdn.hashnode.com/res/hashnode/image/upload/v1692088195952/e00e3856-cda6-4c0d-a913-8d45e048c164.png align="center")

以上圖為例，它會清楚告訴你各瀏覽器各種版本的支援情況，和該版本的基本資訊、全球市占率等。如果查詢的屬性對於那個版本是實驗中的語法，它會告訴你如何才能運作，例如：使用者要打開該瀏覽器的某個設定，或是我們要加上對應的 CSS 實驗性前綴字等。（在本篇最後會介紹什麼是「CSS 實驗性語法」。）

### 查詢各個瀏覽器的市佔率：StatCounter

如果想要更近一步，了解各瀏覽器的市佔率，這個網站「[StatCounter](https://gs.statcounter.com/)」有在做統計。

什麼情況會需要知道瀏覽器的市佔率呢？當網頁只在某種瀏覽器上怪怪的時，我們可以參考市佔率，在團隊內部討論，並判斷出需要花多少成本去調整它。

![台灣 2022/08 至 2023/08 StatCounter 瀏覽器市佔比統計圖](https://cdn.hashnode.com/res/hashnode/image/upload/v1694721611695/2bf81ca4-5816-4bbe-9e5c-bc9fafe44923.png align="center")

以目前最新統計（2023/08）來說，  
瀏覽器在全球市佔率的排名是：  
Chrome &gt; Safari &gt; Edge &gt; Opera &gt; Firefox &gt; Samsung Internet；

而台灣的瀏覽器市佔率是：  
Chrome &gt; Safari &gt; Edge &gt; Samsung Internet &gt; Firefox &gt; Opera。

* [全球瀏覽器市佔率傳送門](https://gs.statcounter.com/browser-market-share)
    
* [台灣瀏覽器市佔率傳送門](https://gs.statcounter.com/browser-market-share/all/taiwan)
    

---

## 瀏覽器的渲染與引擎

瀏覽器之所以能夠渲染（render，將軟體變成畫面的過程）出畫面，是透過瀏覽器引擎（browser engine），它負責將我們所寫的 HTML 及 CSS 解析並排版出來。而常見的有：Webkit（分支有 Google 主導開發的 Blink）、Mozilla 等。

使用同樣瀏覽器引擎的瀏覽器，解析出來的畫面會較為相似，反之就有可能有所落差。

---

## 關於各瀏覽器在開發上的經驗談

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693246586357/70b1ee8c-3219-4082-b4f2-eefe2702f860.png align="center")

### WebKit

* **Chrome**：  
    基於 Blink，當前最主流，寫網頁在這裡絕對不能壞掉。
    
* **Edge**：  
    基於 Blink，在 Chrome 上正常的話，在這裡就不太容易壞。
    
* **Opera**：  
    基於 Blink，台灣很少人用，所以我很少在這裡測試，但是寫這篇文才發現，原來它在全球市占上不亞於 Firefox。
    
* **Samsung Internet：**  
    是三星在手機上的 Android 瀏覽器，使用 Google 的開源 Chromium 項目進行開發，所以也是基於 Blink 的。
    
* **Safari**：  
    由於他並不是基於 Google 的 Blink 開發，所以與上述三者落差稍微大一點。可是，因為 iPhone、iPad 普及的關係，所以市佔率不低，在這裡也是不能壞掉。但也因此，遇到 Safari 的陷阱時就會讓人很傷腦筋，於是被眾人戲稱為 Mac/iPhone 上的 IE。
    
    Mac 和 iPhone 上的呈現有時候也會不一樣，兩者都要測試。  
    到時候寫到 RWD，我再教大家如何使用 Mac debug 手機版的 Safari。
    

### Mozilla

* **Firefox**：  
    它理解網頁的方式偶爾會與 WebKit 家族有滿多不太一樣的地方。許多新語法的支援速度也不太一樣。不過在台灣市佔沒有很高，可以斟酌一下。
    

### Trident（IE核心）

* **Internet Explorer**：  
    已於 2022 被宣布停止支援，正式死去，普天同慶。現在已被 Edge 所取代。過去對於使用者來說，運作效能不好；對於開發者來說，除了有與其他瀏覽器不一樣的規則外，多個版本間還不盡相同。然而，還是有一些相依於 IE 的系統存在，畢竟系統改版並不是能說改就改的吧。
    

### 小結

以上（IE 除外），Safari 和 Firefox 是比較容易出現問題，以我的經驗來說，落差其實是 Firefox 多於 Safari 一些。可是，Safari 比較多人用的關係，所以讓人比較跳腳。XD

不曉得其他人的開發經驗是不是也是這樣呢？歡迎留言一起討論。xD

總結來說，寫網頁要確保還可以的話，至少要測過 Chrome、Safari；要確保完美的話，要測試過 Chrome、Safari、Firefox。

---

## 各瀏覽器的 CSS 實驗性語法

### CSS 前綴字

針對較新的 CSS 屬性，在尚未成為標準前，各家瀏覽器會提供一些實驗性的語法，通常會在新屬性上加上一些前綴字（Prefix，例如：`-webkit-`、`-moz-`、`-ms-`、`-o-`等），有時則會連名字都不一樣。一般來說，前綴字的代表意義如下：

* `-webkit-`：Chrome、Safari、Edge...
    
* `-moz-`：Firefox
    
* `-o-`：Opera
    
* `-ms-`：Internet Explorer
    

### PostCSS 套件——Autoprefixer

但是，有這麼多的 CSS 屬性需要處理相容性問題，我們不可能一個個檢查並加上去，所以通常我們會使用程式處理，最有名也最多人使用的就是：PostCSS 的套件 Autoprefixer。

PostCss 是一個使用 JavaScript 轉換 CSS 的工具，通常使用在寫完 CSS 後，所以稱為「後處理器」。PostCss 可以搭配它的不同的套件來對 CSS 進行處理，而 Autoprefixer 就是其中之一。

你可以告訴它你想涵蓋多少市占率的瀏覽器，然後它會依據 Can I Use 網站的數據，自動添加這些 CSS 前綴，讓你的網頁能夠正常渲染。如此一來，可以減少手動添加前綴的繁瑣工作，也能讓你的 code 保持乾淨、好維護。你只需寫標準的、不帶前綴的 CSS，然後 Autoprefixer 就會處理剩下的事情。

#### 通常搭配前端打包工具使用

PostCss 一般不會單獨使用，會搭配「前端打包工具」使用。下圖是其中一種「前端打包工具」—— [Webpack](https://webpack.js.org/) 官網的示意圖：

![Webpack](https://cdn.hashnode.com/res/hashnode/image/upload/v1692031509400/dc49201f-4d2b-49a9-85a5-6647e46ce0ed.png align="center")

`（來源：`[`Webpack`](https://webpack.js.org/)`）`

「前端打包工具」（Webpack、Vite 等）可以幫你處理開發上的瑣事，如我們剛剛所說的 PostCss Autoprefixer，是針對 CSS 的事後處理（CSS 後處理器）；當然，也可以對 CSS 做些事前處理，讓 CSS 可以寫一些程式邏輯，如：SASS (SCSS)、LESS 等；另外，還有 JS 相容性、CSS 與 JS 的壓縮、圖片或檔案的管理⋯⋯等等瑣事。

不過，這次先讓大家先了解打包工具的概念就好，Webpack 或 Vite 這類工具的細部操作，目前暫時不會深入探討，接下來我們會盡量專注在這次的主題「前端基本觀念與 CSS」上。

---

> 後記：
> 
> 我在寫這篇文章時，本來在 Safari 旁邊寫「我覺得還好，大家不用太擔心」之類的，結果隔天我和同事都被 Safari 小小整了一下，然後我就回來這篇文章把那句話刪掉了⋯⋯ 😂

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")