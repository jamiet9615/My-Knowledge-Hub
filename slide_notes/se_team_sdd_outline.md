---
presentation_title: "《K33p_1t_s1mpl3》軟體設計文件 (SDD) 專題成果報告"
mode: "B. 組別專屬報告"
target_audience: "老師和同學"
source_wiki_pages: ["../wiki/software_engineering/SDD.md", "../wiki/software_engineering/K33p_1t_s1mpl3.md", "../wiki/software_engineering/SRS.md"]
created: "2026-11-11"
status: "reviewed"
---

# 簡報大綱：《K33p_1t_s1mpl3》軟體設計文件 (SDD) 專題成果報告

## 報告目標
本簡報向老師與同學展示第九組專案《K33p_1t_s1mpl3》如何將 SRS 需求標準化轉化為 SDD 軟體架構與詳細設計：
1. 理解專案的無後端純前端單頁事件驅動架構（Event-driven SPA）與五大解耦模組。
2. 掌握核心模組演算法：指令清洗解析器（Parser）、遊戲狀態機（State Machine）與 LocalStorage 資料模型。
3. 認識專案如何依循 IEEE Std 1016 設計視圖落地，並透過需求可追溯性矩陣（RTM）確保 100% 覆蓋功能與非功能需求。

## 故事線
從文字解謎遊戲的黑白極簡 Terminal 概念切入，說明如何以軟體工程思維將 SRS 需求透過 IEEE 1016 框架拆解為五大解耦模組；深入剖析指令解析、狀態機動態管理與資料字典設計；展示防呆與效能對策，最後以 RTM 追溯與專案未來展望收尾。

---

## 逐頁大綱

### 第 1 頁：封面
- **標題**：《K33p_1t_s1mpl3》軟體設計文件 (SDD)
- **副標題**：以 IEEE Std 1016 為準則之架構分解、狀態機與指令解析實作
- **報告團隊**：輔仁大學人工智慧與資訊安全學士學位學程 第九組（王文伶、杜汯溱、余苡萱、吳千心、王瑀彤）
- **指導教授**：杜海倫 教授
- **日期**：2026 年 11 月
- **Wiki 來源**：[K33p_1t_s1mpl3.md](../wiki/software_engineering/K33p_1t_s1mpl3.md)

### 第 2 頁：專案背景與設計目標
- **核心訊息**：將心理驚悚敘事與 Terminal 文字指令解謎結合，並以純前端架構實現極致順暢度與高穩定性。
- **報告目的**：建立聽眾對專案背景與技術邊界（無後端、純原生 JS、SPA）的基礎認知。
- **建議視覺**：三欄對比卡片（願景、技術邊界、三大品質指標：0.1s 回應、100% 防呆、3s 載入）。
- **Wiki 來源**：[K33p_1t_s1mpl3.md](../wiki/software_engineering/K33p_1t_s1mpl3.md), [SRS.md](../wiki/software_engineering/SRS.md)
- **注意**：清楚說明不設後端是為免除帳號管理風險並符合 NF-07/NF-08。

### 第 3 頁：系統架構設計 — 單頁事件驅動五模組
- **核心訊息**：依照 IEEE 1016 分解視圖，將系統清晰解耦為五大職責模組，達成高內聚、低耦合。
- **報告目的**：展示系統整體結構與人員分工對齊。
- **建議視覺**：五模組結構圖與責任表（`parser.js`、`state.js`、`ui.js`、`errorHandler.js`、`audio.js`）。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md)
- **注意**：註記模組對應負責同學。

### 第 4 頁：相依視圖與單次指令資料流
- **核心訊息**：從玩家按下 Enter 到打字機文字呈現，各模組透過標準資料流單向閉環協作。
- **報告目的**：讓老師同學理解執行期流程與事件驅動生命週期。
- **建議視覺**：Mermaid 循序圖或資料流向圖（Input → Parser → State → LocalStorage → UI → Audio）。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md)
- **注意**：強調 LocalStorage 在狀態變更時自動觸發 autosave。

### 第 5 頁：核心元件設計 (一)：指令解析模組 (parser.js)
- **核心訊息**：多層過濾、正規表達式捕捉與多人代號嚴格升冪防呆機制。
- **報告目的**：深入解密如何支援單人 `05_HO_05`、多人 `05_HO_123` 及關鍵字指令。
- **建議視覺**：語法比對規則表與演算法解析虛擬碼。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md), [SRS.md](../wiki/software_engineering/SRS.md)
- **注意**：強調錯誤不崩潰，未知指令返回特定錯誤物件。

### 第 6 頁：核心元件設計 (二)：遊戲狀態管理 (state.js)
- **核心訊息**：狀態機集中控管 14 幕劇情推進、五位人格角色命名與符文連線序列。
- **報告目的**：說明遊戲邏輯的嚴謹性，包括條件前置檢驗與 13~14 幕的關鍵解謎。
- **建議視覺**：狀態機流程圖與符文判定序列（`301 → 204 → 205 → 103`）。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md), [K33p_1t_s1mpl3.md](../wiki/software_engineering/K33p_1t_s1mpl3.md)
- **注意**：提及完成序列將觸發輪迴結局 (Knock Knock)。

