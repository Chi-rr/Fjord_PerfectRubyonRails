# 第3回 パRails輪読会ノート(2020-08-23)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 1-4-1〜2-1-1

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
    - 一言
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴
    - 一言

### @Kyo18 (岸)
- 自動テスト
- 昨日はじめてLT会で発表しました。めっちゃ緊張しました。今はホッとしています。


### @mashiosano (さの)
- 自動テスト
- 早起きは苦手ですがなんとか起きれました。よろしくお願いします！

### @e6i24v(安達)
-　Linux
-　まだRubyに入っていないので、傍聴だけになってしまうと思いますがよろしくお願いします　

### @oba (おおば)
- Rails歴：たまにお仕事で書くくらいです。
- 輪読会初参加です！よろしくお願いします！

### @universato (ユニ)
- プラクティス: Railsに苦手意識があるのか、Rubyのオブジェクト指向を先に進めています。Rubyは好き。
- 予習したいと思いつつ、いつも予習していない。よろしくお願いします！

### @hogucc（おぐち）
- JavaScript(FizzBuzz問題)
- よろしくお願いします！

### @sanfrecce-osaka (もりつか)

- Rails歴
    - 実務2年前後
    - 学習期間含めると5年弱
- Rails 最近書いてないマンです

### @ima1zumi (いまいずみ)
- プラクティス： JavaScript ESLint と Prettier の共存は不可能なのでは・・・
- Rails と仲良くなりたい

### @chiroru (ちろる)
- プラクティス： オブジェクト指向(wc)
- よろしく願いします〜！！

### @masuyama13 （マスヤマ）
- プラクティス：オブジェクト指向（ボウリング）
- ねむい・・・

### @igaiga
- プラクティス： メンターの採用活動
- たくさん寝たけどまだ眠いです

### @imaharu 
- プラクティス：LT会を見て、LTしたくなったのでネタを探す 
- 頑張るぞ

>### 書き込みサンプル
>@アカウント名 Rails楽しい
### 1-4-1

- @sanfrecce-osaka ファイルを作成する際、それぞれのgenerateコマンド派、scaffold派、手作業派の3流派がありますよね(どれでやるかは好み)
- @sanfrecce-osaka skipオプション、アプリケーションテンプレート作るときに使ったなぁ

- @imaharu `rails g scaffold` でファイル作成順序に理由はあるのか？
    - メモ & Try: 自分で調べてみる。わからなければ、適切なところを質問してみる
    - @ima1zumi 特に理由はなさそうです:
    > 実はscaffoldジェネレータ自身は何も生成していません。生成に必要なメソッドを順に呼び出しているだけです。このような仕組みになっているので、呼び出しを自由に追加/置換/削除できます。
    - https://railsguides.jp/generators.html
        - :eyes: あざす
- @Kyo18 scaffoldで作成される`*.json.jbuilder`をまだ使ったことがない。何に使うのかもあまりわかっていない・・・。
    - @sanfrecce-osaka Web APIとしてjsonをレスポンスで返したい場合でhtmlと同じルーティングにしたいときに使うかんじですかね〜(ほとんどはAPIモードでやることが多いけど)

- @chiroru testは作成しますか？(そのまま使うことはないと聞いたので、`-T`でskipしてもいいのかな？と思っていた)
  - generateで作成されるものを使用する。(ファイル名とかパスとかそのまま使用できるし)
  - 中身を変える

- @mashiosano rails g scaffold を実行した時に表示される invokeってどういう意味だろう?
    - @sanfrecce-osaka 実行時のタスクの名前っぽい
        - https://ejje.weblio.jp/content/invoke
    - @ima1zumi 「呼び出す」とかそういう意味の動詞みたいですね
        - invokeが動詞として使われています： https://guides.rubyonrails.org/generators.html

### 1-4-2

- @imaharu 「最初にschema_migrationsというテーブルを参照しmigrationIDを確認します。そして実行されていないmigrationを検知すると未適用のmigrationファイルを実行しmigrationIDを記録します。そのため、rakedb:migrateを複数回実行しても、実行のたびに同じCREATETABLE文が実行されるようなことはありません。」
    - 具体的に何をやっているか、知らなかったので勉強になった。メモ: 後でソースコードを読む
- @imaharu 「http://localhost:3000/rails/info/routes」 のURL毎回忘れる。記憶力強化以外で、賢い解決策はないものだろうか
    - RubyMineで見る
    - お気に入りに追加
- @sanfrecce-osaka config/environments 配下のファイルの設定次第ではマイグレーションが最新でないと例外が発生する
    - e.g. `config.active_record.migration_error = :page_load # ページをロードした際にマイグレーションが最新でなければ例外発生`

- @ima1zumi `bin/rails db:create` では `development` と `test` の db しか作成されていないようにみえる。本番環境では別のコマンドで作成するのだろうか？
    - @sanfrecce-osaka ローカルでは production は作成する必要がないからですね〜(productionでは環境を指定して `bin/rails db:create` を実行する)
    - @ima1zumi なるほど！
        - `bin/rails db:migrate RAILS_ENV=production`

- @hogucc 自分は`bin/rails db:migrate:status`でいまどこまでマイグレーションファイルが適用されているか確認したことがなかったが、他の方は使うのかどうか、使うのであればどういう状況で使うかが気になった。
    - @imaharu 使う
        - migrateが上手くいってない時、確認するため
        - rollbackを実行した時、自分の期待するmigrationまで戻っているか確認するため
    - @mashiosano 
        - 自分はgitのブランチを切り替えた時に使いますね
- @Kyo18 `db:migrate`する前まで`git reset --hard`したい時にいつも`db:rollback`するのを忘れてしまうのどうにかしたい。


