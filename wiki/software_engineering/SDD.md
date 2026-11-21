---
title: "軟體設計描述 (Software Design Description, SDD)"
domain: "software_engineering"
created: "2026-11-11"
updated: "2026-11-11"
tags: ["SDD", "IEEE 1016", "軟體架構", "設計實體", "設計視點", "ISO/IEC 42010"]
sources: ["se_ieee1016_1998.pdf", "se_ieee1016_2009.pdf", "se_sdd_team_2026.pdf"]
status: "reviewed"
---

# 軟體設計描述 (Software Design Description, SDD)

## 摘要
軟體設計描述（Software Design Description, SDD）是軟體系統架構與實作藍圖的正式呈現媒介。它承接 SRS 中的需求，將其轉換為系統組件、介面、資料結構及處理邏輯。本頁綜合 IEEE Std 1016-1998（經典設計實體屬性與視圖）及 IEEE Std 1016-2009（基於 ISO/IEC 42010 架構概念框架的演進版本），詳解 SDD 的核心概念、資訊模型與設計組織方式。

## 核心概念

### 1. SDD 在軟體生命週期中的定位
- **需求轉譯為藍圖**：SRS 描述「系統要做什麼 (What)」，SDD 描述「系統如何被建構 (How)」（參見 IEEE 1016-1998 Clause 4.3）。
- **可追溯性基準**：SDD 中的每一個設計實體（Design Entity），都必須能雙向追溯至 SRS 的特定功能或效能需求。
- **實作者與利害關係人的通訊媒介**：供專案經理、系統架構師、程式設計師、測試工程師與維護人員獲取相應視角的設計決策。

### 2. IEEE 1016-1998 的資訊模型：設計實體與 10 項屬性
IEEE 1016-1998 採用實體-屬性（Entity-Attribute）模型。一個完整的 SDD 必須針對每個設計實體定義以下 10 項基本屬性（Clause 5.3）：
1. **識別 (Identification)**：實體唯一的命名與代號，不可重複（5.3.1）。
2. **類型 (Type)**：實體的性質（如子系統、模組、程序、行程、資料庫、物件）（5.3.2）。
3. **目的 (Purpose)**：該實體為何存在，指名其對應的特定需求（5.3.3）。
4. **功能 (Function)**：實體對輸入進行何種轉換以產生輸出（5.3.4）。
5. **從屬組件 (Subordinates)**：實體的子組成結構（Composed of 關係），支援階層分解（5.3.5）。
6. **相依性 (Dependencies)**：實體與其他實體的呼叫、共享資料或先後序關係（Uses 關係）（5.3.6）。
7. **介面 (Interface)**：外部如何與該實體互動，包含呼叫方法、通訊協定、參數格式、數值範圍與錯誤碼（5.3.7）。
8. **資源 (Resources)**：實體運作所需的外部資源（如 CPU、記憶體緩衝區、磁碟分割、OS 服務、競爭防範）（5.3.8）。
9. **處理邏輯 (Processing)**：實體內部執行演算法、循序步驟、條件分支與異常處理細節（5.3.9）。
10. **資料 (Data)**：內部資料結構、儲存方式、型態、初值與存取約束（5.3.10）。

### 3. IEEE 1016-1998 的四種核心設計視圖 (Design Views)
為滿足不同專案角色的需要，標準推薦將實體屬性組織為四種視圖（Clause 6.2）：
| 設計視圖 (Design View) | 涵蓋屬性 | 主要用途 / 關注重點 |
|---|---|---|
| **分解視圖 (Decomposition View)** | Identification, Type, Purpose, Function, Subordinates | 呈現系統的階層分解結構，說明各模組與子系統的劃分 |
| **相依視圖 (Dependency View)** | Identification, Type, Purpose, Dependencies, Resources | 描述各實體間的關聯、相依約束與資源競爭 |
| **介面視圖 (Interface View)** | Identification, Function, Interfaces | 提供模組或子系統對外溝通的詳細規格，支援獨立開發 |
| **詳細設計視圖 (Detail Design View)** | Identification, Processing, Data | 提供程式碼實作者所需的內部演算法與內部資料結構細節 |

