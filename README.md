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
