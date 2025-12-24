---
title: "#60 利用 checkbox，做到純 CSS 開關網頁選單、收合側邊欄"
datePublished: Wed Aug 13 2025 11:32:06 GMT+0000 (Coordinated Universal Time)
cuid: cme9w4qcm000y02l56a0e4by1
slug: css-sidebar
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766572871211/31883184-d4b3-461a-98b2-8b659a7b5b1a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766572876797/4c824b26-da84-440a-99ba-7b9cec7b6aa9.png
tags: css3, css, css-animations, animation, css-animation, sidebar, sidecar-container

---

上篇我們教了大家如何客製化 `checkbox` 與 `radio` 樣式，其實運用同樣的原理，我們也可以做到簡單的互相切換（toggle）行為，例如：「點了就開，再點就關」這種動作。

所以，今天我們來做簡單的網頁選單吧！

---

## 基本概念

幫大家複習一下要用的小技巧：

1. HTML 中 `<label>` 中的 `for` 屬性可以選取到 `radio` / `checkbox` 的 id 的特性，例如：
    
    ```xml
    <div class="check-group">
        <input type="checkbox" id="check-1">
        <label for="check-1">Text</label> <!-- 點選文字可勾起 checkbox -->
    </div>
    ```
    
2. CSS 中的選取兄弟的選擇器（`~` 或 `+`），幫大家複習一下選擇器：
    
    1. 使用加號 `+` 是選取到**後面的第一個**
        
    2. 使用波浪號 `~` 是選取到**後面全部兄弟**
        
        > 延伸閱讀：[#08 CSS 選擇器總整理！id、class、:nth-child(n)、:not、:where、:is、:has 都難不倒我](https://ithelp.ithome.com.tw/articles/10326365)
        
3. CSS 中的偽類 `::checked`。
    

---

## DEMO 1：滿版網頁選單

用這些原理，我們可以來做一個簡單的選單：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728567736404/4f118809-ec34-4c5f-9c33-58c253668d9a.gif align="center")

> DEMO: Pure [CSS toggle menu](https://codepen.io/im1010ioio/pen/ExqNELe)

#### HTML

```xml
<input type="checkbox" id="menu-toggle">
<label for="menu-toggle" class="btn-toggle"></label>
<nav class="nav-main">
    <ul>
        <li>
            <a href="#">About Me</a>
        </li>
        <li>
            <a href="#">Works</a>
        </li>
        <li>
            <a href="#">Contact</a>
        </li>
    </ul>
</nav>
```

#### CSS

隱藏起 `checkbox` (`#menu-toggle`) ，然後當他為 `checked` 狀態時，改變漢堡按鈕的線條角度，並且把我們原本隱藏按不到的選單（`.nav-main`）改為出現：

```css
#menu-toggle{
    display: none;
}
#menu-toggle:checked{
    + .btn-toggle:before{
        transform: rotate(-27deg);
    }
    + .btn-toggle:after{
        transform: rotate(27deg);
    }
    ~ .nav-main{
        opacity: 1;
        pointer-events: auto;
    }
}
```

---

## DEMO 2：縮合側邊欄

用一樣的原理，我們也可以來做一個可以往旁邊縮起側邊欄的版面，這常見在後台系統中：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1728571947136/7a7f6d15-972a-4fc9-931c-d8de518de014.gif align="center")

> DEMO: [Pure CSS toggle aside](https://codepen.io/im1010ioio/pen/mdNOKEL)

#### HTML

```xml
<div class="content">
    <input type="checkbox" id="toggle-aside">
    <main id="col-main">
        <nav class="navbar">
            <label for="toggle-aside">
                <span class="material-icons">menu_open</span>
            </label>
            <h1>Title</h1>
        </nav>
    </main>
    <aside id="col-aside"></aside>
</div>
```

#### CSS

這邊的原理是：當 `checkbox` 為 `checked` 狀態時，側邊欄會往左偏移自己的寬度大小，於是會往左滑消失於畫面之中。

```css
:root{
    --aside-width: 200px;
}

#toggle-aside{
    display: none;
}
#toggle-aside:checked{
    ~ #col-aside{
        margin-left: calc(var(--aside-width) * -1);
    }
    ~ #col-main{
        label[for="toggle-aside"] .material-icons{
            transform: rotate(180deg);
        }
    }
}
```

（而最外層的 `.content` 我有下 `overflow: hidden;` 以防萬一出現奇怪的橫向捲軸，雖然往視窗外左偏通常不會產生捲軸。如果有東西往視窗外右偏通常都會出現捲軸，大家要注意一下。）

#### CSS will-change 優化

這種版面常見在後台系統中，所以有可能我兩邊的內容都非常、非常多，比如很長的清單資料等等，有可能在改變寬度時，造成卡頓。

我們在 #54 篇時有建議：「除了透明度（`opacity`）和 `transform`，不要改變任何屬性」，但是我在這裡不得不改變寬度時怎麼辦？這時候就可以使用 `will-change` 了。

> 延伸閱讀：[#54 網頁渲染動畫的建議 & will-change 的使用時機](https://ithelp.ithome.com.tw/articles/10363366)
> 
> `will-change` 屬性是告訴瀏覽器即將會改變的 CSS 屬性，讓瀏覽器預先做出最佳化處理。然而，過度使用 `will-change` 可能會耗費大量資源，因此需要謹慎使用。建議在需要動畫效果的父層元素 `hover` 時才啟動 `will-change`，確保在最需要的時候啟用最佳化。

所以我們用 CSS 告訴瀏覽器：  
當 `#col-main` 裡面有 `label[for="toggle-aside"]` 被 hover 時，`#col-main` 可能會改變寬度，而他後面的 `#col-aside` 可能會改變 `margin-left` 。這樣，瀏覽器就會做出最佳處理，畫面就可能比較不卡囉！

```css
#col-main:has(label[for="toggle-aside"]:hover){
    will-change: width;
    ~ #col-aside{
        will-change: margin-left;
    }
}
```

---

以上兩個 DEMO 都是用 `checkbox` 做到簡單的互相切換（toggle）行為，畫面細節的 Code 請去看 DEMO 連結會更詳細。這些 DEMO 是為了解釋基本原理，實際在開發中，排版的細節可能更多，也可能會搭配自己定義的變數或 UI 框架，到時候需要依據自己的需求調整喔！