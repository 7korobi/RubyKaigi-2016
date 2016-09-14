Ruby コア機能の今後
=====


Ruby 2.3 (現状)
=====


Ruby 2.4 (next)
=====

- ラテン拡張や合字の文字列について、`.upcase`, `.downcase` などの処理に対応
- Deoptimization
  - 事前最適化をおこない、最適化の前提が崩れたら破棄する。
  - 巨大なArrayの取り扱いで1000倍速くなるなど、一部の動作に大きな効果がある。
- Integer <== Fixnum + Bignum
  - object.is_a?(Fixnum) などといった型チェックはできなくなる。
  - JRuby, 32bit CRuby, 64bit CRuby などでstringの範囲が処理系依存のため。
  - http://www.a-k-r.org/pub/2016-09-08-rubykaigi-unified-integer.pdf


deoptimization 最適化手法
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



Ruby 3 (future)
=====

３つの目標を、東京オリンピックまでには実現できるといいなあ。

- Ruby 3x3 (Ruby 3 は ３倍速い)
  - deoptimization の継続的改善
    - 変数の生存解析、共通部分削減など

- concurrency (並列実行性)
  - 安全/簡単 なアプローチをとりたい。
  - Guild が、メモリの共有を安全な範囲に限る。
  - http://www.atdot.net/~ko1/activities/2016_rubykaigi.pdf

- 動的型の欠点（後述）に対策をつける
  - DRY,Duck typing を前提に、型推論できる範囲にはサポートをしたい。



参考文献
=====


☓動的型の欠点☓
-----

- ドキュメント性が低い（プログラマが型を書かないので）
- カバレッジ
- エラーの発見が遅くなる



2016年の主要な言語
-----

- TypeScript (MS)
- Flow (FB)
- Go (Google)
- Swift (Apple)



関連する発表
-----

> Ruby3 Typing
> Yukihiro "Matz" Matsumoto @yukihiro_matz


LINKS
-----

- http://rubykaigi.org/2016/schedule/
- http://togetter.com/li/1021897
- http://memo.goodpatch.co/2016/09/rubykaigi-2016-report-ruby3-typing/

s