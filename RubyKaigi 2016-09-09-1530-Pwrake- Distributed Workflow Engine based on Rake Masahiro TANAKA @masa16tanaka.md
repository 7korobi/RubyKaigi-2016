```
Pwrake: Distributed Workflow Engine based on Rake
Masahiro TANAKA @masa16tanaka
```

LINKS
=====

- http://www.hpcs.cs.tsukuba.ac.jp/~tanaka/publications/open/HPC-135-14.pdf
- https://github.com/ruby-numo
- https://github.com/masa16
- http://docs.ruby-lang.org/ja/2.3.0/library/rake.html
- http://montage.ipac.caltech.edu/
- http://oss-tsukuba.org/software/gfarm
- http://www.hpci-office.jp/
- http://sc-web.nict.go.jp/
- http://himawari8.nict.go.jp/

String#pathmap


Workflow Definition Language

- DAX
- Wsift (not Apple)
- GXP Make

- Rake is powerful as WDL


Pwrake 並列rake
-----

[bartender](https://github.com/seki/bartender) と違い、I/Oと1対１にはしない。


- NFS (ストレージがボトルネック)
- 他 (ネットワークがボトルネック)
- Gfarm (スケールしやすい)