### 第 7 頁：資料設計與 LocalStorage 儲存模型
- **核心訊息**：輕量化的 JSON 資料結構完整持久化遊戲進度，兼顧可靠性與隱私。
- **報告目的**：展示資料字典（Data Dictionary）與存讀檔（Save/Load）容錯設計。
- **建議視覺**：JSON 結構高亮與欄位字典表格（chapter, names, unlocked, runeConnections 等）。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md)
- **注意**：說明若存檔損毀不覆蓋目前執行狀態（保護資料可靠性 NF-06）。

### 第 8 頁：人機介面 (UI) 與錯誤處理 (Error Handling)
- **核心訊息**：純 CSS/JS 打字機逐字渲染、可跳過機制，以及符合心理驚悚氛圍的錯誤回饋。
- **報告目的**：展示前端終端機視覺美學與防護網設計。
- **建議視覺**：ASCII 終端風格原型示意圖與錯誤訊息風格範例對比。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md), [K33p_1t_s1mpl3.md](../wiki/software_engineering/K33p_1t_s1mpl3.md)
- **注意**：說明禁止使用瀏覽器原生的 alert()，全面維持遊戲沉浸感。

### 第 9 頁：需求可追溯性矩陣 (RTM) 與品質驗收
- **核心訊息**：SDD 完整落實 SRS 的 12 項功能需求 (F-01~F-12) 與 10 項非功能需求 (NF-01~NF-10)。
- **報告目的**：以工程化指標向評審老師證明設計的完備性與可驗證性。
- **建議視覺**：需求至模組的追溯矩陣表 (RTM) 與非功能指標對策清單。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md), [SRS.md](../wiki/software_engineering/SRS.md)
- **注意**：防呆覆蓋率與回應時間的量化設計依據。

### 第 10 頁：總結與未來展望
- **核心訊息**：以嚴謹軟體工程規範打造極簡且具深度之作品，並具備清晰的測試與擴充規劃。
- **報告目的**：收尾並銜接下一階段 STD 測試與上線展示。
- **建議視覺**：專案里程碑回顧與後續 STD / Demo 展望清單。
- **Wiki 來源**：[PEP.md](../wiki/software_engineering/PEP.md), [SDD.md](../wiki/software_engineering/SDD.md)

### 第 11 頁：來源清單 (References，必要頁面)
- **核心訊息**：列出本份簡報主張所依據之正式專案文件與 IEEE 標準規範。
- **格式**：
  - 輔仁大學人工智慧與資訊安全學士學位學程第九組（2026）。軟體設計文件 (SDD) —— K33p_1t_s1mpl3 (SDD-2026-001-1 v1.1)。[組別文件]
  - 輔仁大學人工智慧與資訊安全學士學位學程第九組（2026）。系統需求規格書 (SRS) —— K33p_1t_s1mpl3 (SRS-2026-001-1 v1.0)。[組別文件]
  - 輔仁大學人工智慧與資訊安全學士學位學程第九組（2026）。專案執行計畫書 (PEP) —— K33p_1t_s1mpl3。[組別文件]
  - IEEE Computer Society（1998）。IEEE Recommended Practice for Software Design Descriptions (IEEE Std 1016-1998)。[IEEE 標準]
  - IEEE Computer Society（2009）。IEEE Standard for Information Technology -- Systems Design -- Software Design Descriptions (IEEE Std 1016-2009)。[IEEE 標準]

---

## 內容檢查清單

### 結構與順序
- [x] 教學/報告順序對受眾（老師和同學）合理，由淺入深，不跳躍前提知識
- [x] 每頁只傳達一個主要觀念
- [x] 有封面頁與來源清單頁

### 來源與事實
- [x] 每頁有 Wiki 來源對照
- [x] 無來源的數字、百分比、研究結論或引言（幻覺檢查通過）
- [x] 沒有超出來源範圍的推論或誇大表述（誇大檢查通過）
- [x] 來源清單頁列出所有實際使用的 `raw/` 來源

### 語言
- [x] 正文為中文，英文僅用於專有名詞（如 SDD, SRS, Parser, State Machine, LocalStorage 等）
- [x] 首次出現的專有名詞有簡短白話說明

### HTML 技術檢查（產生後填寫）
- [x] 瀏覽器可正常開啟，支援完全離線使用
- [x] 上一頁/下一頁按鈕導覽正常，支援鍵盤左右方向鍵、空白鍵、P/N 鍵
- [x] 文字未溢出，黑白 Terminal 主題配色質感良好
- [x] 進度條與頁碼顯示同步動態更新
