# 【第7回】パRails輪読会ノート(2020-09-20)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 2-4-1〜2-5-4

司会・タイマー
- 司会： @kyo
- タイマー： @chiroru
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
    - 今日のテーマ: コロナが落ち着いたら行きたい場所は？
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/現在のプラクティス
    - 今日のテーマ: コロナが落ち着いたら行きたい場所は？

- @Kyo18 (岸)
    - npmの作成
    - 高校時代の友人と沖縄に修学旅行リベンジに行きたい！

- @sanfrecce-osaka(もりつか)
    - Rails歴
        - 実務2年前後
        - 学習期間含めると5年弱
    - プラクティス
        - 家事
    - コロナが落ち着いたら行きたい場所
        - 地元
        - コミュニティ開催場所(福岡とか)

- @masuyama13 (マスヤマ)
    - プラクティス：JavaScript非同期処理
    - 行きたい場所：ハワイ
    - （途中少し抜けるかもしれません）

- @igaiga
    - プラクティス: オフィスを引っ越しするための書類を取得するミッション
    - 行きたい場所: フィンランド(EuRuKo行きたい)

- @chiroru(ちろる)
  - プラクティス：JS(クラス)
  - 行きたい場所：ベラルーシ

- @ima1zumi
  - プラクティス：VueCLI
  - 行きたい場所：長野県松本市

## 疑問点・気づき
>### 書き込みサンプル
>@アカウント名 Rails楽しい

### 2-4-1(7分)

- @sanfrecce-osaka html だけなら *.erb でもいけるんだっけ？
    - 答えでなさそうなので調べておく

### 2-4-2(8分)

