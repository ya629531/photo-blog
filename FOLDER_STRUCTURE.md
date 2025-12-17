# フォルダ構成の提案

参照サイト（https://anyone-anytime-anywhere.super.site/）のような構造にするためのフォルダ構成案です。

## 推奨構成

```
Blog/
├── index.html                    # トップページ（写真集一覧を表示）
├── .gitignore
├── css/
│   └── style.css                # 共通スタイルシート
├── images/                      # 現在の画像（後で移動）
│   └── ...
└── gallery/                     # 各写真集フォルダ
    ├── tokyo-autumn-2025/       # 写真集1（例：東京の秋 2025）
    │   ├── index.html           # 写真集の個別ページ
    │   └── images/              # この写真集専用の画像
    │       ├── photo1.jpg
    │       ├── photo2.jpg
    │       └── ...
    ├── ueno-park/               # 写真集2（例：上野公園）
    │   ├── index.html
    │   └── images/
    │       └── ...
    └── meiji-jingu/             # 写真集3（例：明治神宮）
        ├── index.html
        └── images/
            └── ...
```

## 構成の説明

### トップページ（index.html）
- サイトタイトル「Anyone, Anytime, Anywhere」を表示
- 各写真集へのリンクを一覧表示
- 各写真集のサムネイル画像とタイトルを表示

### 各写真集フォルダ（gallery/）
- 各写真集は独立したフォルダとして管理
- 各フォルダに`index.html`と`images/`フォルダを含む
- URL例：`/gallery/tokyo-autumn-2025/` → `gallery/tokyo-autumn-2025/index.html`

### メリット
1. **拡張性**: 新しい写真集を追加する際、新しいフォルダを追加するだけ
2. **整理**: 各写真集の画像とHTMLが分離され、管理しやすい
3. **独立性**: 各写真集が独立しているため、削除や移動が容易
4. **URL構造**: クリーンなURL構造（例：`/gallery/tokyo-autumn-2025/`）

## 実装手順

1. `gallery/`フォルダを作成
2. 既存の`images/`フォルダを最初の写真集として移動
3. トップページを写真集一覧ページに変更
4. 各写真集用のテンプレートHTMLを作成
