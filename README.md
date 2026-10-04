# Anyone, Anytime, Anywhere

写真ブログサイト。ミニマルなデザインで写真を縦に並べて表示します。

## プロジェクト概要

- **目的**: 個人の写真作品を公開するブログサイト
- **デザイン**: 参照サイト（https://anyone-anytime-anywhere.super.site/）をベースにしたミニマルなデザイン
- **技術スタック**: 静的HTML/CSS/JavaScript（サーバーサイド不要）

## セットアップ

1. リポジトリをクローン
2. VSCodeで `Blog.code-workspace` を開く
3. 「ターミナル → タスクの実行 → Blog: ローカルプレビュー」を実行し、http://127.0.0.1:8000/ で確認する
4. commit・push後、GitHub Pagesのデプロイを確認する

詳しい作業手順は `docs/DEVELOPMENT.md` を参照してください。

## フォルダ構成

詳細は `docs/FOLDER_STRUCTURE.md` を参照してください。

## 開発

- 新しい写真集を追加する場合は `Gallery/EP####_名前/` フォルダを作成
- トップレベルの `data.json` の `episodes` 配列に新しい投稿を追加
- 各写真集の `data.json` の `images` 配列に画像情報を追加

## デプロイ

GitHub Pagesで自動デプロイされます。

## 参照ドキュメント

すべてのドキュメントは `docs/` フォルダにあります：

- `docs/REQUIREMENTS.md` - 要件定義
- `docs/DESIGN.md` - デザイン仕様
- `docs/COMPONENTS.md` - コンポーネント仕様
- `docs/FOLDER_STRUCTURE.md` - フォルダ構成
