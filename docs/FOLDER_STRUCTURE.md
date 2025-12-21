# フォルダ構成

参照サイト（https://anyone-anytime-anywhere.super.site/）のような構造のフォルダ構成です。

## 現在の構成

```
Blog/
├── README.md                    # プロジェクト概要
├── index.html                   # トップページ（サイトタイトルを表示）
├── data.json                    # エピソードリスト（トップページで使用）
├── .cursorrules                 # Cursor用のプロジェクトルール
├── .gitignore
├── docs/                        # ドキュメントフォルダ
│   ├── REQUIREMENTS.md         # 要件定義
│   ├── DESIGN.md               # デザイン仕様
│   ├── COMPONENTS.md           # コンポーネント仕様
│   └── FOLDER_STRUCTURE.md     # フォルダ構成（このファイル）
└── Gallery/                     # 各写真集フォルダ
    └── EP0001_Ueno/            # 写真集1（EP0001_Ueno形式）
        ├── index.html          # 写真集の個別ページ
        ├── data.json           # エピソードのメタデータ
        └── images/             # この写真集専用の画像
            ├── resize_DSC01732.JPG
            ├── resize_DSC01736.JPG
            └── ...
```

## 構成の説明

### トップページ（index.html）
- サイトタイトル「Anyone, Anytime, Anywhere」を表示
- `data.json`からエピソードリストを読み込んで表示
- エピソード番号で降順ソート（EP0003 → EP0002 → EP0001）

### エピソードリスト（data.json）
- トップレベルに配置
- エピソード名（フォルダ名）の配列を管理
- 新しいエピソードを追加する際は、このファイルにエピソード名を追加

### 各写真集フォルダ（Gallery/）
- 各写真集は独立したフォルダとして管理
- フォルダ名は `EP0001_名前` 形式（Episode + 4桁の通し番号 + アンダースコア + 名前）
- 各フォルダに`index.html`と`images/`フォルダを含む
- URL例：`/Gallery/EP0001_Ueno/` → `Gallery/EP0001_Ueno/index.html`

### ドキュメントフォルダ（docs/）
- プロジェクトのドキュメントをまとめて管理
- `README.md`はトップレベルに残す（GitHubで自動表示される）

### メリット
1. **拡張性**: 新しい写真集を追加する際、新しいフォルダを追加するだけ
2. **整理**: 各写真集の画像とHTMLが分離され、管理しやすい
3. **独立性**: 各写真集が独立しているため、削除や移動が容易
4. **URL構造**: クリーンなURL構造（例：`/Gallery/EP0001_Ueno/`）
5. **ID管理**: EP0001, EP0002... の通し番号で管理しやすい

## 新しい写真集を追加する場合

1. `Gallery/EP0002_名前/` フォルダを作成
2. その中に `index.html` と `images/` フォルダを作成
3. 個別ページの `imageData` 配列に画像情報を追加

