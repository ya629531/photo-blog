# コンポーネント仕様

## トップページ（index.html）

### Header コンポーネント

**場所**: `.container > header`

**構造**:
```html
<div class="site-title-top-left">Anyone, Anytime, Anywhere</div>
<div class="container">
  <header></header>
</div>
<h1>Anyone, Anytime, Anywhere</h1>
```

**スタイル**:
- `text-align: center`
- `margin-bottom: 0`
- `position: relative`

**左上のタイトル（.site-title-top-left）**:
- `position: absolute`
- `top: 20px`
- `left: 20px`
- `font-size: 1em`
- `font-weight: 300`
- `line-height: 1.4`
- `color: #fff`
- モバイル時: `position: static`, `text-align: center`, `margin-bottom: 10px`

**H1スタイル**:
- `font-size: 3.5em`（デスクトップ）、`2.5em`（モバイル）
- `font-weight: 700`
- `letter-spacing: 0.01em`
- `line-height: 1.1`
- `margin-top: 0`
- `margin-bottom: 40px`
- `padding-left: 40px`（デスクトップ）、`10px`（モバイル）
- `padding-right: 40px`（デスクトップ）、`10px`（モバイル）

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
- `grid-template-columns: repeat(3, 1fr)`（デスクトップ）、`1fr`（モバイル）
- `gap: 40px`
- `width: 100%`
- `padding-left: 100px`（デスクトップ）、`0`（モバイル）
- `padding-right: 100px`（デスクトップ）、`0`（モバイル）

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

## 個別ページ（Gallery/index.html）

**注意**: 各エピソードフォルダの`index.html`はリダイレクト用のシンプルなHTMLです。実際の表示は`Gallery/index.html`が動的に生成します。

### Header コンポーネント

**場所**: `.container > header`

**構造**:
```html
<div class="site-title-top-left">
  <a href="../index.html">Anyone, Anytime, Anywhere</a> / <span id="episode-name">Loading...</span>
</div>
<div class="container">
  <header></header>
</div>
```

**左上のタイトル（.site-title-top-left）**:
- トップページへのリンクとエピソード名を表示
- エピソード名は「Episode #1」形式で表示
- リンクのホバー時: `opacity: 0.8`

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
- `banner.jpg`または`banner.jpeg`が見つからない場合、`images`配列の最初の画像（bannerを除く）をbannerとして使用

**H1スタイル（個別ページ）**:
- `font-size: 2.0em`（デスクトップ）、`2.5em`（モバイル）
- `font-weight: 700`
- `letter-spacing: 0.01em`
- `line-height: 1.1`
- `margin-top: 0`
- `margin-bottom: 40px`
- `padding-left: 40px`（デスクトップ）、`10px`（モバイル）
- `padding-right: 40px`（デスクトップ）、`10px`（モバイル）
- 内容は`data.json`の`fullTitle`を使用

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
    // ... ファイル名順に並べる
  ]
}
```

**images配列**:
- 文字列配列形式（推奨）: ファイル名の文字列配列
- オブジェクト配列形式（後方互換性のため）: 各画像の詳細情報を含むオブジェクト配列
- `banner.jpg`と`banner.jpeg`は自動的に除外される

**Photo Gallery（#photo-gallery）**:
- `display: flex`
- `flex-direction: column`
- `gap: 40px`
- `padding-left: 100px`（デスクトップ）、`10px`（モバイル）
- `padding-right: 100px`（デスクトップ）、`10px`（モバイル）

**Photo Item（.photo-item）**:
- `margin-bottom: 0`
- `background-color: #151515`
- `padding: 20px`

**Photo Image（img）**:
- `width: 100%`
- `height: auto`
- `display: block`
- `margin: 0`
- `padding: 0`
- `vertical-align: bottom`
- `loading: "lazy"`

**Photo Item Text（.photo-item-text）**:
- `margin-top: 10px`
- `font-size: 0.85em`
- `color: #fff`
- `font-weight: 300`
- `line-height: 1.4`
- `text-align: right`
- `display: flex`
- `flex-direction: column`
- `align-items: flex-end`
- EXIF情報を3行で表示:
  - 1行目: 撮影諸元（Exposure, Aperture, ISO）
  - 2行目: レンズ名と焦点距離（レンズ名がある場合）、またはカメラ名と焦点距離（レンズ名がない場合）
  - 3行目: カメラ名（レンズ名がある場合のみ）

**Description（説明文）**:
- 写真の最後に表示（`.photo-item`として）
- `padding-top: 40px`
- `text-align: left`
- フォント: `Georgia, "Times New Roman", serif`
- `font-style: italic`
- `font-size: 0.95em`
- `line-height: 2`
- `font-weight: 200`
- `letter-spacing: 0.02em`
- 英語と日本語の両方を表示可能
- 日付を別行で表示（英語: "December 2025"形式、日本語: "2025年12月"形式）

---

## 共通コンポーネント

### Container（.container）

**用途**: すべてのページで使用

**スタイル**:
- `max-width: 1400px`
- `margin: 0 auto`
- `padding: 20px`（デスクトップ）、`10px`（モバイル）

### Footer

**現在の状態**: 非表示（`display: none`）

---

## JavaScript関数

### 個別ページ

#### `getEpisodeName()`
- URLパラメータまたはパスからエピソード名を取得
- エピソード名が見つからない場合は`null`を返す

#### `getEpisodeName()`
- URLパラメータまたはパスからエピソード名を取得
- エピソード名が見つからない場合は`null`を返す
- 取得順序:
  1. URLパラメータ（`?episode=EP0001_Suikeien`）
  2. パス名（`/Gallery/EP0001_Suikeien/index.html`）
  3. href（`file://`プロトコルの場合）

#### `setBannerImage()`
- バナー画像を設定する関数
- `banner.jpg`を試し、見つからない場合は`banner.jpeg`を試す
- どちらも見つからない場合、`images`配列の最初の画像（bannerを除く）を使用

#### `loadImages()`
- `data.json`から画像データを読み込んで、`#photo-gallery`内に写真を動的に生成
- EXIF情報を取得して表示（exif-jsとexifrライブラリを使用）
- 説明文（英語・日本語）と日付を写真の最後に表示
- エピソード名を取得後、エピソードの`data.json`を読み込んで実行

#### Google Analytics統合
- エピソード名を取得後、Google Analyticsのページパスを動的に設定
- ページパス形式: `/episode/{エピソード名}`（例: `/episode/EP0001_Suikeien`）
- これにより、Google Analyticsでエピソード別のページビューを分析可能

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

