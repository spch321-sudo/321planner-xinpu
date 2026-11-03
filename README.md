# 321planner-xinpu

## 2026-11-03 1.16.0-up1103（自動更新：由「自我清除型 SW」改為正規自動更新）
- 原本 `sw.js` 是自我清除型（啟動就刪全部快取並註銷自己），頁面也每次載入刪光所有快取（連同網域其他 321 App 的快取一併誤刪），而且「版本更新提醒」去讀 321planner 的 version.json（讀錯 repo）。已改為：
  - 正規自動更新 SW（`sw.js`）：skipWaiting、activate 只清自己前綴（`plxp321-`）、clients.claim、通知頁面並把背景中的舊頁面帶到新版；HTML／JS／JSON 一律 no-cache 走網路；version.json 永遠 no-store。
  - **維持原本「不離線」的意圖**：`OFFLINE=false`（預設）時 SW 不預快取、不寫入任何快取，離線就和以前一樣開不了；要開離線備援，把 `sw.js` 的 `OFFLINE` 改成 `true`（網路優先、離線才用最近一次快取）。
  - 通用掛件 `upd321.js`：version.json（本 repo 自己的）輪詢＋`reg.update()`，空閒時自動換新版；開著任何視窗（*-modal）、輸入中、朗讀、美圖工作室中只顯示頂端更新條；防無限重整。設定視窗底部新增「版本與更新」（檢查更新／強制更新）。
  - 移除頁面的「清除所有快取與 SW」程式碼；舊的 `checkAppUpdate`／`doAppUpdate`／`dismissUpdate` 保留為薄包裝，既有橫幅按鈕不會壞。
- 版本 `1.16.0-up1103` 四處一致：`version.json`、`sw.js`、`index.html`（APP_VERSION／APPVER）、本 README。

## 2026-11-03 1.15.1-gx1103
- 美圖工作室預設團名、小智自我介紹、鎖屏顯示改為「貴格會新埔教會」。

## 2026-11-03 v1.15.1-gx1103
- 新增朗讀（🔊逐句高亮、背景播放、Azure TTS）、畫線、小智、美圖工作室、321 工具箱（gxr.js / gxa.js）。
- 版本號：index.html APP_VERSION、version.json、README 一致（sw.js 為自我清除型，無版本字串）。
