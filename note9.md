# 【第9回】パRails輪読会ノート(2020-10-4)
###### tags: `パRails`
## 時間
### 予定
- 08:30〜10:30

### 司会・タイマー
- 司会： @chiroru 
- タイマー： @ima1zumi
- 順番 @kyo → @masuyama → @chiroru → @ima1zumi

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
- 目的
- 輪読
  - 読書&hackmdに疑問点・気づきを記入(マイクオフ・[タイマー](https://timer.onl.jp/)使用)
  - 疑問点・気づきを確認(都度)
- 振り返り(10分くらい)

※休憩はなしでやってみます！


## 自己紹介の記入をお願いします！
> - フィヨルド生
    - 名前(@username + 呼び名)
    - 現在のプラクティス 
    - kaigionrailsを見た方、良かった講演はなんでしたか？
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - kaigionrailsを見た方、良かった講演はなんでしたか？

- @igaiga 
    - Rails歴 10年 / プラクティス: 新しい仕事の準備をしてます
    - kaigionrails: 良い発表ばかりでしたが、アーロンさんの講演に驚きました。黒曜さんのDBの気持ちに寄り添うのも勉強になりました。

- @hogucc（おぐち）
    - プラクティス：アジャイル・スクラムを理解する
    - kaigionrails：アーロンさんのリクエストからviewがrenderされるまでのお話（でも、どれも良かった）

- @sanfrecce-osaka(もりつか)
    - Rails歴
        - 実務2年前後
        - 学習期間含めると5年弱
    - プラクティス
        - rails の issue を読む
        - erd のコードを読む
            - https://github.com/amatsuda/erd
    - kaigionrailsを見た方、良かった講演はなんでしたか？
        - Viewがレンダリングされるまでの技術とその理解
        - Ruby 3.0におけるドキュメンテーションと端末制御の未来 :fire:
        - というか全部 :smile: 
        

- @coe401_(しおい)
  - Rails歴実務2年ちょっと/お借りしたキーボードを使えるようにしないといけない
  - Aaronさん！！！！！

- @chiroru (ちろる)
  - JSメモアプリではまっています・・
  - アーロンさんのお話(Viewがレンダリングされるまでの技術とその理解)

- @ima1zumi (いまいずみ)
  - スクラム開発/自作webアプリ
  - 就活準備中...
  - Aaronさん、makicamelさん

- @mashiosano (サノ)
  - JS(クラス)
  - Kaigi on Rails 録画で見る予定です...

- @Kyo18 (岸)
    - スクラム開発/自作アプリ
    - みなさんと同じくアーロンさんのお話がめちゃくちゃタイムリーで面白かったです！

- @masuyama13 (マスヤマ)
    - Vue CLI
    - すぐに役立ちそうだった発表
        - 「Railsパフォーマンス・チューニング入門」、「コードレビュー100本ノックで学んだRailsリファクタリング」、「TDD with git. Long live engineering.」

- @tam-03(田村) 
    - 現在のプラクティス : Rails devise
    - kaigionrails見てないです😅

## 疑問点・気づき
>### 書き込みサンプル
>@アカウント名 Rails楽しい

### 3-2-4〜3-2-5(8分)
#### 3-2-4

- @sanfrecce-osaka このあたりちょうど昨日Aaronさんが話してたあたりだなぁ

- @coe401_ 何と偶然にも便利な図解が！
![](https://i.imgur.com/dDBZkba.png)
![](https://i.imgur.com/2edZBRx.jpg)

- @ima1zumi 今日間に合わなかったけど、Rackアプリケーション/ミドルウェア作ってみたい
- @ima1zumi ミドルウェアという言葉はコンテキストによって何を指すのか変わって難しいけど、サンドイッチの具みたいなものかなと思った

- @masuyama13 シンプルすぎてびっくり
- @Kyo18 本の例ではミドルウェアが呼ばれる順番はSimpleMiddleware→Rack::Runtimeの順？
    - Rack::Runtime→SimpleMiddleware→App.new→SimpleMiddleware→Rack::Runtimeという順

#### 3-2-5

- @sanfrecce-osaka 先頭から2番目に yucao24hours さんの発表にあった ActionDispatch::HostAuthorization が :eyes: 
- @sanfrecce-osaka Webpacker::DevServerProxy が production では使われないミドルウェアの例かな :eyes: 

### 3-2-6(8分)

- @sanfrecce-osaka middleware を置く場所としては lib配下が一般的なのかな？ :thinking_face: 
  - @coe401_ 実際プロダクションコードでミドルウェアを作ったことはないのですが、gemとして切り離してしまった方が管理が楽な気はしますね
  - @igaiga libよさそうな気がします(app以下に置きたくないので消去法で)

- @ima1zumi どうして devise は Rack ミドルウェアとして作ったんだろうと気になった
    - Warden のラッパーだから、ということは分かった
    - なぜ Warden は..
    - DeviseってRailsエンジンじゃなかったですっけ…
      - > in Rack based Ruby applications.
        - https://github.com/wardencommunity/warden/wiki
        - 何かと勘違いしてたかも..
```
$ bin/rails middleware
...
use Warden::Manager
use OmniAuth::Strategies::GitHub
run BooksApp::Application.routes
```
- Devise は Railsエンジン. Rails アプリに Rails アプリを入れられるようなもの
- 認証は Rails に入る前に処理仕掛けたい, 生のHTTPリクエスト/レスポンスを触りたいかも

routes.rb
```
Rails.application.routes.draw do
  devise_for :users, only: :omniauth_callbacks, controllers: {
    omniauth_callbacks: "users/omniauth_callbacks"
  }
...
```


- @masuyama13 Rack自体をミドルウェアと呼ぶこともありますか？
    - ミドルウェアは何かと何かの間にあるソフトウェアのこと
    - RackミドルウェアはRackミドルウェアと呼ぶ
    - ソフトウェアと読み替えても問題なさそう
    - >RackはHTTPリクエストとレスポンスを可能なかぎり簡単な方法でラッピングすることで、Webサーバー、Webフレームワーク、その間に位置するソフトウェア (ミドルウェアと呼ばれています) のAPIを1つのメソッド呼び出しの形にまとめます。
<cite>[Rails と Rack \- Railsガイド](https://railsguides.jp/rails_on_rack.html)</cite>
        - > その間に位置するソフトウェア
        - を指してミドルウェアと呼んでいるような気もする :eyes:

- @hogucc middlewareを削除するケースってどんなときだろう...config.middleware.deleteの使いどころがわからなかった
    - 自作のミドルウェアではなくRailsの内部のミドルウェアを削除するときに使う
    - production環境では使うけどstaging環境では使わないミドルウェアがあったときにstagingでdeleteするとか

- https://railsguides.jp/rails_on_rack.html#%E3%83%9F%E3%83%89%E3%83%AB%E3%82%A6%E3%82%A7%E3%82%A2%E3%82%B9%E3%82%BF%E3%83%83%E3%82%AF%E3%81%AE%E5%86%85%E9%83%A8
    - @sanfrecce-osaka ActiveRecord::PendingMigrationError って Rack層で raise してたのか :eyes: 
    - @ima1zumi bootcamp で pull したあと bin/setup せずに  Rails 起動したときによくでるやつだ

### 3-3-1〜3−3−2（8分+α）
#### 3-3-1

- @ima1zumi `rails db:seed:replant` の説明にある `TRUNCATE` は、TABLE の中身を高速に削除するSQL
    - https://www.postgresql.jp/document/12/html/sql-truncate.html
    - 物理削除も即座にやってくれるので、ディスク容量がきついときに便利そうなSQLだ
        - `DELETE` SQLは基本的に内部で削除フラグを立てるだけで、物理的に削除されるのはまた別のタイミング (DBMSによってやりかたは違いそう)
        - https://www.postgresql.jp/document/12/html/sql-vacuum.html
        - @igaiga 勉強になる

- @coe401_ そういえばこの表には`$ rails db:migrate:reset`と`$ rails db:migrate:redo`が載っていませんね（開発中よく使う）
    - @sanfrecce-osaka :crab: 
    - @igaiga 載ってた方が良いですねー
    - @hogucc 現場Railsの380ページにredoを習慣にしようという話が書かれてます
    - @chiroru redoはrollback + migrate

#### 3-3-2
- @coe401_ いまだに`change`と`up` `down`の使い分けがよくわからない…（小声）
    - @sanfrecce-osaka 反映するmigrationが可逆なやつはchangeでOKで、不可逆な場合はupとdownを書く必要ある、という話なのかなぁというき気もします:thinking_face:
      - 可逆なものと不可逆なものって何ですか…
    - @igaiga changeで書いて migrate:redo で失敗したらup/downで書いてます
      - @coe401_ なるほど〜〜〜〜〜
- [Active Record マイグレーション \- Railsガイド](https://railsguides.jp/active_record_migrations.html#change%E3%83%A1%E3%82%BD%E3%83%83%E3%83%89%E3%82%92%E4%BD%BF%E3%81%86)
- @sanfrecce-osaka migration 関連のコードは ActiveRecord の中ではまだ読みやすい方らしい(昨日。Kaigi on Rails の懇親会にて某エンジニア談)
    - なのではじめて ActiveRecord 読む際はぜひ :grin: 

### 3-3-3〜3-3-5(7分)
#### 3-3-3


#### 3-3-4

- @sanfrecce-osaka seed、生で使うのか seed_fu を使うのかどっち派が多いんだろう？ :thinking_face: 
  - @coe401_ 弊社はseed-fuですね
    - seed-fuのfuって何なんだろう ← @sanfrecce-osaka :crab: 

#### 3-3-5


- @ima1zumi （ご存じの方がいれば教えて下さい）webアプリケーションに繋いでるDBの再編成(reorg/shrink/optimize)ってやってますか？
    - 前触ってたメインフレームのDBでは定期的に仕掛けてたんですが、I/Oが多いとオンライン再編成大変そうだしどうやっているんだろうときになりました
    - MySQL だと `OPTIMIZE` っぽいです https://dev.mysql.com/doc/refman/5.6/ja/optimize-table.html

- @Kyo18 最近システム開発参加の準備のときに`bin/setup`を使ったので、内部で`db:prepare`が利用されているのかと納得。

```ruby
# bin/setup:L28
  puts "\n== Preparing database =="
  system! 'bin/rails db:prepare'
```

- @chiroru `db:reset`はブランチでmigrateした後に別ブランチでも作業する時に使った気がします
  - @coe401_ ↑よくやる！
  - https://bootcamp.fjord.jp/questions/684 (lampさんのQA)

- @hogucc [ちょっと待った! Railsでgitリポジトリから除外すべきでないファイル:Gemfile.lockとdb/schema.rb｜TechRacho（テックラッチョ）〜エンジニアの「？」を「！」に〜｜BPS株式会社](https://techracho.bpsinc.jp/hachi8833/2014_02_07/15390)
  - rails db:setupはschema.rbに依存しているのでschema.rbをgitignoreに書かないように注意しなきゃという話

- @mashiosano db:seed:replant便利 Railsのプラクティスの時はdb:reset db:seedを繰り返していたな…
    - @igaiga Rails6.0で入った機能みたいですね。rails db:setup + db:seed なのかな。勉強になりました。
    - https://github.com/rails/rails/issues/34765

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！


- @sanfrecce-osaka ちょうど昨日の Kaigi on Rails で出てきたタイムリーな話が結構あり学びが多かった :raised_hands: 
    - ディスカッションも盛り上がって楽しかった :smile_cat: 

- @chiroru rackは言葉、rackミドルウェアは話者という説明がとても分かり易かったです！

- @masuyama13 Rackのイメージができてよかった。ミドルウェアという言葉が難しいと思ったが、そんなに深く考えなくてもよさそう😀DB難しいけど理解したいので ActiveRecord のコード読んでみたい。


- @hogucc Rackミドルウェアのイメージがつかめました。実際の動きは自分で作って動かして理解していきたいと思いました（この後、作ってみます！）

- @coe401_ 今日もRackのことをお話しできて幸せです〜そして知らないことばかりで勉強になりました！
    - @sanfrecce-osaka :heart_eyes_cat: 
    - @sanfrecce-osaka 輪読会は来週以降もやるのでもしよければご参加ください〜 :grin::grin::grin: 


- @mashiosano Rack、middlewareに触れてこなかったので勉強になりました 後で自分で動かしてみます

- @ima1zumi ミドルウェアとは何か？の理解が深まって良かった！ミドルウェアはミドルウェアとしか言いようがない（ときがある）
- @ima1zumi Rackが身近な存在になった!!

- @tam-03
まだRailsを始めたばかりで、分からない所も多かったですが、DBのresetの話はちょうど昨日詰まっていた所で、勉強になりました！

- @Kyo18 Rackミドルウェアがどんなものなのかある程度理解できたので、具体的にどのような処理を行うミドルウェアが存在するのか知りたくなりました！


