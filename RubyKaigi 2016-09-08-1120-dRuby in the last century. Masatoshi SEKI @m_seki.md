
```
dRuby in the last century.
Masatoshi SEKI @m_seki
```

LINKS
=======

- https://speakerdeck.com/m_seki/druby2016
- http://docs.ruby-lang.org/ja/2.2.0/library/drb.html


### dRubyの生い立ち

1999年 最初のコードはTシャツに書けるサイズ。
2000年 perl/rubyカンファレンスで、同じ会場で同じ発表をした。


Before dRuby 8years
BD8 Unixを使った組み込み。小さなデーモンの組み合わせ。
BD5 CGIの単純な世界。
BD1 Ruby & shttpsrvに出会う。HTTPをプロセスに埋め込む。

Rubyの世界とWebの世界の翻訳ばかりやっていて、嫌になってきた。
メソッドコールというより、関数呼び出しのような感じになっていた。


RubyなのだからRuby Objectをあつかいたい。
- RPCでなくRMI
- Rubyのメソッド呼び出しをSocketで拡張しよう。
- 簡単通信ライブラリではなく、もっと情緒的なもの。


20世紀には、IDLを定義する言語が多かった。
サーバーとクライアントの立場が入れ替わります。
```
 kvs['outlet'] = $stdout
 $stdout
```

オブジェクトを公開する。ので、$stdoutのメソッドをコールできる。

- dump可能 複製
- dump不能 Proxy


```
Marshal.dump
- kvs['outlet'] = $stdout
- = kvs.send(:[], 'outlet', $stdout)  # 'outlet' 複製
$stdout  Proxy
```

Queue, Mutex, Monitor, Thread同期メカニズムがそのまま使える。

dRubyが向いていること
- 寿命が違う情報を扱う。
- 待ち合わせをデザインすることが多い。
- (coffeeなどで非同期になれたうえで使うと、結構いいと思う。)
- ex. prototyping Twitter. ( dRuby/Rinda だった。)


#### これから

- 初期の実装に戻したいところがいくつか
-- ACL, insecure_method
-- 危ないものは危なく見えるべき。
- 啓蒙する。
-- まずおもしろがってもらう。
-- 並行処理の勘所に気づいてもらう

