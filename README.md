# 出荷温度記録システム

SwitchBot防水温湿度計のデータをスマホから記録し、Google Spreadsheetに自動保存するWebアプリです。

## 機能

- 🌡️ SwitchBotセンサーから温度・湿度・バッテリーをリアルタイム取得
- 📦 出荷先・品番・備考を入力して記録
- 📊 Make Webhook経由でGoogle Spreadsheetに自動保存
- 📋 本日の記録履歴をアプリ内で確認

## セットアップ

### 1. `index.html` の設定箇所を編集

```javascript
const CONFIG = {
  TOKEN:     "SwitchBot Token",      // SwitchBotアプリで取得
  SECRET:    "SwitchBot Secret",     // SwitchBotアプリで取得
  DEVICE_ID: "デバイスID",            // デバイスのMACアドレス
  WEBHOOK:   "Make Webhook URL"      // MakeのWebhook URL
};
```

### 2. GitHub Pagesで公開

1. GitHubにリポジトリを作成
2. `index.html` をアップロード
3. Settings → Pages → Branch: main → Save
4. 発行されたURLをスマホでブックマーク

## 必要なもの

- SwitchBot防水温湿度計 + Hub
- Make.com アカウント（Webhookシナリオ設定済み）
- Google Spreadsheet（Make連携済み）
- GitHub アカウント

## Google Spreadsheet の列設定

| A | B | C | D | E | F |
|---|---|---|---|---|---|
| 記録日時 | 出荷先 | 品番 | 温度 | 湿度 | バッテリー |

Makeのマッピング：
- A: `{{1.recordedAt}}`
- B: `{{1.destination}}`
- C: `{{1.productCode}}`
- D: `{{1.temperature}}`
- E: `{{1.humidity}}`
- F: `{{1.battery}}`
