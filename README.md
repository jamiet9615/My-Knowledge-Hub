# My Knowledge Hub

通用型個人知識庫專案，使用 LLM Wiki 方法將原始資料逐步整理為可連結、可追溯、可持續維護的 Markdown Wiki，並從 Wiki 產生不同形式的成果。

## 目前展示領域

軟體工程（PEP、SRS、SDD 等）。目前先建立專案骨架；正式 Wiki 內容須在提供並確認至少 5 篇合法可用的來源後建立。

## 開始使用

1. 使用 Antigravity 開啟此資料夾。
2. 確認 Claude Sonnet 可讀取根目錄的 `AGENTS.md`。
3. 將 LLM Wiki 方法論文件放在專案中供 Agent 閱讀（本專案附有 `LLM Wiki.md`）。
4. 先與 Agent 討論領域範圍、來源及 Wiki 結構，再開始 ingest。
5. 將取得授權或可合法使用的來源放入 `raw/`。
6. 執行 ingest、query、lint，並將實際執行紀錄寫入 `wiki/log.md`。
7. 由 Wiki 產生 `slide_notes/`，檢查通過後產生 `presentation/`。

## 目錄

- `AGENTS.md`：Agent 工作規範。
- `ideas/`：規劃及討論。
- `raw/`：不可修改的原始來源。
- `wiki/`：整理後知識庫。
- `slide_notes/`：簡報大綱及來源對照。
- `assets/`：選用視覺素材。
- `presentation/`：最終簡報。
- `index.html`：專案入口。

