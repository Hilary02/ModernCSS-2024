---
theme: seriph
fonts:
  sans: "HiraMaruProN-W4"
background: cover_bg.png
class: text-center
highlighter: shiki
lineNumbers: true
info: |
  ## 今日から使えるモダンCSS
   by hilary
drawings:
  persist: false
transition: slide-left
title: 今日から使えるモダンCSS
---

<div style="background: linear-gradient(90deg, #aaff00 0%, #91cfff 40%, #0ff 100%);
color: transparent;
-webkit-background-clip: text;
background-clip: text;
-webkit-text-fill-color: transparent;
text-fill-color: transparent;" >

# 今日から使えるモダンCSS
</div>

## 最新のスタイリング手法の紹介

---

# モダンCSSとは？

- 柔軟なレイアウトと効率的な開発を実現する機能群
- 厳密な定義が決まっているわけではない
- ここでは2022年のIEサポート終了を節目として、使いやすくなった機能を紹介

---

# なぜモダンCSSが大事か？

- より効率的なデザイン実装が可能
- CSS単体での強力な機能
  - 動的なスタイル変更
  - ネスト記法
  - 条件分岐

---

# 従来のCSSの課題

- ブラウザごとの対応の差
- クラス名の衝突、命名問題
- 複雑なセレクタ

---
layout: section
---

# スタイルの紹介

---

# 紹介するスタイル
- Grid Layout
- Flexbox
- Filter効果
- :has() セレクタ
- CSS Custom Properties
- CSS Nesting
- コンテナクエリ @container

---

# Grid Layout

- 2次元レイアウトの制御
- レスポンシブデザイン
- 複雑なレイアウトの実現

```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}
```

---

# Grid Layout(Demo)

<GridDemo />

<footer class="absolute bottom-0 left-0 p-2 text-sm">https://gridbyexample.com/examples/example1/</footer>

---

# Grid Layoutの余談

- IE11ではサポートされていなかった...
- vendor prefixで基本的な機能は使えたが、一部の機能は使えなかった

![](./grid-support.jpg)

<footerNote>https://web.archive.org/web/20211022054307/https://developer.mozilla.org/ja/docs/Web/CSS/grid</footerNote>

<!-- https://caniuse.com/?search=grid -->

---

# Flexbox

```css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

- 1次元方向の柔軟なレイアウト
- 要素の配置と間隔の調整
- モバイルファーストデザインに最適

---

# Flexbox (Demo)

<FlexDemo />

<FooterNote>https://developer.mozilla.org/ja/docs/Web/CSS/flex</FooterNote>

---

# GridやFlexboxで遊べるページ

- [Grid Garden](https://cssgridgarden.com/#ja)
- [CSS Grid Mastery Quiz](https://css-grid-mastery.uhyo.space/?lang=ja)
- [Flexbox Froggy](https://flexboxfroggy.com/)

ゲームを通じてプロパティを知ることができる

---

# Filter効果

```css
.glass-effect {
  backdrop-filter: blur(10px);
  background: rgba(255, 255, 255, 0.1);
}

.image {
  filter: brightness(1.2) contrast(1.1);
}
```

- 画像加工がCSSでできる
- 簡単にUI表現を実現
- disable画像などをこれだけで実現できる
- 2024年で最も使われた機能(※1)

<FooterNote>より詳しい紹介: https://www.asobou.co.jp/blog/web/css-filter <br/>
※1 https://2024.stateofcss.com/en-US/features/
</FooterNote>

---

# Filter効果(Demo)

<FilterDemo />

<FooterNote>https://developer.mozilla.org/ja/docs/Web/CSS/filter</FooterNote>


---

# CSS Custom Properties（変数）

```css
:root {
  --primary-color: #3b82f6;
  --spacing-unit: 8px;
}

.button {
  background-color: var(--primary-color);
  padding: calc(var(--spacing-unit) * 2);
}
```

- SASSの変数機能をCSS単体で実現
- 値の一元管理
- テーマ切り替えの実装

---

# :has() セレクタ

```css
.card:has(.image) {
  padding: 0;
}

form:has(:invalid) {
  border-color: red;
}
```

- 子要素に基づいて親要素のスタイルを変更
- 従来だとJSで実装する必要があった
- inputの状況に応じたスタイル制御が可能に

- デモ： https://codepen.io/tonkotsuboy/pen/rNqxaQJ

<FooterNote>https://coliss.com/articles/build-websites/operation/css/css-has-pseudo-class.html</FooterNote>
---

# CSS Nesting (Before)

```css
.card {
  padding: 1rem;
}

