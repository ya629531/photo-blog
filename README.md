# Anyone, Anytime, Anywhere

写真ブログサイト。ミニマルなデザインで写真を縦に並べて表示します。

## プロジェクト概要

- **目的**: 個人の写真作品を公開するブログサイト
- **デザイン**: 参照サイト（https://anyone-anytime-anywhere.super.site/）をベースにしたミニマルなデザイン
- **技術スタック**: 静的HTML/CSS/JavaScript（サーバーサイド不要）

## セットアップ

1. リポジトリをクローン
2. `index.html`をブラウザで開く（ローカル開発）
3. GitHub Pagesでデプロイ可能

## フォルダ構成

詳細は `docs/FOLDER_STRUCTURE.md` を参照してください。

## 開発

- 新しい写真集を追加する場合は `Gallery/EP####_名前/` フォルダを作成
- トップページの `posts` 配列に新しい投稿を追加
- 各写真集の `imageData` 配列に画像情報を追加

## デプロイ

GitHub Pagesで自動デプロイされます。

## 参照ドキュメント

すべてのドキュメントは `docs/` フォルダにあります：

- `docs/REQUIREMENTS.md` - 要件定義
- `docs/DESIGN.md` - デザイン仕様
- `docs/COMPONENTS.md` - コンポーネント仕様
- `docs/FOLDER_STRUCTURE.md` - フォルダ構成

