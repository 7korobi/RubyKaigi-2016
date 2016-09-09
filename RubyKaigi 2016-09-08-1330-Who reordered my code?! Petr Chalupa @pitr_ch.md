
```
Who reordered my code?!
Petr Chalupa @pitr_ch
```

LINKS
=======

- http://togetter.com/li/1021946
- https://github.com/jruby/jruby/wiki/Truffle


Jruby & truffle

一方だけがクリティカルセクションを走るような２つのスレッド。

### Performance

並列性。

When We can see it?

- Method body is stable
- Constant's value is stable
- Type speculation


Truffle - self optimizin AST interpreter
GraalVM - 


Atomic operation - attr_atomic


MRI 比較で、Jruby かなりはやい（x5くらい）

https://ja.wikipedia.org/wiki/%E3%83%87%E3%83%83%E3%82%AB%E3%83%BC%E3%81%AE%E3%82%A2%E3%83%AB%E3%82%B4%E3%83%AA%E3%82%BA%E3%83%A0

デッカーのアルゴリズムとかメモリモデルとか，その手の話を聞いたんだけど，わりと一般的っぽい話なので Ruby を題材に解説してるなぁぐらいの印象しか持てな... と思ったら最後ようやく JRuby + Truffle でパフォーマンスが上がった話になった感

Ruby3にはactorやchannelといったconcurrency libraryが提案されているが、どれも高級な仕組み。高速なconcurrent data structureを作るときや、別の抽象化方法を考えるのに課題。

https://github.com/ruby-concurrency/concurrent-ruby

