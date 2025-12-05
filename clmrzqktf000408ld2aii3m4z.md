---
title: "#04 GIT 實戰練習：GitHub Desktop、GitHub Page 基礎教學"
datePublished: Tue Sep 19 2023 16:00:00 GMT+0000 (Coordinated Universal Time)
cuid: clmrzqktf000408ld2aii3m4z
slug: git-github-gitpage-practice
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1764751447165/0cd87c71-332b-4b6c-9add-5208e0f2e744.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1764751458995/1a74d0aa-425e-4436-b9f5-4faa4807db58.png
tags: github, git

---

上一篇我們了解了 Git 與實際應用的概念，  
接下來我們要實際練習使用 GIT 和 GitHub。

> #### ↓ 今日學習重點 ↓
> 
> * 安裝寫程式必要軟體
>     
> * 實際操作 GIT & GitHub
>     

## 安裝必要軟體

首先要先安裝必要軟體，請照著下面的步驟做：

1. 安裝 GIT（[Windows](https://git-scm.com/download/win)、[Mac](https://git-scm.com/download/mac)）
    
2. 註冊 [GitHub](https://github.com/) 帳號
    
3. 安裝 [GitHub Desktop](https://desktop.github.com/) 軟體（不過你也可以用終端機打 GIT 指令操作）
    
4. 安裝寫程式的編輯器（推薦：[VS Code](https://code.visualstudio.com/)）
    

## 練習使用 Git

請照著下面的步驟試試看：

### 1\. 建立一個新的 Repository

到 [GitHub](https://github.com/) 右上角上找到一個「＋」的新增符號，按下「New repository」，新增一個 GitHub Repository。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693407551755/072cab6c-9c91-4c92-b605-e21a1c251b1b.png align="center")

### 2\. 複製（`Clone`）剛剛建立的 Repository 到你的電腦

在你剛剛建立的 repository 上面按「Set up in Desktop」就能快速幫你帶到 GitHub Desktop 新增（或者你也可以自己複製 URL 新增）。接著，選擇電腦裡一個空的資料夾存放你的 Git 檔案（一定要是完全空的）。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693407581000/cbd01e39-caf2-4c38-98d1-a354faedbf1d.png align="center")

完成後，你就已經建立本地的 repository 了喔！現在，在你選的資料夾裡，會發現多了一個隱藏的資料夾叫做 `.git` ，Git 會在這個資料夾內儲存變更紀錄。如果看不到，可能表示你的「檔案總管 / Finder」沒有開放顯示隱藏的檔案。如何顯示隱藏的檔案，請參考以下連結：

* [在 Windows 中檢視隱藏的檔案和資料夾](https://support.microsoft.com/zh-tw/windows/%E5%9C%A8-windows-%E4%B8%AD%E6%AA%A2%E8%A6%96%E9%9A%B1%E8%97%8F%E7%9A%84%E6%AA%94%E6%A1%88%E5%92%8C%E8%B3%87%E6%96%99%E5%A4%BE-97fbc472-c603-9d90-91d0-1166d1d9f4b5)
    
* [Mac 隱藏的檔案與資料夾如何顯示出來？教你一招最快速的方法](https://applealmond.com/posts/199729)
    

### 3\. 開啟 VS code(或其他的編輯器)，打開剛剛選擇的資料夾

選擇剛剛那一個資料夾，然後打開它（不用選任何檔案）。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693408281219/d3ca3b8c-673d-45e2-a7ab-1dfbdd9c9a28.png align="center")

### 4\. 新建一個 HTML 檔案，叫做 `index.html`

打開後這個資料夾內什麼都沒有，試試看新增一份 HTML 檔案，叫做 `index.html` 。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693409021539/d0dc8de3-dfba-46d9-b865-cdf7107d2fe2.png align="center")

新建檔案後，在這份 HTML 打一個驚嘆號 `!` ，然後按下 `tab` 按鍵（這是 VS Code 內建 Emmet 快捷語法），你就建立了一份基礎格式的 HTML，接著記得要存檔。而關於 HTML 的介紹，我們下一篇會講解。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693409153116/68541ed8-a997-4bcd-9635-4716db7f7e73.png align="center")

> PS: 這邊的截圖我打錯存成了 htm 檔案，但基本上與 html 是一樣的，關於這個我們一樣在下篇詳細說明。

### 5\. 在 GitHub Desktop 將檔案推送（`Push`）到 GitHub 上

因為我們在這個資料夾有異動了檔案，Git 會追蹤到我們有做更動，於是在 GitHub Desktop 上可以看到一筆變更記錄。我們可以打一些關於這次更新的描述，然後按下「Commit to main」後，會發現這裡多了一筆 Commit 記錄，然後要按下「Push Origin」才會將更新推送到 GitHub 上喔！

另外，GitHub Desktop 會自動幫你確認與雲端上的版本有無差別 (`fetch`)，介面上會在這一格位置顯示目前同步狀態，你也可以再按一次讓它再去 `fetch` 一次，如果雲上的檔案與本地有差異，就會出現提取（`pull` ）選項可以按。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693410371374/a30e89cd-a72d-4753-a79f-e303bcc65e5d.png align="center")

Push 後，在 GitHub 網頁上就會看到剛剛這一個檔案了喔！

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693410491286/9b7b0c6a-55e8-4f55-ad64-2d4cd996808b.png align="center")

### 6\. 新增分支（`branch`）

試試在 GitHub 或 GitHub Desktop 上新增一個分支 `dev`，新增的位置如下圖：

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693411370709/18d60ea3-7ead-485e-acca-8f5a393c1068.png align="center")

