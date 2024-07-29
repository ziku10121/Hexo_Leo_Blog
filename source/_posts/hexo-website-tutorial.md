---
title: Hexo 架設個人部落格
date: 2024-07-25 20:50:05
tags:
  - Hexo
  - notes
---

# 介紹

本篇介紹如何利用 Hexo 框架與 GitHub Page 服務來架設完全免費的個人 Blog，讓自己成為徹徹底底的免費仔。

<!-- more -->

## 什麼人適合用 Hexo?

適合技術愛好者、分享技術與筆記、能自由建立和經營個人空間、不受平台限制、且不需額外花費即可架設自己網站的地方。

要充分利用 Hexo 的特性和功能，使用者需要學習並掌握 Markdown 語法。儘管 Markdown 語法相對簡單，但對於新手來說，仍需要時間和練習才能熟練運用。然而，對於願意學習新語法的人來說，這是一個值得投資的過程。

# 前置作業

- VSCode (編輯器)
- Node.js + npm (Hexo 官方建議使用 Node.js 10.0 及以上版本)
- Git (版本控制)

# 環境建置

## 安裝 Hexo

開啟 CLI 介面(終端機)，並輸入下列指令：

```console
$ npm install hexo-cli -g
```

## 查看 Hexo 版本

安裝完成，輸入<mark style="background-color:#e7e9eb;color:#ff0000; "> hexo -v </mark>查看 Hexo 版本，確認是否安裝成功。
<image style="margin:0;" src="https://firebasestorage.googleapis.com/v0/b/leoli-blog.appspot.com/o/hexo-version.jpg?alt=media&token=6a859fa1-0879-42fe-8911-8a5d48214dad" alt="hexo-version" width="300">

## 初始化 Hexo

建立一個新的網站。Hexo 會在目前的資料夾建立網站。

```console
$ hexo init '資料夾名稱'
```

### 確認檔案

```console
├── node_modules  存放該專案所依賴的工具
├── scaffolds     建立新文章的Layout
├── source        網站所有的資源(Markdown檔、圖片、文章...)
├── themes        主題資料夾
├── _config.yml   網站配置檔案
└── package.json  紀錄專案所需要的模組套件
```

# 常用指令

## 套件管理

安裝 package.json 所記錄的 library

```console
$ npm install
```

## new 新增文章

```console
hexo new [layout] "MyNewPost"
```

<mark style="background-color:#e7e9eb;color:#ff0000;">/source/\_posts/<span style="color:#5cb85c;">MyNewPost.md</span></mark> 編輯文章內容
檔案名稱盡量以英文命名，避免出現亂碼

## server 啟動伺服器

```console
$ hexo server
```

## generate 產生靜態檔案

建立出<mark style="background-color:#ff00004a">public 資料夾</mark>，可放置 GitHub Page 架設網站

```console
$ hexo generate
```

## clean 暫存清空

資料修改後看不到更改畫面

```console
$ hexo clean
```

````建議在修正後的檔案之前，輸入此指令來清除快取檔案(db.json)
## Deploy 部屬

```console
$ hexo deploy
````

## 新增頁面

```console
$ hexo new page 頁面
```

http：//localhost:4000/about/index.html

# 架設網站

在架設網站之前，還必須準備存放網站的空間，例如架設主機、現有的平台(ex:GitHub Page or Heroku …)。

## 建立 GitHub 空間

**Step 1.** 需準備好 Git、註冊 GitHub 服務

**Step 2.** 點選右上『＋』，新增 New repository(專案）

**Step 3.** 將專案名稱命名設定
<image style="margin:0;" src="https://firebasestorage.googleapis.com/v0/b/leoli-blog.appspot.com/o/git-repository.jpg?alt=media&token=e649a51d-0dd4-43dd-b92f-0cb020065cb7" alt="github-repository" width="600">
獲得該空間的網址: <lable style="color:#ff0000;">https：//github.com/username/空間專案名稱</lable>

## 專案一鍵部屬

**Step 1.** Install

```console
$ npm install hexo-deployer-git --save
```

**Step 2.** 修改設定
修改 \_config.yml 設定檔中的 Deploy 的設定。

```console
deploy:
  type: git
  repo: https://github.com/[username]/[空間專案名稱]
  branch: master
  message: "Update Blog"
```

- type：部屬模式
- repo：儲存庫(Github repository)的 url
- branch：選擇分支，預設 master
- message：commit 訊息
  **Step 3. 部屬**
  第一次使用部署指令會要求登入 GitHub 帳號。

```console
$ hexo deploy
```

每次修改後，依序輸入執行 clean → generate → deploy 三向指令來完成更新。

**Step 4.** 設置 GitHub Pages
至 GitHub 空間上 > Settings > 左側 Pages > 設定 Branch
<image style="margin:0;" src="https://firebasestorage.googleapis.com/v0/b/leoli-blog.appspot.com/o/github-pages.jpg?alt=media&token=64219565-2700-428a-a8e5-a1425a78c86a" alt="github-pages" width="100%">

預設畫面：
<image style="margin:0;" src="https://firebasestorage.googleapis.com/v0/b/leoli-blog.appspot.com/o/blog.jpg?alt=media&token=b66b596d-033b-4e40-a36d-534b467640dc" alt="blog" width="100%">
