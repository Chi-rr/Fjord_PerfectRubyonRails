# 【第38回】パRails輪読会ノート(2021-5-9)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @hogucc
タイマー： @chiroru
順番 @chiroru → @ima1zumi → @kyo → @masuyama → @hogucc

## 概要
箇条書きでご記入ください。また現在は「疑問点・気づき」の1項目ですが、追加したい項目があればご自由に追加ください。
輪読会後、こちらのノート＋チャットは公開させていただくので、よろしくお願いいたします。

## 目次
> [TOC]

## HackMDの使い方
1. HackMDのアカウントを登録します。
2. settings の Username を設定します。
3. 左上の✏️Editか📖Bothボタンを押すとmarkdown形式で編集できます。
4. 書いた行に名前を書いてください。
    - 例：xxページのこの文がよくわかりませんでした。 @ima1zumi 

### HackMDの特徴
- リンクを知っている人なら誰でも閲覧・編集が可能です。
- 色がついているところにマウスオンすると、誰が入力したか分かります。
- 自動保存です（保存ボタンなどはありません）

## 本日の予定
- 自己紹介
- 休憩挟みつつモブプロ(10:10~15くらいまで)
- 振り返り書く(3~5分くらい)
- 雑談(15分くらい)


## 自己紹介の記入をお願いします！
> - フィヨルド生
    - 名前(@username + 呼び名)
    - 現在のプラクティス 
    - 今日のテーマ：最近どう？
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：最近どう？


- @sanfrecce-osaka(もりつか)
    - 現在のプラクティス
        - Gem 作成
    - 最近どう？
        - ようやく Notion に入門した :raised_hands: 
        - 今日で GW が終わるらしいですがもっと休みほしい、365 連休くらいほしい :joy_cat: 
        - 昨日寝たのが 4:00 くらいで眠い :sleepy: 

- @fuga 
    - ふーがと申します。
    - 現在のプラクティス：オブジェクト指向
    - 最近どう？：
        - テストを書くおもしろさがわかってきました。
        - 小口さん、ちろるさん、就職おめでとうございます！うらやまし
            - @hogucc ありがとうございますー！！！

- @asya81(かわかみ)
    - 現在のプラクティス　CSS上級
    - 最近どう？
        - お仕事でCSS触る機会があって、恐怖心がなくなっているのを実感しました！
        - Notion気になってて、まだ触れないでいます

- @hogucc（おぐち）
    - 現在のプラクティス：５月から仕事が始まりました〜
    - 最近どう？
    　　 - 社用Macのセットアップをしてました
    　　 - 分割キーボードにだんだん慣れてきました

- @imaharu 
	- Rails2年
	- 最近どう？
		- 試着して服を買うことに成功
		- エンジニア主導でビジネスの人の要求定義を引き出すムーブメントの初めの一歩がわからず、PMBOK勉強し始めた
		- コード書く副業をゆるっと探し始めた

- @isshi-hasegawa（いっしー）
    - 現在のプラクティス：ssh の基本を理解する（Railsは少し経験あります）
    - 最近どう？
        - 寝床で娘に顔を蹴られてあまり眠れておりません…
        - プラクティスは順調に？すすめられています
        - 参加して8日間くらい連続で活動できています

- @chiroru (ちろる)
  - 4月からお仕事しています〜先月卒業式でした！
  - 最近どう？
    - お料理動画を見て、自分でもてきとうに作ったりしてます

- @igaiga
  - Rails歴/プラクティス: 10年/執筆やってます
  - 今日のテーマ： 「なめらかな社会とその敵」を7年ぶりくらいに読んだら理解できるようになってて嬉しい



### zoom の画面共有について

- zoom で画面共有ができるか確認しておいてください。
    - 画面共有できない場合、 システム設定 > セキュリティとプライバシー > プライバシー > 画面の録画で zoom.usにチェックを入れます。
    - https://support.zoom.us/hc/ja/articles/201362153-%E7%94%BB%E9%9D%A2%E3%82%92%E5%85%B1%E6%9C%89


### 今日のスタート
13章からスタート

## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい


### 順番ガチャ

```ruby=
%w[sanfrecce_osaka hogucc chiroru fuga asya81 imaharu isshi-hasegawa].
  partition { |user| !%w[fuga asya81 imaharu isshi-hasegawa].include?(user) }.
  flat_map(&:shuffle)
  # => ["hogucc", "chiroru", "sanfrecce_osaka", "fuga", "isshi-hasegawa", "imaharu", "asya81"]
```

### 13章 複雑なデータ操作を実装する 

#### 13-1 Concern

##### 13-1-1 Concern とは

- 

##### 13-1-2 いつ利用すべきか

```ruby=
# クラスメソッド
Photo.tagged_with

# インスタンスメソッド
photo = Photo.new
photo.tags
```

##### 13-1-3 利用例

- @hogucc モデルとformオブジェクトの使い分けがよくわかっていない
    - 複数のモデルを扱う場合？
    - DBのバリデーションとフォームから来た値のバリデーションをモデルでやっているとつらくなるときがある。そのときがフォームオブジェクトの出番
        - モデルがそのままフォームになっている場合はつらくないけど、DBと入力フォームの形が違うときがつらい
            - フォームによって分岐が発生するため

