---
title: "#05 Html 基礎語法"
datePublished: Wed Sep 20 2023 17:08:52 GMT+0000 (Coordinated Universal Time)
cuid: clms00h9k000008jxbqed27r7
slug: html-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693882131012/5ed0ecef-0982-459d-bffa-a30f0449d8d9.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695229427778/d242982d-08c1-4b85-9d2a-5527f22c51cf.webp
tags: html, html5

---

> #### ↓ 今日學習重點 ↓
> 
> * 了解 HTML 的語法
>     

上一篇文章，我們有建立了一份 HTML 檔案，  
那麼這些語法到底是什麼意思呢？讓我們往下看。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693500614650/4d3642a8-c27f-4ac2-bf89-288bb696482e.png align="center")

## HTML、HTML5、HTM 是什麼？

#### **HTML（Hypertext Markup Language）**

HTML 是一種標記語言，中文全名為「超文字標示語言」，它使用各種標籤（tags）來定義不同的網頁元素，例如：

* 文字段落（paragraph）是 `<p></p>`；
    
* 第一重要的標題（heading 1）是 `<h1></h1>`；
    
* 圖像（image）是 `<img>` 等等。
    

#### **HTML5**

HTML5 是 HTML 的第五個版本，也是目前大家所使用的版本。  
它較 4 代新增並改良許多功能。

比如說，HTML5 新增了多媒體，讓網頁可以播放音樂和影片；HTML5 新增了語意化標籤，讓標籤的名稱更有意義，如： `<nav></nav>` 就是導覽列（navigation），這樣可以讓瀏覽器能快速抓到網頁的重點，也讓學習和開發更簡單。

#### **HTM（Hypertext Markup）**

HTM 是 HTML 的一種，通常與舊的網頁文件有關。在早期的網頁開發中，某些操作系統或瀏覽器可能只支援三個字母的副檔名，因此人們可能會使用 `.htm` 代替 `.html`。不過，現在已經沒有這個問題了，大部分情況下都是使用 `.html` 作為副檔名。

---

## HTML 的語法構成

### 語法架構

HTML 文件不區分大小寫，不過 W3C 協會建議都寫小寫。  
而它的標籤的基本語法架構會有：

#### 1\. 起始標籤

用大於 `>`、小於的符號 `<`，框住標籤的名稱，代表了一個標籤的開始，如：`<textarea>`。

#### **2\. 結束**標籤

與起始標籤一樣，只是在標籤名稱前面多了個斜線 `/`，代表了這個標籤的結束，如：`</textarea>`。

不過，依據不同標籤的性質，有可能會不需要結束標籤，例如：`<input>`、`<img>`。有些人為了區分這種標籤，會在標籤結尾加上一個「斜線」，如：`<input/>`、`<img/>`。有沒有加上斜線都是可以運作的。

#### 3\. 內容

這個標籤的內容物。

#### **4\. 屬性（Attribute）**

根據不同標籤的特質，會有不同的屬性可以運用，可以添加許多設定。例如：`<textarea rows="5"></textarea>` 就是指一個有 5 行高度的文字輸入框。

![HTML 標籤的基本語法架構](https://cdn.hashnode.com/res/hashnode/image/upload/v1693761494077/e1941e58-02a3-4db6-b560-e632e9012edd.png align="center")

如果網頁沒有套用 CSS 的話，HTML 會依據瀏覽器預設的樣式呈現。

HTML 是種寬容的語法，如果寫錯了（像是結束標籤忘了寫），依然能夠跑出來，只不過呈現結果可能會不如預期。

### 巢狀（Nesting）的特性

標籤裡面可以再放進標籤，這樣的結構我們稱之為「**巢狀結構（Nesting）**」。我們可以透過一層包一層的方式，區分網頁中不同的區塊。

比如說：

* 側邊區塊 `aside` 裡面，放了一份清單（unordered list） `ul`，清單內有許多項目（list item） `li`，每個項目中有連結 `a`；
    
* 而旁邊的主要內容 `main`，放了文章 `article`，而文章內放了許多文字段落 `p`。
    

![HTML的巢狀結構](https://cdn.hashnode.com/res/hashnode/image/upload/v1693761534771/6299ab25-fe83-48d3-9854-704eb55713e7.png align="center")

不過巢狀結構不宜包太多層，因為太多層時會變得很肥大、很難管理，沒有辦法一目瞭然。在爸爸的爸爸們與他們的子子孫孫間徘徊周旋，絕對會頭暈腦脹，改起來會十分痛苦。這個建議也適用於其他語言，如 JS 和 CSS 等。

### 註解的語法

HTML 有提供註解語法，讓人在開發時可以寫一些筆記在 HTML 中，並且不會被輸出在網頁上。註解的內容是由 `<!--` 和 `-->` 所包起來，只要被包起來的內容都是註解的範圍，所以也可以寫成多行。

雖說不會輸出到網頁上，但是在網頁上按下「右鍵 &gt; 檢視原始碼」（以 Chrome 為例），還是可以被人看到寫了些什麼，所以不建議用這個寫一些敏感資訊（基本上前端的東西在瀏覽器的開發者模式中都可以找得到，所以前端的東西都不建議放敏感資訊）。

有些開發人員會在 HTML 註解中面放一些彩蛋，寫一些隱藏訊息，或用文字符號畫畫，雖然很少數，但發現的時候總覺得很有趣。像寫這篇時，我發現 [Firefox 的網站](https://www.mozilla.org/zh-TW/firefox/new/) 裡面原來藏了一隻恐龍。XD

![Firefox HTML Comments](https://cdn.hashnode.com/res/hashnode/image/upload/v1693841627276/18b6e8bc-e562-4941-9bd0-4b770d83e1a5.png align="center")

大家無聊的話，也可以去看看各大網頁原始碼有沒有藏有彩蛋。XD

今天就先到這裡囉！明天我們要來寫一份簡單的 HTML。

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")