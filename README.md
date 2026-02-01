
基於 Spring Boot 的高併發加護病房生理訊號監控系統
# ICU Physiological Signal Monitoring System (ICU 生理訊號監控系統)

## 📖 專案概述 (Project Overview)
這是一個基於 **Spring Boot** 建構的醫療物聯網 (IoT) 後端系統，旨在模擬並處理加護病房 (ICU) 的高頻生理數據。系統包含一個**資料接收端 (Receiver)** 與一個**多執行緒模擬器 (Simulator)**，能即時接收心率、脈搏與 ECG 心電圖數據並進行持久化儲存。

## 🛠️ 技術堆疊 (Tech Stack)
* **Language:** Java 17
* **Framework:** Spring Boot (Web, Data JPA)
* **Database:** H2 / MySQL
* **Architecture:** RESTful API, MVC, DTO Pattern
* **Concurrency:** Java Util Concurrent (ScheduledExecutorService)
* **Tools:** Maven, Lombok, Jackson

## ⚡ 核心功能與亮點 (Key Features)

### 1. 高併發訊號模擬 (High-Concurrency Simulation)
- 使用 `ScheduledExecutorService` 取代傳統的 `Timer`，解決了多台儀器同時發送訊號時的執行緒阻塞問題。
- 模擬器可產生符合常態分佈的隨機心率與正弦波 ECG 數據。

### 2. RESTful API 設計
- 符合業界標準的 API 設計規範。
- **POST** `/api/upload`: 接收來自感測器的 JSON Payload。
- **GET** `/api/latest`: 查詢特定病患 (National ID) 的最新 N 筆生理紀錄。

### 3. 資料流處理 (Data Ingestion)
- 實作 **DTO (Data Transfer Object)** 模式，將複雜的巢狀 JSON (Nested JSON) 轉換為資料庫實體 (Entity)，確保資料結構的安全性與一致性。

---
