# 第1回 パRails輪読会ノート(2020-08-09)
###### tags: `パRails`
## 時間
予定：08:30〜10:00
実績：08:30〜10:30
1-1-1 〜 1-2-5まで

## 概要
箇条書きでご記入ください。また現在は「疑問点」「気づき」の2項目ですが、追加したい項目があればご自由に追加ください。

## 目次
> [TOC]

## HackMDの使い方
1. HackMDのアカウントを登録します。
2. Profile/settings/「Username」を設定します。
3. 左上の✏️Editか📖Bothボタンを押すとmarkdown形式で編集できます。
4. 書いた行に名前を書いてください。
    - 例：@ima1zumi xxページのこの文がよくわかりませんでした。

### HackMDの特徴
- このノートは、リンクを知っている人なら誰でも閲覧・編集が可能です。
- 色がついているところにマウスオンすると、誰が入力したか分かります。
- 自動保存です（保存ボタンなどはありません）

## 本日の予定
- 自己紹介
- 輪読
  - 読書&hackmdに疑問点・気づきを記入(マイクオフ・[タイマー](https://timer.onl.jp/)使用)
  - 疑問点・気づきを確認(都度)
- 振り返り(10分くらい)

※休憩はなしでやってみます！



## 自己紹介の記入をお願いします！
  - フィヨルド生
    - 名前(@username + 呼び名)
    - 現在のプラクティス 
    - 一言
  - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴
    - 一言

### @chiroru (ちろる)
- 現在Railsテスト・オブジェクト指向のプログラミングのプラクティス進めています！
- まだまだわからないことばかりですので、輪読会を通じて色々学ばせていただければと思っています！どうぞよろしくお願いします🤲


### @imaharu

- Rails歴は、1年ぐらいです。

### @ima1zumi (今泉)
- wcコマンド（オブジェクト指向版）
- よろしくお願いします！

### @Kyo18 (岸)
- フィヨルドのプラクティスではRailsのフォロー機能の実装を進めています！
- 輪読会に通しで参加してみたいと思っていたので楽しみです！💪

### @sasabo （ササボー）
- スクラム開発と自作サービスをやっています。
- 開催ありがとうございます。

### @masuyama13 （マスヤマ）
- プラクティス：Rails テスト
- パRails をやりきって Rails をパーフェクトにしたいです！

### @hogucc（おぐち）
- ボウリングのスコア計算プログラム（オブジェクト指向版）
- みなさんと一緒にパRailsを最後まで読み切りたいと思います！よろしくお願いします。

### @gallardo16(ほそがや)
- プラクティス：Railsの基本（現場Rails）
- よろしくお願いします！

### @mashiosano(さの)
- Railsのユーザーフォロー
- 輪読会未経験です。よろしくお願いします!

### @haruguchi-yuma (ゆうま)
- プラクティス:WebアプリからのDB利用（Sinatra）
- Rails未経験ですが頑張って理解していきたいです。よろしくお願いします！！

### @sanfrecce-osaka(森塚)
- Rails歴
    - 実務2年弱
    - 独学含めると約5年

### @gogutan(ごぐたん)
- プラクティス：システム開発
- 輪読会開催ありがとうございます、まだまだRails分からないことだらけなので頑張ります！

### @universato(ユニ)
- プラクティス:WebアプリからのDB利用（Sinatra）
- 実務経験がないですが、頑張っていきたいです。よろしくお願いします！

### @Hisao Toriyama(鳥山)
- RESTの考え方を理解するです
- 頑張って近々になんとかRailsの課題に入りたいので本日参加させていただきます。おそらくついていくこと難しいかもしれませんがせっかくの機会なのでまずはチャレンジさせてください。よろしくお願いいたします。

### @igaiga
- Rails歴 約10年
- 私もパRailsの読書会ははじめてなので楽しみにしてます

### @yokki
- プラクティス：Sinatra
- パRailsは「はじめに」だけ読みました。フレッシュな気持ちで参加します！

### @mh
- プラクティス: システム開発
- 輪読会初めてです


## 疑問点
> ※ ページ数, セクション数と併せてご記入ください
> ※ ex). XXXとはどういうことでしょうか？(1-1-1 P1)


### 1-1-1
特になし


### 1-1-2
- @ima1zumi `gem install` したときはグローバルのRubyのバージョンではいるんだっけ？と思った
    - => グローバル（rbenv使っていればそのバージョン）で入る
- @sanfrecce-osaka `rails _5.2.3_ new app_name` で new する際のバージョンを変えられる？
    - サンプルだと `-v` なので
    - もし↑の通りならどういう実装になっているのか気になる :eyes: 

- @hogucc gem installとbundle installの使い分けがいまいちわからない。どっちをどういうときに使うのが最適とかあれば知りたいです
    - bundle installは発注書をもとに実行するイメージ
    - Gemfileが発注書、Gemfileがあればbundle installすればいい
    - 超入門(238~)
- @Kyo18 `gem uninstall`した時点でGemfile.lockの内容が変わる？
    - `bundle update`で内容が変わる。
    - `bundle install`でもいけるかも？
        - @igaiga GemfileからGemを追加削除した場合は、bundle installでGemfile.lockが更新されました。


### 1-1-3

- @imaharu rubyをinstallすると、rakeコマンドが利用できるようになる意図がわからないなかった。他の言語でもmakeコマンド的なのは、言語をinstallした時点で自動的に利用できるようになるのか？
    - 環境ごとの差分をなくすため
- @sanfrecce-osaka rakeタスク、実務だとバッチ処理で使うのが多いかなぁ :thinking_face: 
- @yokki シェルスクリプト的な感じ？
- @ima1zumi imaharuさんと同じことが気になった
- @hogucc そもそもmakeコマンドとはなにかというところがよくわかっていない。。rakeはmakeコマンド風にタスクを実行するとあるが、両者の違いはどこなんだろう。。
  - @gogutan 調べていたら Rake は Ruby-Make の略であることも初めてわかりました
  - @sanfrecce-osaka makeは書いたコードを実行ファイル(機械語)にコンパイルするためのコマンドですね〜
- @ima1zumi 普通Rakefileという名前で作るんだ〜とおもった Task複数ある時は一つのRakefileに書くのだろうか？
- @sanfrecce-osaka RailsだとRakefileに書かず `lib/tasks/**.rake` に書くのが多いかなぁ :thinking_face: 
    - さらにいうと実行ファイルの実体は `app/tasks` 辺りに書いて `lib/tasks/**.rake` からは実行ファイルの実体にある処理を呼び出すだけにするというやり方はよくある気がする
- @ima1zumi ↓Railsの `Rakefile`
```
# frozen_string_literal: true

# Add your own tasks in files placed in lib/tasks ending in .rake,
# for example lib/tasks/capistrano.rake, and they will automatically be available to Rake.

require_relative "config/application"

Rails.application.load_tasks
```

- @Kyo18 `rake db:migrate` と `rails db:migrate`に違いはない？ちょっと昔の記事❓とかだとrakeの方で書かれている気がする。
  - rails5からrailsを使えるようになったらしい。



### 1-1-4

- @sanfrecce-osaka `bundle pristine Gem名` は知っておくと便利 => Gemの中をインストール時に戻せるのでデバッグコードを全部消せる
    - @ima1zumi `bundle pritstine` いいですよね！！
    - @igaiga `gem pristine` も便利〜 ← @sanfrecce-osaka :wakaru:
- @ima1zumi bundle update 全然使ったことなかった(アップデートしたいときでもbundle installしてました..)
- @masuyama13 Bundler でインストールしたのに `bundle exec` をつけ忘れることが多い…
    - @ima1zumi わかる...
- @sanfrecce-osaka railsの場合は `bundle exec` ではなく `bin/rails` で叩くのが多いかも :thinking_face: 
    - あとで伊藤さんの記事のリンクを調べる
    - @Kyo18 https://qiita.com/jnchito/items/c5a0848144203dce6e26 これかもです ← @sanfrecce-osaka yes!

```bin/rails
#!/usr/bin/env ruby
begin
  load File.expand_path('../spring', __FILE__)
rescue LoadError => e
  raise unless e.message.include?('spring')
end
APP_PATH = File.expand_path('../config/application', __dir__)
require_relative '../config/boot'
require 'rails/commands'
```

### 1-2-1〜1-2-5
特になし

## 気づき
>※ なるべく自分の言葉に置き換えて書いてみてください

### @imaharu

- railsのversionを任意指定できるの知らなかった。gem全体で機能なのか調べる

### @sanfrecce-osaka

- Gemfileから消して`bundle install` でGemfile.lockに反映されるか確認する
    - @igaiga さんが確認してくださって解決した :+1: 
- rails でバージョンを指定した際の実装を調べてみる
- binなしの `rails command名` は中で `bin/rails` を呼んでいるらしい(@igaiga さんからの情報)





## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします

- @sanfrecce-osaka igaigaさんの裏話等が非常に面白かった〜 :laughing: 

- @chiroru 時間の把握や全体の様子見をして、読書だけで精一杯になってしまった。慣れかもしれないですが、事前に少し読んでおこうかなと思いました。(個人的に)

- @chiroru もう少しいろんな人が発言しやすくなるにはどうしたらいいんだろ？気軽に質問とか相槌打ってもらいたいと思いました！

- @sasabo 自分では何も疑問に思わなかったことを皆さんが質問されていて、皆で輪読する意味がとてもあると思いました。ちゃんと議事録を残すのもとても良いと思います！運営の皆さんの連携もとても良かったです。次も参加しま〜す！

- @masuyama13 他の方の疑問点などを聞いて、読んだつもりでさらっと読み飛ばしている自分に気づき衝撃を受けた。すごく深いところまで聞けてとても勉強になった。 @igaiga さんや @sanfrecce-osaka さんの知識を分け与えていただいてありがたい！

- @hogucc 疑問点と気づきを書く欄は統一してもいいかも？読書の時間設定は今のところちょうどいいかんじだと思いました〜！開催ありがとうございます

- @universato 自分も並べて一括にしていいかも、と思いました。自分では調べなかったことが聞けてよかったです。

- @gogutan 1人で読んでいたらスルーしてしまいそうな点について、理解が深まり良かったです！@igaiga さん、@sanfrecce-osaka さんを始め皆さまありがとうございました！

- @gogutan カメラとタイマーをオンにして黙読する仕組みは、いい刺激になって良いなと思いました。

- @haruguchi-yuma 自分では思いもしない疑問点が聞けたりしてよかったです。あと、周辺知識？付属知識？がわかよかった。読んでいくので精一なので、少し先読みしておきたいなぁ。
 
- @yokki 質問がしやすい雰囲気がいいですね。実務に関する話も聞けて勉強になります。また、他の方の問題意識がわかってよかったです。今後は、どこから始まってどの章までやるとか、大まかに事前に決めてアナウンスしてはいかがでしょう？

- @mashiosano igaigaさんから裏話を聞けるのすごい!一人で読んでいると小さな疑問に対して「まあ　いっか」となることもありますが、みんなで疑問を共有できるので、参加できてよかったです。

- @igaiga 前説ができた。私も学びが多くてたのしい時間でした。
- @igaiga このページは公開されてますか？（宣伝tweetとかして大丈夫ですか？)
- @igaiga もし可能ならwherebyのチャットも残せると学びが残っていいなぁ。（と思ったけど、書くハードル上がっちゃうかな・・・。最初にみんなにアナウンスしたらみんな気にしない、だったら嬉しいな。）

