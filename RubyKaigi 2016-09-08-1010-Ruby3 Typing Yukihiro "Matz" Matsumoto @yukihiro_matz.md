
```
Ruby3 Typing
Yukihiro "Matz" Matsumoto @yukihiro_matz
```

LINKS
=======

- http://togetter.com/li/1021897
- http://memo.goodpatch.co/2016/09/rubykaigi-2016-report-ruby3-typing/


静的型、動的型の振り子のような関係。
Future of (Dynamic) Typing?


### 脳の負担を下げたい。

型に期待するもの
- 血液型 A,B,AB,O - 共通の性質

Class is not Type!
(Duck Typing. ex. StringIO)

"Duck" is not a (nominal) type.
"Duck" is not a class.
"Duck" is an expected behavior.

Go interface is far better.
-  Structural subtyping.

☓
- documentation
- coverage
- エラーの発見が遅くなる


### どうするとよいのか。(concept)

ふるまいによって、型を推論する。
- 80%でも0%よりよい。
- メソッドの集合
- 型名をプログラマが与えない。どうやって名前をつける？

ad-hoc expection.
- a is expected to have methods gsub, slice, map.
- no class has them all.
- it should be an error.

run-time type information.
- collect type data at run-time.
- especially from test.
- build type database for the Gem.


東京オリンピックまでにはRuby3があるといいなあ。
- Soft typing
- Ruby 3x3
- Concurrency


To keep moving forward
Happy Hacking!


型推論の実現性
- 伝統的な型推論は不変を前提にしているので、ダメ。

IDEの使用を前提にする方法
- 決定版IDEが今はまだないので、まだ決断しづらい。
- IDEありきの言語仕様は興味深いが、rubyの歴史があるのでそうはならないように感じる。

Rubyとのかかわり
- 言語デザイナーとしてかかわる。

Soft Typingと意味がずれてきているので、新しい用語が必要ですね



