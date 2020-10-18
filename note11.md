# 【第11回】パRails輪読会ノート(2020-10-18)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
司会・タイマー
司会： @chiroru
タイマー： @masuyama
順番 @kyo → @masuyama → @chiroru → @ima1zumi
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
    - 今日のテーマ(日々の運動何をしていますか？)
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ(日々の運動何をしていますか？)

### @ima1zumi（いまいずみ）
- スクラム開発、自作サービス、就職活動
    - 自分の就活の軸ってなんだろう.. :thinking_face: ということをずっと考えている
- 今日のテーマ
    - Youtubeでヨガを見てます
    - リングフィットアドベンチャー
    - 散歩
- 自己紹介の形式間違えました :pray: 


### @Kyo18 (岸)
- スクラム開発/ペーパープロトタイプ/就職活動
    - ペーパープロトタイプもOKをもらい、いよいよ開発に取り掛かります！
- ポモドーロテクニックの合間に腹筋ローラーやってます


### @imaharu 
- Rails歴/プラクティス
    - 1.5年
- プラクティス
    - unicornのドキュメントを読む
- 今日のテーマ
    - 腹筋30回
    - ランニング
    - 会社に出社する

### @igaiga
- Rails歴 10年
- プラクティス 登壇資料づくり
- ランニング、最近自転車を直して乗り始めました

### @uda (うだ)
- Railsのdevise機能
- 散歩、通勤



### @masuyama13 
- アジャイル開発/スクラムを理解する
- 運動を何もしなかった結果、散歩で気分が悪くなりました（何かやらねば…）


### @chiroru (ちろる)
- Vue CLI(メモアプリ)
- ごく稀にウォーキング・ラジオ体操
    - 良さそう:+1: 

### @sanfrecce-osaka(もりつか)
- Rails歴
    - 実務2年前後
    - 学習期間含めると5年弱
- プラクティス
    - Cypress 触る
        - 手動テストがﾂﾗｲﾉﾃﾞｽ
- 今日のテーマ(日々の運動何をしていますか？)
    - ｻｲｷﾝﾅﾆﾓﾃﾞｷﾃﾅｲ :innocent: 
        - その影響でいよいよ腰痛ががががががが
    - 強いて言えばラジオ体操第1第2
    - 以前はバーピーとかビリーズブートキャンプとかやってた
    - そろそろジムいきたい・・・
        - ただマスクしながらというのは気が進まない・・・

### @hogucc（おぐち）
- システム開発、自作サービス案作成
- リングフィット（最近さぼり気味...）

## 疑問点・気づき
>### 書き込みサンプル
>@アカウント名 Rails楽しい

### 4-1-1〜4-1-2 (10分)

