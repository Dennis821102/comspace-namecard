# 寬憶行銷商務中心 電子名片（LIFF）

張立群 John｜Comspace 寬憶行銷商務中心 的 LINE 電子名片。
分享後送出一則四張卡片的 Flex Message：個人名片／服務項目／方案一覽／據點。

與 `king-namecard`（依燃）、`jiden-namecard`（傑登）完全獨立：不同 repo、不同 LIFF ID。

## 檔案

| 檔案 | 用途 |
|---|---|
| `index.html` | 名片頁 + Flex Message + LIFF 分享邏輯 |
| `img/hero-lounge.jpg` | 交誼廳，第一張卡片主視覺 |
| `img/hero-office.jpg` | 共享辦公區，第二張 |
| `img/hero-meeting.jpg` | CBD 館大會議室，第三張 |
| `img/hero-building.jpg` | 昭揚乾坤商辦外觀，第四張 |

素材來自 `寬憶網頁_依燃.docx` 與 `寬憶-20261013T041848Z-1-001.rar`。

## 上線三步驟

### 1. 推上 GitHub 並開 Pages

```bash
cd ~/Desktop/comspace-namecard
git remote add origin git@github.com:Dennis821102/comspace-namecard.git
git push -u origin main
```

Settings → Pages → Source 選 `main` / `root`，
網址為 `https://dennis821102.github.io/comspace-namecard/`。

### 2. 建立 LIFF App

LINE Developers → LINE Login channel → LIFF → Add：

| 欄位 | 值 |
|---|---|
| Endpoint URL | `https://dennis821102.github.io/comspace-namecard/` |
| Size | Full |
| Scope | `profile` |
| Share target picker | 開啟（API 設不了，必須在後台手動開） |

### 3. 填 LIFF ID

```js
const LIFF_ID = 'YOUR_LIFF_ID';   // ← 換成實際的 LIFF ID
```

## 待補

- **官方網站**：第二張卡片的「官方網站　即將上線」目前是沒有 action 的佔位按鈕。
  網址確定後，在 `LINKS` 補 `web: '...'`，並把 `btnSoon('官方網站　即將上線')`
  換成 `btn('官方網站', LINKS.web)`。
- **Logo**：素材裡沒有 logo 檔，目前用 `COMSPACE` 字標代替。有 AI/SVG/PNG 檔可換上。
- **人像照**：沒有 John 的形象照，第一張卡片先用空間照。
  有照片的話可改成依燃那種半身照版型。

## Flex 大小注意

目前送出為 9,915 bytes，上限 10,240。要再加內容請先量測；
超過的話就把四張拆成兩則訊息（`shareTargetPicker` 最多可送 5 則）。
