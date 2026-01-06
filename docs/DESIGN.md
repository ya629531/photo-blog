# デザイン仕様

## デザインの特徴

1. **カラースキーム**
   - 背景: 完全な黒（#000000）
   - テキスト: 純白（#FFFFFF）
   - アクセント: なし（モノクロのみ）

2. **タイポグラフィ**
   - フォント: システムフォント（サンセリフ）
   - ウェイト: 細い（300）
   - サイズ: 大きめのH1（3.5em）、標準の本文（1em）
   - レタースペーシング: 0.01em（タイト）

3. **レイアウト**
   - コンテナ: 最大幅1400px、中央揃え
   - パディング: 20px（全方向、デスクトップ）、10px（モバイル）
   - トップページのフォトグリッド: `gap: 40px`, `padding-left: 100px`, `padding-right: 100px`（デスクトップ）
   - 個別ページのフォトギャラリー: `gap: 40px`, `padding-left: 100px`, `padding-right: 100px`（デスクトップ）
   - バナー画像: フル幅、高さ300px（デスクトップ）、100px（モバイル）、`object-fit: cover`でアスペクト比を維持
   - その他の画像: フル幅、縦横比を維持
   - 個別ページの写真アイテム: `background-color: #151515`, `padding: 20px`

4. **インタラクション**
   - ホバー: 透明度0.8に変化
   - トランジション: 160ms ease
   - カーソル: ポインター（リンク時）

## 実装詳細

### カラーパレット

```css
--bg-color: #000000;
--text-color: #FFFFFF;
--hover-opacity: 0.8;
```

### タイポグラフィ

```css
/* H1 */
font-size: 3.5em;
font-weight: 300;
letter-spacing: 0.01em;
line-height: 1.1;

/* 本文 */
font-size: 1em;
font-weight: 300;
line-height: 1.4;
```

### スペーシング

```css
/* コンテナ */
max-width: 1400px;
padding: 20px; /* デスクトップ */
padding: 10px; /* モバイル */
margin: 0 auto;

/* トップページのフォトグリッド */
gap: 40px;
padding-left: 100px; /* デスクトップ */
padding-right: 100px; /* デスクトップ */
padding-left: 0; /* モバイル */
padding-right: 0; /* モバイル */

/* 個別ページのフォトギャラリー */
gap: 40px;
padding-left: 100px; /* デスクトップ */
padding-right: 100px; /* デスクトップ */
padding-left: 10px; /* モバイル */
padding-right: 10px; /* モバイル */

/* 個別ページの写真アイテム */
background-color: #151515;
padding: 20px;
margin-bottom: 0;
```

### コンポーネントスタイル

#### トップページの投稿（.post）

```css
.post {
  display: block;
  text-decoration: none;
  color: #fff;
  opacity: 1;
  transition: opacity 160ms ease;
}

.post:hover {
  opacity: 0.8;
}
```

#### 個別ページの写真（.photo-item）

```css
.photo-item {
  margin-bottom: 0;
  background-color: #151515;
  padding: 20px;
}

.photo-item img {
  width: 100%;
  height: auto;
  display: block;
  margin: 0;
  padding: 0;
  vertical-align: bottom;
}

.photo-item-text {
  margin-top: 10px;
  font-size: 0.85em;
  color: #fff;
  font-weight: 300;
  line-height: 1.4;
  text-align: right;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}
```

## レスポンシブデザイン

### ブレークポイント

- デスクトップ: 1400px以上
- タブレット: 768px - 1399px
- モバイル: 767px以下

### モバイル対応

- パディングを調整（コンテナ: `padding: 10px`）
- フォントサイズを調整（トップページH1: `2.5em`、個別ページH1: `2.5em`）
- バナー画像の高さを調整（100px）
- フォトグリッド/フォトギャラリーのパディングを調整（左右: `10px`または`0`）
- トップページのフォトグリッドを1列に変更（`grid-template-columns: 1fr`）
- 左上のサイトタイトルを中央配置に変更（`position: static`, `text-align: center`）
- その他の画像は引き続きフル幅

## アクセシビリティ

- すべての画像に`alt`属性を設定
- コントラスト比: 21:1（黒背景・白文字）
- キーボードナビゲーション対応（リンク）

## パフォーマンス

- 画像の遅延読み込み（`loading="lazy"`）
- インラインCSS（外部CSSファイルなし）
- 最小限のJavaScript（Vanilla JS）