### 4. 實務對照案例：《K33p_1t_s1mpl3》軟體設計文件 (SDD v1.1)
第九組依據 IEEE Std 1016 簡化範本將 SRS 規格落地為五大解耦模組（參見 `se_sdd_team_2026.pdf`）：
- **分解視圖**：系統劃分為指令解析（`parser.js`）、狀態管理（`state.js`）、介面渲染（`ui.js`）、錯誤處理（`errorHandler.js`）與音效控制（`audio.js`）。
- **相依視圖與資料流**：使用者輸入觸發事件驅動流：`ui.js` 傳送原始字串至 `parser.js`，有效指令轉由 `state.js` 更新並寫入 `LocalStorage`，結果字串返回 `ui.js` 播放打字機動畫並觸發 `audio.js` 播放音效。
- **介面視圖與資料字典**：規範 `GameState` 與 LocalStorage JSON 結構（含 `chapter`, `location`, `names`, `unlocked`, `runeConnections`），以及模組間關鍵函式（如 `parseCommand(raw)`, `updateState(cmd)`, `renderTypewriter(text, el)`）。
- **詳細設計視圖**：指令解析正規表達式匹配、14 幕狀態推進、符文房號連線驗證（`301→204→205→103`）與多層防呆機制（不崩潰、永遠可繼續輸入）。

## 詳細說明：IEEE 1016-2009 的現代化演進

2009 年修訂的 IEEE Std 1016-2009 進行了重大範式轉換，全面對齊 **ISO/IEC 42010 (IEEE Std 1471)** 系統架構描述標準，主要更新包括：

1. **架構概念框架化 (Conceptual Foundations)**：
   - 引入 Stakeholder（利害關係人）、Concern（關注點）、Architecture Viewpoint（架構視點）與 Architecture View（架構視圖）的嚴謹定義。
   - 設計描述不再受限於單一功能分解思維，全面相容物件導向（OOAD）、元件式（Component-based）與微服務架構。
2. **標準化設計視點擴充 (Design Viewpoints)**：
   2009 版定義了更細緻且模組化的視點體系：
   - *Context Viewpoint*（上下文視點）：系統與外部環境、使用者及外圍系統的邊界與介面。
   - *Composition Viewpoint*（結構合成視點）：內部組件劃分與階層封裝。
   - *Logical Viewpoint*（邏輯視點）：靜態類別結構、資料型態與介面關係。
   - *Information Viewpoint*（資訊視點）：資料模型、持續性儲存與生命週期。
   - *Patterns Viewpoint*（模式視點）：所採用的架構模式與設計模式（如 MVC、State Machine、Observer 等）。
   - *Interface Viewpoint*（介面視點）：詳細服務操作協定。
   - *Structure Viewpoint*（結構視點）與 *Interaction Viewpoint*（動態互動視點）。
   - *State Dynamics Viewpoint*（狀態動態視點）：以狀態機描述系統生命週期狀態變遷。
   - *Algorithm Viewpoint*（演算法視點）與 *Resource Viewpoint*（資源分配視點）。

## 注意事項與限制
1. **標準版本選用**：小型專案或初學教學中，IEEE 1016-1998 的「10 項實體屬性 + 4 大視圖」結構直觀易懂；而在現代大型複雜系統或物件導向架構中，IEEE 1016-2009 基於 ISO/IEC 42010 的多重視點體系更具彈性。
2. **避免過早實作**：SDD 應專注於設計決策與架構權衡，而非直接張貼未經抽象的原始程式碼。

## 相關頁面
- [軟體需求規格書 (SRS)](SRS.md)
- [專案執行計畫書 (PEP)](PEP.md)
- [軟體測試文件 (STD)](STD.md)
- [專案實體：K33p_1t_s1mpl3](K33p_1t_s1mpl3.md)

## 來源
- 檔名：`raw/software_engineering/se_ieee1016_1998.pdf`，標題：IEEE Recommended Practice for Software Design Descriptions (IEEE Std 1016-1998)，機構：IEEE Computer Society，日期：1998-12-04。
- 檔名：`raw/software_engineering/se_ieee1016_2009.pdf`，標題：IEEE Standard for Information Technology -- Systems Design -- Software Design Descriptions (IEEE Std 1016-2009)，機構：IEEE Computer Society，日期：2009-08-20。
- 檔名：`raw/software_engineering/se_sdd_team_2026.pdf`，標題：K33p_1t_s1mpl3 軟體設計文件 (SDD) (SDD-2026-001-1 v1.1)，作者：輔仁大學軟體工程概論第九組，日期：2026-11-08。
