# AGENTS.md

本文件提供給後續維護者與 AI 代理閱讀，說明此專案的目的、檔案結構、維護方式與注意事項。請以繁體中文溝通與撰寫內容，並優先維持現有靜態網站架構。

## 專案概述

- 專案名稱：FaceBook
- 專案類型：GitHub Pages 靜態網站
- 主要用途：作為 Aaron Hunter 的 Facebook / 社群分享入口，整理研究貼文、科技觀察與公開分享內容。
- 線上網址：https://aaronhunter918.github.io/FaceBook/
- GitHub Repository：https://github.com/aaronhunter918/FaceBook
- 主要分支：`main`

## 目前資料夾結構

```text
FaceBook/
├─ .gitattributes
├─ AGENTS.md
├─ Automation/
│  └─ WindowsCodexDaily_Myles_Edit.md
├─ index.html
└─ Posts/
   └─ 2026-05-30-secureboot-cert/
      ├─ FkMs.png
      └─ index.html
```

## 檔案說明

### `index.html`

首頁檔案，也是 GitHub Pages 進入點。

目前首頁包含：

- 導覽列與品牌標示 `Aaron Hunter`
- 封面式 hero 區塊
- 最新貼文入口
- 專案定位說明
- GitHub Pages 與 GitHub Repository 連結
- 基本 SEO 與 Open Graph 預覽資訊

首頁目前引用的主要圖片：

```text
./Posts/2026-05-30-secureboot-cert/FkMs.png
```

首頁目前引用的主要文章：

```text
./Posts/2026-05-30-secureboot-cert/
```

### `Posts/2026-05-30-secureboot-cert/index.html`

第一篇文章頁。主題為 Secure Boot 2011 / 2023 憑證與 2026 到期相關整理。

文章頁包含：

- 文章標題與摘要
- Open Graph / Twitter Card metadata
- 文章封面圖
- 研究整理內容
- 來源連結

### `Posts/2026-05-30-secureboot-cert/FkMs.png`

文章封面圖，同時也被首頁 hero 與最新貼文卡片使用。

### `.gitattributes`

目前設定文字檔自動偵測並進行換行正規化：

```text
* text=auto
```

### `AGENTS.md`

本文件。用來記錄專案背景、維護規則與後續代理操作注意事項。

## 維護原則

- 使用純 HTML / CSS / 靜態檔案即可，不需要引入建置工具。
- 若沒有明確需求，不要新增框架、套件管理器或複雜的 JavaScript。
- 保持 GitHub Pages 可直接讀取的結構。
- Repo 是技術文章靜態網站；所有文章放在 `Posts/`。
- 每篇文章是一個獨立資料夾，主檔案固定為 `index.html`。
- 新增文章的標準預覽圖檔名固定為 `preview.png`。
- 首頁應維持清楚、好分享、可快速進入文章的設計。
- 文字內容請使用繁體中文。
- HTML 應保留 `lang="zh-Hant"`。
- 圖片路徑請使用相對路徑，方便 GitHub Pages 正常載入。
- 修改前請留意目前 repo 可能已有未提交變更，不要覆蓋使用者的其他修改。

## 新增文章流程

新增文章時，建議依照以下格式建立資料夾：

```text
Posts/YYYY-MM-DD-article-slug/
├─ index.html
└─ preview.png
```

新增文章後，請同步更新首頁 `index.html`：

- 在「最新貼文」區塊新增一張文章卡片。
- 更新文章標題、日期、分類標籤、摘要與連結。
- 若要讓新文章成為主視覺，請同步更新 hero 背景圖片路徑。
- 若社群分享圖片有變更，請更新首頁的 `og:image`。

## Windows Codex Daily Post 自動化

此 Repo 有每日 Windows Codex 文章自動化流程，任務入口說明在：

```text
Automation/WindowsCodexDaily_Myles_Edit.md
```

每日文章輸出資料夾固定為：

```text
Posts/YYYY-MM-DD-windows-codex-daily/
```

每日資料夾內必須包含：

```text
index.html
preview.png
```

維護規則：

- Windows Codex daily post 必須使用 Anysearch skill 搜尋資料。
- 搜尋範圍固定為過去 24 小時。
- 搜尋主題固定為 `Windows Codex`，語言以繁體中文為主。
- 文章必須基於 Anysearch 搜尋結果整理，不得憑空杜撰。
- 不要加入未確認消息；若資料有限，文章中必須明確寫出「過去 24 小時內可整理的繁體中文 Windows Codex 資料有限。」
- 完成每日文章後，必須更新根目錄 `index.html`，讓新文章出現在首頁文章列表較前面的位置。
- 完成後需自動執行 git add、commit、pull --rebase、push。
- Commit message 格式固定為 `Add Windows Codex daily post - YYYY-MM-DD`。
- 提交前必須確認不得包含內部 IP、Token、密碼、公司機敏資訊或其他敏感資料。
- 如果 `git pull --rebase` 發生 conflict，停止 push，保留變更並提示需要人工處理。

## 首頁設計規範

- 首頁第一屏應清楚呈現專案定位與最新內容。
- 避免讓首頁只剩單一文字連結。
- 使用封面圖或實際內容圖片作為主要視覺，不使用純裝飾性的背景。
- 卡片圓角維持在 8px 左右。
- 保持手機與桌面版都能閱讀，不讓文字或按鈕互相重疊。
- 按鈕文字應簡潔，例如「看最新貼文」、「閱讀文章」。
- 色彩可維持目前的藍、青綠、珊瑚與琥珀點綴，不要讓頁面只剩單一色系。

## SEO 與社群預覽

每個公開頁面建議至少包含：

```html
<meta name="description" content="頁面摘要">
<meta property="og:title" content="頁面標題">
<meta property="og:description" content="頁面摘要">
<meta property="og:type" content="website 或 article">
<meta property="og:url" content="完整網址">
<meta property="og:image" content="完整圖片網址">
```

文章頁若要分享到 Facebook、LINE、Discord 或其他社群平台，請確認：

- `og:title` 能清楚說明文章主題。
- `og:description` 不要太長。
- `og:image` 使用完整 GitHub Pages URL。
- 圖片比例建議接近 1200 x 630。

## 發佈與 Git 操作

目前遠端設定：

```text
origin = https://github.com/aaronhunter918/FaceBook.git
branch = main
```

一般發佈流程：

```bash
git status
git add index.html AGENTS.md
git commit -m "Update project documentation"
git push origin main
```

GitHub Pages 更新可能不會立刻生效，通常需要等待一小段時間。

## 注意事項

- 不要修改 `.git/` 內部檔案。
- 不要刪除 `Posts/2026-05-30-secureboot-cert/FkMs.png`，首頁目前依賴這張圖片。
- 若文章或首頁出現中文亂碼，優先檢查檔案是否以 UTF-8 儲存。
- Windows PowerShell 終端有時會顯示中文亂碼，但不一定代表檔案本身已損壞；請用瀏覽器或支援 UTF-8 的編輯器確認。
- 若需要大幅調整文章內容，請先確認來源與原始語意，避免誤改研究結論。

## 快速檢查清單

修改完成後，建議檢查：

- `index.html` 是否可直接用瀏覽器開啟。
- 首頁圖片是否正常載入。
- 最新貼文卡片是否連到正確文章資料夾。
- 手機寬度下導覽列、按鈕與卡片是否不重疊。
- `git status` 是否只包含預期修改。
- 推送後 GitHub Pages 網址是否更新。
