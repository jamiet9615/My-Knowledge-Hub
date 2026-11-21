---
presentation_title: "解構 IEEE Std 1016：軟體設計描述 (SDD) 撰寫邏輯與標準實務"
mode: "A. IEEE 通用教學"
target_audience: "老師和同學"
source_wiki_pages: ["../wiki/software_engineering/SDD.md", "../wiki/software_engineering/SRS.md"]
created: "2026-11-11"
status: "reviewed"
---

# 簡報大綱：解構 IEEE Std 1016：軟體設計描述 (SDD) 撰寫邏輯與標準實務

## 教學目標
本簡報為同學與老師提供一份清晰、系統化且親切的 SDD 撰寫教學：
1. 理解為什麼軟體開發需要 SDD，以及 SDD 如何銜接 SRS (What) 與程式碼實作 (How)。
2. 掌握 IEEE Std 1016 核心設計實體（Design Entity）的 10 項黃金屬性。
3. 學會使用四種經典設計視圖（分解、相依、介面、詳細設計）與現代 ISO/IEC 42010 架構視點組織文件。
4. 避免過早沉溺程式碼細節、維持雙向需求可追溯性（Traceability）。

## 故事線
從現實軟體開發中「需求很美好，實作一團糟」的困境出發，溫柔揭示 SDD 作為系統設計藍圖的重要性；用擬人化與圖解方式帶出 IEEE 1016 的設計實體 10 項屬性；介紹四大設計視角，並以第九組網頁解謎遊戲為實作範例對照，最後整理出一套好寫、好懂的 SDD 撰寫最佳步驟。

---

## 逐頁大綱

### 第 1 頁：封面
- **標題**：解構 IEEE Std 1016
- **副標題**：軟體設計描述 (SDD) 撰寫邏輯與標準實務入門
- **受眾與場合**：課堂教學與通識介紹（老師與同學）
- **風格定位**：手帳清新可愛風（暖鵝黃、莫蘭迪粉藍與櫻花粉配色）
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md)

### 第 2 頁：為什麼我們需要 SDD？（從 What 走到 How）
- **核心訊息**：SRS 告訴我們「系統該做什麼」，SDD 則指引工程師「系統該如何建構」。
- **教學目的**：說明需求規格與程式實作之間的斷層，建立 SDD 作為溝通橋樑的重要性。
- **建議視覺**：橋樑對比卡片（左：SRS 需求清單；中：SDD 藍圖橋樑；右：程式碼實作）。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md), [SRS.md](../wiki/software_engineering/SRS.md)
- **注意**：清楚說明沒有 SDD 容易導致架構隨意拼裝與維護災難。

### 第 3 頁：SDD 的靈魂：設計實體 (Design Entity)
- **核心訊息**：任何軟體系統都是由具有獨立命名與責任的「設計實體」堆疊而成。
- **教學目的**：介紹 IEEE 1016 的基本本體論（實體可以是模組、類別、子系統、資料庫或程序）。
- **建議視覺**：積木組合圖解與實體定義卡片。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md)
- **注意**：強調「高內聚、低耦合」的設計初衷。

### 第 4 頁：設計實體的 10 項黃金屬性 (Attributes)
- **核心訊息**：描述一個設計實體，標準規定了這 10 個不能少的問題。
- **教學目的**：系統梳理 IEEE 1016-1998 Clause 5.3 的 10 個核心要素。
- **建議視覺**：雙欄分類卡片（基礎身份類：名稱、類型、目的、功能；架構關聯類：從屬、相依、介面、資源；內部細節類：處理邏輯、資料結構）。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md)
- **注意**：說明若無特定內容可標記為 None，但不可直接遺漏。

### 第 5 頁：IEEE 1016-1998 四大經典設計視圖 (Design Views)
- **核心訊息**：不同專案角色看系統的角度不同，四種視圖讓每個人找到需要的資訊。
- **教學目的**：介紹分解視圖、相依視圖、介面視圖與詳細設計視圖的分工。
- **建議視覺**：四象限彩色卡片（配搭可愛圖示）。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md)
- **注意**：為每種視圖標明目標讀者（專案經理、系統架構師、前端/後端工程師、維護者）。

