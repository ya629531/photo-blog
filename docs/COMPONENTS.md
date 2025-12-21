# コンポーネント仕様

## トップページ（index.html）

### Header コンポーネント

**場所**: `.container > header`

**構造**:
```html
<header>
  <div class="site-title-top-left">Anyone, Anytime, Anywhere</div>
  <div class="site-title-small">Anyone, Anytime, Anywhere</div>
  <h1>Anyone, Anytime, Anywhere</h1>
</header>
```

**スタイル**:
- `text-align: center`
- `margin-bottom: 60px`
- `position: relative`

**左上のタイトル（.site-title-top-left）**:
- `position: absolute`
- `top: 0`
- `left: 0`
- `font-size: 1em`
- `font-weight: 300`
- `line-height: 1.4`
- `color: #fff`

**小さいタイトル（.site-title-small）**:
- `font-size: 1em`
- `font-weight: 300`
- `line-height: 1.4`
- `margin-bottom: 0`
- `padding-bottom: 0`

**H1スタイル**:
- `font-size: 3.5em`
- `font-weight: 300`
- `letter-spacing: 0.01em`
- `line-height: 1.1`
- `margin-top: 0`
- `margin-bottom: 0`

---

### Banner コンポーネント

**場所**: `.container > .banner`（ヘッダーの下）

**構造**:
```html
<div class="banner">
  <img src="images/banner.jpg" alt="Banner" class="banner-image">
</div>
```

**スタイル**:
- `width: 100%`
- `margin-bottom: 0`
- `padding: 0`

**Banner Image（.banner-image）**:
- `width: 100%`
- `height: auto`
- `display: block`
- `margin: 0`
- `padding: 0`
- `loading: "lazy"`

---

### Photo Post Grid コンポーネント

**場所**: `.container > .photo-grid`（バナーの下）

**構造**:
```html
<div class="photo-grid">
  <a href="..." class="photo-post">
    <div class="photo-post-caption">日付 説明文</div>
    <img src="..." class="photo-post-image" alt="...">
    <div class="photo-post-date">日付</div>
  </a>
  <!-- 複数の投稿が横に並ぶ -->
</div>
```

**データ構造（Blog/data.json）**:
```json
{
  "episodes": [
    "EP0001_Suikeien",
    "EP0002_Rikugien",
    "EP0003_Gaien"
  ]
}
```

**episodes配列**:
- エピソード名（フォルダ名）を文字列で列挙
- エピソード番号で降順ソート（EP0003 → EP0002 → EP0001）
- 各エピソードの`Gallery/EP####_名前/data.json`から`fullTitle`を取得して表示

**Photo Grid（.photo-grid）**:
- `display: grid`
- `grid-template-columns: repeat(3, 1fr)`
- `gap: 0`
- `width: 100%`

**Photo Post（.photo-post）**:
- `text-decoration: none`
- `color: #fff`
- `display: block`
- `opacity: 1`
- `transition: opacity 160ms ease`
- ホバー時: `opacity: 0.8`

**Photo Post Caption（.photo-post-caption）**:
- `font-size: 1em`
- `font-weight: 300`
- `line-height: 1.4`
- `margin: 0`
- `padding-bottom: 0`

**Photo Post Image（.photo-post-image）**:
- `width: 100%`
- `height: auto`
- `display: block`
- `margin: 0`
- `padding: 0`
- `loading: "lazy"`

**Photo Post Date（.photo-post-date）**:
- `font-size: 1em`
- `font-weight: 300`
- `line-height: 1.4`
- `margin: 0`
- `padding: 0`

---

## 個別ページ（Gallery/EP####_名前/index.html）

### Header コンポーネント

**場所**: `.container > header`

**構造**: トップページと同じ

---

### Banner コンポーネント

**場所**: `.banner > .banner-image`

**データ構造（data.json）**:
```json
{
  "title": "EP0001 Suikeien",
  "fullTitle": "Suikeien Garden at Shibamata Taishakuten in the rain, Tokyo",
  "bannerPosition": "60%",
  "images": [...]
}
```

**bannerPosition**:
- バナー画像の縦方向の表示位置を指定（パーセンテージ）
- デフォルト値: `"60%"`
- 例: `"50%"`（中央）、`"30%"`（上部寄り）、`"80%"`（下部寄り）
- `object-position: center {bannerPosition}`として適用される

**動作**:
- `banner.jpg`または`banner.jpeg`が見つからない場合、`images`配列の最初の画像をbannerとして使用

---

### Photo Gallery コンポーネント

**場所**: `.container > main#photo-gallery`

**構造**:
```html
<main id="photo-gallery">
  <div class="photo-item">
    <div class="photo-caption">日付 説明文</div>
    <img src="images/ファイル名.JPG" alt="説明文">
    <div class="photo-caption">日付</div>
  </div>
  <!-- 複数の写真が繰り返される -->
</main>
```

**データ構造（data.json）**:
```json
{
  "title": "EP0001 Suikeien",
  "fullTitle": "Suikeien Garden at Shibamata Taishakuten in the rain, Tokyo",
  "bannerPosition": "60%",
  "images": [
    "DSCF0973_resize.JPG",
    "DSCF0985_resize.JPG",
    // ... ファイル名順に並べる
  ]
}
```

**images配列**:
- 文字列配列形式（推奨）: ファイル名の文字列配列
- オブジェクト配列形式（後方互換性のため）: 各画像の詳細情報を含むオブジェクト配列

**Photo Item（.photo-item）**:
- `margin-bottom: 0`

**Photo Caption（.photo-caption）**:
- `font-size: 1em`
- `font-weight: 300`
- `line-height: 1.4`
- `color: #fff`
- `margin: 0`
- `padding: 0`

**Photo Image（img）**:
- `width: 100%`
- `height: auto`
- `display: block`
- `margin: 0`
- `padding: 0`
- `vertical-align: bottom`
- `loading: "lazy"`

---

## 共通コンポーネント

### Container（.container）

**用途**: すべてのページで使用

**スタイル**:
- `max-width: 1400px`
- `margin: 0 auto`
- `padding: 60px 40px`

### Footer

**現在の状態**: 非表示（`display: none`）

---

## JavaScript関数

### 個別ページ

#### `loadImages()`
- `imageData`配列を読み込んで、`#photo-gallery`内に写真を動的に生成
- `DOMContentLoaded`イベントで実行

---

## コンポーネントの命名規則

- **クラス名**: ケバブケース（`post-caption`）
- **ID名**: ケバブケース（`photo-gallery`）
- **JavaScript変数**: キャメルケース（`imageData`）

## 新しいコンポーネントを追加する場合

1. `docs/COMPONENTS.md`に仕様を追加
2. HTML構造を定義
3. CSSスタイルを定義
4. JavaScript関数を定義（必要に応じて）
5. 実装後に動作確認

