```
SciRuby Machine Learning Current Status and Future
Kenta Murata @mrkn
```


LINKS
=====

- http://togetter.com/li/1022377
- https://sciruby-slack.herokuapp.com/
- http://www.s-itoc.jp/activity/research/ml/60
- https://github.com/SciRuby/iruby
- https://github.com/mrkn/enumerable-statistics
- https://github.com/mrkn/num_buffer
- https://github.com/kei500/liblinear-ruby
- https://github.com/febeling/rb-libsvm
- 他にも...
  - gem decisiontree
  - gem ai4r
  - gem classifier-reborn
  - gem data_mining
- https://github.com/domitry/nyaplot
- https://github.com/scikit-learn/scikit-learn
- https://speakerdeck.com/smly/python-todetafen-xi-kontesutofalseshi-jian
- https://github.com/zeromq/rbzmq
- http://qiita.com/chezou/items/d090f26dcb31818d6964

機械学習
-----

データサイエンスの仕事は7工程
- データ集め
- 探索的データ解析
- データをキレイにする
- 複数データソースを合体
- 前処理
- 機械モデル作成
- 世界に適用

python は全部できるが、ruby は全部できない。

データに基づいて、ビジネス上の意思決定をしたい。
異常検出
感情分析

教師なし学習
教師あり学習
強化学習


Scikit-learn (python)
-----

Scipy stack のうえで動く。デファクト・スタンダード。

この例えが良いかは分からないけど、Rubyの単体のgemとsklearnは、素のSinatraとRailsくらい違ってかなり便利なヘルパーがいっぱいいるんですよね。複数のアルゴリズムを容易に比較できたり、前処理からパイプラインでひとまとめにできたり #rubykaigiA

JuliaはPython,Matlab,R,C++を同じREPLで言語またいでやり取りできるからなぁ。こういうbindingは好きなんですよね #rubykaigiA


The Future of SciRuby in ML
-----

NumBuffer need more contributer
Numo::NArray ライブラリがたりない
NMatrix がもっと高速でないと。
sparse matrices に対して四則演算しかできない。
NMatrix と NArray に互換性がない。


