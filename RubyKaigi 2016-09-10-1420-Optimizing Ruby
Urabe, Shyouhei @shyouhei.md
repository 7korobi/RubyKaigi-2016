```
Optimizing Ruby
Urabe, Shyouhei @shyouhei
```

LINKS
=====

- spoiler
- http://benchmarksgame.alioth.debian.org/
- https://github.com/ruby/ruby/pull/1419

SPOILER
-----


Ruby is SLOW
-----

- GC?
- GVL?
- Dynamic?

no.
not optimized!


redefinition rarely happens
-----

邪悪なことをしなければ、１＋２は３。

- 400+ times faster.
- JITは今回は手を入れない。
- VMシーケンスを最適に変更するアプローチ
- On the Fly


deoptimization
-----

- ruby 2.4
- redefine などで、前提が崩れたら破棄できる機構
- 再定義がおこったときにカウントアップしていく（とても軽い）
  - プログラム・カウンタを変更しない処理内容
    - VM stack のスキャンが不要。


最適化手法
-----

- Folding constants
- 最適化可能なメソッドを `pure` とよぶ
  - ローカル変数以外を使うものは `not pure`
  - yield を使うものは `not pure`
  - C関数を呼ぶものは `not pure`
- Eliminating send-ish instructions
  - 戻り値を捨てているメソッドは最適化可能
- Elimination of variable
  - 一度も参照されていない変数代入は最適化可能
  - pure メソッドのみを対象にする（binding hackを警戒）


ベンチマーク
-----

- eval    8% 遅くなった。
- block  30% 遅くなった
- bigarray 1000倍速くなった


今後のこと
-----

- 共通部分の削減
- 変数の生存解析
- and more.



