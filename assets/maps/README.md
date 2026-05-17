# Gemini CLI 実務活用講座 マップ画像

## 生成手法

- 手法: HTML/CSS 固定レイアウト + Headless Chrome スクリーンショット
- 理由: 日本語テキスト、章番号、所要時間、ファイル名を正確に描画しやすく、画像生成 AI による文字崩れや内容のハルシネーションを避けるため
- 出力: PNG、白背景、透過なし、3508 x 2480 px
- ソース: `assets/maps/map-source.html`

## 出力ファイル

| ファイル | 内容 |
| --- | --- |
| `map-01-curriculum.png` | 講座全体マップ。0:00 から 3:00 までの流れ、6 つのレッスン、事前準備、受講後に残る 7 つの成果物を俯瞰。 |
| `map-02-project-flow.png` | プロジェクト管理マップ。`sample_data_messy/` から `sample_data_clean/`、分析データ、Office 資料、PDF / QR 配布までの流れを整理。 |
| `map-03-next-step.png` | 次の一歩マップ。Gemini CLI 後の発展ルートを「使う / 作る」と「CLI / IDE・GUI」の 2 x 2 で整理。 |

## 画像 1: 講座全体マップ

- 上部: 講座テーマ「セミナー集客 5 年分のデータを AI に分析・予測させて提案資料に仕上げる」
- 中央: 0:00 から 3:00 のタイムライン、休憩・質問タイム
- レッスンカード:
  - 🚀 第1部: Gemini CLI の起動と基本操作、所要時間 約30分
  - 📁 第2部: フォルダ整理ハンズオン、所要時間 約40分
  - 📊 第3部: Excel・Word・PowerPoint の作成、所要時間 約50分
  - 📈 第4部: データ分析と未来予測、所要時間 約35分
  - 📄 第5部: PDF 化・QR コード生成、所要時間 約25分
  - 🎯 第6部: まとめと次の一歩、所要時間 残り時間
- 下部: 整理されたフォルダ、Excel、Word、PowerPoint、2025 年 3 シナリオ予測、PDF、QR コード画像
- バッジ: 事前準備 Node.js + Gemini CLI

## 画像 2: プロジェクト管理マップ

- 横長フロー:
  - 散らかった生データ: `sample_data_messy/`
  - 整理されたフォルダ: `sample_data_clean/`
  - 分析データ: `セミナー集客データ_2020-2024.xlsx`
  - Office 資料: `報告書.docx` / `提案資料.pptx`
  - PDF / QR で配布: `配布用.pdf` + `qr.png`
- 各ステージにプロンプト例を配置
- 下部に整理の 4 原則を配置:
  - 確認してから実行
  - 命名規則を AI に考えさせる
  - 階層は浅く
  - README を各フォルダに置く
- 右下に `gemini-workshop-output/` の最終フォルダ構成例を配置

## 画像 3: 次の一歩マップ

- 上部に学習ステップ 4 段階を配置:
  - 本講座: Gemini CLI / ChatGPT
  - 次の段階: VS Code + Copilot
  - 発展: Cursor / Windsurf
  - 応用: Claude Code / Codex CLI / Antigravity
- 中央に 2 x 2 マトリクスを配置:
  - 使う x CLI: Gemini CLI、ChatGPT
  - 使う x IDE / GUI: VS Code + GitHub Copilot、AI 補完 / Chat
  - 作る x CLI: Claude Code、Codex CLI
  - 作る x IDE / GUI: Cursor、Windsurf、Antigravity
- 下部に注意書き:
  - いきなり全部使う必要はなく、1 つずつ試す
  - 無料枠・料金体系は変動するため公式サイトで確認する

## 参照した主な教材

- `/Users/apple/Desktop/masaki-sigoto-deploy/index.html`
- `00_講座設計概要.md`
- `01_講座ゴールと対象者.md`
- `02_3時間タイムテーブル.md`
- `03_講師用進行台本.md`
- `04_受講者用ハンズオン手順書.md`
- `05_プロンプト集.md`
- `06_よくあるエラーと対処.md`
- `07_成果物一覧.md`
- `08_事前準備案内.md`
- `09_受講者へのお願い.md`

## index.html へのリンク追加パッチ案

`index.html` の「コンテンツ一覧」セクション直下、レッスンセクションの前に追加する想定です。

```diff
       </div>
 
+      <h3 style="margin-top:24px;">講座全体マップ</h3>
+      <div class="nav-grid">
+        <a href="assets/maps/map-01-curriculum.png" class="nav-card" target="_blank" rel="noopener">
+          <div class="nav-icon">📍</div>
+          <div class="nav-title">講座全体マップ</div>
+          <div class="nav-desc">3時間の流れ、6つのレッスン、受講後に残る成果物をA4横の1枚で確認できます</div>
+        </a>
+        <a href="assets/maps/map-02-project-flow.png" class="nav-card" target="_blank" rel="noopener">
+          <div class="nav-icon">🗂️</div>
+          <div class="nav-title">プロジェクト管理マップ</div>
+          <div class="nav-desc">散らかった生データから分析・Office資料・PDF/QR配布までの流れを確認できます</div>
+        </a>
+        <a href="assets/maps/map-03-next-step.png" class="nav-card" target="_blank" rel="noopener">
+          <div class="nav-icon">🧭</div>
+          <div class="nav-title">次の一歩マップ</div>
+          <div class="nav-desc">Gemini CLI後に試せるAI開発環境の発展ルートを確認できます</div>
+        </a>
+      </div>
+
       <h3 style="margin-top:24px;">レッスンセクション</h3>
       <div class="nav-grid">
```