.card > .title {
  font-size: 1.5rem;
}

.card > :hover {
  background-color: #f3f4f6;
}

```

- 毎回親クラスを記述する必要があった

---

# CSS Nesting (After)

```css
.card {
  padding: 1rem;

  & .title {
    font-size: 1.5rem;
  }

  & :hover {
    background-color: #f3f4f6;
  }
}
```

- 従来SASSでしか書けなかった記法
- コードの可読性向上
- メンテナンス性の改善

---

# コンテナクエリ @container

```css
/* コンテナの定義 */
.container {
  container-type: inline-size;
}

/* コンテナクエリの記述 */
@container (width <= 400px) {
  /* スタイルの定義 */
  .card {
    padding: 1rem;
  }
}
```

- メディアクエリ（@media）が画面幅に基づくのに対し、コンテナクエリは要素幅に基づく
- コンポーネントベースの設計に適している
- サイドバーやカード型UIの実装に便利
- デモ: [Simple CQ Demo](https://codepen.io/web-dot-dev/pen/dymdbpg)

<FooterNote>https://coliss.com/articles/build-websites/operation/css/container-and-has-in-chrome105.html</FooterNote>

---

# 参考資料

- [HTMLやCSSのレイアウトの歴史を振り返る #HTML5 - Qiita](https://qiita.com/otome0927@github/items/8428265ae6caf98afb94)
[2023年モダンCSSの最新トレンド - Speaker Deck](https://speakerdeck.com/tonkotsuboy_com/2023nian-modancssnozui-xin-torendo)
<!-- - [2023年モダンCSSの最新トレンド](https://tonkotsuboy.github.io/20230413_findy_css/#1) -->

---
layout: section
---

# Appendix

---

# 時間があったら話したいコーナー
- Chrome開発者ツール
- CSSの情報収集ソース
- CSS3とはなにか
- リセットCSS

---

# Chrome開発者ツール

- 131からAIが搭載される
- grid, flexboxのプレビューが可能

---

# 情報収集ソース

- [MDN](https://developer.mozilla.org/ja/docs/Web/CSS)
  - リファレンス
  - ブラウザサポート確認

- [コリス](https://coliss.com/)
  - 情報キャッチアップ
  - かなり更新が早い

 <!-- [CSS-Tricks](https://css-tricks.com/) -->

---

# CSS3とはなにか

- CSS2.1以降、各モジュールが機能を追加していく形に変化した
- CSS3とはCSS2.1+追加モジュールの総称で単一の規格ではない

![](./CSSLevel.jpg)

<footerNote>https://techracho.bpsinc.jp/hachi8833/2016_10_03/26581</footerNote>

<!-- https://zenn.dev/helloiamktn/articles/444a937f41238d 
https://allabout.co.jp/gm/gc/376450/
https://zenn.dev/helloiamktn/articles/444a937f41238d#css-level-2.1-(css2.1)
-->

---

# CSSがW3C勧告になるまで

[W3C勧告とはなんぞ？Web標準化とW3Cにおける勧告プロセスについて | WEMO](https://wemo.tech/795#index_id6)

今あるCSSのドキュメント
[CSS current work & how to participate](https://www.w3.org/Style/CSS/current-work)


<FooterNote>https://www.w3.org/Style/CSS/</FooterNote>

<!-- [CSS Grid Layout Module Level 2](https://drafts.csswg.org/css-grid/)
[CSS Working Group Editor Drafts](https://drafts.csswg.org/) 
[CSSの仕様が標準化されるまで](https://zenn.dev/helloiamktn/articles/444a937f41238d)
-->
---

# リセットCSS

- ブラウザのデフォルトの挙動を打ち消すCSS
- 環境で挙動を統一するために利用

<footerNote>https://coliss.com/articles/build-websites/operation/css/css-reset-for-modern-browser.html</footerNote>

<!-- 社内で用いられているRIFFのリセットCSSも改善の余地があるかも...? -->

---

# 書き方のテクニック

この辺りの記事を参考にするとよいかも
[プロが実践するモダン CSS の書き方入門テクニック20選まとめ | PhotoshopVIP](https://photoshopvip.net/93818)
