# 第2回 パRails輪読会ノート(2020-08-16)
###### tags: `パRails`
## 時間
予定：08:30〜10:30
実績：1-2 〜 1-3-4まで

## 概要
箇条書きでご記入ください。また現在は「疑問点・気づき」の1項目ですが、追加したい項目があればご自由に追加ください。
輪読会後、こちらのノート＋チャットは公開させていただくので、よろしくお願いいたします。

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
>  - フィヨルド生
    - 名前(@username + 呼び名)
    - 現在のプラクティス 
    - 一言
>  - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴
    - 一言

- @ima1zumi(今泉)
    - JSふりがな
    - よろしくお願いします！！

- @chiroru(ちろる)
  - オブジェクト指向設計(ボウリング・ls)
  - よろしくお願いします！

- @Kyo18（岸）
    - 自動テスト
    - 今日もなんとか起きれました❗


- @hogucc（おぐち）
    - lsコマンド作成（オブジェクト指向）
    - よろしくお願いします！


- @masuyama13 （マスヤマ）
    - オブジェクト指向プログラミング
    - オブジェクト指向楽しいけど難しい

- @universato(ユニ)
  - RailsのGitHub認証に入ったところです。
  - よろしくお願いします

- @igaiga（五十嵐）
    - Rails歴: 10年
    - 9/12とちぎRuby会議09（オンライン）で話しますのでみなさんよかったら来てください

- @haruguchi-yuma(ゆうま)
    - プラクティスはrailsの基本を知るに入りました。
    - よろしくお願いします。

