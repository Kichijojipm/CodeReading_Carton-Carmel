# Kichijojipm-mini 005 Carton/Carmelコードリーディングのレジュメ

* 日時: 2015/5/20 19:30-22:00
* 場所: コワーキングスペース「ぴこす」

## Crtonとは？

Bundler or pip freeze for Perl

[`https://github.com/perl-carton/carton`](https://github.com/perl-carton/carton)

Cartonとは，アプリケーションにおけるPerlモジュールの依存関係を管理するコマンドラインツールです。

### メリット

### Cartonのインストール

    $ cpanm Carton

### 基本的な使い方

    $ cd webapp
    $ cat cpanfile
    requires 'Amon2', '6.11'
    
    $ carton install
    ......
    Successfully installed Amon2-6.11
    50 distributions installed
    Complete! Modules were installed into /Users/xxxx/webapp/local
    $ cat cpanfile.snapshot
    # carton snapshot format: version 1.0
    DISTRIBUTIONS
      Amon2-6.11
        pathname: T/TO/TOKUHIROM/Amon2-6.11.tar.gz
        provides:
          Amon2 6.11
          ....

    $ git add cpanfile cpanfile.snapshot
    # 他の環境へリポジトリを展開
    $ carton install
    $ ls local/
    bin   cache lib
    $ carton exec amon2-setup.pl
    Usage:
    ....
    
### Cartonの仕組み

### 今日特に読んでみたいモジュール

## Carmelとは？

[`https://github.com/miyagawa/Carmel`](https://github.com/miyagawa/Carmel)

CPAN Artifact Repository Manager

### Carmelのインストール

まだdevelリリースなので`--dev`が必要

    $ cpanm Carmel --dev

もしくはフルパスで指定。

    $ cpanm https://cpan.metacpan.org/authors/id/M/MI/MIYAGAWA/Carmel-v0.1.22-TRIAL.tar.gz
    --> Working on https://cpan.metacpan.org/authors/id/M/MI/MIYAGAWA/Carmel-v0.1.22-TRIAL.tar.gz

### 基本的な使い方

    $ carmel install Plack@1.0033
    $ mkdir demo
    $ cd demo
    $ echo "requires 'Plack', '== 1.0033';" > cpanfile
    $ carmel install
    $ echo 'use Carmel::Setup;use Plack;print $Plack::VERSION."\n";' > demo.pl
    $ perl demo.pl
    1.0033
