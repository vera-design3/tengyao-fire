# 苗栗騰曜｜防火填塞

騰曜防火工程官方網站。單頁式，無框架、無外部相依，所有樣式與腳本內嵌於 `index.html`。

## 結構

```
index.html      網站本體
images/         圖片素材（WebP 為主）
```

## 本機預覽

直接用瀏覽器開啟 `index.html` 即可。

## 部署

推送到 main 分支後由 GitHub Pages 自動發布。

## 維護筆記

`index.html` 為部署即上線的檔案，內容不含註解，相關說明集中在此。

### 網域

線上位置 `https://tengyue.tw/`（GoDaddy 註冊，DNS 亦在 GoDaddy）。

DNS 設定：`@` 四筆 A 記錄指向 `185.199.108~111.153`，`www` CNAME 指向 `vera-design3.github.io`，repo 根目錄的 `CNAME` 檔負責讓 GitHub Pages 認領網域。

**日後若更換網域**，全檔搜尋 `https://tengyue.tw/` 一次替換，並同步修改 `sitemap.xml` 與 `CNAME`。需要改的位置：`canonical`、`og:url`、`og:image`、JSON-LD 的 `@id`／`url`／`image`。

### 追蹤與索引

Google Tag Manager 容器 `GTM-5T2LQNXB`，head 內一段 script、body 開頭一段 noscript iframe。

### 進場動畫的保護機制

`.rv` 的隱藏規則掛在 `html.js` 前綴下，由 head 的一行 script 加上該 class；底部主腳本整段包在 `try/catch` 裡，任何錯誤都會移除 `js` class 讓內容還原。

**日後新增 JS 請維持這層保護** — 若讓 `.rv{opacity:0}` 無條件生效，JS 一出錯整頁會空白。

### RWD 斷點的判斷理由

| 斷點 | 處理 | 原因 |
|---|---|---|
| ≤ 900px | 服務卡降為單欄 | 兩欄在平板直向會擠 |
| 901~1080px | 服務卡維持兩欄 | 此區間寬度仍夠 |
| ≤ 400px | 雙欄卡片改單欄 | iPhone SE 等窄螢幕文字會擠成兩三字一行 |
| 橫拿手機（視窗高度不足） | Hero 不鎖滿高 | 讓標題與按鈕排得開 |

### 圖片

以 WebP 為主，`og-image.jpg` 保留 JPG（部分社群爬蟲對 WebP 支援不穩）。流程圖示 `step-1~6` 顯示尺寸僅 142px，來源檔已壓到 300px，勿再換回大圖。
