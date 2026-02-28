# 舌健康診断アプリ - スマホインストール手順

## アイコンファイルについて

アプリアイコンは以下の場所に生成されています。`icons` フォルダにコピーしてください。

**生成されたアイコンの場所:**
- `C:\Users\Admin\.cursor\projects\c-Users-Admin-Desktop\assets\icon-512.png`
- `C:\Users\Admin\.cursor\projects\c-Users-Admin-Desktop\assets\icon-192.png`

**コピー先（プロジェクト内）:**
- `icons/icon-512.png` （必須）

**コピーコマンド（PowerShell）:**
```powershell
Copy-Item "C:\Users\Admin\.cursor\projects\c-Users-Admin-Desktop\assets\icon-512.png" -Destination ".\icons\icon-512.png" -Force
```

512px のアイコン1つで動作します（manifest で 192px 用にも同じファイルを参照）。

### アイコンデザイン
- **背景**: ダークネイビー（#1a2332）の角丸四角
- **メイン**: コーラルピンクの舌のシルエット
- **アクセント**: ゴールド（#e8b86d）の心拍ライン
- 舌の健康診断アプリであることが一目で分かるデザイン

---

## スマホにインストールするための関連ファイル

| ファイル | 役割 |
|---------|------|
| `manifest.json` | PWAの設定（名前、アイコン、テーマ色、起動URLなど） |
| `icons/icon-512.png` | アプリアイコン（512×512px） |
| `index.html` | メインアプリ + manifestリンク・Apple用メタタグ |

### index.html に追加済みの設定
- `<link rel="manifest" href="manifest.json">` … PWAマニフェスト
- `<meta name="theme-color">` … ブラウザUIの色
- `<meta name="apple-mobile-web-app-capable">` … iOSでフルスクリーン表示
- `<link rel="apple-touch-icon">` … ホーム画面追加時のアイコン

---

## インストール手順（ユーザー向け）

### Android（Chrome）
1. アプリのURLをChromeで開く（**HTTPS必須**）
2. メニュー（⋮）→「アプリをインストール」または「ホーム画面に追加」
3. ホーム画面にアイコンが追加される

### iPhone / iPad（Safari）
1. アプリのURLをSafariで開く
2. 共有ボタン（□↑）→「ホーム画面に追加」
3. 名前を確認して「追加」

### 注意事項
- **HTTPSが必須**: ローカル（`file://`）ではインストールできません
- デプロイ例: GitHub Pages、Netlify、Vercel、自前サーバー（SSLあり）
- ローカル確認: `npx serve .` や `python -m http.server` でHTTPサーバーを起動（localhost は一部ブラウザでPWA対応）

---

## オプション: Service Worker（オフライン対応）

オフラインでも使えるようにするには、`sw.js`（Service Worker）の追加を検討してください。現状はオンライン専用です。
