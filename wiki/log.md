# Wiki Operation Log

此檔案採追加式紀錄。每次 ingest、query、lint 或重要修正後新增一筆，不覆寫舊紀錄。

## [2026-11-10] initialize | 建立 My Knowledge Hub 專案骨架
- 建立基本資料夾及工作規範。
- 尚未執行正式來源 ingest。
- 尚未建立正式軟體工程知識頁。
- 待辦：加入並確認至少五篇合法可用的來源，再執行 ingest。

## [2026-11-11] ingest | 完成軟體工程領域 6 份來源 Ingest 與 5 篇核心知識頁建立
- **讀取來源**：
  1. `se_ieee830_1998.pdf`（SRS 大綱範例模板）
  2. `se_ieee1016_1998.pdf`（IEEE Std 1016-1998 SDD 實務標準）
  3. `se_ieee1016_2009.pdf`（IEEE Std 1016-2009 現代架構設計標準）
  4. `se_ieee829_1983.pdf`（Sneed & Seidl 關於 IEEE 829 與 ISO 29119 測試文件之學術論文）
  5. `se_pep_team_2026.pdf`（第九組專案執行計畫書 K33p_1t_s1mpl3）
  6. `se_srs_team_2026.pdf`（第九組系統需求規格書 K33p_1t_s1mpl3）
- **建立/更新頁面**：
  - `wiki/software_engineering/SRS.md`
  - `wiki/software_engineering/PEP.md`
  - `wiki/software_engineering/SDD.md`
  - `wiki/software_engineering/STD.md`
  - `wiki/software_engineering/K33p_1t_s1mpl3.md`
  - `wiki/index.md`
  - `raw/software_engineering/_sources_meta.md`
- **確認與決策**：
  - 使用者確認 IEEE 830 採範例模板定位（選項 A）。
  - 使用者保留 IEEE 1016 舊版（更名為 1998）並補入 2009 版，已於 SDD.md 中完成對比與整合。
  - 使用者確認 IEEE 829 採學術論文/評述文章定位（選項 A）。
  - PEP 與 SRS 內容核對無實質矛盾。

## [2026-11-11] lint | 軟體工程 Wiki 知識庫完整健康檢查
- **來源檔案存在性**：6 份來源全部 PASS（`se_ieee830_1998.pdf`, `se_ieee1016_1998.pdf`, `se_ieee1016_2009.pdf`, `se_ieee829_1983.pdf`, `se_pep_team_2026.pdf`, `se_srs_team_2026.pdf`）。
- **正式 Wiki 檔案**：5 篇核心知識頁面全部 PASS。
- **Wiki Index 連結**：所有 5 個指向知識頁的相對路徑皆有效（PASS）。
- **內部雙向參照連結**：頁面間相互參照連結無任何失效（PASS）。
- **幻覺與誇大檢查**：所有功能需求條目（F-01~F-12）、非功能需求指標（0.1s 回應、100% 防呆、3s 載入）、五重人格設定與 16 週時程均嚴格對齊 raw 文件（PASS）。

## [2026-11-11] query | 產生第九組《K33p_1t_s1mpl3》軟體設計文件 (SDD) HTML 專題成果報告
- **查詢依據**：
  - `wiki/software_engineering/SDD.md`
  - `wiki/software_engineering/K33p_1t_s1mpl3.md`
  - `wiki/software_engineering/SRS.md`
  - `wiki/software_engineering/PEP.md`
- **產出檔案**：
  - 簡報大綱與檢查清單：`slide_notes/se_team_sdd_outline.md`
  - 最終 HTML 簡報：`presentation/index.html`（共 11 頁，黑白極簡 Terminal 風格，離線支援，鍵盤導覽）
  - 專案入口更新：`index.html`
- **內容特色**：
  - 涵蓋五模組分解（`parser.js`、`state.js`、`ui.js`、`errorHandler.js`、`audio.js`）。
  - 單次指令處理資料流與事件驅動閉環。
  - 核心演算法：正則表達式語法解析、嚴格升冪多人防呆、14 幕狀態機推進、符文連線判定序列（301→204→205→103）。
  - LocalStorage JSON 資料結構與損毀防護（NF-06）。
  - 沉浸式驚悚錯誤處理與 RTM 雙向追溯矩陣。
  - 末頁嚴格遵循標準包含正式「來源清單」。

## [2026-11-11] query | 產生模式 A 通用教學簡報《解構 IEEE Std 1016：軟體設計描述 (SDD) 撰寫邏輯與標準實務》
- **查詢依據**：
  - `wiki/software_engineering/SDD.md`
  - `wiki/software_engineering/SRS.md`
  - `wiki/software_engineering/K33p_1t_s1mpl3.md`
- **產出檔案**：
  - 簡報大綱與檢查清單：`slide_notes/se_ieee1016_tutorial_outline.md`
  - 最終 HTML 簡報：`presentation/sdd_tutorial.html`（共 11 頁，清新暖色可愛手帳風格，純原生離線支援，鍵盤導覽）
  - 專案入口更新：`index.html`（支援雙簡報切換導覽）
- **視覺與設計規範**：
  - 遵循使用者自訂之溫暖色調配色（`#FEF9E3`, `#FBF7EE`, `#2B5B76`, `#5C7A8C`, `#F4B3C2`, `#8ECFE3`, `#7FCDC5`, `#F7E5A8`）。
  - 採用大圓角卡片、柔和手帳陰影、彩色便簽與友善排版，消除冷酷 AI 感。
- **內容特色**：
  - 從 What (SRS) 到 How (SDD) 的架構橋樑。
  - 設計實體 (Design Entity) 與 IEEE 1016-1998 十大黃金屬性詳解。
  - 四大經典設計視圖（分解、相依、介面、詳細設計）。
  - 現代演進：對齊 ISO/IEC 42010 架構視點體系。
  - 結合第九組《K33p_1t_s1mpl3》實例對照。
  - 三大黃金原則、避坑指南與五步撰寫指引。
  - 末頁嚴格遵循規範附帶正式「來源清單」。
