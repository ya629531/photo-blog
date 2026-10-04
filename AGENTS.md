# 写真ブログの作業方針

このフォルダが `ya629531/photo-blog` のGitリポジトリ。静的HTML/CSSとVanilla JavaScriptを使う。

- 変更に関連する `docs/` の仕様を読み、仕様を変更するときはドキュメントを先に更新する。
- エピソードは `Gallery/EP####_名前/` で管理し、タイトル・日英紹介文・画像一覧は各 `data.json` を編集する。
- 公開一覧はルートの `data.json` の `episodes`。共通表示は `Gallery/index.html`。
- 紹介文は既存エピソードの語り口を参考にする。歴史的事実は公式資料で確認し、写真から確認できない撮影体験を勝手に追加しない。
- CSSは既存のインライン形式に合わせ、JavaScript変数はcamelCase、クラス名・IDはkebab-caseを使う。
- 写真には `alt` と `loading="lazy"` を設定する。
- 記事データ取得時の `cache: 'no-cache'` を維持する。
- プレビューは `docs/DEVELOPMENT.md` のHTTPサーバーを使う。
- Gitはこのフォルダで操作し、差分を確認して対象の変更のみcommitする。公開を依頼されたらpushし、GitHub Pagesの成功と公開内容を確認する。
- 認証情報や認証情報を含むremote URLを出力しない。
