# 麻將馬拉松輪班報名網頁

## 功能
- 12 個兩小時時段，每班 4 個座位
- Firebase 匿名驗證
- Realtime Database 即時同步
- 使用 transaction 避免同一座位被同時認領
- 使用者可取消自己名下的座位

## 先完成設定
1. 在 Firebase Console > 專案設定 > 一般 > 您的應用程式，複製 Web App 的 Firebase config。
2. 編輯 `firebase-config.js`，填入 apiKey、authDomain、projectId、storageBucket、messagingSenderId、appId。
3. `databaseURL` 已先填入本專案對話中提供的網址；請確認與 Firebase Console 顯示一致。
4. Authentication > Sign-in method 中啟用 Anonymous。
5. Realtime Database > Rules 中發布與程式資料路徑相符的安全規則。

## 部署（Windows）
1. 安裝 Node.js LTS：https://nodejs.org/
2. 開啟 Windows Terminal / 命令提示字元，執行：
   `npm install -g firebase-tools`
3. 解壓本 ZIP，進入解壓後資料夾。
4. 執行 `firebase login`
5. 執行 `firebase use --add`，選擇你的 Firebase 專案。
6. 執行 `firebase deploy --only hosting`
7. 完成後終端機會顯示 Hosting 網址，可貼到 LINE 群組。

## 重要安全說明
- 匿名驗證不等於 LINE 群組成員驗證。任何取得網址的人都可能建立匿名身分。
- 目前規則只限制已驗證使用者操作自己的座位；若需真正限制邀請對象，建議再加入伺服器端邀請碼驗證或其他可信任的存取控制。
- 這個範例未包含管理者專用介面、跨裝置身分恢復或個資刪除流程。
- 請勿將 Admin SDK 私密金鑰放入前端網頁。
