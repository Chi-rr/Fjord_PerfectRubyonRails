# 【第51回】パRails輪読会ノート(2021-8-22)
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
 

### zoom の画面共有について

- zoom で画面共有ができるか確認しておいてください。
    - 画面共有できない場合、 システム設定 > セキュリティとプライバシー > プライバシー > 画面の録画で zoom.usにチェックを入れます。
    - https://support.zoom.us/hc/ja/articles/201362153-%E7%94%BB%E9%9D%A2%E3%82%92%E5%85%B1%E6%9C%89

### 順番ガチャ

```ruby=
%w[sanfrecce_osaka hogucc asya81 fuga].
  partition { |user| !%w[asya81 sanfrecce_osaka hogucc].include?(user) }.
  flat_map(&:shuffle)
  # => ["sanfrecce_osaka", "hogucc", "asya81"]
  # partition のブロックの中の配列で空白文字が半角スペースになっていなくてひとつづきの文字列として認識されていたみたいです〜
```

### 今日のスタート
12-1から

### 12-1 ユースケースとモデル(5分)

- @sanfrecce-osaka ユースケースのロジック(特定のユースケースに固有のロジック)
    - サービスの利用規約の同意にチェックを入れているかどうかを検証する => Validation
    - ユーザー登録が完了したらウェルカムメールを送信する => Callback
- @hogucc ユースケース固有のロジックとドメインロジックは別物
- @sanfrecce-osaka [ドメイン知識とユースケースの違いは何か？[ドメイン駆動設計][DDD]](https://little-hands.hatenablog.com/entry/2019/07/26/domain-knowledge)
    - > - ユースケース
      >     - ユーザーとソフトウェアの間の相互関係を起こすアクション
      >     - "このソフトウェアの"ユースケースであり、アプリケーションがなければ存在しない
      > - ドメイン知識
      >     - ソフトウェア化する対象領域に存在するルール
      >     - ソフトウェアがなくても、現実世界に存在する
- @sanfrecce-osaka https://qiita.com/little_hand_s/items/dfa4b156f533ba1a1491
- @hogucc https://note.com/cyberz_cto/n/n26f535d6c575

- @asya81 DDD何もわからない。。。こういう課題感から登場した考え方ってこと？
    - https://codezine.jp/article/detail/9546
 ![ソフトウェア開発の課題とDDDが解決すること](https://cz-cdn.shoeisha.jp/static/images/article/9546/9546_001_s.gif)
- @sanfrecce-osaka https://speakerdeck.com/yasaichi/what-is-ruby-on-rails-and-how-to-deal-with-it
- [ドメイン駆動設計入門 ボトムアップでわかる！ドメイン駆動設計の基本](https://www.amazon.co.jp/dp/B082WXZVPC)

### 12-2 データベースと紐づかないモデルを作る(12分)

- @hogucc [Active Record バリデーション バリデーションヘルパー - Railsガイド](https://railsguides.jp/active_record_validations.html#%E3%83%90%E3%83%AA%E3%83%87%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%83%98%E3%83%AB%E3%83%91%E3%83%BC)
- @sanfrecce-osaka [Active Model の基礎](https://railsguides.jp/active_model_basics.html)
    - 他にも色々なモジュールがある
        - [Conversionモジュール](https://railsguides.jp/active_model_basics.html#conversion%E3%83%A2%E3%82%B8%E3%83%A5%E3%83%BC%E3%83%AB)
        - [Dirtyモジュール]()
        - Namingモジュール
        - Translationモジュール
        - Lintテスト
        - SecurePasswordモジュール
- @hogucc Active ModelのおかげでRailsが用意してくれている機能を使いつつ、ARと密結合にならないモデルが書けそう
- @hogucc ARと紐づかないモデルはbootcampアプリだとこれ
    - https://github.com/fjordllc/bootcamp/blob/main/app/models/generation.rb
- @hogucc 定数参照の優先順位
    - [変数と定数 (Ruby 3.0.0 リファレンスマニュアル)](https://docs.ruby-lang.org/ja/latest/doc/spec=2fvariables.html)

### 12-3 フォームオブジェクト(10分)


### 12-4 プレゼンター(7分)



## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @hogucc DDD実践するかどうかはアプリケーションの規模次第かなぁという気がした
    - ひとまずModelを分割して、ActiveModelのモジュールをincludeするところから始めるのが良さそうということがわかった
- @hogucc ドメインロジックとユースケースロジックの違いについてなんとなく理解できた
- @hogucc 次回最終回！！！！！！
    - @sanfrecce-osaka うおおおおおおおおお :laughing: :tada: :tada: :tada: 
- @asya81 DDDの考え方やActiveModelなど普段触れていないものを学べて良かった！
- @asya81 ActiveModelは知っておくと使える場面がいつか出てくるかも。
- @asya81 DDDは何にもわからないので、どこかで本を読んでみたい。
    - @igaiga やさいちさんとt-wadaさんのpodcastがわかりやすくておすすめです https://anchor.fm/textafm
    - @asya81 ありがとうございます。聞いてみます！ :pray::sparkles: 
- @chiroru DDDと言葉だけ聞いたことがあったけど、なんとなくイメージが湧きました
- @chiroru 以前話を聞いた時よりもARと紐づかないモデルについて理解が深まった
- @sanfrecce-osaka また一つ DDD に関して知識が深まったゾイ :raised_hands: 
    - 成瀬さんの本も読まんとなぁ :thinking_face: 
- @sanfrecce-osaka ぼんやりとした理解でいた ドメイン と ユースケース の違いをはっきりと認識できた