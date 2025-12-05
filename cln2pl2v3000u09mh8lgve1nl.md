---
title: "#12 4 個常見的 Css 設計方法與命名建議：oocss、smacss、bem、rscss"
datePublished: Thu Sep 28 2023 05:02:25 GMT+0000 (Coordinated Universal Time)
cuid: cln2pl2v3000u09mh8lgve1nl
slug: oocss-smacss-bem-rscss
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1764825953417/f3fdec25-906a-485b-9786-d59b9515eeec.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1764825947596/fcec4c61-3b80-4926-83f7-76325f3798fa.png
tags: css3, css

---

上篇我們了解了寫 Code 的三大方向，主要都是為了更簡單、更好維護。

所以，以此延伸，有許多 CSS 的模組化命名方法論就此而生，其中包括 OOCSS、SMACSS、BEM、RSCSS 等等。他們提供了一些命名原則建議，讓 CSS 好讀又好維護，並且作為團隊的開發共識，讓協作更順利。

> #### ↓ 今日學習重點 ↓
> 
> * 了解 CSS 命名建議：OOCSS、SMACSS、BEM、RSCSS
>     

---

這篇文章將簡單介紹四種 CSS 常見命名原則與設計模式：

* **OOCSS**：將容器與內容用「**物件**」的概念進行管理
    
* **SMACSS**：依照結構，將樣式分成五類管理
    
* **BEM**：訂定可以共同遵循的規範
    
* **RSCSS**：將樣式區分為不同的「**元件 (Components)**」撰寫
    

---

## **OOCSS**

OOCSS 全名是 「Object Oriented CSS」，意思是「物件導向 CSS」，物件導向聽起來很難，但其實很簡單，是類似積木的概念，我們要將 CSS 寫成一個一個可以獨立拆開的積木，而不是用漿糊黏再一起無法拆開的 CSS。

