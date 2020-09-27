# 【第8回】パRails輪読会ノート(2020-09-27)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
司会・タイマー
- 司会： @masuyama
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
    - 最近で一番楽しかったプラクティス（最近でなくてもOK）
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴
    - 最近で一番楽しかったこと（最近でなくてもOK）

- @Kyo18(岸)
　　- Vue CLI
　　- npmの作成がミニアプリ作成のようで楽しかったです
　　- 安い水出しコーヒーだとコーヒー風味の水になりがちなのが最近の悩みです
 
- @coe401_(しおい)
  - Rails歴 初めて触ってから3年弱くらい？
  - 「達人プログラマー」よかった！

- @chiroru (ちろる)
  - JS(メモアプリ)
  - ruby

- @igaiga
    - プラクティス: 自転車の修理
    - 今日のテーマ: if 晴れ then 隣駅で自転車回収 else ごろごろ end

- @masuyama13 (マスヤマ)
    - プラクティス：Vue CLI
    - 楽しかったプラクティス：Vue.js の基本

- @hogucc（おぐち）
    - プラクティス: Vue CLI
    - 楽しかったプラクティス: lsコマンドオブジェクト指向版（リファクタリングしていく過程が楽しかった）

- @sanfrecce-osaka(もりつか)
    - Rails歴
        - 実務2年前後
        - 学習期間含めると5年弱
    - プラクティス
        - Machida.rbのイベント作成(もう今週 :sweat_smile:)
    - 最近で一番楽しかったこと（最近でなくてもOK）
        - ボウリング(オブジェクト指向)
        - https://gist.github.com/sanfrecce-osaka/49360e106c2926d603c6909ccf41d419


## 疑問点・気づき
>### 書き込みサンプル
>@アカウント名 Rails楽しい

### 3-1-1〜3-1-2(7分)

- @sanfrecce-osaka integration は使ったことないなぁ(bootcamp で使われている箇所がないというのもあるけど)
  - @coe401_ このディレクトリ構成はRailsが用意してくれているもの？ですよね…RSpecだとリクエストスペックが該当するのかな？
      - @sanfrecce-osaka ディレクトリ構成に関してはそうですね〜(デフォルトがminitestなので)
- @sanfrecce-osaka migrate で RAILS_ENV が必要なときとそうでないときの区別がきちんと整理できてないなぁ :thinking_face: 
    - 何もつけないと development
    - RAILS_ENV=test つけると test
    - schema.rb があると、テスト実行時にスキーマがロードされてテストDBが自動で作成されるので、 RAILS_ENV=test をつけてmigrationを実行しなくても、DBが作成されていることがあります
- @coe401_ 「早めにテスト、何度もテスト、自動でテスト」
    - @igaiga しおいさん「達人プログラマー脳になってて・・・」
- @Kyo18 小規模なアプリしか作ったことがないので、テストの実行時間をあまり意識したことがない。実行時間はどのような場面で必要となるのか？
    - @igaiga テスト時間が出ると自分のアプリの普通のテスト時間がわかります。結果、その時間だけtwitterをやりにいくようになります。
- @hogucc minitestだとテスト環境で未実行のマイグレーションファイルがあってもテスト用のDB設定をロードしてくれるのか。RSpecはそこまでしてくれなかったような？
    - @hogucc 勉強会後に確認したところ、RSpecでも`rails db:migrate RAILS_ENV=test`を実行しなくてもテストは実行できた。
      - `rails g scaffold task content:text`で雛形作成→`rails db:create/db:migrate`でデータベースの設定（テスト環境ではmigrateしていない）→rspecの導入→request_specの作成＆実行　の手順で確認しました。
      - 作成したrequest_spec
        ```
        require 'rails_helper'

        RSpec.describe "Tasks", type: :request do
          context "index" do
            it "responds successfully" do
              get tasks_path
              expect(response).to have_http_status(200)
            end
          end
        end
        ```

### 3-1-3〜3-1-5(7分)

- @sanfrecce-osaka setup でのインスタンス変数、Ruby的には実際にはクラスインスタンス変数なのかなぁ :eyes: (あくまで推測)
  - @coe401_ `instance_eval`でブロックを渡してますね（多分インスタンス変数） https://github.com/seattlerb/minitest/blob/15ed8e4ce504c8313058a1d6fc4918299be34328/lib/minitest/spec.rb#L184 ← @sanfrecce-osaka :naruhodo:

- @masuyama13 `test do`〜`end`の書き方、test-unit では使える（前Machida.rbで発見👀）
  - @chiroru minitestはブロックでメソッドを表現できないけど、minitestをベースにしたRailsのテスト(ActiveSupportTest)とtest-unitは、ブロックでメソッドを表現できる。これは内部でブロック→メソッドとする処理のメソッドが、2つに存在しているため(ドキュメント確認済み)