因為目前在 `main` 分支上，所以新增的 `dev` 會是從 `main` 分支出來的。`dev` 有異動再 push，就會在 GitHub 上建立這個新分支（不然沒有異動的話新分支都是存在本地端，不會推上去）。

現在，在 GitHub 上，就看得到有 2 個分支了（2 branches）。

### 7\. 在 GitHub 上也能夠編輯檔案

在 GitHub 上也能夠編輯檔案，按進那一個檔案，右邊有個鉛筆按鈕，就可以編輯了喔！編輯時上方會顯示目前是哪個檔案、在哪個分支上。編輯完一樣要 commit，可以選擇是 commit 在目前的分支上，或是要新開一個分支。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693412037137/17caac57-c9c2-413d-b7a9-4b4a790c924d.png align="center")

### 8\. 合併衝突（`merge`）

如果雲上版本和本地 local 版本修改了同一行，就會出現衝突，關於衝突的細節：

* `<<<<<<< HEAD` 到 `=======` 間，是我本地所修改的部分；而
    
* `=======` 到 `>>>>>>> 25f2... (這是雲上那筆紀錄的 id)` 間，則是雲上的版本。
    

在 VS Code 中，已經幫你做了好幾個快速選項，或者你也可以自己手動編輯合併，調整好存檔後就可以 push 解決衝突了。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693412638596/86efc631-26cd-4e7c-a2e3-646f4c243c27.png align="center")

附帶一提，VS Code 旁邊也有 Git 面板可以操作，功能基本上是一樣的，只是畫面操作稍有不同，大家也可以試試看。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693412864855/31dbe643-0080-4c5c-a375-171072acb748.png align="center")

### 9\. 建立免費的 GitHub Page

雖然這不是已經不是 Git 操作的範疇。  
但是，提個很實用的 GitHub 功能，那就是 GitHub Page。

他能幫你部署的網頁到網路上，而且還有 https（有基本的安全性），只不過要免費使用這個功能，你的 repository 必須是公開的，而且有一些[使用限制](https://docs.github.com/zh/pages/getting-started-with-github-pages/about-github-pages#github-pages-%E4%BD%BF%E7%94%A8%E9%99%90%E5%88%B6)，不過在練習和做普通網站上已經綽綽有餘。

在你的 repository 中的 Setting &gt; Pages 中，在 Branch 這一區選擇你希望部署的分支，通常是 `main` ，然後按下 Save。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693477724196/7c8348e3-73c3-4822-b48b-f843b435d783.png align="center")

過幾分鐘後，再重整頁面，它就會告訴你已經成功部署到網路上了，通常預設的連結會是：  
`https://你的帳號名稱.github.io/repository名稱/`

如果你的 repository 名稱是 `你的帳號名稱.github.io` ，你的連結就會是：  
`https://你的帳號名稱.github.io/`

當然，你也可以在下面 Custom domain 換上你自己購買的網址。

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693477730770/27c4b66a-6293-48aa-b445-ab6f0830d47a.png align="center")

關於網域等相關知識可以參考下面這篇文章：

> 連結：[網站與建築的關係](https://blockstudio.tw/blog/the-link-between-the-website-and-the-building)

好的，Git、GitHub、GitHub Desktop 與 GitHub Page 的簡易教學就先到此為止囉！  
恭喜你已經會使用 Git 版控了！

---

## 更進階的 Git 學習

剛剛我們所做的練習，當然除了 GitHub Desktop，也有許多其他的 GUI 軟體可以操作，例如在上一篇有提到的 Sourcetree，也是很好用的軟體。

### 使用指令操作

而在這些軟體上面的操作，其實全部通通都可以用終端機輸入指令運作，以下這個網站有很完整的指令：

> 連結：[Git命令快速參考 | 連猴子都能懂的Git入門指南 | 貝格樂（Backlog）](https://backlog.com/git-tutorial/tw/reference/)

### 更完整的學習資源

這個 Git 猴子，是非常有名又完整的 Git 教學網站，大家有空也可以去看看喔！

> 連結：[連猴子都能懂的Git入門指南 | 貝格樂（Backlog）](https://backlog.com/git-tutorial/tw/)

### Git 的陷阱：不區分大小寫

Git 預設是忽略檔案名稱大小寫的，但是如果雲上可能是有區分大小寫的。如果雲上的版本兩個大寫版本都有，例如同時存在 `index.html` 與 `Index.html`，在本地端可能會造成檔案不管怎麼修改都沒有更新，或不管怎麼樣都刪不掉，像鬼打牆一樣。

這時候可以對受害的檔案或資料夾，試試看這個指令：

```bash
git mv -f OldFileNameCase newfilenamecase
```

更詳細的說明，請參考以下文章：

> 延伸閱讀：  
> [GIT 檔案名稱大小寫修正](https://cola.workxplay.net/fix-git-case-sensitive/)  
> [關於 Git 的檔案名稱大小寫問題與修正](https://israynotarray.com/git/20221230/27133639/)

---

#### ↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓↓

感謝看到最後的你，若你覺得獲益良多，請不要吝嗇給我按個喜歡。❤️

如果你喜歡我的創作，還想看看其他有趣的分享與日常，  
可以追蹤我的 IG [@im1010ioio](https://www.instagram.com/im1010ioio/)，或者是[🧋送杯珍奶鼓勵我](https://im1010ioio.bobaboba.me/)，謝謝你🥰。

![Eva Chen 送杯珍奶鼓勵我](https://cdn.hashnode.com/res/hashnode/image/upload/v1682564435616/c15640fc-6cee-4c33-a898-9cd6820f165a.png align="center")