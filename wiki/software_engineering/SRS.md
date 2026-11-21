---
title: "軟體需求規格書 (Software Requirements Specification, SRS)"
domain: "software_engineering"
created: "2026-11-11"
updated: "2026-11-11"
tags: ["SRS", "IEEE 830", "需求工程", "功能需求", "非功能需求", "RTM"]
sources: ["se_ieee830_1998.pdf", "se_srs_team_2026.pdf"]
status: "reviewed"
---

# 軟體需求規格書 (Software Requirements Specification, SRS)

## 摘要
軟體需求規格書（SRS）是明確規範軟體系統功能、外部介面、非功能性品質屬性及約束條件的正式基準文件。本頁結合 IEEE 830 標準推薦架構模板與實務案例《K33p_1t_s1mpl3》SRS（編號 SRS-2026-001-1），系統性整理 SRS 的章節規範、需求分類方法與可追溯性管理機制。

## 核心概念

### 1. SRS 的目的與角色
- **開發基準**：作為系統設計、實作、介面開發及測試驗收的契約與共同基準（參見 `se_srs_team_2026.pdf` 第 1.1 節）。
- **團隊溝通**：串聯利害關係人（客戶、專案經理、開發者、測試者）消除認知歧義。
- **追溯起點**：透過需求編號銜接後續設計實體（SDD）與驗收測試（STD/Test Case）。

### 2. IEEE 830 經典三層結構大綱
根據 `se_ieee830_1998.pdf` 大綱模板，標準 SRS 包含三大主要章節：
1. **第 1 章：引言 (Introduction)**
   - 目的 (Purpose)
   - 範圍 (Scope)
   - 定義、縮寫與簡稱 (Definitions, acronyms, and abbreviations)
   - 參考文件 (References)
   - 概述 (Overview)
2. **第 2 章：整體描述 (Overall description)**
   - 產品觀點 (Product perspective)
   - 產品功能 (Product functions)
   - 使用者特徵 (User characteristics)
   - 約束條件 (Constraints)
   - 假設與相依性 (Assumptions and dependencies)
3. **第 3 章：具體需求 (Specific requirements)**
   - 外部介面需求 (External interface requirements)：使用者介面、硬體介面、軟體介面、通訊介面
   - 功能需求 (Functional requirements)：依模式/使用者組織需求條目（如 MF101...）
   - 效能需求 (Performance requirements)
   - 設計約束 (Design constraints)
   - 軟體系統屬性 (Software system attributes)
   - 其他需求與附錄 (Appendixes)

## 詳細說明

### 1. 需求分類與撰寫實務（以《K33p_1t_s1mpl3》為例）

#### (1) 功能需求 (Functional Requirements)
在實務專案中，功能需求以結構化編號（如 `F-xx` 及子項目 `F-xx-yy`）呈現，涵蓋：
- **F-01 指令輸入與基本解析**：空白移除 (F-01-01)、不區分大小寫比對 (F-01-02)、指令辨識 (F-01-03)、錯誤格式檢查 (F-01-04)。
- **F-02 提示指令**：輸入 `simple` 提供當前進度提示。
- **F-03 已解鎖內容清單**：輸入 `list` 列出已調查物件與章節。
- **F-04 物件調查**：`inspect [物件名稱]` 調查機制與錯誤容錯。
- **F-05 劇情觸發**：如 `05_HO_05` 依章節、地點、人物觸發對話並推進進度。
- **F-06 / F-12 重新命名**：角色與資料夾自定義命名（`name [代號] [新名稱]`），且不破壞底層識別碼。
- **F-07 歷史紀錄**：`history` 與 `log` 查閱。
- **F-08 進度儲存與讀取**：`save [位置]` 與 `load [位置]`，整合瀏覽器 LocalStorage。
- **F-09 遊戲狀態管理**：控管章節、位置、5 位角色解鎖狀態及 14 幕劇情進度。
- **F-10 介面與文字渲染**：黑底淺色 Terminal 風格、打字機動畫、Enter/Space 跳過動畫機制。
- **F-11 錯誤指令處理**：心理驚悚風格報錯、不崩潰保證 (100% 防呆)。

#### (2) 非功能需求與品質屬性 (Non-Functional Requirements)
實務中需訂立量化與可驗證的品質標準（如 `NF-xx`）：
- **回應時間 (NF-01)**：送出指令後 0.1 秒內開始顯示執行結果（不含打字機動畫播放時間）。
- **穩定性與防呆覆蓋率 (NF-02)**：未預期輸入不可造成未捕獲例外或介面卡死。
- **跨平台相容性 (NF-03)**：支援最新版及前一版 Chrome、Edge、Firefox、Safari。
- **初始載入 (NF-07)**：正常網路下初始頁面 3 秒內完成顯示。
- **資料隱私與隔離 (NF-08, NF-09)**：不要求帳號密碼，存檔純本機 LocalStorage 隔離，不外傳伺服器。

### 2. 需求可追溯性矩陣 (RTM, Requirements Traceability Matrix)
- SRS 應提供 RTM（如《K33p_1t_s1mpl3》附錄 A），縱軸為功能需求條目（F-01 至 F-12），橫軸為使用者案例（UC-01 至 UC-10）。
- **效益**：確保每一項使用者案例都有對應的功能需求支撐，且沒有孤立或無用的需求項目。

## 注意事項與限制
1. **來源性質說明**：`se_ieee830_1998.pdf` 僅為 2 頁大綱模板（中央大學 NIICC 樣本），並未包含 IEEE 830-1998 的完整 40 頁標準條文；標準條文細節以該大綱架構與團隊 SRS 實作為準。
2. **排版筆誤紀錄**：`se_srs_team_2026.pdf` 第 1.5 節存在文字誤植（`IEEE 830-1《K33p_1t_s1mpl3》998` 應為 `IEEE 830-1998`），此為團隊撰寫時的排版問題，不影響需求定義實質。
3. **無後端約束**：純前端與 LocalStorage 架構下，存檔不支援跨裝置同步，需在 SRS 明確載明裝置獨立性限制。

## 相關頁面
- [專案執行計畫書 (PEP)](PEP.md)
- [軟體設計描述 (SDD)](SDD.md)
- [軟體測試文件 (STD)](STD.md)
- [專案實體：K33p_1t_s1mpl3](K33p_1t_s1mpl3.md)

## 來源
- 檔名：`raw/software_engineering/se_ieee830_1998.pdf`，標題：SRS (IEEE 830) 範例大綱模板，機構：中央大學 NIICC 實驗室，年份：1998（參照標準年份）。
- 檔名：`raw/software_engineering/se_srs_team_2026.pdf`，標題：K33p_1t_s1mpl3 系統需求規格書 (SRS) (SRS-2026-001-1 v1.0)，作者：輔仁大學軟體工程概論第九組，日期：2026-10-20，段落：第 1 章至第 5 章。