- @mh 普段何事も思っていなかったことでも、いろいろな視点や気付きがあることを知って、学びが多かった。

- @HisaoToriyama（お先に失礼します！本日はありがとうございました） 自分には難しいところが多々ありましたが、多少なりとも気づき（考えるヒント、勉強しなければならないポイントの発見）があったので、引き続き可能な限り参加させていただきたいと思います。


- @ima1zumi お見合いが多くなってしまったのでいい感じにしたい
    - @sanfrecce-osaka オンラインだとどうしてもこれはおおくなっちゃいますよね〜(難しい・・・)
    - @yokki 自由に意見交換する場面ではある程度仕方ないと思いますが、それ以外の部分では、場合によっては「次〇〇さんお願いします」「〇〇さんいかがですか？」とかさばくのはいかがですか？つまりコントローラ笑
    - @ima1zumi 話が止まりそうだったらすかさずさばくくらいがいいのかな〜。人間コントローラ笑
- @ima1zumi みんなの疑問点が集まってめっちゃ勉強になった
- @ima1zumi 質問しやすかった！
    - @ima1zumi メモ：公開することを書いておく, お見合い対策, wherebyのチャットどうする？, 事前にどのセクションやるかアナウンス
- @ima1zumi Slackでリアクションつけて参加するの、気軽な感じだし前日リマインドなので忘れにくいしでいい仕組みだと思った

- @Kyo18 疑問を放っておかずその場で聞けるので、一人で学習しているときよりも理解度が段違いでした！良い教材を良い環境で勉強できるのは素晴らしいです・・・！
         これから手を動かしながら読んでいく部分が増えていくので、時間設定等は考えておく必要がありそう。　

- @gallardo16 深いところまでお話を聞けたのはとても良かったです。(ごめんなさい、間に合わなかったです)