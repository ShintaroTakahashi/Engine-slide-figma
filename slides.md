---
theme: seriph
themeConfig:
  primary: '#ffffff'
class: "text-center"
highlighter: shiki
lineNumbers: true
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
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

---

# 自己紹介

- **名前** : 高橋 伸太朗
- **所属** : DCB1U
- **仕事** : FE
- **年齢** : 25 歳
- いつも窓際でパソコンカタカタしてます

<img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSdyW_rzI6DfekDkZw_wPByHtisEueDZHAtSMXaP4fPBUDFcs8&s" />

<style>
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

# storybook ってなんだっけ？

<br>

## 概要

<br>

<p>

UI のカタログ作成ツール(コンポーネントカタログ)。<br>
コンポーネントという UI のパーツ単位での挙動が確認でき、画像のようにそれぞれのコンポーネントごとに見た目や挙動を確認できる。<br><br>
Visual Regression Test や Interaction Test にも利用できて**みんな幸せになる**。

</p>

<style>
  p {
    font-size: 24px;
  }
</style>

---

<iframe src="https://storybook.js.org/" width="100%" height="100%"></iframe>

---

## これを

<br>

```jsx
// Button.jsx
export const Button = ({ children, onClick }) => (
  <button className="button" onClick={onClick}>
    {children}
  </button>
);
```

```scss
// button.css
.button {
  border-radius: 34px;
  border: 3px solid transparent;
  background-image: linear-gradient(#ffffff 0 100%), linear-gradient(93.15deg, #ffe679 0, #ff3333 100%);
  background-origin: border-box;
  background-clip: padding-box, border-box;
  // ...any styles

  &:disabled {
    background-image: linear-gradient(#ffffff 0 100%), linear-gradient(93.15deg, #bdbdbd 0, #949494 100%);
    opacity: 0.45;
  }
}
```

---

## こうすると

<br>

```jsx
// Button.stories.js
import { Button } from "../components/atoms/Button";

export default {
  component: Button,
} ;

export const Default = {
  args: {
    children: "Button",
  },
};

export const Disabled = {
  args: {
    disabled: true,
    children: "Button",
  },
};
```

---

## こうなります

<br>
<img src="/images/button-story.png" alt=""/>

---

# 出来る事

1. storybook 上に Figma のデザインデータを表示させる

2. Figma 上に storybook のコンポーネントを表示させる

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

<div>

1. コンポーネントとデザインを紐づけやすい
2. 開発中のコンポーネントをエンジニア以外に共有しやすい

<br>

↓

- デザイナーやディレクターとFEの間のコミュニケーションコストが下がる
- コンポーネント駆動開発(CDD)がさらに捗る！！

</div>

<style>
  ol {
    margin-top: 80px;
  }
  li {
    font-size: 26px;
    margin-top: 30px;
  }
  p {
    font-size: 26px;
    margin-left: 100px;
  }
</style>

---

# storybook 上に Figma のデザインデータを表示させる

<style>
  div{
    display:grid;
    place-items: center;
  }
</style>

---

# storybook 上に Figma のデザインデータを表示させる

## 手順

<br>

1. storybookのaddonを入れる
2. ちょちょいっと設定する
3. storyを書く
4. Figmaの共有リンクをstory紐づける
5. 良い感じになる！


<style>
  li {
    font-size: 30px;
  }
</style>

---

# storybook 上に Figma のデザインデータを表示させる

<br>

## 手順1 : storybookのaddonをinstallする

<br>
<br>

`yarn add -D storybook-addon-designs`

<style>
  code {
    display: inline-block;
    padding: 10px;
    margin-top: 50px;
    font-size: 30px;
  }
</style>


---

# storybook 上に Figma のデザインデータを表示させる

<br>

## 手順2 : ちょちょいっと設定する

<br>

```js{11}
// .storybook/main.js
module.exports = {
  stories: [
    "../stories/**/*.stories.mdx",
    "../stories/**/*.stories.@(js|jsx|ts|tsx)",
  ],
  addons: [
    "@storybook/addon-links",
    "@storybook/addon-essentials",
    "@storybook/addon-interactions",
    "storybook-addon-designs",
  ],
  framework: "@storybook/react",
  core: {
    builder: "@storybook/builder-webpack5",
  },
};

```


---

# storybook 上に Figma のデザインデータを表示させる

<br>

## 手順3 : storyを書く

<br>
<br>

```jsx
//...
export const Default = {
  args: {
    children: "Button",
  },
};

export const Disabled = {
  args: {
    disabled: true,
    children: "Button",
  },
};
```

---

# storybook 上に Figma のデザインデータを表示させる

<br>

## 手順4 : Figmaの共有リンクを紐づける

<img src="/images/get-figma-link.png" alt="" />

---

```jsx{3-8,15-20}
//...
export const Default: ButtonStory = {
  parameters: {
    design: {
      type: "figma",
      url: "https://www.figma.com/hogehoge",
    },
  },
  args: {
    children: "Button",
  },
};

export const Disabled: ButtonStory = {
  parameters: {
    design: {
      type: "figma",
      url: "https://www.figma.com/fugafuga",
    },
  },
  args: {
    disabled: true,
    children: "Button",
  },
};
```

