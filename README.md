# pgf – A Portable Graphic Format for TeX

![Test suite](https://github.com/pgf-tikz/pgf/actions/workflows/check.yml/badge.svg?branch=master)

PGF はグラフィックを生成するための TeX マクロパッケージです。  
プラットフォームやフォーマットに依存せず、`pdftex` や `dvips` を含む最も重要な TeX バックエンドドライバと一緒に動作します。  
また Ti*k*Z と呼ばれるユーザーフレンドリーなシンタックスレイヤーが付属しています。  

より多くの情報を得るには `doc/generic/pgf` を参照して下さい。  
マニュアルは `doc/generic/pgf/pgfmanual.pdf` (https://pgf-tikz.github.io/pgf/pgfmanual.pdf も利用できます) を参照して下さい。  
このマニュアルはインストール方法についても説明しています。  
ライセンスの詳細については `doc/generic/pgf/license/LICENSE` を参照して下さい。  

バグレポートや新しい機能のリクエストは、[公式リポジトリ](https://github.com/pgf-tikz/pgf)または[公式メーリングリスト](https://github.com/pgf-tikz/pgf)にアクセスしてください。  

Matrix network [#pgf-tikz:matrix.org](https://matrix.to/#/#pgf-tikz:matrix.org) ([read-only version](https://view.matrix.org/room/!NuxCISwYQJuyWwNsEI:matrix.org/)) でもチャットを行っています。  

## インストール方法
一般的には、お使いの TeX ディストリビューションに同梱されているバージョンの PGF をお使いください。  
パッケージのインストール方法については、各ディストリビューションのドキュメントを参照してください。  

もし興味があれば、私たちの tlcontrib リポジトリから TeX Live の最新開発版をインストールすることができます。  
```console
$ tlmgr repository add http://pgf-tikz.github.io/pgf/tlnet pgf-development
$ tlmgr pinning add pgf-development "*"
$ tlmgr update --self --all
$ tlmgr install pgf --reinstall
```

## 開発
現在のところ、PGF にはリグレッションをチェックするための非常に初歩的なテストスイートしかありませんので、今のところ、コミットごとにマニュアルをビルドすることでバグをチェックしています。  
ローカルにマニュアルを構築するには、PGFリポジトリを texmf ツリーにコピーするか（非推奨）、 TeX Live の usertree オプションを使用します。  
GNU/Linux で usertree オプションを使用する場合は、以下の手順に従ってください：
```console
$ git clone https://github.com/pgf-tikz/pgf
$ tlmgr init-usertree --usertree pgf
$ export TEXMFHOME=$(readlink -f pgf)
$ cd pgf
$ l3build doc -q -H
```
上の例で示したように、少なくとも LuaTeX 用のバージョンをビルドすることをお勧めします。  
アニメーション機能をテストするには、 dvisvgm 用のバージョンをビルドする必要があります。  
