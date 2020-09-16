# 第6回 パRails輪読会ノート(2020-09-13)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 2-2-5〜2-3-5

司会・タイマー
- 司会： @ima1zumi
- タイマー： @masuyama
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
    - 一言
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/現在のプラクティス
    - 一言

- @hogucc（おぐち）
    - npmの作成
    - npmの案出しが難しい...

- @Kyo18 (岸)
    - JSのクラス
    - RubyMineを使いこなしたい今日このごろ。
        - @sanfrecce-osaka :sunglasses: :+1: 


- @mashiosano (さの)
  - オブジェクト指向、JS
  - オブジェクト指向難しい...

- @chiroru(ちろる)
  - JS(非同期処理)
  - JS慣れない難しい・・ 

- @haruguchi-yuma(はるぐち)
    - Railsのページング処理
    - 貯金生活をはじめました。（昨日から）

- @ima1zumi(いまいずみ)
    - Vue.jsの基礎
    - そろそろスクラム！
    - 自作サービスどうしようか悩み中

- @masuyama13 (マスヤマ)
    - npm(JavaScript)
    - プラクティス進まない…

- @sanfrecce-osaka(もりつか)
- Rails歴
    - 実務2年前後
    - 学習期間含めると5年弱
- プラクティス: 来週金曜のドリンクアップの準備
- 昨日、ボウリングのスコア計算プログラムオブジェクト指向版ができた
    - https://bootcamp.fjord.jp/products/5052
    - Rubyキメられてひとまず満足
        - @ima1zumi :+1: 


- @igaiga
  - プラクティス: 会社の登記上の引越しをしています
  - 角谷トークがとてもよかった

- @e6i24v(あだち)
- プラクティス：Nginx
- もう少しでRuby

## 疑問点・気づき
>### 書き込みサンプル
>@アカウント名 Rails楽しい

### 2-2-5(12分)

- @sanfrecce-osaka enum を定義しただけで色々メソッドが生えるのは本当にRailsっぽい挙動だなぁ(感想)
- @sanfrecce-osaka 「!」付きは例外発生させるのではなくて値の更新(メモ)
- @sanfrecce-osaka カラム名_before_type_cast は知らなかった :eyes: 

- @chiroru `attributes_before_type_cast`というメソッドもあるんですね〜
  -  https://api.rubyonrails.org/classes/ActiveRecord/AttributeMethods/BeforeTypeCast.html

- @chiroru Enum便利そう！でも使われてるのみたことがないかも🤔
    - @sanfrecce-osaka bootcamp でいくつか使われている箇所があるのでご参考までに〜 :+1: ←👀✨
        - c.f. https://github.com/fjordllc/bootcamp/search?q=enum&unscoped_q=enum
        

- @mashiosano ブートキャンプのユーザーモデル
  - https://github.com/fjordllc/bootcamp/blob/master/app/models/user.rb
  - _prefix: true をつけることで同じ値を持つ複数のenumを定義できる ← @sanfrecce-osaka :eyes: 
  - https://qiita.com/emacs_hhkb/items/fce19f443e5770ad2e13

### 2-3-1(8分)

- @sanfrecce-osaka ジェネレータで sass の生成とかはオフることが多いかなぁ
    - c.f. https://railsguides.jp/generators.html#%E3%83%AF%E3%83%BC%E3%82%AF%E3%83%95%E3%83%AD%E3%83%BC%E3%82%92%E3%82%AB%E3%82%B9%E3%82%BF%E3%83%9E%E3%82%A4%E3%82%BA%E3%81%99%E3%82%8B
- @sanfrecce-osaka 【参考】 Controller 関連の gem は action-pack
- @sanfrecce-osaka ここにはないけど redirect_to に関して、研修のメンターをしていた際に MPA の View から API にリクエストされた際に redirect_to を使ってハマったことがある

