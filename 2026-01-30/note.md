# TIL: Twine (Harlowe 3.3.9) Start画面のボタンが左寄りになる問題をCSSで確実に中央寄せする

## 症状

* Start画面でリンク（ボタン）を `text-align:center` したのに、**ボタンが左寄り**に見える
* 文字は中央っぽいのに、**ボタンの外枠（クリック領域）が中央に来ない**

## 原因（だいたいこれ）

* `text-align:center` は **「中身（インライン）」の整列**に効くが、
  ボタン（`tw-link`）自体が **ブロックとして左に配置**されていると外枠は中央に来ない
* Harlowe側のレイアウト（親要素の padding/width など）で、`margin:auto` が効きにくい/ズレるケースがある

## 解決方針

* **Startタグが付いたパッセージだけ**に限定して、

  * 親（`tw-passage`）の左右ズレ要因を抑え
  * 子（`tw-link`）を **display:block + width指定 + margin:auto** で “外枠ごと”中央固定する

## コピペ用CSS（CSSの一番下に追加）

```css
/* ===== Start: ボタンを「外枠ごと」確実に中央に固定 ===== */
tw-passage[tags~="start"]{
  /* 親側のズレ要因を潰す */
  padding-left: 0 !important;
  padding-right: 0 !important;
  margin-left: auto !important;
  margin-right: auto !important;

  /* “中の要素”の中央寄せも担保 */
  text-align: center;
}

/* ボタン本体（tw-link）を中央に固定 */
tw-passage[tags~="start"] tw-link,
tw-passage[tags~="start"] tw-link.visited{
  display: block;

  /* 幅を決めて margin:auto で中央 */
  width: min(34rem, 88vw);
  margin-left: auto !important;
  margin-right: auto !important;

  /* レイアウト計算のズレを減らす */
  box-sizing: border-box;

  /* 中の文字も中央 */
  text-align: center;

  /* もし以前の transform が残ってたら無効化 */
  transform: none;
}
/* ===== /Start ===== */
```

## 使い方（手順）

1. Startパッセージに **tag: `start`** を付ける
2. 上のCSSを **Stylesheet の一番下**に貼る
3. スマホ/PCで表示確認（ボタンの外枠が真ん中に来る）

## メモ

* 今回は「最終兵器」系の追加調整は不要だった（このセットだけで解決）
* Startだけに効かせるのが安全（本文パッセージのレイアウトに影響しにくい）
