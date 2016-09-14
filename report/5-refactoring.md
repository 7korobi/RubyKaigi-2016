リファクタリング
=====


Suture
-----



静的解析
-----

rubyプログラムを構文解析して、呼ばれていないメソッド定義を表示する。
開発者が見て使っていないものであれば、消してしまいましょう。

- Dead code
  - Over-engineering
  - poorly written code
  - refactoring, deprecations



参考文献
=====

- gem https://github.com/testdouble/suture
- gem http://docs.seattlerb.org/debride/
- gem https://github.com/amatsuda/traceroute