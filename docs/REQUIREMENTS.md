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

### 参照サイト

- URL: https://anyone-anytime-anywhere.super.site/
- 特徴:
  - 黒背景
  - 細いフォント（font-weight: 300）
  - 余白を最小限に
  - 写真はフル幅表示
  - 縦に密着して配置

### カラーパレット

- 背景色: `#000000`
- テキスト色: `#FFFFFF`
- ホバー時の透明度: `0.8`

### タイポグラフィ

- フォント: システムフォント（-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif）
- H1: `3.5em`, `font-weight: 300`, `letter-spacing: 0.01em`
- 本文: `1em`, `font-weight: 300`, `line-height: 1.4`

### レイアウト

- コンテナ: `max-width: 1400px`, `padding: 60px 40px`
- 要素間のギャップ: `0`（密着）
- 画像: `width: 100%`, `height: auto`

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

### トップページの投稿データ

```javascript
{
  date: 'YYYY/MM',
  description: '写真の説明文',
  image: 'Gallery/EP####_名前/images/ファイル名.JPG',
  url: 'Gallery/EP####_名前/index.html'
}
```

### 個別ページの画像データ

```javascript
{
  file: 'resize_DSC####.JPG',
  date: 'YYYY/MM',
  description: '写真の説明文'
}
```

## 今後の拡張予定

- [ ] Google Fonts（Inter）の導入
- [ ] 画像の最適化ツールの導入
- [ ] RSSフィードの追加
- [ ] 検索機能の追加

