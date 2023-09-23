---
title: "#07 Css 基本語法 & 權重介紹"
datePublished: Sat Sep 23 2023 04:57:36 GMT+0000 (Coordinated Universal Time)
cuid: clmvk7mf9000409jsfonj7kvl
slug: css-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694508854399/bd957ef1-b18f-48c8-92b3-b79edd4f389d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695445041718/f4e54214-20c2-46bd-a251-d9d9aad15636.png
tags: css3, css

---

> #### ↓ 今日學習重點 ↓
> 
> * 了解 CSS 的基本語法
>     
> * 對於 CSS 的權重有基本概念
>     

我們終於進入我們的重點 CSS 啦！今天要來講解 CSS 權重與選擇器。

本篇會先講解如何撰寫 CSS 與權重概念，下一篇會用實例與註解說明各種實用的 CSS 選取器。

---

## CSS 的基本語法

在了解各種選擇器前，我們要先了解 CSS 的基本語法。

### 語法架構

在 CSS 中會區分大小寫，要注意大小寫的部分，如果寫錯了可能會選不到喔！  
而它的標籤的基本寫法會像下圖：

![CSS 的基本語法](https://cdn.hashnode.com/res/hashnode/image/upload/v1694014738265/91e1cc5d-b2ff-4417-a4a4-04246118c3de.png align="center")

以這個例子來說，這樣寫會選取到 HTML 中的 `body` 標籤，然後將他的背景色（`background-color`）設定為 `AliceBlue` 這個顏色。

`body{ ... }` 前面的 `body` 就是一種選擇器，是 Tag 元素選取器，用來選取 HTML Tag。而內容會使用大括號 `{}` 括弧起來，在中間用冒號區隔 `:` 屬性與屬性值，最後以分號 `;` 作為這個屬性的結尾。

> 延伸閱讀： [CSS Colors (](https://www.w3schools.com/cssref/css_colors.php)[w3schools.com](http://w3schools.com)[)](https://www.w3schools.com/cssref/css_colors.php) ，不過關於顏色的部分我們之後會再解說。

### 註解

CSS 中的註解的寫法是 `/* 註解 */` ，只要位於 `/*` 與 `*/` 間的東西，都會被當成註解，所以也可以寫成多行。

```css
/* 一句註解 */

/*
這句
分成
好幾
行
*/

/* 以下是暫時取消這個樣式，註解起來 */
/*
span {
  color: blue;
  font-size: 1.5em;
}
*/
```

---

## CSS 的權重

在 CSS 中，權重是一個用來確定哪些樣式會套用於 HTML 上的重要依據。

### 權重的基本順序

以下是 CSS 權重由低到高的順序：

1. `*` **通用選擇器：**  
    這是最低權重的選擇器，它影響所有 HTML 元素。由於影響範圍甚廣，所以一般會建議不要濫用這個選擇器。
    
2. `div`**、**`p` **元素選擇器：**  
    當只使用 HTML Tag 名稱作為選擇器時，只需要寫 tag 本身的名字就能選到它，它的權重會稍微比 `*` 高。
    
3. `.class` **類別選擇器：**  
    在 HTML 上寫上屬性 `class=""`，就能使用「點 + class 名稱」選到這個 html 元素。它就像一個人的小名，可以有多個。它的權重比 Tag 選擇器高。
    
4. `#id` **ID 選擇器：**  
    在 HTML 上寫上屬性 `id=""`，使用「井字 + id 名稱」選到它。因為 HTML 中的 ID 不可以重複，所以 ID 選擇器的權重更高。可以當做個絕對的存在，就像一個人的身分證字號。
    
5. `inline style 屬性` **行內樣式：**  
    行內樣式就是下面範例中的「`style="color: orange;"`」，它的權重比上述選擇器都高，因為它直接寫在 HTML tag 上。在 HTML 寫了行內樣式，就難以使用 CSS 檔案改變，所以會建議不要濫用這種寫法。
    
6. `!important`**：**  
    當 CSS 屬性值的尾巴加了 `!important`，將會覆蓋其他所有權重，即使其他 CSS 的權重更高。因為它權重最高，彈性較差，一般也會建議不要濫用它。
    

```xml
<p id="main-text" class="text text-center" style="color: orange;"> ... </p>
```

```css
p           { color: red; !important } /* 最後 p 的顏色會是紅色  */
p.text      { color: yellow; }
p#main-text { color: blue; }
```

以上提到不要濫用的 CSS 並不是不能使用他們，只是用他們之前要想清楚：會不會別的地方也會吃到這個樣式？會不會未來變得不好改？⋯⋯等等因素。

隨著前端開發方式的演進，這些建議都不是絕對。也許在某個時期不推薦這麼寫，但是因為技術背景的不同，在某個時期卻是推薦的。我們只要熟悉 CSS 原本的規則與不同建議背後的成因，隨著自己的經驗增長，自然就能夠取捨了。而我也還在路上 xD。

### 後面寫的會蓋過前面

如果有多個相同權重的 CSS 用於同一個 HTML 元素上，後面寫的 CSS 將覆蓋前面的 CSS，因此撰寫的順序也很重要。

```css
p { color: red;    }
p { color: yellow; }
p { color: blue;   } /* 最後 p 的顏色會是藍色  */
```

---

## 練習前端語法的好工具

### CodePen

> 連結：[https://codepen.io/](https://codepen.io/)

![CodePen](https://cdn.hashnode.com/res/hashnode/image/upload/v1694268557766/c96a04ca-eef4-4bfa-9f58-063f7390d5da.png align="center")

和大家分享個好用的前端工具——CodePen。

CodePen 是一個專為網頁開發者設計的在線平台，它可以讓你同時編輯 HTML、CSS 和 JS，所見即所得。讓你能夠輕鬆測試、分享前端的 Code。

通常，遇到新語法我會在這裡測試看看，大家也可以試試看喔！  
之後如果有需要 Demo 的地方，我也會放在這裡。

---

好的，今天就先到這裡了！  
明天，下一篇是 CSS 各種實用的選擇器總整理。

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")