Ruby コア機能の今後
=====

RubyKaigi2016 で発表のあった、Rubyの現状と将来のバージョンへの展望をまとめます。


関連文書
-----

- http://rubykaigi.org/2016/presentations/yukihiro_matz.html
  - http://memo.goodpatch.co/2016/09/rubykaigi-2016-report-ruby3-typing/ 
- http://rubykaigi.org/2016/presentations/tanaka_akr.html
- http://rubykaigi.org/2016/presentations/duerst.html
- http://rubykaigi.org/2016/presentations/ko1.html


Ruby 2.3 (現状)
=====

- `String#upcase`,`String#downcase`,`String#casecmp`,`String#capitalize` の取り扱い対象は、ASCII文字である
- 動的再定義が可能な言語なので、最適化処理は行わない。
- 整数は、値の範囲によって Fixnum, Bignum にわかれている。

| version             | Fixnum 範囲                      | Bignum 範囲 |
|:------------------- |:-------------------------------- | ----------- |
| 32bit CRuby (ILP32) | `-2**30 .. 2**30 - 1`            | それ以外 |
| 64bit CRuby (LLP64) | `-2**30 .. 2**30 - 1`  ※windows  | それ以外 |
| 64bit CRuby (LP64)  | `-2**62 .. 2**62 - 1`            | それ以外 |
| JRuby               | `-2**63 .. 2**63 - 1`            | それ以外 |



Ruby 2.4 (next)
=====

- ラテン拡張や合字(ligature)を含む文字列について、`String#upcase`,`String#downcase`,`String#casecmp` での処理に対応
- Deoptimization
  - 事前最適化をおこない、最適化の前提が崩れたら破棄する。
  - 巨大なArrayの取り扱いで1000倍速くなるなど、一部の動作に大きな効果がある。
- Integer <== Fixnum + Bignum
  - object.is_a?(Fixnum) などといった型チェックはできなくなる。
  - JRuby, 32bit CRuby, 64bit CRuby などでstringの範囲が処理系依存のため。


ラテン拡張への文字列処理
-----

```
'Résumé ĭñŧėřŋãţĳňőńæłĩżàťïōņ'.upcase # ⇒ 'RÉSUMÉ ĬÑŦĖŘŊÃŢĲŇŐŃÆŁĨŻÀŤÏŌŅ'
'Юрий Соколов'.upcase                 # ⇒ 'ЮРИЙ СОКОЛОВ'
'ß'.upcase                            # ⇒ 'SS' (German sz/sharp s)
'ﬃ'.upcase                           # ⇒ "FFI" (ﬃ ligature)
```

deoptimization 最適化手法
-----

ここでは、最適化可能な式を `pure` とよぶ。
pureの定義を外れた式は、最適化（による実行のスキップ）を伴ってしまうと動作がおかしくなってしまう。

- `pure` の検査方法
  - ローカル変数以外を使うものは `not pure`
  - yield を使うものは `not pure`
  - C関数を呼ぶものは `not pure`

- 最適化方法
  - Folding constants
  - Eliminating send-ish instructions
    - 戻り値を捨てているメソッドは最適化可能
  - Elimination of variable
    - 一度も参照されていない変数代入は最適化可能
    - pure メソッドのみを対象にする（binding hackを警戒）



Ruby 3 (future)
=====

３つの目標を、東京オリンピックまでには実現できるといいなあ。

- Ruby 3x3 (Ruby 3 は ３倍速い)
  - deoptimization の継続的改善
    - 変数の生存解析、共通部分削減など

- concurrency (並列実行性)
  - 安全/簡単 なアプローチをとりたい。
  - Guild が、メモリの共有を安全な範囲に限る。

- 動的型の欠点（後述）に対策をつける
  - DRY,Duck typing を前提に、型推論できる範囲にはサポートをしたい。


Ruby3 Guild モデルについて
-----

ロック手続きがなくとも安全であるメモリアクセスだけを可能にする、メモリコピーの手法です。

- `Guild`は1つ以上の`Thread`を持つ（`Thread`は`Guild`に所属する）
- `Thread`は1つ以上の`Fiber`を持つ（`Fiber`は`Thread`に所属する）
- `Guild`の異なる`Thread`は、並列動作させてよい。
- つまり、排他処理をしたい`Thread`同士は、同一の`Guild`に属すべき
- 変化するオブジェクトは、`Guild`の外からのアクセスができない。
- `Guild::Channel`で`Guild`間のオブジェクトやり取りを行う。
  - 複製：他の`Guild`にオブジェクトをdeep-copyする。
  - 移動：他の`Guild`にオブジェクトをtransferし、元の`Guild`からアクセスできなくする。
- 変化しない(immutable)オブジェクトは、すべての`Guild`が共有アクセスしてよい。
  - Numeric
  - Symbol
  - true
  - false
  - nil
  - 上記immutableオブジェクトのみを保有し、`.freeze`済みのArray



