---
title: middleman-blogでブログを開設する
tags: blog, middleman
---

middleman-blogでブログを開設しました  
将来の自分のために備忘録をまとめておきます

READMORE

### 僕の環境

- MacOSX
- `homebrew`インストール済み

### Rubyのインストールのためのrbenv

まずはRubyのインストールから  
MacOSXには初めから古いRubyがあるけど新しいものを使う

今なら`rbenv`を使ってRubyをインストールする  
`rbenv`を使うモチベーションになるわかりやすい利点があったので引用

- [rbenvで複数バージョンのRubyを管理する](http://tech-sketch.jp/2014/04/rbenvで複数バージョンのrubyを管理する.html)

>・新しいバージョンのRubyの機能を試したい  
>・新しいバージョンでアプリケーションの動作確認がしたい  
>・Rubyを古いバージョンに一時的に戻したい  
>・アプリケーションごとに使いたいバージョンが異なる

もう一つ利点を追加するとRubyをインストールするからには`gem`と言われるRubyで作られたパッケージをいくつもインストールしてやりたいことをする。なんてことがとても多くなる。`middleman`もその`gem`の一つ

`gem`は、Rubyのバージョンに強く紐付いてるからRubyのバージョンを上げようと思ったら、インストールしてある`gem`は当然動かなくなる。（Rubyのバージョンは結構すぐ上がる）

`rbenv`を使ってRubyのインストールを行っていれば`gem`をインストールする時も、アクティブになっているRubyのバージョンと同じところに`gem`をインストールするようになる

`rbenv`はRubyのバージョンを切り替えながら、実はこの`gem`も切り替えてる

そういった背景があるので`rbenv`をインストールしてRuby（と`gem`）を管理する

```shell
# homebrewを使ってrbenvをインストール
$ brew updage
$ brew install rbenv ruby-build
$ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
$ source ~/.bash_profile

# rbenvを使ってRubyをインストール
$ rbenv install 2.1.4
$ rbenv global 2.1.4
$ rbenv rehash
```

- [[rbenv]コマンド備忘録 - Qiita](http://qiita.com/a_ishidaaa/items/8cc14453289dba1413dd)

### Bundlerのインストール

Rubyをインストールしたら、同時に`bundler`をインストールする  
`bundler`を使う利点は以下の記事を参照

- [Ruby書くならBundler使え](http://shokai.org/blog/archives/7262)

```shell
$ gem install bundle
```

### middlemanとmiddleman-blogのインストール

まずはBundlerを使わずに、普通にインストールする  
後述するmiddleman-blogのプロジェクトテンプレートを展開するコマンドのために、どうしてもシステムワイドにインストールが必要なんだよね。このへんややこしい  
Bundler管理下のmiddlemanと、システムワイドの（普通に`gem install middleman`とインストールした）middlemanを混同しないようにする

```shell
$ gem install middleman
$ gem install middleman-blog
```

### プロジェクトテンプレートを利用して作業を開始する

Middlemanには色々なテンプレートが用意されていて、テンプレートを元にひな形をポコっと作って作業を開始することが出来る  
`middleman-blog`もその一つ

```shell
$ middleman init BLOG_DIR_NAME --template=blog --skip-bundle
```

`BLOG_DIR_NAME`を指定しないと、カレントディレクトリに色んなファイルやディレクトリが展開されてしまう。作業ディレクトリを掘ってからその中で実行するか、上記のように作業ディレクトリ名を指定して実行しないとひどいことになる（なった）

`--template=blog`と指定してるのがプロジェクトテンプレート名にあたる  
今回はブログを開始するので`blog`を指定

※ちなみにMiddlemmanはブログ以外にも様々な目的で使用されていて、そのためのプロジェクトテンプレートもいくつか用意されてる

- [Middleman Directory](http://directory.middlemanapp.com/#/templates/all)

`--skip-bundle`は、プロジェクトテンプレートの展開と同時にMiddlemanが勝手に`bundle install`を実行してしまうのを防ぐため。これは好みの問題なので、正直どちらでも良い


さて、プロジェクトテンプレートが展開されたので中に入って見てみる

```shell
$ cd blog-dir-name
$ tree
.
├── Gemfile
├── config.rb
└── source
    ├── 2012-01-01-example-article.html.markdown
    ├── calendar.html.erb
    ├── feed.xml.builder
    ├── images
    ├── index.html.erb
    ├── javascripts
    ├── layout.erb
    ├── stylesheets
    └── tag.html.erb

4 directories, 8 files
```

**Gemfile**  
使用したい`gem`を記載するところ  
変更したら`bundle update`を実行する  
Gemfileの書き方は色々あって、すごく良くまとまってる記事があるのでこれを参考にすると良いと思う

- [Gemfileについて調べてみた - xxxcaqui.log](http://xxxcaqui.hatenablog.com/entry/2013/02/11/013421)

**config.rb**  
グローバル設定的なところ  
middleman関連の`gem`は全部ここに設定を書き込んでおくと参照してくれるようになる  
設定を書くところだけど、普通にRubyのファイルなのでここでゴニョゴニョと変数を作っておけばテンプレートからも使用できる変数になる  
ブログ関連の設定は公式サイトを参考にすると良いと思う

- [Middleman: ブログ機能](https://middlemanapp.com/jp/basics/blogging/)

**source**  
ここには見慣れた見慣れたファイルが入ってるのでこの辺を編集していくことになる
軌道に乗ってしまえば後はここの中の作業が中心になるはず

**.erb**  
この拡張子はテンプレートエンジンのもので、Rails界隈で見られる  
ビルドすると`.erb`を取ったファイルに展開される  
書き方（というか読み方も）はRailsのドキュメントがわかりやすかった  
今なら[Slim](http://slim-lang.com/)とか[haml](http://haml.info/)とかの方が流行ってるので書きなおしても良いかもしれない

- [ビュー(view) - Railsドキュメント](http://railsdoc.com/view)


とりあえずは何も変更せず、素の状態を見れるようにするために`bundle install`を行って、作業用サーバを立ち上げる

```shell
$ bundle install --path=bundle
$ bundle exec middleman server
```

Bundler管理下に置かれたmiddlemanを実行したいので`bundle exec`をコマンドの先頭に追加してある  

そうすると`http://localhost:4567/`に<s>ものすっごい殺風景な</s>シンプルなサイトが立ち上がる  
あとは煮るなり焼くなりすればいい
