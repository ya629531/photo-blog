# フォルダ構成

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
    ├── index.html              # エピソードページの共通テンプレート（動的に生成）
    └── EP0001_Suikeien/        # 写真集1（EP####_名前形式）
        ├── index.html          # リダイレクト用のシンプルなHTML
        ├── data.json           # エピソードのメタデータ
        └── images/             # この写真集専用の画像
            ├── banner.jpg      # バナー画像（オプション）
            ├── DSCF0988_resize.JPG
            ├── DSCF0992_resize.JPG
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
- フォルダ名は `EP####_名前` 形式（Episode + 4桁の通し番号 + アンダースコア + 名前）
- 各フォルダに`index.html`（リダイレクト用）、`data.json`、`images/`フォルダを含む
- 実際の表示は`Gallery/index.html`が動的に生成
- URL例：`/Gallery/EP0001_Suikeien/index.html` → `Gallery/index.html`がエピソード名を取得して表示

### エピソードページの共通テンプレート（Gallery/index.html）
- すべてのエピソードページで使用される共通のHTMLファイル
- URLパラメータまたはパスからエピソード名を取得
- エピソード名に基づいて`data.json`を読み込み、動的にコンテンツを生成
- Google Analyticsでエピソード別のトラッキングを実装

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

1. `Gallery/EP####_名前/` フォルダを作成（####は4桁の通し番号）
2. その中に以下を作成:
   - `index.html`: リダイレクト用のシンプルなHTML（既存のエピソードを参考）
   - `data.json`: エピソードのメタデータ（title, fullTitle, date, bannerPosition, description, images）
   - `images/` フォルダ: 画像ファイルを配置（`banner.jpg`または`banner.jpeg`を推奨）
3. トップレベルの`data.json`の`episodes`配列に新しいエピソード名を追加

**例**:
```json
{
  "episodes": [
    "EP0001_Suikeien",
    "EP0002_Rikugien",
    "EP0003_Gaien",
    "EP0004_Maeda",
    "EP0005_Fushimi",
    "EP0006_Chourakukan",
    "EP0007_新しいエピソード"  // 追加
  ]
}
```

