---
title: "#08 Css 選擇器總整理！"
datePublished: Sat Sep 23 2023 18:16:16 GMT+0000 (Coordinated Universal Time)
cuid: clmwcqp60000009l25ya54qhq
slug: css-selectors
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1764762600944/2a5ec0e7-5f49-4322-bf68-1ae60773551b.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1764762607161/895ada6b-742d-4a25-8c26-3c47e3846606.png
tags: css3, css

---

本篇會用實例與註解說明各種實用的 CSS 選取器，由於很多所以可以先存起來，之後要用到時再查詢。

我的 Photoshop 老師[游閔州](https://www.facebook.com/james8photoshop)曾說過：「掌握了 Photoshop 中的選取範圍，就掌握了大部分的 Photoshop 功能。」在 CSS 上，也是同樣的道理，掌握了 CSS 選擇器，我想可能就掌握了一半的 CSS。因為兩者都是選取到某個範圍，然後針對這個範圍進行調整。

所以，大家一起來學好選擇器吧！選擇器也許能做到比你想像中還要多的事情。

> #### ↓ 今日學習重點 ↓
> 
> * 了解 CSS 各種實用的選擇器
>     

---

> 另外，關於選擇器的好文大家也可以參考看看：  
> [\[CSS\] 選擇器表 (Selectors) - iT 邦幫忙](https://ithelp.ithome.com.tw/articles/10243699)  
> [金魚都能懂的 CSS 選取器 - 金魚都能懂了你還怕學不會嗎 :: 第 11 屆 iThome 鐵人賽](https://ithelp.ithome.com.tw/users/20112550/ironman/2799)

---

### 1\. 選擇 Tag、Class、Id

上篇我們有介紹過這三種選擇器，這三種是我們最常使用的選擇器。  
寫個範例給大家說明：

#### HTML

```xml
<body id="app" class="main-content container"> ... </body>
```

#### CSS

如果將 tag 選擇器直接接上 Class 或 Id 選擇器，代表的是「選取該 Class/Id 的 Tag」，權重會相加而增加喔！

如果使用逗號隔開，則會同時選到 2 個選擇器（群組式宣告）。

```css
body              { ... } /* 選取 Tag */
#app              { ... } /* 選取 Id */
.main-content     { ... } /* 選取 Class */

body#app          { ... } /* 選取 Id 為 app 的 body */
body.main-content { ... } /* 選取 Class 為 main-content 的 body */

body, .list       { ... } /* 同時選取 Tag 與 Class */
```

---

### **2\. 選擇孩子/兄弟**

#### 選取孩子

要選取孩子，使用空格隔開就可以了，會選取到底下全部的孩子。如果只想要選取到自己的第一層（親生的）孩子，要在中間加上大於 `>` 符號，有時候我們不希望樣式干擾到孫子的樣式（比如說子選單），就會使用這個語法。

#### 選取兄弟

要選取到兄弟，使用加號 `+` 是選取到後面的第一個。如果要選取到後面全部兄弟，而是使用波浪號 `~`。那選取到前面的呢？目前沒有辦法做到。

以下以一個常見的導覽列 navbar 作為例子，大家可以試想看看會選到什麼：

#### HTML

```xml
<nav>
    <h1>iT 邦幫忙</h1>
    <a class="item" href="#">2023鐵人賽</a>
    <ul class="list list-start">
        <li class="item">
            <a href="#">技術問答</a>
        </li>
        <li class="item">
            <a href="#">技術文章</a>
        </li>
    </ul>
    <ul class="list list-end">
        <li class="item">
            <a href="#">發文</a>
        </li>
        <li class="item">
            <span>個人資料</span>
            <ul class="list list-start">
                <li class="item">
                    <a href="#">個人檔案</a>
                </li>
                <li class="item">
                    <a href="#">個人檔案</a>
                </li>
            </ul>
        </li>
    </ul>
</nav>
```

#### CSS

```css
.list *     { ... } /* 選取 list 底下的所有東西 */
nav   .item { ... } /* 選取到 nav 下所有的 "item" class   (所有的小孩) */
nav > .item { ... } /* 選取到 nav 下第一層的 "item" class (親生的小孩) */
h1  + .list { ... } /* 選取 h1 後面第一個 "list" class */
h1  ~ .list { ... } /* 選取 h1 後面所有的 "list" class */
```

---

### **3\. 選擇順序**

CSS 選擇順序分為 `nth-child` 與 `nth-of-type` 兩種，

* `nth-child` 是選取同層的兄弟，不限種類，以下為例，連同 `li`、`hr` 也會一同列入計算的範圍；
    
* `nth-of-type` 則是選取同層「同一種」的兄弟，以下為例，只會計算 `li` 的數量。
    

#### HTML

```xml
<ul>
    <li>最新商品</li>
    <hr>
    <li>熱門商品</li>
    <hr>
    <li>商品據點</li>
    <hr>
    <li>品牌故事</li>
</ul>
```

#### CSS

```css
/* 選取同層元素，會連不同種類的 tag 一起找（li, hr...） */
li:first-child         { ... } /* 第一個 */
li:last-child          { ... } /* 最後一個 */
li:nth-child(3)        { ... } /* 第 3 個 */
li:nth-last-child(2)   { ... } /* 到數第 2 個 */
li:nth-child(odd)      { ... } /* 基數 */
li:nth-child(even)     { ... } /* 偶數 */
li:nth-child(n+4)      { ... } /* 第 4 個（含自己）以後的 */
li:nth-child(3n)       { ... } /* 3 的倍數 */
li:nth-child(3n-1)     { ... } /* 3 的倍數減 1 */

/* 選取同層的同一種元素，只會找與自己同樣的 tag (只找 li) */
/* 括號內的寫法與上面 nth-child() 一樣 */
li:first-of-type        { ... } /* 第一個 */
li:last-of-type         { ... } /* 最後一個 */
li:nth-of-type(3)       { ... } /* 第 3 個 */
li:nth-last-of-type(2)  { ... } /* 到數第 2 個 */
```

> 延伸閱讀：[CSS3選擇器「:nth-child()」與「:nth-of-type()」用法大不同](https://www.minwt.com/webdesign-dev/css/10885.html)

---

### **4\. 操作狀態（偽類）**

這系列的選擇器可以操控元素與互動的各種狀態，常常用在 HTML 的 `a`、`button` 或 `input` 上。

#### HTML

```xml
<a href="#pricing">價目表</a>

<!-- 當連結寫上別的元素的 id 名稱，點擊後可快速移動到該元素的所在位置 -->
<!-- 這就是網頁的錨點，URL 上會帶上連結 #pricing (hash link) -->
<div id="pricing"></div>
```

#### CSS

```css
/* 最常用的 */
a:link          { ... } /* 連結未被拜訪過，預設的樣式 */
a:visited       { ... } /* 連結已被拜訪過 */
a:hover         { ... } /* 移上去的時候（停懸） */
a:active        { ... } /* 點擊到放開前 */
a:focus         { ... } /* 當元素被聚焦（使用滑鼠或 Tab） */

/* 進階的 */
a:focus-within  { ... } /* 當子層的元素有被聚焦時 */
a:focus-visible { ... } /* 使用鍵盤聚焦元素時（例外：input, textarea 使用滑鼠聚焦也會吃這段） */
div:target      { ... } /* 當元素的 id (錨點) 與 URL 上的 hash 相同 */
```

有了這些選擇器，我們可以做到許多基本的互動效果，更詳細的實例 DEMO 預計會放在未來的互動章節裡。

> 延伸閱讀：  
> [浅谈 :focus 伪类选择器和聚焦后 outline 边框的设置问题 - 掘金](https://juejin.cn/post/7179149715458490405)  
> [:target - CSS：层叠样式表 | MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:target)

---

### **5\. Input 狀態**

* [當 `<inp`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/:target)`ut>` 沒有 `disabled` 屬性時就是 `enabled` 狀態，反之就是 `disabled`。
    
* `checked` 專門用在 `type="radio"` 或 `type="chechbox"` 的 `<input>` 上。
    

#### HTML

```xml
<input type="checkbox">
<input type="checkbox" disabled>
```

#### CSS

```css
input:enabled  { ... } /* 可以操作時 */
input:disabled { ... } /* 不可以操作時 */
input:checked  { ... } /* 勾選起來時 */
```

---

### 6\. 文字相關

#### HTML

```xml
<p>這樣的篤定是美麗的，但變化無常更是美麗。<p>
<p lang="en-US">Such certainty is beautiful, but uncertainty is more beautiful.<p>
```

#### CSS

```css
p::first-letter { ... } /* p 的第一個字母 */
p::first-line   { ... } /* p 的第一行 */
p::selection    { ... } /* p 的反白樣式 */
*:lang(en-US)   { ... } /* 選擇是美式英文的所有東西 */
```

---

### 7\. `::Before`, `::After`**（偽元素）**

`::before` & `::after` 可以在元素內部的前和後添加東西，不過因為它們是偽元素，所以無法跟任何東西互動，滑鼠點也點不到。

這樣無中生有又無法點擊的東西，我們經常把它用 CSS 魔改後，變成裝飾性元素。

#### CSS

```css
/* 如果在 content 內打文字，會接續在內容的前或後 */
p::before { content: "把東西加在前面"; }
p::after  { content: "把東西加在後面"; }

/* 當成裝飾性元素時，我們會這樣使用： */
p::before { 
    content: "";    /* content 一定要有定義才會出現，可以是空的 */
    display: block; /* display 也一定要有定義 */
    /* 其餘是自訂的樣式 */
}
```

`::before` & `::after` 也可以寫成一個冒號的 `:before` & `:after`，不過為了區分偽類和偽元素，還是建議寫成兩個冒號喔！

> 延伸閱讀：[CSS | 全都是假的！關於那些偽類和偽元素 - 基本用法. 先來說說偽類（ Pseudo-classes ）吧！所有的偽類都會用 …](https://medium.com/enjoy-life-enjoy-coding/css-%E5%85%A8%E9%83%BD%E6%98%AF%E5%81%87%E7%9A%84-%E9%97%9C%E6%96%BC%E9%82%A3%E4%BA%9B%E5%81%BD%E9%A1%9E%E5%92%8C%E5%81%BD%E5%85%83%E7%B4%A0-%E5%9F%BA%E6%9C%AC%E7%94%A8%E6%B3%95-4de48feb8607)

---

### 8\. **反選偽類**

#### HTML

```xml
<a href="abc.docx"   download><a>
<a href="info.docx"  download>info.docx<a>
<a href="detail.jpg" download>detail.jpg<a>
```

#### CSS

```css
a:not(:last-child) { ... }            /* 選取不是最後一個的 a */
a:empty            { display: none; } /* 選取標籤內容是空的 a */
```

---

### **9\. 屬性選擇器**

CSS 也可以針對 HTML 中的屬性去選擇元素。

#### HTML

```xml
<a href="https://">                                   連結文字 </a>
<a href="https://" disabled>                          連結文字 </a>
<a href="http://"  target="_blank">                   連結文字 </a>
<a href="https://www.instagram.com/" target="_blank"> 連結文字 </a>
<a href="/files/info.docx" download>                  連結文字 </a>

<img src="..." alt="rains dogs and cats">
<img src="..." alt="rainsDogsAndCats">
```

#### CSS

```css
a[disabled]          { ... } /* 選取有 disabled 屬性的 a */
a[target="_blank"]   { ... } /* 選取有新開視窗屬性的 a */
a[href~="instagram"] { ... } /* 選取連結文字有包含 "instagram" 的 a */
a[href^="https" i]   { ... } /* 選取連結開頭有 "https" 的 a, 不分大小寫 */
a[href$="docx" i]    { ... } /* 選取連結結尾有 "docx" 的 a,  不分大小寫 */
img[alt*="cats"]     { ... } /* 選取 alt 的「單字」(要有空格)有包含 "cats" 的 img */
                             /* 例如：「alt="cute cats"」可以，但「alt="cutecats"」不可以  */
```

關於屬性選擇器的各種等於符號：`~=`、`^=`、`$=`、`*=`，其實十分有用。我們可以不用透過 JS，單靠 CSS 就能做到很多判斷，依據不同條件加上不同樣式。例如：

* 如果連結中有某種 social media 的關鍵字，就使用 `::before` 加入該 social media 的 icon。
    
* 如果連結不是 https 開頭，就使用 `::after` 於尾巴加上「（可能為不安全連結）」的文字。
    
* 如果連結是某種檔案格式結尾，就使用 `::before` 加入該種檔案的 icon。
    

---

### 10\. `:is`、`:where`（偽類函數）

`:is` 和 `:where` 是新推出的選擇器，它們提供了新的方式讓你綜合選取多個元素，再往下統一設定 CSS。

#### CSS

```css
/* 用 where 不會增加權重，反之 is 會，所以 is 權重大於 where */
/* 不能與 ::before 和 ::after 併用 */
:is(header, main, footer)    a:hover { ... }
:where(header, main, footer) a:hover { ... }

/* 
如果沒有使用 where 或 is，過往沒有巢狀 CSS 的情況下要這麼寫：
header a, main a, footer a { ... }

不夠一目瞭然，而且重複寫了好多 a。
*/

/*
其實這樣類似巢狀 CSS 的結果：
header, main, footer ｛
    a:hover { ... }
｝
*/
```

> 延伸閱讀：[CSS :is, :where 和 :has 伪类选择器如何工作 - 掘金 (juejin.cn)](https://juejin.cn/post/7174749819276099642)

---

### 11\. 父層選擇器

`:has` 也是新推出的選擇器，他可以讓你選到父層（不只侷限於爸爸，爺爺也可以）。

寫文的當下還不支援，現已支援各大瀏覽器囉！

順便提一下，當 CSS 支援度還不高時，我不會使用在會影響到版面配置，這種重要的地方；相反地，我會使用在一些 UI 的小優化，例如 hover 到刪除鈕，父層的背景色就變為淺紅色，這樣即使沒有也不影響操作，有的話則會對使用者更好。

#### CSS

```css
tr:has(.btn-delete:hover) > td{ ... }
/* 當 tr 裡面有 class 叫 btn-delete 的元素被 hover 時，他的親兒子 td 會變 ... */
```

---

### 12\. **變數相關**

`:root` 選擇器是指 CSS 的根，目前只有使用在定義變數上，下篇我們將會詳細解說。

#### CSS

```css
:root{
    --color-default: #666;
}

body{
    color: var(--color-default);
}
```

---

### 補充：CSS 選擇器小遊戲——CSS Dinner

如果覺得要學很多選擇器很累，可以來玩個 CSS 小遊戲，輕鬆一點，透過遊戲認識 CSS 選擇器吧！

> 連結：[CSS Diner - Where we feast on CSS Selectors!](https://flukeout.github.io/)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696330590818/5ff0a2cc-2aaf-4256-82de-4f9b5b49e381.png align="center")

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")