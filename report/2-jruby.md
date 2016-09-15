
JRubyに関する紹介
=====

RubyKaigi2016で、JRubyのとっている手法について、Oracleの人からの発表がいくつかありました。


関連文書
-----

- http://rubykaigi.org/2016/presentations/pitr_ch.html
- http://rubykaigi.org/2016/presentations/anildigital.html
- http://rubykaigi.org/2016/presentations/nirvdrum.html
- http://rubykaigi.org/2015/presentations/nirvdrum.html
- https://github.com/jruby/jruby/wiki/Truffle
- http://www.spinute.org/ruby/gsoc2016/japanese.html


Graalプロジェクト
-----

- Graal
  - GraalVM : Javaが使っているLLVM
  - Truffle
    - Ropes

Ropes
-----

Rubyでは、Stringは２つの目的で使われている。

- sequence of characters
- Byte buffer


このうち、Sequence of Characters に異なるアプローチを用意して、改善をはかったもの。
RopesはStringの内部構造にバランス木を採用し、高速化をはかる。
代わりに、長さ検査、IOへの出力速度が落ちる。

- O(1) operation
  - Immutable
  - Tree representation
  - Logical string fragment oriented
  - shares memory by building new trees with existing nodes
- `String#+`, `String#<<` など、40倍〜130倍高速になる。
- `String#bytesize`,`String#size` など、17倍〜100倍低速になる。

