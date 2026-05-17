# Gemini CLI 実務活用講座

ターミナル/PowerShell から AI を起動し、散らかったフォルダ整理から Excel・Word・PowerPoint・PDF・QRコード作成までを体験する 3 時間講座の単一ページ HTML 教材。

## デプロイ

Cloudflare Pages にて `index.html` をルートで公開（ビルドコマンド不要）。

## 構成

- `index.html` … 全教材を統合した単一ページ。CSS/JS はすべて埋め込み済み。

## ローカル確認

```bash
python3 -m http.server 8000
# http://localhost:8000 にアクセス
```
