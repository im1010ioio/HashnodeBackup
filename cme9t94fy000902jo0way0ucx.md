---
title: "#54 網頁渲染動畫的建議 & will-change 的使用時機"
datePublished: Wed Aug 13 2025 10:11:32 GMT+0000 (Coordinated Universal Time)
cuid: cme9t94fy000902jo0way0ucx
slug: css-web-rendering-will-change
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1766490372496/80715d83-8022-485a-b447-2aee2b9d1553.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1766490377939/6e4c8998-91bb-45b6-92b8-eec9b169c64a.png
tags: css3, css, web-development, css-animation, rendering, will-change, web-rendering

---

在現代網頁設計中，動畫是提升使用者體驗的一大關鍵。然而，過度或不恰當的動畫設計不但會影響效能，還可能帶來不理想的使用體驗。因此，在設計網頁動畫時，我們必須謹慎考量各種因素。以下是幾個實用建議，幫助你打造順暢且高效能的網頁動畫。

### 1\. 除了透明度（`opacity`）和切換（`transform`），不要改變任何屬性

動畫時最常使用的兩個屬性是 `opacity` 和 `transform`，這是因為它們不會觸發瀏覽器對其他元素的重新渲染（repaint）或重新排版（reflow），只會改變屬性的呈現方式，不會大幅增加渲染成本。當你改變其他屬性，例如 `width`、`height`、`margin` 等時，瀏覽器可能會重新計算整個 Layer tree（層樹），導致性能下降。因此，除了必要的情況外，請儘量使用 `opacity` 和 `transform` 來做動畫效果，並避免其他屬性的改變。

> 延伸閱讀：[Day 19 - 為什麼實作 CSS 動畫位移效果使用 translate() 比 absolute 絕對定位更好？](https://ithelp.ithome.com.tw/articles/10362313)

### 2\. 善用 `pointer-events` 隱藏未出現的元素，避免誤觸

當你設計一些進場或滾動動畫時，常常會有元素從不可見變成可見的狀態。在這種情況下，如果該元素實際上還未完全出現，使用者可能會意外點擊到它，這時就可以使用 `pointer-events: none` 來防止使用者誤觸。在動畫結束或元素進場之後，再將 `pointer-events` 設定回 `auto`，讓使用者可以正常與元素互動。

```css
.hidden-element {
  opacity: 0;
  transform: translateY(20px);
  pointer-events: none;
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.visible-element {
  opacity: 1;
  transform: translateY(0);
  pointer-events: auto;
}
```

### 3\. 避免同時運行過多動畫

雖然動畫能增添視覺效果，但過多的動畫同時運行會拖慢頁面的效能，尤其是當你在低效能的裝置上進行測試時，這個問題會更加明顯。建議一次最多只執行 2 到 3 個動畫，這樣既能保持頁面的流暢性，也不會影響使用者體驗。

### 4\. 善用 `transition-delay`，錯開動畫運行時間

當你需要多個動畫效果同時存在時，可以使用 `transition-delay` 來設置動畫的延遲時間，這樣可以避免多個動畫同時啟動，造成效能瓶頸。藉由錯開動畫的運行時間，你能創造一種更平滑的過渡效果，並有效減少瀏覽器的工作負擔。

```css
.element-1 {
  transition: transform 0.3s ease;
}

.element-2 {
  transition: transform 0.3s ease;
  transition-delay: 0.1s;
}

.element-3 {
  transition: transform 0.3s ease;
  transition-delay: 0.2s;
}
```

### 5\. 善用 `will-change`，但謹慎使用

`will-change` 屬性是告訴瀏覽器即將會改變的 CSS 屬性，讓瀏覽器預先做出最佳化處理。然而，過度使用 `will-change` 可能會耗費大量資源，因此需要謹慎使用。建議在需要動畫效果的父層元素 `hover` 時才啟動 `will-change`，確保在最需要的時候啟用最佳化。

```css
.parent:hover .animated-element {
  will-change: transform, opacity;
}
```

這樣的作法可以減少不必要的資源浪費，並保證效能最佳化。

### 6\. 使用手機裝置測試

設計完網頁後，請務必使用多種不同的手機裝置來進行測試，尤其是效能方面。不同裝置的處理器性能不同，動畫在高效能裝置上可能運行得非常流暢，但在低效能裝置上就可能顯得卡頓。因此，多設備測試是確保你的動畫在各種環境下表現一致的重要步驟。

### 結語

網頁動畫雖然能夠提升使用者體驗，但設計時必須考量效能，避免過度負擔瀏覽器。透過以上幾個簡單的技巧，你可以打造既美觀又高效能的動畫效果，讓網頁在不同裝置上都能有最佳的表現。

---

> 延伸閱讀：[10 principles for smooth web animations](https://blog.gyrosco.pe/smooth-css-animations-7d8ffc2c1d29#.oqnbskp19)

---

[https://github.com/xitu/gold-miner/blob/master/TODO/smooth-css-animations.md](https://github.com/xitu/gold-miner/blob/master/TODO/smooth-css-animations.md)