> 專有名詞：耦合，兩個模組間的相依性。  
> 也就是說我們要寫出低耦合的 CSS，以方便未來擴展的彈性。
> 
> 更多解釋請參考：[11\. 斷開鎖鏈! 低耦合、高內聚 - iT 邦幫忙](https://ithelp.ithome.com.tw/articles/10191761)

OOCSS 最主要代表的框架就是 [Bootstrap](https://getbootstrap.com/)。而它的主要是兩個概念是：

1. 結構與樣式分離 (Separate structure and skin)
    
2. 容器與內容分離 (Separate container and content)
    

### 1\. 結構與樣式分離

例如，一個登入按鈕我們可以改成這樣的寫法：

#### HTML

```xml
<!-- 舊有寫法：
<button type="button" class="btn-login">登入</button> -->
<button type="button" class="btn btn-primary">登入</button>
```

#### CSS

```css
/* 舊有寫法：
.btn-login {
    padding: 0.5rem 1rem;
    border-radius: 0.5rem;
    background-color: blue;
} */

/* 獨立出結構 */
.btn { 
    padding: 0.5rem 1rem;
    border-radius: 0.5rem;
}
/* 獨立出樣式 */
.btn-primary { 
    background-color: blue;
}
```

獨立出結構與樣式後，我們就可以輕鬆重複套用在其他按鈕上，不需要為不同的按鈕再寫很多遍相似的 code。（其實上一篇已經有解釋過類似的概念）

此外，OOCSS 還有一個觀念叫做 utilities，就是將常用的樣式獨立寫出來，作為小工具，讓你可以於任何地方套用。例如：

```css
.w-100 { width: 100%; }
.w-50  { width: 50%; }
.p-0   { padding: 0; }
.pt-1  { padding-top: 1rem; }
```

### 2\. 容器與內容分離

其實這個概念也在有上篇提過類似的，抽出重複樣式的部分，不過這裡強調的是應用在容器身上：

```css
/* 舊有寫法：
header {
    max-width: 1000px;
    margin: auto;
    background-color: #ccc;
    ...
}
footer {
    max-width: 1000px;
    margin: auto;
    background-color: #aaa;
    ...
} */

/* 「容器」：獨立出共用的部分 */
.container {
    max-width: 1000px;
    margin: auto;
}
/* 「內容」：額外撰寫各自的樣式 */
header {
    background-color: #ccc;
    ...
}
footer {
    background-color: #aaa;
    ...
}
```

這樣好處是 CSS code 變得很乾淨，缺點是 HTML 上的 class 數量可能會變很多個（如果加了一堆 utilities 的話）。

大家也可以多去看看 [Bootstrap](https://getbootstrap.com/) 的文件，就能更深入地了解 OOCSS 的應用了喔！

---

## **SMACSS**

SMACSS 全名是 「Scalable and Modular Architecture for CSS」，意思是**可擴展**與**模組化**的設計模式。

它將 CSS 分為 **Base**、**Layout**、**Module**、**State**、**Theme** 五個層級：

* **Base**：全域設定，用來定義 HTML 元素的基本樣式，例如 a, h1 - h6 ...。通常會透過 [Normalize](https://necolas.github.io/normalize.css/) 來統一各個瀏覽器的差異。
    
* **Layout**：用來定義網頁的版面架構，例如 `.container`、格線系統等等。
    
* **Module**：用來定義獨立、可重複使用的元件，例如 `.btn`、`.nav`。
    
* **State**：用來定義元素的狀態，例如 `.active`、`.disabled`。
    
* **Theme**：用來定義元素的顏色、字體等主題，例如 `.theme-dark`、`.theme-light`。
    

其實他的概念和 OOCSS 滿像的，只不過分界有點模糊。

---

## **BEM**

BEM 全名是「Block Element Modifier」，是一種命名方法論，它將命名分為：塊（Block）、元素（Element）和修飾符（Modifier）。

詳細內容如下：

* **Block（塊）：** 塊是一個獨立的元件，它們應以小寫字母命名，例如： `.header`、`.menu`。
    
* **Element（元素）：** 元素是塊的一部分，它們使用兩個下底線「`__`」連接起來，例如：`.header__text`、`.menu__item`。
    
* **Modifier（修飾符）：** 用於修改塊或元素的外觀或狀態。它們使用兩個破折號「`--`」連起來，例如：`header--dark`、`menu__item--active`。
    

BEM 的好處是一眼就能明白這個 class 做什麼用途，缺點是單一一個 class 名稱可能會變得很長。

---

## **RSCSS**

RSCSS 的全名是「Reasonable System for CSS Stylesheet Structure」，它是一套有跡可循的邏輯系統，將網頁中的東西視為各個獨立元件（Components）去管理。

它的官網文件寫得很詳盡，大家可以去看看：

> 官網說明：[rscss](https://ricostacruz.com/rscss/)  
> 繁中翻譯：[Introduction · rscss 繁中翻譯](https://eddiewen.gitbooks.io/rscss/content/)

不過我這邊就簡單說明一下，他主要分為：

1. 元件 (Components)
    
2. 元素 (Elements)
    
3. 變形 (Variants)
    
4. 巢狀元件 (Nested components)
    
5. 佈局 (Layouts)
    
6. 輔助類別 (Helpers)
    

### 1\. 元件 (Components)

名稱**至少為兩個字**，並以破折號 `-` 相連，例如：`.search-form`、`.article-card`。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695550327695/deba1283-5b39-407b-a885-171a632e9a55.png align="left")

如果想不到兩個詞的組合，有些元件只需要一個詞就可以表達它們的意思了，像是：`.alert`，它建議後面加上一些簡單的後綴詞，例如：`.alert-box` 、`.alert-card` 。

> 延伸閱讀：[擔憂 (Apprehensions) · rscss 繁中翻譯](https://eddiewen.gitbooks.io/rscss/content/apprehensions.html)

### 2\. 元素 (Elements)

元素的名稱只能是**一個字**，多個元素就會構成一個元件(Component)。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695550366406/b7e28d10-3766-4430-bb48-59b079c865e7.png align="left")

這邊建議使用 `>` 撰寫元件裡面的元素的樣式，避免巢狀時候的污染到子層元件。

```css
.search-form > .field { ... }
```

### 3\. 變形 (Variants)

作為元件的變化型時，他建議使用破折號 `-` 作為前綴詞。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695550398419/17ef6c38-a22d-400c-9f20-b435305d4198.png align="left")

### 4\. **巢狀元件 (Nested components)**

元件可以包元件，成為巢狀元件。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695550438094/55bee102-e9c8-4302-9663-e294f1ac14db.png align="left")

### 5\. 元件的**佈局 (Layouts)**

元件應該要夠彈性，能重複利用於很多地方，要避免使用到影響版面佈局（Layouts）的 CSS，例如：`position`、`float`、固定外距（`margin`）、固定寬高（`width`, `height`）。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695550475425/125faac4-0788-41db-897e-0647d003edc6.png align="left")

### 6\. 輔助類別 (Helpers)

輔助類別是為了方便快速覆蓋樣式，並以底線 `_` 作開頭命名，通常會將這些寫上 `!important`。所以使用時，要特別小心。

```css
._unmargin { margin: 0 !important; }
._center   { text-align: center !important; }
```

RSCSS 在區分元件的概念很值得參考，不過在命名上有時候可能會有不夠用的情況。

> 詳細可以參考這篇文章：[談 CSS 命名](https://editor.leonh.space/2020/css-naming/)

個人覺得 RSCSS 好的概念有幾點：

* 元件、元素、變形清楚定義。
    
* 名稱至少為兩個字，這樣就不容易撞名，也更容易理解這個命名是什麼。
    
* 有考慮到巢狀 CSS 污染的問題。
    
* 元件設計避免影響到整體版面佈局。
    

---

## 結論

我在開發上較常使用的是 OOCSS，雖然有著 class 會變很多的缺點，但是我覺得很彈性；另外，我也會運用 RSCSS 的概念去思考如何區分元件，只是命名不會完全依他的方式。

大家這幾種方式都可以試試看，多試幾次後選擇一個你喜歡、團隊 OK 的撰寫風格吧！當然，這些都不是硬性規範，你也可以依據自己需求微調，只要你的撰寫邏輯清楚，能夠簡單、好維護就可以了。

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")