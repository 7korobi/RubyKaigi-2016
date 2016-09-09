
```
How to create bindings 2016
Kouhei Sutou @ktou
```

LINKS
=======

- https://github.com/kou/rabbit-slide-kou-rubykaigi-2016
- https://oss-gate.doorkeeper.jp/


C ext.
自動生成された binding がいかに強力か。

今は安全なバージョンのTypedData_Wrap_Structがあるから、拡張ライブラリを書くときはData_Wrap_Structは避けるのじゃよ #rubykaigiA

SWIGが生成してくれるやつはAPIとしては不十分だから、結局低水準操作はお任せできるという程度の意味で、高水準の対象言語らしいAPIでラップしてやる必要があることが多い気がする #rubykaigiA

### binding の作り方

- `Ext` Extension library (inpl by hand)
- `SWIG` (inpl by Generate)
- `FFI` (**inpl by hand on ruby**)
- `GI` GObject Introspection (inpl by Generate)


### GIのつかいかた

``` ruby
require "gi"

WebKit = GI.load("WebKit2")
w = Gtk::Window.new
w.show
w.keep_above = true
w.set_size_request 400, 300
w << web_view = WebKit::WebView.new
web_view.show
web_view.load_uri "http://rubykaigi.org"


# スクリーンショットをとってみる

w2 << s = Gtk::ScrollWindow.new
s  << image = Gtk::Image.new
w2.show_all
w2.keep_above = true
w2.set_size_request 500, 500

webview.get_snapshot :full_document, :none do |_, result|
  image.surface = web_view.get_snapshot_finish result
end
```

- GI は実行時に binding を生成する。→ バージョンアップ時にリビルド不要
- 全言語バインディング用にアノテーションを１つメンテナンス。
