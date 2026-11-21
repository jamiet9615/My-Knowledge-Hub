---
title: "軟體測試文件 (Software Test Documentation, STD / IEEE 829)"
domain: "software_engineering"
created: "2026-11-11"
updated: "2026-11-11"
tags: ["STD", "IEEE 829", "ISO/IEC 29119", "軟體測試", "測試計畫", "測試案例"]
sources: ["se_ieee829_1983.pdf"]
status: "reviewed"
---

# 軟體測試文件 (Software Test Documentation, STD)

## 摘要
軟體測試文件（Software Test Documentation）是軟體品質保證與驗收流程中評估測試範圍、追溯缺陷及確認發布決策的制度性產出。本頁依據 Harry Sneed 與 Richard Seidl 的研究論文，整理 ANSI/IEEE Std 829 經典八大測試文件規範，以及其後續演進為國際標準 ISO/IEC/IEEE 29119-3 的三層測試架構。

## 核心概念

### 1. 測試文件的核心價值與需求
根據 Sneed & Seidl（2013）分析，測試文件主要承擔五大角色：
- **發布決策 (Decision Makers)**：作為審計與版本是否可 Release 的事實依據。
- **維護者 (Maintainers)**：提供變更後的迴歸測試指引。
- **測試人員 (Testers)**：作為定位缺陷根本原因與工作生產力的評估基準。
- **追溯架構 (Architecture Tie)**：將測試用例與軟體架構及 SRS 需求對齊。
- **可重現性 (Reproducibility)**：讓他人能精確重建測試路徑與環境。

### 2. ANSI/IEEE 829 的八大經典測試文件
ANSI/IEEE 829 最早於 1983 年發布（並於 1998 年修訂），聚焦於「系統測試產出什麼 (Deliverables)」，規定了以下八種標準文件：
1. **測試計畫 (Test Plan)**：涵蓋 16 項規劃要素，包含測試項目、測試途徑、通過/失敗準則、暫停與重啟準則、交付物、環境與人力配置。
2. **測試設計規格書 (Test Design Specification)**：規劃測試架構與工具，定義受測功能特性及其通過/失敗細則。
3. **測試案例規格書 (Test Case Specification)**：明確規範每個測試案例的目的、輸入數據（Pre-conditions）與預期輸出（Post-conditions）。
4. **測試程序規格書 (Test Procedure Specification)**：定義執行測試案例的具體操作步驟、執行順序、搭建與清除環境的流程（即現代概念中的 Test Script）。
5. **測試項目傳送報告 (Test Item Transmittal Report)**：清點移交測試的軟體版本、資料庫與文件清單、版本狀態與負責人。
6. **測試日誌 (Test Log)**：按時間順序忠實記錄測試執行步驟、執行者、時間戳記、Pass/Fail 結果及異常事件。
7. **測試事件報告 (Test Incident Report)**：詳細記錄異常現象（不該發生而發生、或該發生而未發生），作為缺陷報告（Bug Report）的根本依據。
8. **測試總結報告 (Test Summary Report)**：綜合各階段測試成果、記錄與預期行為的偏差，並由測試者提出是否可正式發布系統的量化建議。

## 詳細說明：演進至 ISO/IEC/IEEE 29119-3

隨著軟體工程演進，IEEE 829 與後續標準被整合昇華為 **ISO/IEC/IEEE 29119-3:2013**。新標準定義了涵蓋整個多層級測試流程的完整文件體系：

```
┌────────────────────────────────────────────────────────┐
│ 1. 組織層級 (Organizational Test Process)              │
│    - Organizational Test Policy (公司級測試政策)        │
│    - Organizational Test Strategy (組織級測試策略)      │
├────────────────────────────────────────────────────────┤
│ 2. 測試管理層級 (Test Management Processes)           │
│    - Test Plan (專案測試計畫)                           │
│    - Test Status Report (測試進度狀態報告，週期性產出)   │
│    - Test Completion Report (測試結案報告)             │
├────────────────────────────────────────────────────────┤
│ 3. 靜態與動態測試層級 (Static & Dynamic Processes)     │
│    - 靜態：Review Checklist, Static Analysis Rules 等  │
│    - 動態：Test Specification (Design/Case/Procedure)  │
│           Test Data / Environment Requirements         │
│           Test Environment Readiness Report (環境就緒) │
│           Test Outcome (實際輸出) / Test Results (比對) │
│           Test Execution Log / Incident Report         │
└────────────────────────────────────────────────────────┘
```

### 新舊標準演進關鍵差異
- **新增指標**：新標準新增了「測試環境就緒報告 (Environment Readiness Report)」與「測試輸出實際值 (Test Outcome)」，嚴格區分實際輸出與預期結果比對。
- **覆蓋率維度擴充**：測試案例規格書除了傳統程式碼覆蓋（Code Coverage），強制納入等價類分割覆蓋（Equivalence Class Coverage）與使用案例覆蓋（Use Case Coverage）。
- **現代敏捷開發實務**：在敏捷開發（Agile/Scrum）中，傳統手寫文件多轉變為工具自動產出（CI/CD Automated Test Reports），如自動化測試腳本、單日測試計畫（One-day Test Plan）與即時狀態看板。

## 注意事項與限制
1. **來源性質說明**：`se_ieee829_1983.pdf` 是 Harry Sneed 與 Richard Seidl 所撰寫之德英文學術論文評述，非 IEEE 或 ISO 官方標準文本全文；內容反映作者對標準演進與業界實踐的專業詮釋。
2. **裁剪原則 (Tailoring)**：各專案應依風險等級（關鍵安全系統 vs. 一般網頁系統）適度裁剪測試文件數量，避免無謂的文檔負擔。

## 相關頁面
- [軟體需求規格書 (SRS)](SRS.md)
- [專案執行計畫書 (PEP)](PEP.md)
- [軟體設計描述 (SDD)](SDD.md)
- [專案實體：K33p_1t_s1mpl3](K33p_1t_s1mpl3.md)

## 來源
- 檔名：`raw/software_engineering/se_ieee829_1983.pdf`，標題：Software Testdokumentation (nach den IEEE und ISO Standards)，作者：Harry Sneed & Richard Seidl，年份：2013。