---

# storybook 上に Figma のデザインデータを表示させる

<br>

## 手順5 : 良い感じになる！
<br>

<img src="/images/figma-on-storybook.png" />

---

# 良いところ

- 実装したコンポーネントとデザインを同じ画面で見れる
<br>
→ ブラウザの行ったり来たりが減る

<br>

- 埋め込みのFigma上に最終更新日時が出る
<br>
→ デザインの変更が追いやすい(ただしファイル単位で時間もざっくり)

<style>
  li {
    margin-top: 20px;
    font-size: 30px;
  }
</style>

---

# 注意点

- page直下のframe単位でしか表示できない(ネストされたframeは×)
  <br>→ Figmaの仕様上page直下のframeしか固有のURLが生成されない

<br>

- Figmaファイルの閲覧権限が無い(inviteされていない)場合はstorybookからも見れない

<div class="container">
  <img src="/images/not-found-figma.png" />
</div>

<style>
  .container {
    margin-top: 20px;
    margin-left: 50px;
    width:500px;
    height:300px;
  }

  li {
    font-size: 24px;
  }
</style>

---

# Figma 上に storybook のコンポーネントを表示させる

<style>
    div{
    display: grid;
    place-items: center;
  }
</style>

---

# Figma 上に storybook のコンポーネントを表示させる

- パターン1 : ChromaticとStorybook Connectを使用する
- パターン2 : Gist pluginを使用する

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

# Figma 上に storybook のコンポーネントを表示させる

- パターン1 : ChromaticとStorybook Connectを使用する
<br>
<br>
  Chromatic : storybook公式のホスティングサービス
<br>
  Storybook Connect : storybook公式のFigma plugin、まだ発展途上感。

- パターン2 : Gist pluginを使用する

<style>
  ul {
    margin-top: 80px;
  }
  li {
    font-size: 24px;
    margin-top: 50px;
  }
  li:not(:first-child) {
    opacity: 0.3;
  }
</style>

---

# ChromaticとStorybook Connectを使用する

<br>

## 手順

<br>

1. storybookをChromaticにホストする
2. Figma に Storybook Connect をインストールする
3. ホストしているChromaticのURLを紐づける
4. Figma上にコンポーネントが表示される

<style>
  li {
    font-size: 30px;
  }
</style>

---

# 個人的イケてないポイント
- ホスト先がChromaticに縛られる
  - Chromaticの月額課金がかかる場合もある
- storybookの機能を全て使える訳ではない

<style>
  li {
    margin-top: 20px;
    font-size: 30px;
  }
</style>

---

# Figma 上に storybook のコンポーネントを表示させる

- パターン1 : ChromaticとStorybook Connectを使用する
- パターン2 : Gist pluginを使用する
  <br>
  Gist plugin : Figma上に外部ドキュメントを埋め込めるplugin

<style>
  ul {
    margin-top: 80px;
  }
  li {
    font-size: 24px;
    margin-top: 50px;
  }
  li:first-child {
    opacity: 0.3;
  }
</style>

---

# Gist pluginを使用する

<br>

## 手順

<br>

1. storybookをどこかにホストする
2. Figma に Gist plugin をインストールする
3. ホストしているstorybookのURLを紐づける
4. Figma上にstorybookが表示される
5. 良い感じ！

<style>
  li {
    font-size: 30px;
  }
</style>

---

# Gist pluginを使用する

<br>

## 手順1 : storybookをどこかにホストする

<br>
<br>

これはどこでも良いです。

今回はGithub-pagesにしました。

<style>
  p{
    font-size: 24px;
  }
</style>

---

# Gist pluginを使用する

<br>

## 手順2 : Figma に Gist plugin をインストールする

<div class="container">
  <img src="/images/gist-plugin.png" />
</div>

<style>
  .container {
    margin-top: 20px;
  }
</style>

---

# Gist pluginを使用する

<br>

## 手順3 : ホストしているstorybookのURLを紐づける

<div class="container">
  <img src="/images/gist-link-figma.png" />
</div>

<style>
  .container {
    margin-top: 20px;
    margin-left: 50px;
    height: 350px;
  }
  img{
    height: 100%;
  }
</style>

---

# Gist pluginを使用する

<br>

## 手順4 : Figma上にstorybookが表示される

<div class="container">
  <img src="/images/storybook-on-figma.png" />

   良い感じ ( ﾉ ﾟｰﾟ)ﾉ

</div>

<style>
  .container {
    display: flex;
    align-items: center;
    width: 100%;
    margin-top: 20px;
    height: 350px;
  }
  p{
    margin-left: 30px
  }
  img{
    height: 100%;
  }
</style>

---

# 良いところ

- Figma上で実際のコンポーネントも見れる
<br>
→ 非エンジニアが新しいツールをわざわざ覚えなくて良い

<br>

- storybookの機能も全て使える
<br>
→ ほとんどiframeで埋め込んでいるだけなので

<br>

- storybookのホスト先を縛られない
<br>
→ 認証もOK(のハズ)

<style>
  li {
    margin-top: 20px;
    font-size: 30px;
  }
</style>
