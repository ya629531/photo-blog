# 要件定義

## プロジェクト概要

写真ブログサイト「Anyone, Anytime, Anywhere」の要件定義書。

## 機能要件

### トップページ（index.html）

- [x] サイトタイトル「Anyone, Anytime, Anywhere」を表示

- [x] 各投稿は1枚の写真と日付・説明文を含む
- [x] 投稿をクリックで個別ページへ遷移
- [x] ホバー時に透明度が変化（opacity: 0.8）

### 個別ページ（Gallery/EP####_名前/index.html）

- [x] サイトタイトルを表示
- [x] 写真集内の写真を縦に並べて表示
- [x] 各写真に日付と説明文を表示（上部と下部）
- [x] 画像は遅延読み込み（lazy loading）

### 共通要件

- [x] レスポンシブ対応（モバイル・デスクトップ）
- [x] 黒背景（#000）
- [x] 白文字（#fff）
- [x] シンプル・ミニマルなデザイン

## デザイン要件

### カラーパレット

- 背景色: `#000000`
- テキスト色: `#FFFFFF`
- ホバー時の透明度: `0.8`

### タイポグラフィ

- フォント: システムフォント（-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif）
- H1: `3.5em`, `font-weight: 300`, `letter-spacing: 0.01em`
- 本文: `1em`, `font-weight: 300`, `line-height: 1.4`

### レイアウト

- コンテナ: `max-width: 1400px`, `padding: 20px`
- トップページのフォトグリッド: `gap: 40px`, `padding-left: 100px`, `padding-right: 100px`（デスクトップ）
- 個別ページのフォトギャラリー: `gap: 40px`, `padding-left: 100px`, `padding-right: 100px`（デスクトップ）
- 画像: `width: 100%`, `height: auto`
- バナー画像: `height: 300px`（デスクトップ）、`100px`（モバイル）、`object-fit: cover`

## 技術要件

### 技術スタック

- HTML5
- CSS3（インラインスタイル）
- Vanilla JavaScript（フレームワーク不使用）

### パフォーマンス

- 画像は最適化済み（`resize_*.JPG`）
- 画像の遅延読み込み（`loading="lazy"`）
- 静的サイト（サーバーサイド不要）

### ブラウザ対応

- モダンブラウザ（Chrome, Firefox, Safari, Edge）
- モバイルブラウザ対応

### デプロイ

- GitHub Pagesでデプロイ可能
- 静的ファイルのみ

### Google Analytics

- [x] トップページ（`index.html`）にGoogle Analyticsを実装
- [x] 各エピソードページ（`Gallery/index.html`）にGoogle Analyticsを実装
- [x] エピソード別の分析が可能（ページパスにエピソード情報を含める）
  - エピソードページのページパス: `/episode/{エピソード名}`（例: `/episode/EP0001_Suikeien`）
  - Google Analyticsでエピソード別のページビューを分析可能

## データ構造

### トップページのエピソードデータ（data.json）

```json
{
  "episodes": [
    "EP0001_Suikeien",
    "EP0002_Rikugien",
    "EP0003_Gaien",
    "EP0004_Maeda",
    "EP0005_Fushimi",
    "EP0006_Chourakukan"
  ]
}
```

### 各エピソードのデータ構造（Gallery/EP####_名前/data.json）

```json
{
  "title": "EP0001 Suikeien",
  "fullTitle": "Suikeien, a garden at Shibamata Taishakuten in the rain, Tokyo",
  "date": "2025/10/25",
  "bannerPosition": "60%",
  "description": {
    "en": ["英語の説明文（配列形式）"],
    "ja": ["日本語の説明文（配列形式）"]
  },
  "images": [
    "DSCF0988_resize.JPG",
    "DSCF0992_resize.JPG",
    ...
  ]
}
```

**データフィールドの説明**:
- `title`: エピソードの短いタイトル（例: "EP0001 Suikeien"）
- `fullTitle`: エピソードの完全なタイトル（トップページと個別ページのh1で使用）
- `date`: 撮影日（形式: "YYYY/MM/DD"）
- `bannerPosition`: バナー画像の縦方向の表示位置（パーセンテージ、デフォルト: "60%"）
- `description`: 説明文オブジェクト
  - `en`: 英語の説明文（文字列配列または文字列）
  - `ja`: 日本語の説明文（文字列配列または文字列）
- `images`: 画像ファイル名の配列（文字列配列形式を推奨）

## 今後の拡張予定

- [ ] Google Fonts（Inter）の導入
- [ ] 画像の最適化ツールの導入
- [ ] RSSフィードの追加
- [ ] 検索機能の追加

