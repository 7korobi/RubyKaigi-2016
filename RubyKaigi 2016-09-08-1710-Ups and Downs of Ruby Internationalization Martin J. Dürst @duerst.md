
```
Ups and Downs of Ruby Internationalization
Martin J. Dürst @duerst
```

LINKS
=======

- http://ref.xaio.jp/ruby/classes/string/casecmp
- https://en.wikipedia.org/wiki/Latin_script_in_Unicode
- http://www.sw.it.aoyama.ac.jp/2016/pub/RubyKaigi/
- http://unicode.org/Public/UCD/latest/ucd/CaseFolding.txt


ラテン拡張、ウムラウト、合字に対する文字列変換メソッドのあるべき挙動。
（と、実装の難しさ）

SHIFT_JIS, EUC-JP, GB2312, EUC-KR, Big-5, EUC-TW
- 日本人からもう不要と言われた。

全UNICODEでテスト。413テスト、221万アサーション。

