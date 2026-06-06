# Codex Skill GitHub Top20 Weekly 自動化任務

本文件是此 Repo 的每週 Codex Skill GitHub 熱門專案整理任務入口。Codex App 已建立週期排程；若排程暫時不可用，也可以依照本文件作為手動執行規格。

## 任務名稱

Codex Skill GitHub Top20 Weekly

## 任務目的

- 每週整理 GitHub 上過去 7 天內有更新，且與 Codex Skill、Codex Skills、OpenAI Codex Skill、Agent Skill、Codex agents、Codex plugin 或 Codex automation 相關的熱門 Repository。
- 依 GitHub Stars 由高到低排序，取 TOP20。
- 產生一篇繁體中文技術整理文章，更新首頁文章列表，最後完成 Git commit 與 push。

## 專案路徑

所有讀取、寫入、文章產生、首頁更新與 Git 操作都必須在下列 Repo 根目錄執行：

```text
C:\Users\Hunter\Desktop\FaceBook
```

不要在其他資料夾建立檔案，不要修改 Git remote URL，不要改動既有 GitHub Pages 架構。

## 排程設定

- 頻率：每週一次
- 執行時間：每週六 19:00
- 時區：Asia/Taipei
- Codex App automation id：`codex-skill-github-top20-weekly`

## Anysearch Skill

任務必須使用 Anysearch skill 搜尋資料。

Skill 路徑：

```text
C:\Users\Hunter\.codex\skills\anysearch\SKILL.md
```

建議搜尋方向：

- `Codex skill`
- `Codex skills`
- `OpenAI Codex skill`
- `Agent skill`
- `Codex agents`
- `Codex plugin`
- `Codex automation`

注意：不要把「繁體中文」當成 GitHub Repository 的語言篩選條件。GitHub 專案語言應保留原始資料，例如 Python、TypeScript、Shell、HTML。

## 搜尋條件

- 搜尋平台：GitHub Repository
- 更新範圍：過去 7 天內有 push 或等效更新
- 排序依據：GitHub Stars 由高到低
- 數量：TOP20
- 必須排除與 Codex Skill / Agent Skill / Codex plugin / Codex automation 關聯不明確的項目
- 不得加入未確認消息
- 不得憑空杜撰 stars、forks、主要語言、最近 push 時間或 description

如果可驗證結果不足 20 個，只列出實際找到且可驗證的項目，並在文章中明確寫出：

```text
過去一週內符合條件且可驗證的 GitHub Codex Skill 相關專案不足 20 個。
```

## 文章輸出路徑

每週文章資料夾格式：

```text
Posts/YYYY-MM-DD-codex-skill-github-top20/
```

文章主檔案：

```text
Posts/YYYY-MM-DD-codex-skill-github-top20/index.html
```

若首頁卡片或 Open Graph 需要圖片，預覽圖固定放在：

```text
Posts/YYYY-MM-DD-codex-skill-github-top20/preview.png
```

如果同一天資料夾已存在，更新既有資料夾內的 `index.html` 與 `preview.png`，不要建立第二個同日期資料夾。

## 表格欄位

文章排名表至少包含：

1. 排名
2. 專案
3. Stars
4. Forks
5. 語言
6. 最近 Push
7. 原始描述
8. 功能簡介

欄位規則：

- 專案名稱必須連結到 GitHub 原始 Repository。
- Stars、Forks、主要語言、最近 Push 必須來自 GitHub 可驗證資料。
- 最近 Push 使用 `YYYY-MM-DD` 格式。
- 原始描述使用 GitHub Repository description；如果空白，標示「未提供描述」。
- 功能簡介可以用繁體中文整理，但必須基於原始描述、README 或 Repository 內容。
- 無法確認的欄位標示「未確認」。

## 文章內容要求

文章標題固定使用：

```text
GitHub Codex Skill 熱門專案 TOP20
```

文章內容至少包含：

- 前言
- 搜尋條件
- TOP20 排名表格
- 觀察重點
- 適合 MIS / 技術人員注意的項目
- 本週變化簡述
- 結語

文章中必須標示：

- 資料整理日期
- 搜尋時間範圍
- 排序依據
- 資料來源為 Anysearch 搜尋結果與 GitHub 可驗證 Repository 資料

文章底部必須加入提醒：

```text
Stars、Forks 與最近 Push 時間會隨 GitHub 即時變動，此頁保留本次整理結果。
```

## 首頁更新規則

完成文章後必須更新根目錄：

```text
index.html
```

要求：

- 將新文章加入首頁「最新貼文」或文章列表區塊。
- 新文章連結指向 `./Posts/YYYY-MM-DD-codex-skill-github-top20/`。
- 新文章放在文章列表較前面的位置。
- 保留既有 HTML / CSS 風格。
- 不要移除既有文章。
- 不要刪除或替換 Secure Boot 文章圖片。
- 沒有必要時，不要任意更動 hero 區塊。

## Git 流程

完成文章、首頁與文件更新後，在 Repo 根目錄執行：

```text
git status
git add .
git commit -m "Add Codex Skill GitHub Top20 - YYYY-MM-DD"
git pull --rebase origin main
git push origin main
```

如果沒有任何實際變更，不要建立空 commit。

## 安全檢查

提交前必須確認：

- 不包含內部 IP
- 不包含 Token
- 不包含密碼
- 不包含公司機敏資訊
- 不包含未確認消息
- 不包含暫存檔、log 檔、cache 檔或不必要檔案
- 未修改 Git remote URL
- 未修改 unrelated files

如果發現敏感資訊，停止 commit / push 並提示 Hunter 檢查。

## Conflict 處理

如果 `git pull --rebase origin main` 發生 conflict：

- 停止 push
- 保留目前變更
- 回報 conflict 檔案與狀態
- 等待人工處理

不要強制 push，不要使用 `git push --force`。

## 手動執行提示詞

可在 `C:\Users\Hunter\Desktop\FaceBook` 手動要求 Codex 執行：

```text
依照 AGENTS.md 與 Automation/CodexSkillGitHubTop20Weekly_Myles_Edit.md，建立或更新今天的 Codex Skill GitHub Top20 Weekly 文章。必須使用 Anysearch skill 搜尋過去 7 天內有更新的 GitHub Codex Skill / Agent Skill 相關 Repository，依 GitHub Stars 由高到低整理 TOP20。建立或更新 Posts/YYYY-MM-DD-codex-skill-github-top20/index.html 與必要的 preview.png，更新根目錄 index.html，安全檢查後執行 git add / commit / pull --rebase / push。
```
