# TIL: Twine(Harlowe)でVNのUI調整（GitHub Pagesで実機確認）

- GitHub PagesでTwine作品をホストして、Pixel 10で実機表示できた。
- Harloweのマクロ周りで詰まり：`(add-class:)` は無い／`em`指定が通らないのでCSS寄せに。
- Passage名の `_TODO` が temp variable 扱いでエラー → `A_01` / `B_01` に変更して解決。
- Startだけ中央寄せ・他は左寄せ、字幕風の固定UI（bg＋ビネット＋下暗帯＋グレイン）を作成。
- ただし「中央が右にズレる」「早すぎる改行」が残課題で、デフォCSS/レイアウトを切り分け予定。
