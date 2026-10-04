# VSCodeでの開発

## 作業フォルダ

`Blog.code-workspace` をVSCodeで開く。リポジトリのルートはこの `Blog` フォルダであり、親のObsidianノートフォルダではない。

## 編集とプレビュー

1. `Gallery/EP####_名前/data.json` のタイトル・日英紹介文・画像一覧を編集する。
2. 新しいエピソードはトップレベルの `data.json` の `episodes` に追加する。
3. VSCodeの「ターミナル → タスクの実行 → Blog: ローカルプレビュー」を実行する。
4. ブラウザで http://127.0.0.1:8000/ を開く。
5. タスクを終了するには「ターミナル → タスクの終了」を選ぶ。

Python 3が必要。HTMLをファイルとして直接開くとJSONの読み込みが制限されることがあるため、HTTPサーバーで確認する。サーバーはこのMacからのみ接続できる。

## GitHubへ公開

VSCodeのソース管理で差分を確認し、今回の変更だけをステージしてコミットする。その後pushする。統合ターミナルでも実行できる：

```sh
git status
git diff --check
git add Gallery/EP0010_Kasugataisha/data.json
git commit -m "Update Kasuga Taisha episode"
git push origin main
```

新しいエピソードやドキュメントも変更した場合は、それらもステージする。

push後はGitHub Actionsの最新の `pages-build-deployment` が成功したことを確認し、公開ページでタイトル・本文・写真を確認する。pushの成功だけではデプロイ完了を意味しない。

- 公開サイト： https://ya629531.github.io/photo-blog/
- 公開処理： https://github.com/ya629531/photo-blog/actions

## プロジェクトの指示

作業方針は `AGENTS.md`、仕様は `docs/` を参照する。Cursorの既存設定は `.cursorrules` に残っている。
