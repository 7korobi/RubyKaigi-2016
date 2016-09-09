
```
Unifying Fixnum and Bignum into Integer
Tanaka Akira @tanaka_akr
```

LINKS
=======

- http://togetter.com/li/1022003
- http://www.a-k-r.org/d/2016-09.html#a2016_09_08_1


Ruby2.4

- `Fixnum`  obsolete
- `Bignum`  obsolete
- `Integer == 1.class`
- `Integer == (2**100).class`


C拡張ライブラリのビルドは通らなくなるものあり、書き換えが必要。


Fixnum range

- 32bit CRuby (ILP32) `-2**30 .. 2**30 - 1`
- 64bit CRuby (LLP64) `-2**30 .. 2**30 - 1` ※windows
- 64bit CRuby (LP64)  `-2**62 .. 2**62 - 1`
- JRuby               `-2**63 .. 2**63 - 1`


Ruby specification

- ISO/IEC 30170:2012
- JIS X 3017:2011
- Fixnum, Bignum は、規格上許されるが、必須ではない。


Fixnum, Bignum は Lisp specification には明記してある。


ドキュメントがシンプルになる

- Fixnum#foo、Bignum#foo の2重のドキュメントがひとつになる。

