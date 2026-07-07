# 2026 鹿兒島旅行小 App

這是一個用 Google Sheet 當資料源的手機旅行網頁。

- `2026鹿兒島`：行程資料
- `鹿兒島記帳`：旅途中共同記帳
- `index.html`：手機瀏覽的行程與記帳前端
- `apps-script.js`：貼到 Google Apps Script 的後端

## 1. 建立 Apps Script

1. 打開你的 Google Sheet。
2. 選單進入「擴充功能」→「Apps Script」。
3. 將 `apps-script.js` 的內容貼進去。
4. 儲存後，選「部署」→「新增部署作業」。
5. 類型選「網頁應用程式」。
6. 執行身分選「我」。
7. 存取權選「任何知道連結的使用者」。
8. 部署後複製結尾是 `/exec` 的 Web App URL。

## 2. 設定網頁

打開 `index.html`，找到這一行：

```js
const GAS_URL = 'PASTE_YOUR_APPS_SCRIPT_WEB_APP_URL_HERE';
```

把字串換成剛剛複製的 `/exec` URL。

## 3. 建議的行程欄位

`2026鹿兒島` 第一列建議使用這些欄位名稱：

```text
日期, 時間, 行程, 地點, 分類, 備註, 地圖
```

欄位名稱不用完全一樣，程式也會辨識常見名稱，例如「項目」「活動」「Google Maps」「連結」。

如果地點儲存格本身有 Google Maps 超連結，Apps Script 會優先把那個連結帶進網頁。

## 4. 建議的記帳欄位

`鹿兒島記帳` 第一列建議使用：

```text
日期, 項目, 人員, 金額, 備註, 建立時間
```

如果分頁是空白的，Apps Script 第一次寫入時會自動建立標題列。

## 5. 發佈

最簡單的方式是把 `index.html` 放到 GitHub Pages。

如果之後重新部署 Apps Script，Google 可能會產生新的 `/exec` URL。記得同步更新 `index.html` 裡的 `GAS_URL`。