- @hogucc generateするときにJSON関連のコードを生成しないようにする方法を調べたら伊藤さんの記事が出てきました
  - [Scaffold作成時にJSON関連のコードを生成しないようにする - Qiita](https://qiita.com/jnchito/items/ec070f7551c983cc5b60)

- @mashiosano routes.rbのコードの量が増えた場合、ファイルを分割することもあるのかな?
    - @igaiga やるときもあります。1ファイルで管理しつづけることもあります。
    - @igaiga Rails6.1で公式に分割して書く書式が導入予定です
        - 参考: https://speakerdeck.com/willnet/rails6-dot-1dexin-sikuru-ruji-neng-nituite?slide=12

- @Kyo18 generatorって結構細かくカスタマイズできるんだ・・・。逐一skipオプションを付けなきゃいけないと思ってた。

### 2-3-2(12分)

- @sanfrecce-osaka set_* は好みがわかれるやつ(既出の話題かも・・・😅 )
- @sanfrecce-osaka コールバックにはブロックじゃなくて lambda(``->() {...}``) を渡すことも多い(短く書けるので)
    - lambda は ブロックをオブジェクト化したもの
- @sanfrecce-osaka セキュリティまでしっかり面倒見てくれるのは本当にありがたいな〜
- @sanfrecce-osaka arround_* では yield で action 本体の処理を呼び出している
    - @sanfrecce-osaka yield はブロックを実行するメソッド

- @ima1zumi `before_action` にブロック渡せるんだ!と思った
- @ima1zumi (メモ) CSRFの細かい説明：
    - [Rails セキュリティガイド \- Railsガイド](https://railsguides.jp/security.html#%E3%82%AF%E3%83%AD%E3%82%B9%E3%82%B5%E3%82%A4%E3%83%88%E3%83%AA%E3%82%AF%E3%82%A8%E3%82%B9%E3%83%88%E3%83%95%E3%82%A9%E3%83%BC%E3%82%B8%E3%82%A7%E3%83%AA-csrf)
    - [IPA ISEC　セキュア・プログラミング講座：Webアプリケーション編　第4章 セッション対策：リクエスト強要（CSRF）対策](https://www.ipa.go.jp/security/awareness/vendor/programmingv2/contents/301.html)
    - GET:GETで削除できるような実装はまずい ← @sanfrecce-osaka :naruhodo: :eyes: 
    - POST:jsonでやりとりするようなHTMLを介さない場合はCSRF対策を外さないといけない. HTMLでのやりとりではCSRF対策外しちゃダメなことに気をつける
    - @igaiga CSRFのざっくりした説明 https://esa-pages.io/p/sharing/4060/posts/2045/2b92833867f4151cf181.html
- @sanfrecce-osaka (@igaiga さんの話を受けて)フロントが React とか Vue とかでかつ SPA (Rails側は API) だとフォームヘルパーが使えないので CSRF 対策自前でやらないといけないのつらたん😭

### 2-3-3(10分)

- @sanfrecce-osaka member と collection 初めて知った、知見だ :eyes: 
- @sanfrecce-osaka resource の挙動そうなるのか、なるほどなぁ :eyes: 
    - index が生成されない(ノート)
    - show・edit・update・destroy は id を必要としない(ノート)
    - コントローラ名は単数にならないのか :eyes: 

- @Kyo18 この輪読会でブックマークに`rails/info/routes`を登録するルートの確認方法を知ってめちゃくちゃ快適になりました！
  - @ima1zumi :iihanashi: :+1: 

- @haruguchi-yuma ルーティングの情報はブラウザ（`rails/info/routes`）でみるか、`bin/rails routes`でみるかどちらで見ることが多いですか？

- @ima1zumi `member` は `user/1/following` みたいなルーティングを作ったときに使ったなぁ（感想）


### 2-3-4(8分)

- @sanfrecce-osaka 404 や 500 等の場合の例外ページをカスタマイズしたい場合は public/ステータスコード.html を編集する
- @sanfrecce-osaka Rails の例外設計については伊藤さんの記事がオススメです〜 :grin: 
    - [Railsアプリケーションにおけるエラー処理（例外設計）の考え方](https://qiita.com/jnchito/items/3ef95ea144ed15df3637)
    - @sanfrecce-osaka 握りつぶしダメ、絶対 :angry: 


- @ima1zumi 例外が発生したら対応するステータスコードを返してることをあんまり意識してなかったので気づけてよかった
- 例外は rescue したい
    - なんでも500 Errorになっちゃうので
- 上げた例外はlogに書き出すとか、Slackに通知するとかダイイングメッセージは残したい
    - ダイイングメッセージを残した上で4xx, 5xxのエラーにするのは仕方ない
- 例外をrescueしてるのに何事もなかったかのように正常系に乗せるのはダメ


### 2-3-5(8分)

- @sanfrecce-osaka require なしで permit だけでも OK
    - c.f. https://railsguides.jp/action_controller_overview.html#strong-parameters
    - キー無しで平坦な構造で params を受け取りたい場合に

- @ima1zumi `id` などそもそも書き換えできてはいけないものを StrongParameter で許可するのって危険ですよね..? (うろ覚え)
    - @igaiga idを書き換えると、mass assignmentで他人の情報を更新できてしまうケースにほぼなってしまうので、危険なことが多いと思います。
        - 「情報更新するときは、操作ユーザーの書き換えて良い情報だけをStrongParameterで許可する」「許可の無い情報（他人の情報とか、権限昇格とか）はStrongParameterで許可しない」

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！
>

- @ima1zumi 自己紹介書く時間5分は長いかな？
- @sanfrecce-osaka ima1zumi さんに若干のタイムラグがあった？(タイマー終了のタイミング)
    - @sanfrecce-osaka タイマーは音を鳴らすといい？(ミュートとの兼ね合いどうするか :thinking_face:)
    - 音って出せるんですか？(あ、マイクオンにして出せばいいのか？)
    - @ima1zumi タイマーについて、HackMDの画面見てて忘れてましたすみません mm
    - PC内の音は出すのめんどくさいですね
- @sanfrecce-osaka @igaiga さんの補足が毎回すごく勉強になります :smile_cat: 
- @hogucc route.rbのresourceの定義やCSRFの話など、Railsに備わっている機能で知らなかったところが結構あるなと思いました。

- @Kyo18 igaigaさんのCSRFのお話がとてもわかり易く、他の攻撃方法への対策も知りたくなりました！

- @mashiosano igaigaさんのCSRFのお話がとてもわかりやすかったです! 

- @masuyama13 ルーティングのmemberやcollection全然わかってなかった。自分の声が @ima1zumi さんに届いてなかった気がする😓
- @ima1zumi 聞こえてなかったです申し訳ない...

- @chiroru CSRF、自分で読んだときはサーっと読んでこんなのがあるんだ程度だったのですが、igaigaさんの解説がとてもわかりやすくて勉強になりました！

- @haruguchi-yuma CSRFの話がわかりやすかったです。セキュリティの話は難しくて、なんとなくの理解しかしていなかったので、今回の話でイメージ湧きました。

- @ima1zumi CSRF, 例外の話とても勉強になりました! 自分でも説明できるように理解したいなと思いました。