# 新世代博碩士論文網 API

## Swagger 
### 階段一
- [最新公告](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage1/announcements.yaml)
- [論文統計](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage1/statistics.yaml)
- [排行榜](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage1/rankings.yaml)
- [論文](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage1/theses.yaml)
- [會員](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage1/my.yaml)
- [申請](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage1/apply.yaml)


## 資料庫

### 1. announcements（公告）    

| 欄位名稱        | 型別           | 說明                          | 範例                              |
| ----------- | ------------ | --------------------------- | ------------------------------- |
| id          | VARCHAR(20)  | 公告 ID                 | 2024011501                      |
| title       | VARCHAR(255) | 公告標題                        | 系統維護公告                          |
| type        | VARCHAR(20)  | 公告分類（系統公告、最新消息）             | 系統公告                            |
| summary     | TEXT         | 公告短內容                       | 2024/01/15 凌晨2:00-4:00系統維護，暫停服務 |
| content     | TEXT         | 公告完整內容                      | 2024/01/15 凌晨2:00-4:00進行系統維護... |
| date        | DATETIME         | 公告日期（YYYY-MM-DD hh:mm:ss）            | 2024-01-15  12:00:00       |
| created\_at | TIMESTAMP    | 建立時間（預設 CURRENT\_TIMESTAMP） | 2024-01-10 12:00:00             |
| updated\_at | TIMESTAMP    | 更新時間（預設 CURRENT\_TIMESTAMP） | 2024-01-10 12:00:00             |

### 2. tags（公告用的標錢）
| 欄位名稱 | 型別          | 說明             | 範例 |
| ---- | ----------- | -------------- | -- |
| id   | BIGINT      | 標籤 ID（PK，自動遞增） | 1  |
| name | VARCHAR(50) | 標籤名稱（唯一）       | 重要 |


### 3. announcement_tags（公告與標籤關聯表）

| 欄位名稱             | 型別          | 說明          | 範例         |
| ---------------- | ----------- | ----------- | ---------- |
| announcement\_id | VARCHAR(20) | 公告 ID | 2024011501 |
| tag\_id          | BIGINT      | 標籤 ID（FK）   | 1          |