- @sanfrecce-osaka (森塚)
    - Rails歴
        - 実務: 2年弱
        - 学習期間含める: 5年くらい
    - 今日も輪読会頑張るぞい！(ruby-jpに#ganbaruzoiというチャンネルがあるので興味があればぜひw)

- @imaharu
    - Rails歴
        - 実務: 1年
    - 起きれて嬉しい

## 疑問点・気づき

>### 書き込みサンプル
>- @アカウント名 Rails楽しい

### 1-2-1 CoC（ConventionoverConfiguration）

- @imaharu Railsの規約に従って実装されてる、他のライブラリを実務で利用した際、エラー文言がわかりにくく原因の追求に詰まったことがある。規約違反である旨と、その修正方法を伝える工夫がないと、辛いのかも。(ファイル名も規約だったと認識して書いてます)
    - @imaharu 多分、自動ロードファイルの話だから違うかも。
- @sanfrecce-osaka 以前Strutsとかやってたときはxmlで設定ファイルがいっぱいあった記憶・・・(この辺り Rails は本当に楽)
- @sanfrecce-osaka 逆に規約から外れているプロジェクトは辛い
- @haruguchi-yuma 規約を守らず作ってしまっても、ロジックがおかしくなければ動いてしまうのでしょうか？何か怒られる？
    - @sanfrecce-osaka わかりやすいのだとZeitwerkがわかりやすいかな〜
    - @sanfrecce-osaka ファイル名とクラス名が規約から外れているとファイルのロードがうまくいかないやつ
- @ima1zumi ×API ⭕Api? ← :+1: 

### 1-2-2 DRY

- @hogucc `rails s`したときにテーブルのカラム名のメソッドが自動で定義される仕組み？そういえば`rails s`したときにrailsが何しているか、あまり意識したことなかった...
    - @ima1zumi この辺？ ORマッパーわからない.. [Active Record の基礎 \- Railsガイド](https://railsguides.jp/active_record_basics.html#active-record%E3%81%AE%E3%83%A2%E3%83%87%E3%83%AB%E3%82%92%E4%BD%9C%E6%88%90%E3%81%99%E3%82%8B)
    - @igaiga ORマッパー： ObjectとRelation(=データベース)を結びつける道具。RailsだとORマッパーとしてActive Recordが使われる。

- @imaharu `情報の重複` というが肝。コードの重複ではない。

### 1-2-3・1-2-4
特になし
### 1-2-5 まとめ

- @ima1zumi Rails始めたての頃Railsのレールに乗るの大変だった（今もまだ分かっているとはいいがたい…）
- @sanfrecce-osaka Rails で開発するならレールに乗るの本当大事
- @imaharu 正直、Rails以外のWebフレームワークで開発したことがないので、真の意味で「レールに乗る」感覚を知らないかも

### 1-3-1
特になし
### 1-3-2
- @chiroru  .ruby-versionがすでにあった場合はどうなりますか？
  - @imaharu rails newした時のruby versionが書き出されると思います
    - ~/
        - .ruby_version(2.6.6)
    - ~/my_app
        - .ruby_version(2.6.5) # ここが、使われるはず
  - @chiroru →階層が違うので同時に存在することはない
- @chiroru railsのrubyバージョンを指定したいときは、gemfileで修正する？
  - @chiroru →gemfile & .ruby-versionの2つを修正する。この二つに差異があった場合、bundle installができない。
(rails s Your Ruby version is 2.7.1, but your Gemfile specified 2.6.5)


#### プロジェクトのファイル構成
- @sanfrecce-osaka `lib` はよく議論になるやつ(このあとコラムがあるから詳しくはそっちで)
- @imaharu プロダクションコードを確認すると、Rakeタスクは `lib/task/` にあった
- @imaharu RSpecだと、`test` -> `spec`
- @imaharu lsコマンドの`F`オプション知らなかった。

#### bin ディレクトリの内容を知る

- @ima1zumi `bundle exec` しなくても `bin/rails` で起動できる理由考えたことなかったので知れて良かった
- > このようなファイルを binstub と呼びます
    - @sanfrecce-osaka 恥ずかしながらここで初めて知った :eyes: (binstubという単語とかコマンドはたまに見ていたけど)
    - @hogucc 逆に`bundle exec`をつけたほうがいいシチュエーションってあるのかな...
    　　- @hogucc rspecやrubocopの実行ファイルがbinディレクトリになければ、bundle execをつける必要がある
- @sanfrecce-osaka `setup` コマンドをきちんと書いてあるプロジェクトは良いプロジェクト
    - bootcamp はもちろん書いてあります :+1: (さすが @komagata さん! :raised_hands: )

#### app ディレクトリ

- channelsやjobs、mailers
    - @imaharu 利用しないなら、`rails new`の時にファイル生成しないようにする

#### config ディレクトリ
特になし
#### db ディレクトリ

- > seeds.rbはアプリケーションを起動する際に必要となるマスターデータなどを投入するために利用するファイル
    - @ima1zumi ここでいう「アプリケーションを起動」は `production` ではなく `development` `test` 環境での起動のことかな？
    - @igaiga むしろ production で使うイメージでした
        - production(, development)で使うものにして欲しい
        - testで使われると「このテストデータどこでつかうの？」ってわからなくなるので、テストケースごとにテストデータをつくって欲しいという気持ちがあります
    - https://github.com/fjordllc/bootcamp/blob/master/db/seeds.rb

- seeds.rbはアプリケーションを起動するさいに必要となるマスターデータなどを投入するために利用するファイル
    - @imaharu 悲しいことに、STGのdumpデータ使ってます。
        - @sanfrecce-osaka メンテされてないこと結構ありますよね :cry: 
        - @igaiga どっかのDB　dumpデータつかう作戦もありですね（必要なものだけ抽出するのが大変だけど）
- @masuyama13 ステージング：本番に似せた環境。複数あることもある（会社によって意味が違うので注意！）

### 1-3-3
### COLUMN

- @hogucc もともとlibディレクトリに置いていた独立性の高いコードをどこに移動するか問題が発生しそう...
    - @igaiga わかる。とりあえずapp/libへ移動（対処療法なのであんまり良い方法ではない）とか。
    - @imaharu gemにしましょう ← @sanfrecce-osaka :crab: 
- @sanfrecce-osaka lib/tasks は例外かな？(もう上で話した)

### 1-3-4

- @sanfrecce-osaka `dbconsole` 知らなかった
- @imaharu `dbconsole` DBクライアント使ってる(sequel pro)
- @ima1zumi `rails c` で作ったデータがDBに保存されることしばらく知らなかった 
- @ima1zumi 保存したくない場合は`rails c -s` でしたっけ
    - そうです。たぶん、トランザクション貼ってるのかな？
    - @sanfrecce-osaka ↑たしかそうですねー(ロールバックされるので)
- @sanfrecce-osaka `rails c --sandbox 便利(既に上で書かれてた)
- @Kyo18 `rails routes | grep hoge`を使うようになって大量の出力の中から目的のルートを探す作業から開放されました・・・
    - @ima1zumi いつもブラウザ(http://localhost:3000/rails/info/routes)から見てました...grepすればよかったんですね...!! ありがとうございます
    - @imaharu ブラウザからの方が、楽そう。自分は、config/routesを直で見てます
    - @igaiga ブラウザから見る派です
    - @sanfrecce-osaka RubyMineのプラグインで見てます
        - https://qiita.com/Avene/items/756c17f87d28d2ee47a4#%E3%81%93%E3%82%8C%E3%81%A0%E3%81%91%E3%81%AF%E5%A4%96%E3%81%9B%E3%81%AA%E3%81%84%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3railways
- @ima1zumi `bin/rails s -h` で表示されている `bin/rails s --daemon` の `daemon` とはなんですか？
    - @igaiga 「バックグラウンドで動きつづけるプログラム」のことをdaemonと言います
        - https://ja.wikipedia.org/wiki/%E3%83%87%E3%83%BC%E3%83%A2%E3%83%B3_(%E3%82%BD%E3%83%95%E3%83%88%E3%82%A6%E3%82%A7%E3%82%A2)
        - --daemonオプションをつけて起動するとshellに処理がすぐ戻ってきて裏で動きつづきます(ps auxコマンドで確認できます)
    - @sanfrecce-osaka (「悪魔」の方のデーモンとは別) ←@Kyo18 昔メールが送れなかった時の`Mailer Daemon`で「メールの悪魔とは？」となってました😂
    - @imaharu Unixコマンドの `bg` や `&` で実行したコマンドもデーモンと呼びますか？
        - @igaiga うーん、わからない
- @imaharu `stats` 知らんなんだ
- @sanfrecce-osaka db:create の 「SQLite3 の場合は不要」 は間違い？(db:create で development.sqlite3 とかが作られなかったでしたっけ？ :thinking_face:)
    - @igaiga SQLite3 は db:migrate で create もされるかも？
- @sanfrecce-osaka `rails runner` は研修で千葉さんが使ってるのを見て知ったなぁ
    - @ima1zumi `rails runner` 使うとRailsに守られてるのでRakeより書きやすい
- @hogucc Rakeタスクじゃなくて、個別のコマンドで単体のスクリプトを用意したくなるときってどういうときだろう？単純な動作確認するときとか？
    - @hogucc `rails runner`でタスクを書いてRakeからそれを呼ぶことも多い。上でima1zumiさんが書かれているとおり、単体のスクリプトで書いてrunnerで実行するほうがRailsの記法でかけるため作りやすい。
- @sanfrecce-osaka `db:setup` と `db:reset` の挙動はどっちがどっちかちょくちょく忘れる


## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします

- @sanfrecce_osaka HackMDは事前に共有しておけばよかったですね(自分も失念してました :innocent:)
  - @chiroru 先週の勉強会後にslackで共有して以降そのままでした・・直前にも再度共有いたします！


- @imaharu 実は、予習してHackMDに先に書いてもらった方が、気になる人が調べる余裕ができて質の高い回答を得られるのでは？
    - @sanfrecce-osaka 予習をMUSTにしちゃうと参加の障壁が上がりそうなのでMUSTにはしていない状況です :pray: (でも予習した方が質問等の質が上がるのはおっしゃるとおりです :bow:) ← :+1:

- @chiroru ↑私も質問してみて(自分は)予習の必要性を感じました。今日はざっくり読んで行ってみたのですが、自分の中で曖昧な部分とわからない部分が混同してしまった気がする。次回に活かす。

- @imaharu 感想と疑問は、分けた方が良さそう。感想は、発表しなくていい。 ← @sanfrecce-osaka :crab:
    - @imaharu 自分が感想書きすぎ説はある。 
    
- @haruguchi-yuma 先週ぐらいからRailsのプラクティスに入って、初めてnewしたときに、なんでこんなにいっぱいディレクトリあるんだー！と焦っていたのですが、大きく捉えることで理解できました。その上で、今日の学習で今まで気にしていなかった、lib/とかbin/の中身のこととか知れてよかったです。個人的には予習していってよかったと思います。

- @universato 参加出来てよかったです。

- @hogucc HackMDにも黙読でどこまで読みすすめるかを「--ここまで--」と明記いただいていたのでわかりやすかったです。

- @masuyama13 rails new したときに作られるファイル群について、よく使うところはわかってきたがあまり触らない部分は知らないことがたくさんあった

- @sanfrecce-osaka `rails runner` と `rake` の知見を得られたのは大きな収穫でした :raised_hands:

- @sanfrecce-osaka みんな慣れてきて前回よりも進行がスムーズになったイメージがあります〜 :grin:

- @Kyo18 Railsのプラクティスを終えた後でも全然知らないことが大量にあるので、パRaisで幅広く学べるのはありがたい。HackMDの重さは人によって違うんだろうか？

- @ima1zumi rails runner など、他の方の一言から広がって学べることが多くて勉強になりました
- @ima1zumi 司会難しい
- @ima1zumi 2時間どうでしたか？
    - ちょうどよかったっぽい
