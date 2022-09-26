---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: "text-center"
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# use UnoCSS
css: unocss
---

# Engine vol_54

<p>Shintaro Takahashi</p>

<style>
  p {
    font-size: 24px;
    text-align: right;
  }
</style>
<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

theme: seriph
css: unocss

---

# 自己紹介

- **名前** : 高橋 伸太朗
- **所属** : DCB1U
- **仕事** : FE
- **年齢** : 25 歳
- いつも窓際でパソコンカタカタしてます

<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSdyW_rzI6DfekDkZw_wPByHtisEueDZHAtSMXaP4fPBUDFcs8&s" />

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
  h1 {
    background-color: #2B90B6;
    background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
    background-size: 100%;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    -webkit-text-fill-color: transparent;
    -moz-text-fill-color: transparent;
  }
  img {
    margin-left: auto;
  }
</style>

---

# 今日話す内容

<br>
<br>
<br>

## Figma と storybook は連携出来ます！

<style>
   h2 {
    margin-top: 50px;
    text-align: center;
  }
</style>

---

# 出来る事

1. storybook 上に Figma のデザインデータを表示させる
   <br>**ここに画像とか貼る**

2. Figma 上に storybook のコンポーネントを表示させる
   <br>**ここに画像とか貼る**

<style>
 ol {
    margin-top: 80px;
  }
  li {
    font-size: 24px;
    margin-top: 50px;
  }
</style>

---

# 何が嬉しいのか

- デザイナー　 ←→ 　エンジニアのコミュニケーションコスト下げられる(かも？)
- エンジニア以外も開発中の画面やコンポーネントを確認しやすい！

<style>
  ul {
    margin-top: 80px;
  }
  li {
    font-size: 24px;
    margin-top: 50px;
  }
</style>

---

# storybook ってなんだっけ？

## 概要(一般向け)

<br>

UI のカタログ作成ツール(コンポーネントカタログ)。<br>
コンポーネントという UI のパーツ単位での挙動が確認でき、画像のようにそれぞれのコンポーネントごとに見た目や挙動を確認できる。<br>
Visual Regression Test や Interaction Test にも利用できてみんな幸せれになる素敵なツール。

**ここに画像を貼る**

---

# storybook ってなんだっけ？

## (エンジニア向け)

<br>

**ここに code を埋め込む**

**ここに 画像 を埋め込む**

---

# storybook 上に Figma のデザインデータを表示させる

---

# Figma 上に storybook のコンポーネントを表示させる
