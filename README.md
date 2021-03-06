# [ドットインストールjekyllの練習] (http://dotinstall.com/lessons/basic_jekyll)


## バーション
  - ruby 2.1.0
  - gem 2.2.2
  - jekyll 2.5.3

### lesson2  jekyll newコマンド使ってみる
gemのインストール
```
$gem install jekyll
```
sampleというファイルを自動生成する
```
$jekyll new sample	
```
ファイルを生成したらsampleフォルダに移動してjekyllを起動
```
$jekyll serve
```

### lesson3 一からサイトを作ってみる

新規のファイルを作成してその中に仮のmarkdownファイルを作ってみる
その際、markdownをhtmlに変換するおまじないとして上部に
```
---
---
```
と記入しておくこと。
index.mdなどとして、保存。
次に、htmlにビルドする
```
$jekyll build
```
こうすることによって、_siteという特殊なフォルダが生成される
ちなみに
```
$jekyll serve
```
をすると自動的にビルドされるので、いちいちビルドしなくてもよい。

### lesson4 レイアウトを組んでみる

新規で_layoutsというファイルをつくってその中にdefault.htmlを作ってみる。
レイアウトファイルを適用したい場合はmdファイルに
```
---
layout: default
---
```
として関連づけてやる	

### lesson5 css/画像を追加してみる

_layoutなどの特殊なフォルダ以外のものは、ビルドした際に自動で生成されるので
同じ階層にそのまま作成してよい

### lesson6 page変数を使ってみる

タイトルをページごとに変更するための方法
index.mdの上部に以下を追加
```
---
layout: default
title: my first project
---
```
さらに、default.htmlに以下に変更
```
<head>
	<meta charset="UTF-8">
	<title>{{page.title}}</title>
	<link rel="stylesheet" href="/css/default.css">
<body>
```
こうすることで、タイトルをページごとに変更することができる。

### lesson7 site変数を使ってみる

このサイト全体の定義は_config.ymlというファイルの中に書いてやる必要がある。
```
_config.yml を作成
```
次にその中に
```
name:myJekyllSite
encoding: utf-8
```
と記入。
こうすることでmarkdownで日本語が使え、nameという変数を使用できる。
この際注意すべきなのが、_config.ymlファイルはwatch対象外となるので
一度、control+Cで抜けて、再度serveする必要がある。

### lesson8 ページの一部を部品化してみる

サイトの一部（例えばfooterとか）を部品化するには
_includeフォルダというものを作ってあげて、その中に部品となるコードを書く。
今回はfooter_menu.htmlというものを作って、それをdefalut.htmlにインポートしてやる。

インポート方法は以下の通り
```
{% include footer_menu.html %}
```
{%%}でかこってやることでインポートできる。

### lesson9 ブログ記事を作る

まず、ブログのポストファイルを生成する
_post
ポストファイルの中に諸々記述して、{{content}}の中身となるmarkdownを記述
一般的にブログのpostファイルは2015-01-06-post.html
のように記述する。

### lesson10 ブログ記事の一覧を表示する

記事を一覧表示するにはhomeであるindex.mdのなかに制御構造を書いてあげる
ループを回すには以下のように書く
```
{% for post in site.posts %}
{% endfor %}
```
これは、site変数の中に記事の一覧が入っていて、その中で使えるデータを
postの中に入れてループを回すという意味。
