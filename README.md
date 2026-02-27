# App Policies

**アプリケーション向けプライバシーポリシー・利用規約ホスティング**

[![GitHub Pages](https://img.shields.io/badge/deploy-GitHub%20Pages-222?logo=github)](https://ksato8710.github.io/app-policies/)
[![HTML](https://img.shields.io/badge/format-Static%20HTML-E34F26?logo=html5&logoColor=white)](#)

> **Live**: [GitHub Pages](https://ksato8710.github.io/app-policies/)

![App Policies Screenshot](docs/screenshot.png)

---

## Why / Background

モバイルアプリやWebアプリをストアに公開する際、プライバシーポリシーや利用規約のURLが必須になる。各アプリごとにホスティング先を用意するのは非効率なため、App Policies は**すべてのアプリのポリシーページを一元管理する静的サイト**として機能する。GitHub Pages でホスティングし、メンテナンスコストを最小化。

## Features

- **マルチアプリ対応** -- アプリごとにディレクトリを分けてポリシーを管理
- **静的 HTML ホスティング** -- 依存ゼロ、ビルド不要の純粋な HTML ファイル
- **GitHub Pages デプロイ** -- push するだけで自動公開、設定不要
- **日本語対応** -- 日本語のプライバシーポリシー・利用規約を提供
- **ストア申請対応** -- App Store / Google Play の申請要件に準拠した URL を提供

## Tech Stack

| カテゴリ | 技術 |
|---------|------|
| Format | Static HTML |
| Styling | Inline CSS |
| Hosting | GitHub Pages |
| Domain | GitHub Pages デフォルト |

## Getting Started

### Prerequisites

- Git
- Web ブラウザ（ローカルプレビュー用）

### Installation

```bash
git clone https://github.com/ksato8710/app-policies.git
cd app-policies
```

### Environment Variables

特に必要なし。

### Local Preview

```bash
# Python の簡易サーバーでプレビュー
python3 -m http.server 8000

# または任意の静的ファイルサーバーで開く
open index.html
```

ブラウザで [http://localhost:8000](http://localhost:8000) を開く。

## Architecture

### Directory Tree

```
app-policies/
├── index.html                    # トップページ（アプリ一覧 + ポリシーリンク）
├── chuzyuquiz-history/           # AI-ChuzyuQuiz 歴史（クイズアプリ）
│   └── privacy-policy.html       #   プライバシーポリシー
└── README.md
```

### Key Files

| ファイル | 役割 |
|---------|------|
| `index.html` | ポータルページ -- 全アプリのポリシーページへのリンク集 |
| `chuzyuquiz-history/privacy-policy.html` | AI-ChuzyuQuiz 歴史のプライバシーポリシー |

### Adding a New App

新しいアプリのポリシーを追加する場合:

```bash
# 1. アプリ用ディレクトリを作成
mkdir new-app-name

# 2. プライバシーポリシーを作成
touch new-app-name/privacy-policy.html

# 3. 必要に応じて利用規約も作成
touch new-app-name/terms-of-service.html

# 4. index.html にリンクを追加
# 5. コミット & push → GitHub Pages に自動反映
```

## Commands

| コマンド | 説明 |
|---------|------|
| `python3 -m http.server 8000` | ローカルプレビューサーバー起動 |
| `open index.html` | ブラウザで直接開く |

## Deploy

GitHub Pages で自動デプロイ。リポジトリ設定でソースを `main` ブランチのルートに設定済み。

```bash
git add .
git commit -m "add: new app policy"
git push origin main
# → GitHub Pages に自動反映
```

## Test / CI

静的 HTML のみのため、ビルドステップやテストフレームワークは不要。

```bash
# HTML の構文チェック（オプション）
npx html-validate index.html
npx html-validate chuzyuquiz-history/privacy-policy.html

# リンク切れチェック（オプション）
npx broken-link-checker https://ksato8710.github.io/app-policies/
```

push するだけで GitHub Pages に自動反映されるため、CI/CD パイプラインは不要。

## Hosted Policies

| アプリ | ポリシー | URL |
|-------|---------|-----|
| AI-ChuzyuQuiz 歴史 | プライバシーポリシー | `/chuzyuquiz-history/privacy-policy.html` |

## Related Projects

| プロジェクト | 説明 |
|-------------|------|
| [product-hub](https://github.com/ksato8710/product-hub) | プロダクトエコシステム管理ダッシュボード |
| [history-quiz-app](https://github.com/ksato8710/history-quiz-app) | 歴史クイズアプリ（ChuzyuQuiz） |

## Changelog

| 日付 | 変更内容 |
|------|----------|
| 2026-01 | 初期リリース -- AI-ChuzyuQuiz 歴史のプライバシーポリシー追加 |

## Roadmap

- [ ] 利用規約ページの追加（terms-of-service.html）
- [ ] 新規アプリのポリシー追加（必要に応じて）
- [ ] Cookie ポリシーテンプレートの追加
- [ ] 共通 CSS ファイルの分離（デザイン統一）
- [ ] 多言語対応（英語版ポリシー）

## Contributing

Issue や Pull Request は歓迎です。ポリシー文面の改善提案も受け付けています。

## License

MIT