- @imaharu 
　- assert_outputは、lsコマンドのテストをするときに使えそうですね 

### 3-1-6〜3-1-7(8分)
- @coe401_ 以前銀座Railsでfixtureを使用したテストについての発表がありましたが、自分で使った経験はRailsチュートリアルしかない…
  - [Rails Fixtures再考](https://speakerdeck.com/mstshiwasaki/rails-fixtureszai-kao)
- @sanfrecce-osaka c.f. [MinitestとRSpec、FixturesとFactoryGirlの良いところ悪いところをコードを書いて比較してみた](https://blog.jnito.com/entry/2015/05/06/074510)
- @sanfrecce-osaka fixture、最初は seed でそのまま使えて便利だけどバリデーションが走らないのでアプリケーションが大きくなってくると異常なデータがDBに入ってしまうケースが出てきて辛くなってきそう(@jnchito さんの記事にもたしか書いてあった気がしたけど気のせいかもしれない・・・:sweat_smile:)

- @Kyo18 factory_botの使い方に関してはパRails7章にかなりお世話になりました・・・！

- @masuyama13 teardown って「涙が流れる」って意味かと思ったら、「取り壊す」という意味だった😅
    - @igaiga 知らなかったー！

- @coe401_ RSpecだとcontextごとに`before do~end`を書けたりするけど、minitestでも分離したコンテキスト内で`setup` `teardown`することはできるのかな？
    - @sanfrecce-osaka minitest はあんまり構造化しない方針なので難しそう・・・
    - @coe401_ →コンテキストを書き分けたい場合は`test do~end`ブロック内にベタで設定を記述する

- @hogucc teardownの使いどころについてはRailsガイドにのっていました（コントローラーでcacheを使用している場合はcacheをクリアする）[Rails テスティングガイド - Railsガイド](https://railsguides.jp/testing.html#%E3%83%86%E3%82%B9%E3%83%88%E3%82%92%E3%81%BE%E3%81%A8%E3%82%81%E3%81%A6%E8%A1%8C%E3%81%86)
  - @imaharu 予想ですけど、setupで時間を固定した操作を戻すとかに使いそう？
      - @igaiga setupで時間を動かしたら、teardownで戻す、ってのはありそう
      - @igaiga 時間操作はブロックで書けるならブロックで書きたい派

### 3-1-8(6分)
- @chiroru プロセスとスレッドの違いについてよくわからず調べてみたところ、プロセスはOSの処理の実行単位で、スレッドは1プロセスから派生する単位。プロセスはリソースをコピーして使用する一方、スレッドは1プロセス内で1つのリソースを共有して使用する？
  - @imaharu 人に説明できるほどの理解してないので、いい資料あればを知っていれば誰か教えてほしい 
  - c.f. [【 ps 】コマンド――実行中のプロセスを一覧表示する](https://www.atmarkit.co.jp/ait/articles/1603/28/news022.html)

- @imaharu 「なお、並列テストを実行する際はデータベースも並列度に合わせて用意されます。MySQLなどではデータベーススキーマを複数用意し、SQLite3ではデータベースファイルそのものを複数用意することで並列実行時にデータの不整合が起きないようにしています。」
  - 一つのデータベースで、並列処理を行っても早くならないでしょ！と思っていたが、データベースを分けるなら納得

- @coe401_ デフォルトでテストの並列実行がサポートされているのはまだminitestだけなのですよね…
  - RSpecも今頑張っている最中っぽい https://github.com/rspec/rspec-rails/issues/2104

- @sanfrecce-osaka RSpec はまだサポートされていなかった希ガス(もうしおいさんが書いてた :sweat_smile:)
    - 現状は RSpec の場合は [parallel_tests](https://github.com/grosser/parallel_tests) という gem を使う

- @masuyama13 「データベーススキーマが複数」と「データベースファイルが複数」の違いがいまいちわからない
    - @sanfrecce-osaka ↓のような話だと思います〜 :+1: (推測も入っているので若干嘘がはいっているかも？)
        - SQLite3 はデータベースがファイル(e.g. development.sqlite3)なのでそちらが複数あれば並行するテストごとに DB ができる
        - SQLite3 以外の DB(e.g. MySQL) は schema.rb を元に DB を作成する
            - 並行テストの範囲では schema.rb は1つ
            - データベースファイルとの呼び分けの都合上「データベーススキーマ」という呼び方にしている

### 3-2-1〜3-2-3(15分+α)
#### 3-2-1

- @sanfrecce-osaka Rack の話とはズレるけど ActiveJob まわりもデザインパターンの Adapterパターン でインターフェース統一してますよね〜 :eyes: 
    - c.f. [アダプタ(Adapter) | Ruby デザインパターン](https://morizyun.github.io/ruby/design-pattern-adapter.html)

- ＠coe401_ Rackとは①サーバーとアプリケーションをつなぐプロトコル / ②①を実現するためのライブラリ
  - Rack対応サーバー <-（Rack）-> Rackアプリケーション(with Rackミドルウェア）

- @Kyo18 脱字の報告：P.130 4段落目「開発者にとってもより良い組み合わせを選択するとが」の部分「こ」が抜けてます！
    - @igaiga ありがとうございます！ 🙏

#### 3-2-2

##### Rackに必要なインターフェイス

- @imaharu シンプルなインターフェイスで、強力な効果を発揮するrackすごい ← @sanfrecce-osaka :wakaru:

- @coe401_ 「①サーバーとアプリケーションをつなぐプロトコル」のアプリケーション側のお約束ですね（`call`メソッドの実装、環境変数の注入、配列でレスポンスを表現）
  - @coe401_ ちなみにサーバー側のお約束は
    - リクエストが来た時、アプリケーションに対して`call`メソッドを呼ぶ
      - `call`メソッドを呼ぶとき、引数に環境変数を渡す
    - 起動用の`start`メソッドを実装する
    - サーバー自身とRackライブラリを接続する`Handler`モジュールを実装する

##### かんたんなRackアプリケーション

- @sanfrecce-osaka Rails にも config.ru がある

```ruby
# This file is used by Rack-based servers to start the application.

require_relative 'config/environment'

run Rails.application
```

#### 3-2-3

- @sanfrecce-osaka Rackミドルウェア使ったことないんですが、オススメのものはありますか？
    - c.f. https://github.com/rack/rack-contrib
  - @coe401_ 使った覚えがなくても実は使っているのがRackミドルウェア… ← @sanfrecce-osaka :naruhodo:
    - @coe401_ `$ rails middleware`
  - @igaiga Rails標準以外ではdeviseとかomniauthとかが有名Rackミドルウェアかもです
    - https://github.com/omniauth/omniauth/blob/master/omniauth.gemspec#L9

- @coe401_ 頑張って作った資料をご査収ください ← @sanfrecce-osaka :clap::clap::clap::clap::clap:
![](https://i.imgur.com/N4QYOo9.jpg)

    - ↑の出典元: [Rackミドルウェア入門のためのRackミドルウェア](https://speakerdeck.com/coe401_/rackmidoruuearu-men-falsetamefalserackmidoruuea)


- @imaharu method_override.rbがシンプルなので、勉強したい人にオススメ
    - https://github.com/rack/rack/blob/master/lib/rack/method_override.rb

### (3-2-4)
3-2-4は自分でRackミドルウェアを作ってみようという内容です。事前に手を動かしておくと理解が深まるかも
- @coe401_ 何て美しいアーキテクチャ…


## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @imaharu @cor401_ さんの解説がわかりやすくて神 ← @sanfrecce-osaka :sorena:

- @sanfrecce-osaka しおいさんに来てもらえて深い話を色々聞けて楽しかった〜 :raised_hands: 
    - くわしい人がいるのありがたい
    - さすがしおいさんという回だった :clap::clap::clap:

- @coe401_ 好きなことを喋り倒す機会を頂けて最高に楽しかったです（本当にこれで良かったのか）
    - @igaiga 次回もぜひ来てください
      - @coe401_ ぜひぜひ〜 ← @sanfrecce-osaka :raised_hands: 
- @hogucc Rackの話はまだ何がわからないかもわかっていない状態。実際に自分でミドルウェアを作れば動きが理解できるようになるのかな...
  - @coe401_ わたしもtdtdsさんという伝説的RubyistにRackミドルウェアを作ることをお勧めいただいて作った経験が今につながっています 
    - しおいさんのお話が聞けてよかったです！
    - @igaiga tdtdsさんは私がRubyを始めるきっかけになった方です
- @masuyama13 Rack って聞いたことはあっても全然イメージできなかったので、しおいさんのお話が聞けてよかった😄Rack = ミドルウェアかと思ってた
- @igaiga 自分が書いたところをみなさんに読んでいただくの、緊張しますね・・・
    - @sanfrecce-osaka テストの所、すごくわかりやすかったです〜 :raised_hands: 
    - @coe401_ さすが五十嵐さんというわかりやすさでした…！
    - @igaiga 🙌
- @Kyo18 なんとなく難しそう・・・で敬遠していたRackですが、今日のお話で一体何者なのかくらいは分かった気がします！ｗ @coe401_さんの資料を見てもっと理解していきたいです！