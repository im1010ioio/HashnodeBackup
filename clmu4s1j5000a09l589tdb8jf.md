---
title: "#06 寫一份簡單的 Html"
datePublished: Fri Sep 22 2023 04:57:49 GMT+0000 (Coordinated Universal Time)
cuid: clmu4s1j5000a09l589tdb8jf
slug: html-strugtrue
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1693882143778/b15711dd-0c6c-4651-b2e7-cbc778b0ecdd.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1695358644595/426311c1-b679-4141-9d31-1d1c76e74a77.png
tags: html, html5

---

> #### ↓ 今日學習重點 ↓
> 
> * 練習使用 HTML 的各種標籤（tag）
>     
> * 知道 CSS 和 JS 要放在 HTML 的哪裡？
>     

今天，讓我們來了解一份簡單的 HTML 會長什麼樣？  
然後，修改一下第 #04 篇建立的 HTML 檔案，練習看看吧！

---

## 一、HTML 的最外層

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693929695931/c8a6ac22-1713-41bd-8907-9b529c1e97a9.png align="center")

### 1\. HTML 的版本

> 範例：`<!DOCTYPE html>`

告訴瀏覽器這是哪一個版本的 HTML，以這個範例來說，這是一份 HTML5 文件。

### 2\. HTML 的根

> 範例：`<html> ... </html>`

HTML 文件的根，會包含住整個網頁的內容，其中的屬性 `lang="en"` 說明這份 HTML 的語言，瀏覽器的翻譯功能也會優先先抓這個屬性作為翻譯的判斷之一，搜尋引擎也會根據這個優化搜尋結果。

