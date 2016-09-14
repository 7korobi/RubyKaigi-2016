
JRubyに関する紹介
=====

Oracleの人の発表がいくつかありました。
JRuby界隈では、どのように並列性を実現したのか。



GraalVM
-----




Truffle Ropes
-----

Rubyでは、Stringは２つの目的で使われている。
このうち、Sequence of Characters のほうを改善する機能。

- sequence of characters
- Byte buffer


- O(1) operation
  - Immutable
  - Tree representation
  - Logical string fragment oriented
  - shares memory by building new trees with existing nodes
- `String#+`, `String#<<` など、40倍〜130倍高速になる。
- `String#bytesize`,`String#size` など、17倍〜100倍低速になる。



参考文献
=====

- https://github.com/jruby/jruby/wiki/Truffle
- http://www.spinute.org/ruby/gsoc2016/japanese.html