### 第 6 頁：現代演進：IEEE 1016-2009 與 ISO/IEC 42010
- **核心訊息**：從「單純功能分解」走向以「利害關係人關注點」為導向的架構視點體系。
- **教學目的**：介紹 2009 年版本標準的現代轉變，相容物件導向、元件與微服務。
- **建議視覺**：架構視點羅盤（上下文視點、邏輯視點、資訊視點、互動與動態狀態視點）。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md)
- **注意**：用白話說明 Viewpoint（視點/規範）與 View（視圖/實例）的區別。

### 第 7 頁：實務對照：以《K33p_1t_s1mpl3》落地為例
- **核心訊息**：標準不是死板教條，第九組網頁解謎遊戲就是 IEEE 1016 實踐範本。
- **教學目的**：將理論直接對接真實專案，讓同學看懂實際寫出來長什麼樣子。
- **建議視覺**：對照表格（分解：五模組；相依：資料流事件循環；詳細：正則解析與狀態機演算法）。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md), [K33p_1t_s1mpl3.md](../wiki/software_engineering/K33p_1t_s1mpl3.md)
- **注意**：點出團隊如何用 LocalStorage 落地資料字典。

### 第 8 頁：撰寫 SDD 的三大黃金原則與常見陷阱
- **核心訊息**：掌握三個原則，避開「把程式碼直接貼成文件」的最大雷區。
- **教學目的**：提供實務建議：雙向追溯 (Traceability)、適度抽象 (Abstraction)、關注點分離 (Separation of Concerns)。
- **建議視覺**：打勾與叉叉對比清單（Do & Don't）。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md)
- **注意**：強調需求追溯矩陣（RTM）在驗收與評審時的重要性。

### 第 9 頁：五步驟撰寫指引 (Quick Checklist)
- **核心訊息**：一步一步跟著做，新手也能產出一份合格的 SDD。
- **教學目的**：歸納 Actionable 的執行步驟。
- **建議視覺**：可愛的進度步驟條（1. 劃定邊界 ➔ 2. 模組切分 ➔ 3. 定義介面 ➔ 4. 設計演算法與資料 ➔ 5. 繪製 RTM 驗收）。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md)

### 第 10 頁：總結 (Key Takeaways)
- **核心訊息**：好的軟體設計文件是團隊溝通的橋樑，也是系統可維護性的基石。
- **教學目的**：複習核心重點，給同學打氣鼓勵。
- **建議視覺**：三顆暖色總結小卡。
- **Wiki 來源**：[SDD.md](../wiki/software_engineering/SDD.md)

### 第 11 頁：來源清單 (References，必要頁面)
- **核心訊息**：標準條文與參考文獻來源。
- **格式**：
  - IEEE Computer Society（1998）。IEEE Recommended Practice for Software Design Descriptions (IEEE Std 1016-1998)。[IEEE 標準]
  - IEEE Computer Society（2009）。IEEE Standard for Information Technology -- Systems Design -- Software Design Descriptions (IEEE Std 1016-2009)。[IEEE 標準]
  - 輔仁大學人工智慧與資訊安全學士學位學程第九組（2026）。軟體設計文件 (SDD) —— K33p_1t_s1mpl3 (SDD-2026-001-1 v1.1)。[組別實例]

---

## 內容檢查清單
- [x] 教學順序對受眾（老師和同學）循序漸進，由淺入深
- [x] 每頁只傳達一個主要觀念
- [x] 具備封面頁與來源清單頁
- [x] 每頁均有 Wiki 來源對照
- [x] 幻覺檢查與誇大檢查通過
- [x] 正文使用中文，英文僅保留專有名詞
- [x] HTML 支援完全離線使用、圓角暖色可愛風格
