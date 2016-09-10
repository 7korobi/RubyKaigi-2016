```
Web Clients for Ruby and What they should be in the future
Toru Kawamura @tkawa
```

LINKS
=====

- https://sendagayarb.doorkeeper.jp
- http://github.com/tkawa
- https://github.com/lostisland/faraday
- https://github.com/lostisland/faraday_middleware
- https://gist.github.com/mitukiii/2775321
- http://straitwalk.hatenablog.com/entry/2014/05/11/014150
- RFC 5988
- RFC 6570


「Webクライアント」のgemのアイデア
-----

- ✗ 密結合すぎて…
- ✗ 専用的すぎて転用できない…


RubyKaigi2014 HYPERMEDIA
-----

URLの変更で動かなくなる ＝ 密結合のせい
APIの説明をレスポンスに埋め込んでしまうとよい。
WebAPIごとに個別のgemがたくさんある！

- google-api-client
- aws-sdk
- octokit
- twitter
- koala


なぜ？
-----

- Web APIごとのJSONの違い
- 4xxより細かいエラーハンドリング
- APIを１回呼び出すことと、機能を実行することにギャップがある。


どうする？
-----

- 次に呼び出すAPI候補からユーザーに選択させるか、自動選択する。
- （この候補がgemにハードコードされている）
- アプリの状態によって候補が決まる。
  - 今どの画面か
  - どの画面からきたか
  - なにを表示、選択しているか
- 状態をHTTPクライアントが持てば良い。状態管理できるWeb Clientがほしい。


Faraday
-----

- ミドルウェアコンセプトを採用。rackにそっくり。
- HTTPコアをラップするアダプタ。
- url, *_url をリンクとみなして動く。