- @ima1zumi 自分用メモ; 自動作成されるテーブルたち
```
❯ rails dbconsole
sqlite> .tables
ar_internal_metadata  schema_migrations     tasks  
```
- `ar_internal_metadata` ： DB削除誤爆防止
    - ActiveRecord::Base.protected_environments = %w(production staging) で制御するみたい [ドキュメントはこちら](https://apidock.com/rails/v6.0.0/ActiveRecord/ModelSchema/ClassMethods/protected_environments)
- `schema_migrations` ： migrationがどこまで進んだか管理
- `tasks` ： 自分で作ったやつ

### 1-4-3

### 1-4-4

- @sanfrecce-osaka 自分の場合は、↓を教えてもらってから基本の7つのアクション以外はなるべく作らないようにしているなぁ
    - c.f. https://postd.cc/how-dhh-organizes-his-rails-controllers/
    - c.f. https://tech.kitchhike.com/entry/2017/03/07/190739


### 1-4-5

- > ```before_action :set_task, only: [:show, :edit, :update, :destroy]```
    - @sanfrecce-osaka この節の話題からは外れるけどこれは意見わかれるやつだ :eyes:
        - @imaharu 自分は、やらない
        - @ima1zumi scaffold のまま使ってた。。
        - @sanfrecce-osaka RubyMineで確認してみたら before_action の第一引数でコードジャンプいけました  :+1::+1: 
- @masuyama13 `tasks#update`が`PATCH`と`PUT`2つあるのはなぜだろう
  - @igaiga 歴史的な経緯で2つあります。もともとPUTがあったのですが、REST的にはPATCHが正しかろうということで、PATCHが導入されました。(Rails3.2頃？)
      - どちらもつかえるので、両方残しておけば問題ないです
  - @oba [PATCH](https://developer.mozilla.org/ja/docs/Web/HTTP/Methods/PATCH)
```
PATCH	/tasks/:id(.:format)	tasks#update
PUT	/tasks/:id(.:format)   tasks#update
```


### 2-1-1

- @sanfrecce-osaka
    - ロジックは全部 Model にぶちこんで Fat Model を作るのが Rails Way
    - Fat Controllerダメ、絶対(辛いやつ)

- @unversato
  - ロジックとは、バリデーションなどのことでしょうか
  - → バリデーションも含めて色々なこと。
  - プラクティスにあるUserモデルにフォローのメソッドをつけたりすること。コントローラ内だけの処理でも、モデルにメソッドをつけて簡潔にさせた方がよいらしい。

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka 1章終わった！ :raised_hands: 
- @chiroru ↑終わった！！段々慣れてきた気がするから、予定の範囲の見積もりも次回は少し増やしていきたいですね！
- @imaharu 勉強会で学んだことをフィヨルドLT会でアウトプットすると良さそう ← @sanfrecce-osaka :yosaou:
- @imaharu 前回と司会が変更してるといいですね。SPOF(単一障害点)をなくしてる。
- @imaharu 録画とかあれば、復習と後から参加しやすい雰囲気になりそう
- @masuyama13 とってもスムーズでよかった。ルーティング、よく見たら知らない部分があったりしてすごく勉強になった
- @hogucc 今回から感想をWherebyに書くことになったが、分けてよかったと思いました。他の人がどう思ったかも気になる。書くことに対するハードルがあがってないかとか。

- @ima1zumi wherebyとhackMD分けて良かったと思います。
    - 進行としては良かったとおもうんですが、たしかに書くハードルはあがったかも..
- @ima1zumi 自分は時間余っちゃったんですが、今回時間長かったですかね？
    - @imaharu 画像やコードが多いと、読むところ少ないのでページ数で時間を区切らない方がいいかも
- @ima1zumi フィヨルド生がRailsでハマりがちなところ集めてまとめるとめっちゃ知見になりそう、とふと思いました（感想） ← @sanfrecce-osaka :crab: 
    - @igaiga 後生の受講生の知見になりそうでめっちゃええやんですね 🌟

- @universato 1章終わっていて、進んでいて良い!

- @mashiosano PUT/PATCHの違いは意識したことがなかったので勉強になった。

## whereby のチャットログ

08:30
oba
おはようございます！

08:32
oba
👏

08:35
ima1zumi
https://hackmd.io/yrrvikG7Q22P27JZg8pv0w?both

08:44
ima1zumi
バックスラッシュでコマンド入力改行できるんだ

08:50
おぐち
skipオプションがこんなにたくさんあるの知らなかった

09:03
ユニ@universato
1-4-2 15分

09:31
ユニ@universato
👍

09:33
chiroru
👍

09:33
ユニ@universato
1-4-3

09:33
igaiga
昨日のmsauyamaさんのスライドでgit reset --soft を知りました。勉強になりました〜。 https://speakerdeck.com/masuyama13/git-reset-200822?slide=5

09:33
ユニ@universato
1-4-4も！

09:35
masuyama13
お〜！ありがとうございます😄

10:05
ima1zumi
つらそう

10:07
oba
https://developer.mozilla.org/ja/docs/Web/HTTP/Methods/PATCH

10:10
ユニ@universato
👍

10:28
ユニ@universato
👍

10:28
sanfrecce_osaka
👍

10:37
sanfrecce_osaka
👏

10:37
masuyama13
👏

10:37
Mashio Sano
👏

10:37
おぐち
👏

10:37
oba
👏

10:37
imaharu
👏

10:37
oba
👏

10:37
ユニ@universato
👍
👏

10:37
おぐち
👏

10:37
oba
👋

10:37
sanfrecce_osaka
👋