# Gemini CLI 実務活用講座

ターミナル/PowerShell から AI を起動し、散らかったフォルダ整理から Excel・Word・PowerPoint・PDF・QRコード作成までを体験する 3 時間講座の単一ページ HTML 教材。

本番サイト：https://gemini-cli-training.pages.dev/

## デプロイ

Cloudflare Pages にて `index.html` をルートで公開（ビルドコマンド不要）。
ブランチ `main` への push で自動デプロイされます。

## 構成

```
.
├── index.html                  ← 唯一の正カノニカルソース（all-in-one 統合版）
├── entry-form.html             ← 申込フォーム暫定ランディング（QR スキャン遷移先）
├── requirements.txt            ← 受講者向け Python ライブラリ一覧
├── assets/
│   ├── downloads/              ← 受講者向けダウンロード ZIP（4 ファイル）
│   ├── maps/                   ← 講座マップ画像（PNG）
│   ├── css/, js/               ← 旧個別ページ用（現在は使用されない）
└── README.md
```

## 教材ソースの単一ソース原則（重要）

> **本番に反映されるのは `index.html` のみ**です。

ローカル原本ディレクトリ（`管理フォルダ/01_会社別/プログラミング教育/01_大人向け_研修・講座/`）には以下のファイル群が存在しますが、**これらはデプロイ対象外**で、現在は参照されません。

- `lesson-01-cli-login.html`
- `lesson-02-folder-organize.html`
- `lesson-03-excel-word-ppt.html`
- `lesson-04-data-analysis-forecast.html`
- `lesson-05-pdf-qr-output.html`
- `lesson-06-wrapup.html`
- `setup-mac.html` / `setup-windows.html`
- `before-you-join.html` / `choose-your-os.html` / `index.html`（旧版）
- `troubleshooting-*.html`

### 編集ルール

1. **教材内容の修正は `all-in-one.html`（原本）→ `index.html`（デプロイ用）にコピー** の順で行う
2. 個別 `lesson-*.html` 等は**触らない**（古い情報が紛れる原因になる）
3. 本番に同期するスクリプトは `cp 原本/all-in-one.html /Users/apple/Desktop/masaki-sigoto-deploy/index.html` の一行で十分
4. 将来「個別ページがやはり必要」となった場合は、`all-in-one.html` から自動分割するスクリプトを書く方が安全（手動同期は事故の元）

### なぜ統合版だけにしたか

- 6 つのレッスン HTML を別々に管理するとリンク切れ・章番号ズレ・CSS 重複が起きやすい
- 教材を 1 ページ完結にした方が SEO・印刷・PDF 化・全文検索すべてに有利
- アンカーリンク（`#section-lesson02` 等）でレッスンへの直接遷移は維持できている

## ローカル確認

```bash
python3 -m http.server 8000
# http://localhost:8000 にアクセス
```

## 配布物の更新方法

サンプルデータや完成例を更新したい場合：

```bash
# 4 ZIP を再生成（macOS）
cd 原本ディレクトリ
for f in sample_data_messy sample_data_clean sample_data_raw output_examples; do
  find "$f" -name ".DS_Store" -delete
  zip -qr "/Users/apple/Desktop/masaki-sigoto-deploy/assets/downloads/${f}.zip" "$f" \
    -x "*.DS_Store" -x "*/.*"
done

# output_examples の中身を再生成したい場合は
python3 /tmp/build_output_examples.py  # 同梱スクリプト
```