- https://github.com/mbleigh/acts-as-taggable-on
    - これはただのモジュールだった

##### 13-1-4 ActiveSupport::Concern

- @imaharu 
	- ブロック渡しができるincludedメソッドとは？
		- https://github.com/rails/rails/blob/6-1-stable/activesupport/lib/active_support/concern.rb#L156-L168

- @hogucc
    - https://docs.ruby-lang.org/ja/latest/method/Module/i/included.html

- @hogucc クラスにメソッドを動的に定義する
    - https://docs.ruby-lang.org/ja/latest/method/Module/i/class_eval.html

- 参考資料
    - https://speakerdeck.com/expajp/the-door-of-meta-programing-is-opened-by-activesupport-concern?slide=20
    - [Concerns about Concerns](https://speakerdeck.com/willnet/concerns-about-concerns)

- bootcamp アプリの場合
    - https://github.com/fjordllc/bootcamp/blob/main/app/controllers/concerns/authentication.rb
    - https://github.com/fjordllc/bootcamp/blob/main/app/models/concerns/commentable.rb

```ruby=
# frozen_string_literal: true

module Hoge
  def self.included(base)
    puts base
    puts base.class
    puts base.fuga
  end
end

class Fuga
  def self.fuga
    puts 'fuga'
  end
  include Hoge
end
Fuga.new
```

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @hogucc 久々に輪読していくスタイルに戻ったので新鮮なかんじだった
    - 今日みたいな進め方でよかったでしょうか？
- @hogucc 結構難しい内容だったと思うので議論するのも難しいのかなという感じがした

- @sanfrecce-osaka 13-1 は次回で終わりそう
- @sanfrecce-osaka 値オブジェクト等、以前の章で説明されている前提で単語が出てくるので進め方が思った以上に難しかった :sweat_smile: 
- @sanfrecce-osaka Ruby の応用的なところ(メタプロ)の話も入ってくるのでなかなか難しい
- @sanfrecce-osaka @igaiga さんの Form オブジェクトの説明、すごくしっくり来た
- 

- @asya81 回し読みしていくの、良い感じでした！
- @asya81 Formオブジェクトを初めて知ることができた。
- @asya81 @imaharuさんがコードを見せてくださって、イメージしやすかったです。
- @asya81 @igaigaさんから11-13章は中級者から上級者に上がるための内容とお聞きして、安心した。1人だったら辛くなったかも。
- @asya81 includeやexclude、クラスメソッド、インスタンスメソッドなど理解できてない部分を動かしつつ理解できるようになりたい

- @imaharu 
	- 起きれた
	- 11-13章は、すごい楽しい
		- yasaichiさん、いつか呼びたい
		- @sanfrecce-osaka :+1: 
	- 読む目的がはっきりしていれば、どこまで詳細を追っていくのか全員の認識揃うのでいいかな〜と思いました


- @isshi-hasegawa（いっしー） 
    - はじめての参加でしたが、雰囲気をつかめました！
    - @imaharuさんの記述された具体例はスッと理解できたけど、書籍のサンプルコードはすんなりと読めなかった
    - 自力で読み進めるのは確かに難しいですね
    - 輪読会の最中にヘッドセットが届きました
        - @sanfrecce-osaka :raised_hands: 


- @fuga 内容的にふんわりとした理解しかできませんでしたが、自分1人で読んだら完全に読み流して終わったと思うので、理解されてる方々と輪読できて本当にありがたかったです。
- @fuga 今後、いつか今日の内容を実際に使うことがあったときに引き出しとして引き出せたらいいなと思います。

- @chiroru なんとなく知っているが使ったことない、みたいな感じだった。こんな感じなんだとなんとなく覚えておきたい。
- @chiroru 


## チャット
hoguccから皆様 (8:32 午前)
https://hackmd.io/JC8zzjn_T-GaIh-71clcKQ
https://hackmd.io/cil0ZypxStq6uvPvxTtWGw?view
imaharuから皆様 (8:50 午前)
Effective Testing with RSpec 3
森塚真年から皆様 (8:51 午前)
https://blog.jnito.com/entry/2017/09/11/051550
hoguccから皆様 (9:07 午前)
%w[sanfrecce_osaka hogucc chiroru fuga asya81 imaharu isshi-hasegawa].
  partition { |user| !%w[fuga asya81 imaharu isshi-hasegawa].include?(user) }.
  flat_map(&:shuffle)
hoguccから皆様 (9:15 午前)
https://railsguides.jp/association_basics.html#has-many-through%E9%96%A2%E9%80%A3%E4%BB%98%E3%81%91
asya81（かわかみ）から皆様 (9:16 午前)
ありがとうございます！
hoguccから皆様 (9:17 午前)
https://railsguides.jp/association_basics.html#has-many%E9%96%A2%E9%80%A3%E4%BB%98%E3%81%91
hoguccから皆様 (10:08 午前)
https://speakerdeck.com/willnet/concerns-about-concerns?slide=10
hoguccから皆様 (10:16 午前)
https://github.com/fjordllc/bootcamp/blob/main/app/models/concerns/checkable.rb
https://github.com/fjordllc/bootcamp/blob/f4b58a8af0e9d2b4279aaf7d222263028728983d/app/models/concerns/commentable.rb#L13