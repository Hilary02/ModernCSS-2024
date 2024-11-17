---
theme: seriph
fonts:
  sans: "HiraMaruProN-W4"
background: cover_bg.png
class: text-center
highlighter: shiki
lineNumbers: true
info: |
  ## 明日から使えるモダンCSS
   by hilary
drawings:
  persist: false
transition: slide-left
title: 明日から使えるモダンCSS
---

<div style="background: linear-gradient(90deg, #82f369 0%, #91cfff 40%, #ffaacc 100%);
color: transparent;
-webkit-background-clip: text;
background-clip: text;
-webkit-text-fill-color: transparent;
text-fill-color: transparent;" >

# 明日から使えるモダンCSS
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

# Styleの紹介

---

# Grid Layout

- 2次元レイアウトの完全な制御
- レスポンシブデザインの簡素化
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

# Grid Layout

- IE11ではサポートされていなかった...
- vendor prefixで基本的な機能は使えたが、一部の機能は使えなかった

![](./grid-support.jpg)

<footerNote>https://caniuse.com/?search=grid</footerNote>

---

# Gridのトレーニング

<FlexDemo />

<FooterNote>https://developer.mozilla.org/ja/docs/Web/CSS/flex</FooterNote>

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

# Flexboxのトレーニング

- [Flexbox Froggy](https://flexboxfroggy.com/)
ゲーム形式でFlexboxの理解を深められる

---

# CSS Filters と Blur効果

```css
.glass-effect {
  backdrop-filter: blur(10px);
  background: rgba(255, 255, 255, 0.1);
}

.image {
  filter: brightness(1.2) contrast(1.1);
}
```

- 画像加工のCSS実装
- モダンなUI表現の実現
- パフォーマンスの最適化
- disable画像などは配信する必要がないかも...

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

- 親クラスを記述する必要がある

---

# CSS Nesting

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

- SASSライクな記法
- コードの可読性向上
- メンテナンス性の改善

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

- 親要素に基づく条件分岐
- 動的なスタイル制御が可能に

---

# @layer による詳細度制御

```css
@layer base, components, utilities;

@layer base {
  /* ベーススタイル */
}

@layer components {
  /* コンポーネントスタイル */
}
```

- 詳細度の明示的な制御
- カスケーディングの管理
- スタイルの優先順位付け

---

# モダンCSSツール群

- **PostCSS**
  - プラグインベースの変換ツール
  - 最新機能の先行利用

- **CSS Modules**
  - スコープ付きのスタイル
  - コンポーネントベースの開発

- **Tailwind CSS**
  - ユーティリティファースト
  - 高速な開発と保守性

---

# デバッグテクニック

```css
* {
  outline: 1px solid red;
}

/* レイアウトデバッグ用 */
body {
  background: #f0f0f0;
  grid-template-columns: repeat(12, 1fr);
}
```

- ブラウザの開発者ツール活用
- アウトラインデバッグ
- グリッドオーバーレイ

---

# 情報収集リソース

- **MDN Web Docs**
  [MDN](https://developer.mozilla.org/ja/docs/Web/CSS)

- **Can I use**
  - ブラウザサポート確認
  - 機能の互換性チェック

---

# CSS3とはなにか

- CSS2.1以降、各モジュールが機能を追加していく形に変化した
- CSS3とはCSS2.1+追加モジュールの総称

![](./CSSLevel.jpg)

<footerNote>https://techracho.bpsinc.jp/hachi8833/2016_10_03/26581</footerNote>

<!-- https://zenn.dev/helloiamktn/articles/444a937f41238d -->

---

# CSS3と未来

- **モジュール化されたCSS**
  - CSS2.1をベースに拡張
  - 継続的な機能追加

- **将来の展望**
  - Chrome 131以降のAIサポート
  - コンテナクエリ
  - カスケードレイヤー

---

# 参考資料

- [HTMLやCSSのレイアウトの歴史を振り返る #HTML5 - Qiita](https://qiita.com/otome0927@github/items/8428265ae6caf98afb94)
- 


---

# リセットCSS

- ブラウザのデフォルトの挙動を打ち消すCSS
- 環境で挙動を統一するために利用

<footerNote>https://coliss.com/articles/build-websites/operation/css/css-reset-for-modern-browser.html</footerNote>

<!-- 社内で用いられているRIFFのリセットCSSも改善の余地があるかも...? -->
