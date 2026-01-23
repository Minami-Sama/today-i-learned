# Python : ord/chr と Caesar

### ord() と chr()
- `ord()`：文字（1文字）→ コードポイント（数字）
- `chr()`：コードポイント（数字）→ 文字
- `ord("A")` は大文字Aの番号
- `chr(65)` は `"A"`

### 連続している範囲
- `"0"〜"9"` は連続（48〜57）
- `"A"〜"Z"` は連続（65〜90）
- `"a"〜"z"` は連続（97〜122）

### チェーン比較
- `A <= x <= Z` みたいに書ける（`and` を書かなくていい）
- 例：英大文字判定
  - `ord("A") <= ord(c) <= ord("Z")`

### 三項演算子（if/else を1行に）
- `print("Yes" if 条件 else "No")`

### Caesar（アルファベットを k だけ進める）
- `y = (x + k) % 26`　美しいね
- `x+k` がどんなに大きくても、`% 26` で必ず 0〜25 に戻る（循環）

#### 英大文字だけ Caesar、他はそのまま（完成）
```python
s = input()
k = int(input())

ans = []
for ch in s:
    oc = ord(ch)
    if ord("A") <= oc <= ord("Z"):
        x = oc - ord("A")
        y = (x + k) % 26
        ans.append(chr(ord("A") + y))
    elif ord("a") <= oc <= ord("z"):
        x = oc - ord("a")
        y = (x + k) % 26
        ans.append(chr(ord("a") + y))
    else:
        ans.append(ch)

print("".join(ans))
```

### 文字列を list() にする必要があるとき／ないとき
- 文字列はそのまま for ch in s: で1文字ずつ回せる（list化しなくてOK）
- list(s) が便利なのは「特定の位置を書き換えたい」時
- 文字列は immutable（直接 s[0] = "X" ができない）
- 今回は「変換結果を別のリストに集めて join で新しい文字列を作る」方式なので list化不要だった

---

### メモ（それ以外）
- 見たい映画候補：Nightcrawler

TIL: ord/chr, chained comparison, ternary, Caesar shift (%26 loop)  
TIL: strings are iterable; build new string with list+join
