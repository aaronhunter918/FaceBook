# Windows Codex Daily 自動化任務入口

本文件是此 Repo 的每日文章自動化入口說明。Codex App 已建立每日排程；若排程不可用，也可把本文件內容作為手動或 Windows 工作排程觸發時的任務規格。

## 任務目標

- 每天早上依 Asia/Taipei 時區執行一次。
- 使用 Anysearch skill 搜尋過去 24 小時與 `Windows Codex` 相關的繁體中文內容。
- 依搜尋結果建立或更新 `Posts/YYYY-MM-DD-windows-codex-daily/`。
- 每日文章資料夾內固定包含：
  - `index.html`
  - `preview.png`
- 更新根目錄 `index.html`，把最新每日文章卡片放在文章列表較前面。
- 完成安全檢查後執行：
  - `git status`
  - `git add .`
  - `git commit -m "Add Windows Codex daily post - YYYY-MM-DD"`
  - `git pull --rebase`
  - `git push`

## 每日任務規格

1. 搜尋必須使用 Anysearch skill，不使用一般瀏覽器搜尋。
2. 搜尋條件：
   - 關鍵字：`Windows Codex`
   - 語言：繁體中文
   - 時間範圍：過去 24 小時
   - 內容類型：文章、貼文、討論、技術分享
3. 文章必須基於 Anysearch 搜尋結果整理，不得憑空杜撰。
4. 若近 24 小時資料有限，文章內必須寫出：
   - `過去 24 小時內可整理的繁體中文 Windows Codex 資料有限。`
5. 文章至少包含：
   - 今日觀察重點
   - 搜尋結果整理
   - Windows Codex 相關消息摘要
   - 對 MIS / Windows 使用者的影響
   - 值得注意的地方
   - 我的實務看法
   - 結論
6. `preview.png` 需是 Codex + AI + Robot 主題，適合技術部落格卡片，不得有亂碼文字。
7. Commit 前必須檢查不得包含內部 IP、Token、密碼、公司機敏資訊或未確認消息。
8. 若 `git pull --rebase` 發生 conflict，停止 push，保留變更並提示需要人工處理。

## 手動執行提示詞

請在 `C:\Users\Hunter\Desktop\FaceBook` 執行以下工作：

```text
依照 AGENTS.md 與 Automation/WindowsCodexDaily_Myles_Edit.md，建立今天的 Windows Codex daily post。
必須使用 Anysearch skill 搜尋過去 24 小時 Windows Codex 繁體中文內容。
建立或更新 Posts/YYYY-MM-DD-windows-codex-daily/index.html 與 preview.png。
更新根目錄 index.html 的文章卡片。
安全檢查後執行 git add / commit / pull --rebase / push。
```