- @ima1zumi UserAgents は廃止され、代替の User Agent Client Hints になる予定。
    - [Google Chrome、ユーザーエージェントを廃止する計画を発表 \| マイナビニュース](https://news.mynavi.jp/article/20200117-955292/)
    - [最新のユーザーエージェント対応はどうするべきか？ \- ICS MEDIA](https://ics.media/entry/200729/)
- @sanfrecce-osaka 確認画面 とか variants を使うといい感じに出し分けられる？(コントローラを分けない方針で行く場合)
    - variants 自体が最近あんまり使われていないので今後のことを考えると使わないほうがいいかも
    - vatiants の仕様次第ではそもそもダメかも
- @sanfrecce-osaka variants を使った実例
    - https://github.com/annict/annict/blob/master/app/views/accounts/show.html%2Bmobile.slim
    - https://github.com/annict/annict/blob/ed3bcf02d00c011bde52e0f5da4e0ceba5a0f7ce/app/controllers/concerns/view_selector.rb#L13
    - https://github.com/annict/annict/blob/ed3bcf02d00c011bde52e0f5da4e0ceba5a0f7ce/app/controllers/concerns/controller_common.rb#L20
- メモ
    - variants は Rails4.1 から入った
    - 昔は gem で variants 相当の機能を扱っていた
    - 最近はレスポンシブで1つのファイルでデバイスごとにデザインを切り替えるのが主流なのであんまり使われていない感

### 2-5-1(12分)

- @igaiga 2-5 の1行目の「前節し解説した」は「前節で解説した」の誤字です
    - 誤字があったら正誤表に載せるので教えてもらえたら嬉しいです ← @sanfrecce-osaka :man-gesturing-ok: 
- @sanfrecce-osaka Qiita とかで Controller で helper を使う方法がのっているけどあれは Rails Way ではないので安易に使うのはやめたほうが良い(と思っている)
    - @sanfrecce-osaka helper は View Helper で View 用の機能なので
    - @ima1zumi Controller で同様の機能を使うなら Concern ですかね？
    - @masuyama13 ビュー以外で使わない方がいいと知らなかった
    - @igaiga どこからアクセスしないと行けないということを考えるのが大事
- @sanfrecce-osaka helper は名前空間がグローバルなので命名かぶりには気をつけておく必要がある
- @sanfrecce-osaka rails routes の際に create や update、destroy に prefix がないのは index や show と URI が同じため
- @sanfrecce-osaka lint_to とか form_with でポリモーフィックパスが利用できるのは内部で url_for を使用しているため
- @sanfrecce-osaka webpacker を使うなら *_pack_tag、sprockets を使うなら *_link_tag

- @Kyo18 console上でappオブジェクトを経由してURLを取得できるのは知らなかった。 ← @sanfreccee-osaka 同じく :eyes: 
- @chiroru (あまり使い道が思い浮かばないのですが)`number_with_delimiter`の区切り文字の位置を調整することはできるのでしょうか🤔
- https://api.rubyonrails.org/classes/ActionView/Helpers/NumberHelper.html#method-i-number_with_delimiter
- @igaiga ⬆️でOKで、もし電話番号であれば専用の number_to_phone ってのもあるんですねー
    - https://api.rubyonrails.org/classes/ActionView/Helpers/NumberHelper.html#method-i-number_to_phone

```ruby
number_to_currency, # 通貨単位
number_to_human, # 百、千、万みたいな区切り
number_to_human_size, # バイト数の区切り B KB MB GB...
number_to_percentage, # %
number_to_phone, # 電話番号の区切り
number_with_delimiter, # ,区切りなど
number_with_precision # 小数切り上げ, 切り下げ, 四捨五入
```

が用意されているみたいですね。便利！ ← @sanfrecce-osaka 知らなかった、知見！ :raised_hands: 

### 2-5-2(5分)
- @ima1zumi markdown など部分的にHTMLを受け付けたいときはどうするんだろうと思った。何かしらの gem を使う？
    - https://github.com/vmg/redcarpet
    - bootcamp は rm redcarpet というコミットがあったので使うのをやめてそう
    - https://github.com/fjordllc/bootcamp/commit/1582c4122b01d94ec7f3fa2f866d9052e36ad35a
    - Vue.jsで制御していた
    - https://github.com/markdown-it/markdown-it
- @igaiga XSSはもっとも危険な攻撃の種類の1つなので、気をつけていきましょう

- @chiroru simple_formatとrawの違い
  - https://railsdoc.com/page/simple_format
  - https://qiita.com/kamesennin/items/8b01e86491297347394b
  - https://api.rubyonrails.org/classes/ActionView/Helpers/TextHelper.html#method-i-simple_format
      - @igaiga simple_format メソッドは複数行のテキストをpとbrで加工して出力するメソッドで、sanitizeオプションtrue/falseでテキスト中のタグを外す/外さないを制御できます←📝🙏✨

### 2-5-3(7分)

- @masuyama13 ERB、Haml、Slim の利用割合が気になる
- @sanfrecce-osaka 個人的には haml くらいが好きかなぁ :thinking_face: 
    - slim の省略具合は結構好き嫌い分かれる感
- @sanfrecce-osaka erb・slim・hamlにはそれぞれに変換するgemがある
    - e.g. erb2haml
- @sanfrecce-osaka ジェネレータや rails コマンドとして rake タスクを提供している Gem を読むときは railtie や enigine を意識するとどこに何が書いてあるか探しやすい
    - 自分で Gem 作るときも同様
    - c.f. https://railsguides.jp/plugins.html
    - c.f. https://github.com/sanfrecce-osaka/katarina/blob/master/lib/katarina/railtie.rb
- @Kyo18 たいていテンプレートエンジンと言うとこの3つが出てくるけど他にも種類はあるのか？使っている人はいるのか？
    - http://sinatrarb.com/intro-ja.html
    - 昨年松田さんが出してましたね〜(実務ではあまり出てこないとは思いますが)

- c.f. https://github.com/amatsuda/himl

### 2-5-4(10分)
※COLUMNまで

- @sanfrecce-osaka jbuilder のような json のシリアライザは未だに戦国時代・・・
    - jbuilder とか AMS とか fastjson_api とか
    - jbuilder は DSL が好みわかれるところ
- @sanfrecce-osaka API モードは include しているモジュールが通常より減ったり変わったりしている
- @sanfrecce-osaka API モードは sprockets 等も外れているので better_errors とか letter_opener_web とかの画面表示を伴う gem を使う場合に設定する一手間が発生する
- @Kyo18 p.112の3段落目の最初の文の句点が抜けています。
- @masuyama13 テストに出そう→「アプリケーションの主要なロジックはなるべくモデルに書く」
- @ima1zumi 5章で Fat Model 対策について書いてあるの楽しみ😆
- @masuyama13 3文目「そのため、〜フィードバックすることになります。」の後に余計なスペースがあります（110ページ）
    - @igaiga 🙏ありがとうございますー！

ココまで
---

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！


- @sanfrecce-osaka 今日は4連休中だからか他の現役生の参加が少なかった :joy: 
- @sanfrecce-osaka 今日も知見いっぱい :raised_hands: 

- @ima1zumi bootcampのmarkdown処理はgemではなくnpm(markdown-it)になってました（Vue.js側で対応するようになってた）
- @ima1zumi 2章終わって嬉しい！
  - やったー！！
  - @sanfrecce-osaka :raised_hands: 

- @chiroru 終わった箇所の質問もさせていただきありがとうございました🙇‍♀️

- @Kyo18 @masuyamaさんが冒頭でおっしゃっていたように自分もRailsで使うのを避けてきた機能が結構あるので反省です・・・。

- @masuyama13 ヘルパーが「ビュー」ヘルパーだと知れてよかった
- @masuyama13 Rails を API サーバとして使うイメージができてよかった

- @igaiga 誤字情報がみつかってめっちゃ助かりました。 @Kyo18 さんありがとうございました。