- @sanfrecce-osaka フロント界隈からは受けが非常に悪い webpacker さん
    - ↑webpack とは別に webpacker の設定・カスタマイズ方法も覚える必要があるため
    - c.f. [Webpackerを導入してから外すまでをふりかえる](https://tech.misoca.jp/entry/2019/02/22/110000)
- @sanfrecce-osaka javascript_pack_tag にはエントリーポイントの文字列を渡す
- @sanfrecce-osaka yarn.lock は yarn における Gemfile.lock
- @chiroru エントリーポイント
>エントリーポイントとは、アプリケーションの中で一番最初に呼び出される部分のことです。
まずHTMLが読み込まれ、次にHTMLの中に書かれているscript要素で指定したJavaScriptファイルが読み込まれます。

(https://jsprimer.net/use-case/todoapp/entrypoint/)

- @ima1zumi エントリーポイントはプログラム一般用語なので、覚えておくとよさそう
    - 実行を開始する行 / 一番最初に呼び出される部分
    - [エントリーポイント \- Wikipedia](https://ja.wikipedia.org/wiki/%E3%82%A8%E3%83%B3%E3%83%88%E3%83%AA%E3%83%BC%E3%83%9D%E3%82%A4%E3%83%B3%E3%83%88)


- @hogucc webpackerがデフォルトになったからRails6ではjavascriptフォルダがapp/assets/配下ではなくapp配下になったのか、知らなかった...
- @hogucc webpackerとsprocketsのどちらを使うか、はたまた併用するのかは意見が分かれそう...
  - [コラム - Ruby on Rails 海外事情コラム | 第57回　なぜRails 6にはWebpackerとSprocketsの両方が含まれているのでしょうか？｜CTC教育サービス 研修/トレーニング](https://www.school.ctc-g.co.jp/ruby/columns/trans/trans57.html)

- @ima1zumi bootcamp の `app/javascript/packs/application.js` がエントリーポイントになっていると知らなかったので勉強になった！
    - https://github.com/fjordllc/bootcamp/blob/master/app/javascript/packs/application.js
    - @Kyo18 bootcampアプリを見ると`app/assets/javascripts/application.js`がコメントアウトされて残ってますね
    - たしかこれ設定ファイル独特の書き方で、コメントアウトじゃなかったような気がします（うろおぼえ） ←知らなかった！
        - [アセットパイプライン \- Railsガイド](https://railsguides.jp/asset_pipeline.html#%E3%83%9E%E3%83%8B%E3%83%95%E3%82%A7%E3%82%B9%E3%83%88%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%A8%E3%83%87%E3%82%A3%E3%83%AC%E3%82%AF%E3%83%86%E3%82%A3%E3%83%96) で 「//=」で検索するとよさそう ← :pray: 
- @chiroru `require("@rails/ujs").start()`は何をしているの？
  - `app/javascript/packs/application.js`の先頭に入れるもの
  -  CSRFセキュリティーエラーを起こさないために重要・・？
### 4-1-3〜4-1-4 (12分+α)

- @sanfrecce-osaka toWebpackConfig の実装
    - @rails/webpacker/package/environments/base.js
    - ちなみに yarn でインストールしたライブラリ群は node_modules 配下にある
- @sanfrecce-osaka loader とは(すごくざっくりした説明だけど)
    - c.f. https://reffect.co.jp/html/webpack-loader-setting-for-beginner#webpackLoader
- @sanfrecce-osaka 画像だけ path に media をつけないといけない話、初見者殺しだ :sweat_smile: 

- @ima1zumi `bin/webpack-dev-server` は bootcamp 開発でお世話になりました！
    - 開発中に View, Vue.js など更新すると全ファイルにビルドがかかって重かった
        - リロードに18秒くらいかかっていた
    - `bin/webpack-dev-server` を使うとリロードが3秒くらいに短縮された
        - 1つのファイルに書く量を少なくしておくといいのか @imaharu  

### 4-1-5〜4-1-6 (9分)

- @sanfrecce-osaka webpacker:install でサクッと導入できるのは便利 :+1: 
    - フロントに疎い人からすると助かるやつー :grin: 
- @sanfrecce-osaka rails-erb-loader 初めて知った :eyes: 
- @sanfrecce-osaka bootstrap は jQuery 依存があるから Sprockets で使ってたときと違って css と js で両方設定しておかないといけなかった記憶・・・(jQueryのとこを見ながら)
- @sanfrecce-osaka loader の設定のかんたんな説明(口頭で)

### 4-2-1〜4-2-2 (13分)

- @sanfrecce-osaka リソースごとの scss、かなりの確率でジェネレータでオフられるやつ :sweat_smile: 
- @sanfrecce-osaka Source Map の説明
    - https://developer.mozilla.org/ja/docs/Tools/Debugger/How_to/Use_a_source_map#:~:text=%E3%82%BD%E3%83%BC%E3%82%B9%E3%83%9E%E3%83%83%E3%83%97%20%E3%81%AF%E5%A4%89%E6%8F%9B%E5%BE%8C,%E6%8C%87%E3%81%97%E7%A4%BA%E3%81%99%E3%82%B3%E3%83%A1%E3%83%B3%E3%83%88%E3%82%92%E5%90%AB%E3%82%81%E3%81%BE%E3%81%99%E3%80%82
- @sanfrecce-osaka stylesheet_link_tag はレスポンシブデザインが主流の今ではあんまり使われてないのかな？ :thinking_face: 
    - フォントなどの読み込みにも使われてそう？ https://github.com/fjordllc/bootcamp/blob/master/app/views/layouts/application.html.slim
- @sanfrecce-osaka Sass には SCSS 記法と SASS 記法 がある
    - @machida さんの推しは SASS記法(という感じの話を以前聞いた記憶がうっすらと)
    - c.f. [【ズボンを脱ごう】SassのSASS記法の魅力【カッコイイ】](https://ken-c-lo.hatenadiary.org/entry/20121220/1355948089)
    - 現場では SCSS 記法の方が多い印象
- @imaharu 「単にassets:precompileを実行した場合、静的なCSSファイルは生成されますが、縮小化などは行われず、SourceMapの宣言が生成されないという不完全な状態になってしまいます。」
    - `config.assets.css_compressor` で、変更できるのかな？

- @Kyo18 誤字報告：「Sprocketsのビルドを確認する」の節の3段落目のファイル名が「applicatino.css」となっています！
    - @igaiga ありがとうございます！ 😃

### 4-3-1 (6分)

- @sanfrecce-osaka form_with のデフォルトが Ajax 通信なの、昔ハマったなぁ
- @sanfrecce-osaka xhr => XMLHttpRequest の略
    - c.f. https://developer.mozilla.org/ja/docs/Web/API/XMLHttpRequest

- @Kyo18 localを指定しないとAjax通信となる❓

- @imaharu submitが再度押せるようになるのは、どのタイミングなんだろ？レスポンスが返ってきてから？

### 4-3-2 (6分)

- > onload や DOMContentLoaded が発火しない
    - @sanfrecce-osaka この挙動が原因で初心者がことごとく外すことで有名な turbolinks さん :sweat_smile: 
    - @sanfrecce-osaka とはいえパーフェクト Rails の説明読んでわかればそんなに怖くないということを理解 :raised_hands: 
- @sanfrecce-osaka 【誤字】 リスト4.17 の後の 「remote: を使って」
    - おそらく form_for の頃のままになっている気がします :eyes: 
    - @igaiga ありがとうございます！
- > POST メソッドで Ajax リクエストした結果がリダイレクトの場合は想定通りに画面遷移を行います
    - @sanfrecce-osaka これが @igaiga さんの言っていた挙動ですね :eyes: 
- @imaharu 「そのため、アプリケーションの状態をwindowオブジェクトなどグローバルなオブジェクトに保存し、画面遷移で初期化されることを前提としたコードは書かないように気をつけた方が良いでしょう」
    - 本当に辛いので、辞めましょう。時々、View触るときにグローバルなオブジェクトが定義されていて、暗い気持ちになる。

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka フロントエンジニアもどきなりに知見共有がんばれた :raised_hands: 
- @sanfrecce-osaka 来週は Stimulus の話があるので使った経験のある @oba さんに来てもらうと面白そう :grin: 

- @imaharu 今までざっくりとした知識がなかったが、基礎知識は網羅できたっぽいのでよかった

- @ima1zumi フロントエンド知らないことがめちゃくちゃ多い...!と痛感

- @ima1zumi Rails と JS は共存するのが大変そうだと思った。他のWebフレームワークではどう共存しているのかすこし気になった
    - @igaiga Laravel Mixを調べてみると、Railsよりもうまくやってる印象があるので面白いかもです

- @hogucc フロントエンドってこんなにたくさんの仕組みで動いているんだなとわかった...奥が深い

- @uda webpacker、名前聞いたことある程度だったのが色々とわかった。使うか使わないかの判断も難しそう。

- @masuyama13 あまり触ったことがないものが多く難しかったが、Rails でフロントエンドも開発しやすくなっていることを知った。ハマりポイントを教えてもらえてよかった

- @chiroru railsでフロントエンドの辺りをしっかり見たことがなかったなぁと読みながら感じました。

- @Kyo18 フロント難しいいい❗
- @Kyo18 スクラム開発でVue.jsのIssueをアサインしてもらっているので、`bin/webpack-dev-server`は知れてよかったです！ :+1: ← @sanfrecce-osaka :iihanashida:

- @sanfrecce-osaka (本編での書き忘れ) Webpacker の類似ライブラリとして cookpad さんが作った simpacker というやつがあります
    - c.f. https://github.com/hokaccha/simpacker
    - c.f. [Simpacker: Rails と webpack をもっとシンプルにインテグレーションしたいのです](https://techlife.cookpad.com/entry/2019/07/08/100000)