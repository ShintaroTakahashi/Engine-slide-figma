---
# try also 'default' to start simple
theme: seriph
themeConfig:
  primary: '#ffffff'
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: "text-center"
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: true
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

- エンジニア以外も開発中の画面やコンポーネントを確認しやすい！
<br>
<br>
→ デザイナーやディレクターとFEの間のコミュニケーションコストが下がる！

<style>
  ul {
    margin-top: 80px;
  }
  li {
    font-size: 30px;
    margin-top: 50px;
  }
</style>

---

# storybook ってなんだっけ？

## 概要(一般向け)

<br>

<p>

UI のカタログ作成ツール(コンポーネントカタログ)。<br>
コンポーネントという UI のパーツ単位での挙動が確認でき、画像のようにそれぞれのコンポーネントごとに見た目や挙動を確認できる。<br><br>
Visual Regression Test や Interaction Test にも利用できて**みんな幸せになる**。

</p>

**ここに画像を貼る**

<style>
  p {
    font-size: 24px;
  }
</style>

---

# storybook ってなんだっけ？(エンジニア向け)

# これを

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

# こうすると

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

# こうなります

![Buttonのstory](/images/button-story.png)


---

# storybook 上に Figma のデザインデータを表示させる

**ここに慣性系のイメージ画像**

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

**ここにfigmaの画像を貼る**

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

**ここに画像を貼る**

---

# Figma 上に storybook のコンポーネントを表示させる
**ここに完成形のイメージ画像**