> 而 `lang` 這個屬性也可以放在其他的 tag 上，使用情境如：這份 HTML 是台灣地區的繁體中文，而其中一個 `p` 段落是英文的（雖然通常我沒有寫到這麼仔細）。
> 
> （台灣使用的繁體中文是：`lang="zh-Hant-TW"`，並不是寫作 `zh-TW` 喔！）
> 
> 以中文來說的話可以細分為：  
> [HTML5的lang速查 ( 注意：繁體中文不是zh-TW喔 ) - VECTOR COOL 威得數位行銷](https://vector.cool/html5%E7%9A%84lang%E9%80%9F%E6%9F%A5-%E6%B3%A8%E6%84%8F%EF%BC%9A%E7%B9%81%E9%AB%94%E4%B8%AD%E6%96%87%E4%B8%8D%E6%98%AFzh-tw%E5%96%94/)
> 
> 更多的 HTML Language Code 設定可參考：  
> [HTML ISO Language Code Reference (](https://www.w3schools.com/tags/ref_language_codes.asp)[w3schools.com](http://w3schools.com)[)](https://www.w3schools.com/tags/ref_language_codes.asp)

---

## 二、 `head` 內的常見元素

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693929707116/8ed5e38f-82f9-4d60-8f25-2d72b6c038e5.png align="center")

寫在 HTML `head` 的內容並不會呈現在網頁畫面上，主要是放一些網頁的基本資訊。

由於瀏覽器與網路爬蟲（如搜尋引擎）是由上往下讀取 HTML，會先讀取到 `head` ，所以 `head` 內會放「優先要讓瀏覽器、搜尋引擎知道的資訊」，如：基本資料（meta data、網頁標題、SEO 結構化資料等等）。

CSS 也會建議在此處載入，提早把樣式載進來，就不會一閃而過 HTML 單調的預設樣式，防止畫面閃爍。如果 CSS 內有字體、圖片資源也能提早下載，早點載完呈現給使用者。使用者體驗會較好。

`head` 中常使用的語法如下：

### 1\. 文字編碼

> 範例：`<meta charset="UTF-8">`

Charset 是指定網頁內容是用什麼文字編碼，現在大多數的網頁編碼都是 UTF-8。

> 延伸閱讀：[網站文字編碼採用Big5與UTF-8 的優點缺點](https://por.tw/Website_Design/%E7%B6%B2%E7%AB%99%E6%96%87%E5%AD%97%E7%B7%A8%E7%A2%BC%E6%8E%A1%E7%94%A8big5%E8%88%87utf-8-%E7%9A%84%E5%84%AA%E9%BB%9E%E7%BC%BA%E9%BB%9E/)

### 2\. 可見區域

> 範例：`<meta name="viewport" content="width=device-width, initial-scale=1.0">`

Viewport 是設定網頁的顯示方式，可以設定網頁的預設寬度、縮放比例、使用者可不可以縮放等等。

最基本的設定為：`content="width=device-width, initial-scale=1.0"` ，意思是「網頁的寬度等於瀏覽裝置的寬度，初始縮放比例為 1」。

> 所有可設定的項目可參考這裡：  
> [viewport meta 标记 - HTML（超文本标记语言） | MDN (](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Viewport_meta_tag)[mozilla.org](http://mozilla.org)[)](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Viewport_meta_tag)

### 3\. 網頁標題

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693925298652/0339250a-0ef3-4bb8-b7f8-d2ad68c9da3d.png align="center")

> 範例：`<title>Documant</title>`

定義瀏覽器標籤中顯示的標題。

### 4\. 載入網頁小圖示 Favicon

> 範例：`<link href="favicon.ico" rel="shortcut icon" type="image/ico">`

HTML 中的 `<link>` 語法是用來載入外部資源使用的，他的屬性 `rel` 代表外部資源與這份 HTML 之間的關係（relationship），`href="..."` 則是檔案的連結。

> 關於如何寫連結，請參考這篇：  
> #06補充 網頁的根、絕對路徑、相對路徑，那些關於路徑的小知識

我們可以透過 `rel="shortcut icon"` 定義瀏覽器標籤中顯示的小圖示。Favicon 就如其名，是瀏覽器「我的最愛」的 icon（favorite icon）。

Favicon 可以自己指定路徑，如果沒寫瀏覽器預設會抓網頁的根（Root）底下的 `favicon.ico` 檔案，所以其實不一定要寫這一行，直接把 favicon 放在根目錄底下就可以了。只不過，為了讓瀏覽器讀取 favicon 順利，我還是會寫這一行。

> 轉換 ico 檔案好用工具：[Favicon Generator](https://www.favicongenerator.com/)  
> Favicon 的大小是 16px x 16px，不過考慮到螢幕倍率，我會準備 48px 以上的圖檔。（關於螢幕倍率，之後會再詳細解說）

### 5\. 載入 CSS

> 範例：`<style> ... </style>`  
> 範例：`<link href="./css/index.css" rel="stylesheet">`

CSS 要套用在 HTML 上，第一種方式是可以在 `head` 內寫在 `<style ></style>` 內。

第二種方式，則是另外寫 CSS 檔案，與剛剛 favicon 相同，使用 `<link>` 載入，`rel="stylesheet"` 代表載入的是樣式表。通常為了好管理檔案，推薦使用這種方式載入 CSS。

關於寫在不同處有何不同，我們下篇會解說。

### 6\. SEO 相關設定

另外，SEO 的相關設定也會放在 `head` 內，關於 SEO 的部分，我們後續的文章會再解說。

---

## 三、 `body` 內的常見元素

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693929725298/a923c595-1428-4f08-9596-1349a4371f0d.png align="center")

`body` 內會放網頁要被他人看見的內容。就是我們在上篇所說的 `main`、`p` ⋯⋯ 大部分的標籤都會放在這裡。

### 1\. HTML 預設的 `display`

這些標籤有預設的版面特質（`display`）：`inline（行內元素）`、`block（區塊元素）`、`list-item`、`table` 等等。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693933670667/33db581e-e60d-4f3f-a408-386de08dc783.png align="center")

如果放在文字間：

* `inline（行內元素）` 會穿插在文字間，也會隨著文字折行；
    
* `block（區塊元素）`、`list-item`、`table` 會佔據畫面的一整行，截斷文字區塊。
    

不同的標籤預設會有不同的 `display`，大家試寫看看就能大致上理解為何 HTML 會如此設計了，比如說超連結 `<a></a>` 需要穿插於文章間，所以預設是 `inline`。

當然，事後也可使用 CSS 改變 HTML 標籤的 `display`，之後的文章會再詳細說明。

### 2\. 常用的 HTML tag

以下列出一些常用的 HTML 標籤，供大家參考：

> 更詳細的 HTML 文件請參考：  
> [HTML Tutorial (](https://www.w3schools.com/html/)[w3schools.com](http://w3schools.com)[)](https://www.w3schools.com/html/)  
> [HTML comment tag (](https://www.w3schools.com/tags/tag_comment.asp)[w3schools.com](http://w3schools.com)[)](https://www.w3schools.com/tags/tag_comment.asp)

#### (1) 容器

上篇我們有提過，在 HTML 中我們會透過巢狀結構，區分網頁中不同的區塊，所以 HTML 中有許多容器性質的標籤。以下除了 `div` 以外，其他都是語意化標籤。建議如果能使用語意化標籤就使用它，這樣能讓瀏覽器與 SEO 爬蟲明白這個區塊放的是什麼內容。

| HTML | 預設 Display | 用途 |
| --- | --- | --- |
| `<div></div>` | block | 區塊（division），一個純粹的容器，沒有代表任何意義。常用於排版上。 |
| `<nav></nav>` | block | 導覽區塊（navigation），裡面通常會放網站的導覽連結。 |
| `<aside></aside>` | block | 側邊欄，跟主要區塊內容無關的區塊，通常放額外資訊。 |
| `<main></main>` | block | 用來放主要資訊的區塊，一個網頁只能有一個。 |
| `<header></header>` | block | 頁首區塊，通常會放介紹性資訊，放網頁的標題、Logo、搜尋框等等。 |
| `<footer></footer>` | block | 頁尾區塊，通常會放會包含作者、版權、聯絡方式等。 |
| `<section></section>` | block | 有明顯意義的區塊，每一塊內容是獨立的，例如：產品網頁中的產品特色、產品使用情境可能就是兩個 `section`。 |
| `<article></article>` | block | 表示文章或留言。 |
| `<figure></figure>` | block | 裡面用來放獨立的內容，像是文字段落、圖片、圖表或程式碼片段等。可搭配 `<figcaption></figcaption>` 當這個內容的標題。 |

#### (2) 文字

`strong` 和 `em` 也是語意化標籤，雖然畫面呈現效果和 `b` 和 `i` 一樣，但是 SEO 會比較優喔！

| HTML | 預設 Display | 用途 |
| --- | --- | --- |
| `<h1></h1> ~ <h6></h6>` | block | 表示一級標題，數字越小，級別越高。總共有 1-6 級。一個網頁 `<h1></h1>` 只能有一個，其他的可以有多個。 |
| `<p></p>` | block | 文字段落（paragraph）。 |
| `<span></span>` | inline | 短句。 |
| `<b></b>` | inline | 粗體字（bold）。 |
| `<strong></strong>` | inline | 重要文字，預設是粗體。 |
| `<i></i>` | inline | 斜體字（italic）。 |
| `<em></em>` | inline | 強調文字（emphasized），預設是斜體。 |
| `<small></small>` | inline | 較小的文字。 |
| `<a href="..." target="_blank"></a>` | inline | 超連結，屬性 `href` 放連結的位置，如果寫內容寫 `mailto:` 或 `tel:` 分別可以開啟預設的寫信、撥號軟體。屬性 `target` 用來放連結互動的方式（不寫的話預設是 `_self` 會在原頁面開連結，常用的還有 `_blank` 是新開視窗）。 |

#### (3) 多媒體

| HTML | 預設 Display | 用途 |
| --- | --- | --- |
| `<img src="..." alt="">` | inline | 圖片。`src` 是圖片連結，`alt` 是圖片替代文字，當連結失效會顯示這段文字，視障瀏覽器也會念這個內容給使用者，SEO 也會依據這個，建議填寫喔！更詳細的圖片相關設定，之後會再說明。 |
| `<iframe src=""></iframe>` | block | 外嵌內容，放的是其他網頁的內容。放在裡面的網頁會有一些限制。在網頁上放 YouTube 影片就是使用這種方式外嵌進來。 |
| `<video></video>` | block | 影片，詳細的寫法請見：[HTML Video (](https://www.w3schools.com/html/html5_video.asp)[w3schools.com](http://w3schools.com)[)](https://www.w3schools.com/html/html5_video.asp) |

#### (4) 表單

一個基本的填寫表單如下：

```xml
<!-- action 是表單資料傳送的位置，不過現在多數人都是將這個行為寫在 JS 中 -->
<form action="">
    <div>
        <!-- label 加上 for="input的id"，點擊 label 就可以選取這個 input -->
        <label for="userName">姓名</label>
        <!-- 單行輸入框 -->
        <input type="text" id="userName">
    </div>
    <div>
        <!-- radio name 一樣，表示是同一種單選欄位 -->
        <input type="radio" name="gender" value="male">
        <label for="userName">男性</label>
        <input type="radio" name="gender" value="female">
        <label for="userName">女性</label>
    </div>
    <div>
        <input type="checkbox" id="agreePrivacy">
        <label for="agreePrivacy">我同意隱私條款</label>
    </div>
    <div>
        <label for="remark">備註</label>
        <!-- 多行輸入框，行數設為 3 行 -->
        <textarea rows="3"></textarea>
    </div>
    <!-- button 預設的 type 是 submit，放在 <form> 中，預設會觸發送出行為 -->
    <!-- 不過在送出前可能還需要做其他事情，如驗證，所以送出行為會寫在 JS 中 -->
    <!-- 於是，button 的 type 設為 button，可避免 HTML 觸發送出行為 -->
    <button type="button">送出</button>
</form>
```

#### (5) 清單

清單的預設 Dispay 是 list-item，分為有序號（`ol`，ordered list）與沒有序號（`ul`，unordered list）的兩種清單，前者預設會有數字標號，後者會有點點標號。不過，也可以使用 CSS 去改變他們的標號格式（list-style），詳細可參考：[list-style - CSS: Cascading Style Sheets | MDN (](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style)[mozilla.org](http://mozilla.org)[)](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style)。

裡面會放 `li` 標籤作為每一個 item，每個 li 預設會有一些內縮間距。基本的格式如下：

```xml
<!-- 前面會有數字標號 -->
<ol>
    <li>清單</li>
    <li>清單</li>
<ol>

<!-- 前面會有點點標號 -->
<ul>
    <li>清單</li>
    <li>清單</li>
<ul>
```

#### (6) 表格

表格的預設 Dispay 是 table，`thead` 與 `tbody` 是表頭與表格內容，`tr` 是行，`th` 是標題格子，`td` 是一般格子。

`th` 與 `td` 使用屬性 `colspan` 可以合併橫向的格子，`rowspan` 則是合併直向的格子，使用後格子數量要對應調整。以下範例：

```xml
<table>
    <thead>
        <tr>
            <th></th>
            <th colspan="2"></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th></th>
            <td></td>
            <td rowspan="2"></td>
        </tr>
        <tr>
            <th></th>
            <td></td>
        </tr>
    </tbody>
</table>
```

#### (7) 其他

| HTML | 預設 Display | 用途 |
| --- | --- | --- |
| `<hr>` | block | 分隔線 |
| `&nbsp;` | inline | 瀏覽器在解析 HTML，兩個以上的空白會被當成一個空白呈現，如果需要呈現許多空白，就需要寫 HTML 的符號編碼。這是最常見的空白，不過空白不只一種，詳細請見：[實用！在HTML插入空白的6種方式](https://aprilyang.home.blog/2020/02/14/6-ways-to-put-spaces-in-html/) |
| `&lt;` | inline | 小於 `<` 符號。由於大於和小於符號是 HTML 的保留字，兩個打在一起的 `<>` 會被當成標籤，如果要呈現出來必須寫 HTML 的符號編碼。 |
| `&gt;` | inline | 大於 `>` 符號，其餘概念同上。 |

### 3\. 載入 JavaScript

> 範例：`<script src="./js/index.js"></script>`  
> 範例：`<script> ... </script>`

要載入 JS，使用的是 `<script></script>` 標籤。  
你可以將 JS 語法直接寫在這個標籤內，也可以透過 `src="..."` 屬性將 JS 檔案載入進來。通常在開發上，為了好管理，我們會使用後者。

JS 建議放在 `<body>` 中的最末端，也就是 `</body>` 結束標籤前，這樣可以確保 JS 在執行時，頁面的 HTML（DOM）結構已經完全載入完畢，避免 JS 操縱尚未存在的元素，從而引發錯誤。

---

## 結論

好的，今天的教學就先到這裡了！今天介紹了許多 HTML 標籤，不過不需要一次全部背起來，只要先有概念和印象就好了。練習的時候，還會遇到很多次，每遇到一次就會多熟悉一次，這樣就可以了。

現在，就拿第 #04 篇建立的 HTML 檔案，隨意打一些 HTML tag，練習看看吧！

推薦大家安裝 VS Code 的 [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) 套件，安裝後按下右下角的「Go live」，就能跑起你的網頁囉！

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693934636778/115d6220-cfaa-4ff6-bab5-f263643f2e71.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693934646186/ebea3e7b-818c-4ef9-bc91-9b5ff8b352a4.png align="center")

此外，操作 VS Code 時，推薦使用快捷鍵，詳細說明請參考這篇文章：

> [\[Editor\] CodePen / VS Code 常用快速鍵 - iT 邦幫忙](https://ithelp.ithome.com.tw/articles/10237385)

而其他 VS Code 版面設定與套件，可以參考我之前寫的這篇文章：

> [10 個 VS Code 設定及套件推薦：色彩、icon 主題、字體、註解、防錯標示，Mac Terminal 設定 (](https://im1010ioio.hashnode.dev/10-useful-settings-plugins-for-vs-code)[hashnode.dev](http://hashnode.dev)[)](https://im1010ioio.hashnode.dev/10-useful-settings-plugins-for-vs-code)

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")