# 新世代博碩士論文網 API

## Swagger 

### 階段一：國圖設定階段




### 階段二：學校設定階段


- [個人資料](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage2/my.yaml)
- [人員管理](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage2/users.yaml)
- [系統設定](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage2/settings.yaml)
- [論文查詢](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage2/thesis.yaml)
- [統計報表](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage2/reports.yaml)
- [論文審查](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage2/reviews.yaml)
- [送存國圖](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage2/submissions.yaml)

### 階段三：論文提交階段

- [上傳論文](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage3/thesis.yaml)
- [靜態資源](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage3/static.yaml)
- [個人資料](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage3/my.yaml)


### 階段四：論文審查階段
### 階段五：論文送存階段
### 階段六：書目管理階段
### 階段七：公開檢索階段
- [最新公告](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage7/announcements.yaml)
- [論文統計](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage7/statistics.yaml)
- [排行榜](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage7/rankings.yaml)
- [論文](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage7/theses.yaml)
- [會員](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage7/my.yaml)
- [申請](https://editor-next.swagger.io/?url=https://raw.githubusercontent.com/chouhsiang/thesis-swagger/main/stage7/apply.yaml)


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

### 4. theses（論文）
| 欄位名稱                  | 資料型別           | 說明         | 範例                                               |
| --------------------- | -------------- | ---------- | ------------------------------------------------ |
| id                    | VARCHAR(64)    | 論文唯一識別碼    | `"1"`                                            |
| title                 | VARCHAR(512)   | 論文標題       | `"台灣博碩士論文網發展現況與展望"`                              |
| author                | VARCHAR(256)   | 作者         | `"王小明"`                                          |
| school                | VARCHAR(256)   | 學校         | `"國立臺灣大學"`                                       |
| degree                | ENUM(碩士/博士/其他) | 學位         | `"碩士"`                                           |
| type                  | VARCHAR(64)    | 論文類型       | `"學術"`                                           |
| college               | VARCHAR(256)   | 學院         | `"工學院"`                                          |
| department            | VARCHAR(256)   | 系所         | `"資訊工程學系"`                                       |
| advisor               | VARCHAR(256)   | 指導教授       | `"陳大明"`                                          |
| language              | VARCHAR(64)    | 論文語言       | `"中文"`                                           |
| year                  | SMALLINT       | 年度（民國年）    | `113`                                            |
| abstract              | MEDIUMTEXT     | 摘要         | `"本論文探討..."`                                     |
| abstract\_en          | MEDIUMTEXT     | 英文摘要       | `"With the rapid development..."`                |
| keywords              | JSON           | 關鍵字陣列      | `["論文網", "台灣", "Open Access"]`                   |
| keywords\_en          | JSON           | 英文關鍵字陣列    | `["Natural Language Processing", "Open Access"]` |
| full\_text\_url       | VARCHAR(1024)  | 全文下載連結     | `"https://.../1.pdf"`                            |
| full\_text\_available | TINYINT(1)     | 是否有全文（0/1） | `1`                                              |
| view\_count           | INT            | 被點閱數       | `1200`                                           |
| download\_count       | INT            | 下載數        | `800`                                            |
| reference\_count      | INT            | 被引用數       | `25`                                             |
| created\_at           | DATETIME       | 建立時間       | `2025-08-14 10:00:00`                            |
| updated\_at           | DATETIME       | 更新時間       | `2025-08-14 10:00:00`                            |
