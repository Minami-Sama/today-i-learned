# GitHubの基本（ChatGPT5.2に教えてもらった）

## GitHubは何を管理しているか
- Gitは「フォルダ」を管理していない
- 管理しているのは「ファイル」だけ
- そのため、UIには「フォルダを作る」メニューがない
- フォルダは「ファイル名に含まれるパス」として扱われる

フォルダを作る方法：
- `フォルダ名/ファイル名` の形でファイルを作る

例：
2026-01-23/README.md

---

## git add / commit / push の役割

### git add
- 「保存候補」「release候補」に入れるイメージ

### git commit
- addした変更を、履歴として確定する
- 普通の保存ではなく「巻き戻せる保存」

### git push
- commitした履歴をGitHub（クラウド）に送る

---

## git status で分かること
git status は「今どの段階にいるか」を教えてくれる実況画面。

主に以下を確認できる：
- 作業中（まだaddしていない）
- add済み（commitできる状態）
- 変更なし（きれいな状態）
- 新しく作ったけど管理されていないファイル

よく出る表示：
- `working tree clean`：変更なし
- `Changes not staged for commit`：作業中
- `Changes to be committed`：add済み（release候補）
- `untracked files`：新しいファイル

---

## 視聴
- 呪術廻戦 第51話：御所園監督、3Dの使い所がうまい人という認識だったけど、すごいアートぽい絵作りでとがりまくっててめちゃくちゃ良かった！
