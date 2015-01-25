---
title: NGUIの公式情報探し方
tags: unity, ngui
---

NGUIの使い方を覚えるにあたってググってみると、導入用のやさしい内容は半年や1年前にアップされた記事が引っかかり、最新版でも通用する解説なのかどうかわからず困ってしまったので、公式の最新情報をどうやって仕入れるかメモっておこうと思います。

READMORE

### NGUIとは

![NGUIロゴ](2015-01-25-ngui-intro/ngui.jpg)

UnityのUIを実装するためのアセットです  
Unity標準機能のuGUIもありますが、NGUIの方が歴史が長いですし、開発も精力的です  
有料です

### 公式情報

NGUIをImport後 **メニュー＞NGUI＞Help** を選択するとヘルプページが開きます  
まずはこのページにあるTutorialを見ながら、Unityを開き、解説されてることを手を動かして確認するだけで、随分分かった気になってくるのでオススメです  
英語の音声で解説されていて、半分ぐらい何を言ってるか理解できなかったのですが、ぶっちゃけ操作をそのままトレースすれば動画と同じ結果が得られるのでそこまで心配することもないと思います

- [Overview](http://www.tasharen.com/forum/index.php?topic=6754)


#### NGUI3.6.0 Tutorial 1: The Environment

NGUIで開発するにあたっての画面構成や環境設定を確認する動画

<div class="youtube">
<iframe width="560" height="315" src="//www.youtube.com/embed/dM44h752LyA" frameborder="0" allowfullscreen></iframe>
</div>

#### NGUI3.6.0 Tutorial 2: The Basics

- 古いバージョンからアップデートする方法
- SpriteやLabelの作り方
- Depthの動作
- アンカーの使い方
- UIコントロールの作り方
- 右クリックメニューについての解説

<div class="youtube">
<iframe width="560" height="315" src="//www.youtube.com/embed/aWZaq1eLqyE" frameborder="0" allowfullscreen></iframe>
</div>


#### NGUI3.6.0 Tutorial 3: Interaction

- ボタンの作り方
- ボタンにカーソルを重ねたり、クリックした時の挙動の制御方法
- Spriteの大きさを変えたり、変化のスピードをコントロールする方法
- Spriteをフェードアウトする方法
- キーボードの入力を受け取って操作

<div class="youtube">
<iframe width="560" height="315" src="//www.youtube.com/embed/jDxWG81sNPc" frameborder="0" allowfullscreen></iframe>
</div>

#### NGUI3.6.0 Tutorial 4

- スクロールするビューを作る方法
- スクロールビューの中にドラッグできるボタンを作る方法
- スクロールビューを複数作って、中身をドラッグで交換できるようにする方法
- スクロールバーと連携させる方法
- Example 11というシーンファイルの概要説明

<div class="youtube">
<iframe width="560" height="315" src="//www.youtube.com/embed/UK3aMHRfgcw" frameborder="0" allowfullscreen></iframe>
</div>

#### NGUI3.6.0 Tutorial 5

- アンカーについての詳しい説明
- UIRootの設定についての説明
- ローカライズのやり方
- Atlas Maker toolの使い方
- テクスチャーについての説明
- atlasにspriteを追加する方法
- フォントの扱い方の説明
- atlasからspriteを消す方法
- スクリプト（C#のコードでした）について

<div class="youtube">
<iframe width="560" height="315" src="//www.youtube.com/embed/GIpccFRIXmo" frameborder="0" allowfullscreen></iframe>
</div>


[Overview](http://www.tasharen.com/forum/index.php?topic=6754)のページにはもっとたくさんYouTubeへのリンクが貼られてるので、たくさん見たい人はリンクへ飛んでください


### 右クリックメニュー＞Help

上記の動画を見ると分かりますが、spriteやtableをSceneビューで右クリックすると **Help** という項目があります。これを選択すると個別に解説しているページに飛ぶことが出来ます  
Inspectorビュー上で名前のところを右クリックしても同様に **Help** を選択できます

いくつかURLを列挙してみました(もっとあります)

* [UISprite](http://www.tasharen.com/forum/index.php?topic=6704)
* [UIScrollView](http://www.tasharen.com/forum/index.php?topic=6763)
* [UITexture](http://www.tasharen.com/forum/index.php?topic=6703)
* [UIPanel](http://www.tasharen.com/forum/index.php?topic=6705)
* [UIGrid](http://www.tasharen.com/forum/index.php?topic=6756)
* [UITable](http://www.tasharen.com/forum/index.php?topic=6758)
* [UIWidget](http://www.tasharen.com/forum/index.php?topic=6702)
* [UIButton](http://www.tasharen.com/forum/index.php?topic=6708)
* [UIToggle](http://www.tasharen.com/forum/index.php?topic=6709)
* [UISlider](http://www.tasharen.com/forum/index.php?topic=6715)

### Tutorialシーンファイル

ProjectパネルのSearch部分に **tutorial** と入力するといくつかのシーンファイルが出てきます  
これらを1つずつ開いて見ると、シンプルなシーンとそれを解説するラベルが入っています

![tutorial](2015-01-25-ngui-intro/tutorial.png)

### Exampleシーンファイル

Tutorialシーンファイルと同様にProjectパネルのSearch部分に **example** と入力するといくつかのシーンファイルが出てきます  
Tutorialシーンファイルよりも若干実践的なシーンと、それを解説するラベルが入っています

![example](2015-01-25-ngui-intro/example.png)


### ReadMeファイル

同じように **ReadMe** と検索すると`ReadMe - X.X.X.txt`というファイルが見つかると思います(Xには数字が入る)  
この中身を読むと、それぞれのバージョンでなにが新しくなったのか把握することが出来ます

### Class Reference

多分最終的にはスクリプトから何にアクセス出来るのか調べるためにこちらを参照するようになると思います

- [NGUI: Next-Gen UI kit: Class List](http://www.tasharen.com/ngui/docs/annotated.html)

### まとめ

公式情報を並べた記事になってしまいましたが、それすらも初めはどこにあるのかわからなくて困ってしまったので、とりあえずググって情報を探す自分のような人のために書いてみました  
注意して欲しいのは、ここに載ってる情報はまたすぐに古くなるということです。探し方やどこから発見したのかも併記してあるのでこの記事が古くなっている時はもう一度、インポートしたNGUIメニューのHelpなどからたどる必要があることを覚えておいてください
