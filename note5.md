# 第5回パRails輪読会ノート(2020-09-06)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 2-2-2〜2-2-4

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

- @sanfrecce_osaka(もりつか)
- Rails歴
    - 実務2年前後
    - 学習期間含めると5年弱
- プラクティス: 来週金曜の社内発表の準備
- 今年のRubyKaigiの糸柳さんの発表は最高なので公開されたらぜひぜひ見てください〜

- @masuyama13 (マスヤマ)
    - プラクティス： オブジェクト指向、JavaScript
    - 台風心配・・・
    - 最近もくもく会をやっています

- @chiroru 
  - JSカレンダー
  - RubyKaigi終えて「まだまだ知らないことがたくさんあるぞ！」とワクワクしております💪

- @e6i24v
　　プラクティス：Linux

- @hogucc（おぐち）
  - プラクティス：JSメモアプリ
  - JSむずかしい...

- @Kyo18 (岸)
    - JSLint
    - 最近野菜が高くて野菜不足気味です。 
        - @sanfrecce-osaka 業務スーパーの冷凍野菜安くておすすめです〜 :+1: 

- @ima1zumi(いまいずみ)
  - JS npm
  - macbookが直りました

- @universato(ユニ)
  - RailsのGitHub認証が終わったところです。
  - 好きなRubyのメソッドが、tally, bsearchです。
     - @sanfrecce-osaka tallyいいですよね、:wakaru:
     - @igaiga tally、ナウい(Ruby2.7〜？) ← @sanfrecce-osaka :+1: 

- @igaiga
    - プラクティス: 会社の住所の引越しをしてしています
    - RubｙKaigi、Ruby3.0が現実に見えてきたのでたのしみです

## 疑問点・気づき
>### 書き込みサンプル
>@アカウント名 Rails楽しい

#### (2) 2-2-2 終わりまで
- @sanfrecce-osaka reload、たまに忘れてハマるやつだ :sweat_smile: 

- @ima1zumi reload [ActiveRecord::Base\#reload はインスタンス変数をクリアしない \- アクトインディ開発者ブログ](https://tech.actindi.net/2018/09/03/090017)
    - 貼ってからアクトインディの技術ブログだと気づいた ← @sanfrecce-osaka :iihanashida:

- @hogucc reloadメソッドのところの「オブジェクトの状態を参照せず、DBのデータを引き直すために利用」の意味がわからなかったです...
    - 一度オブジェクトにDBから取得した値を入れた後に、DB側に更新があるとオブジェクトのデータは古いままの状態になる。なのでその時点での最新のデータを取りたい場合はreloadを使ってDBのデータを直接取得する
    - 例: 同じレコードに対する複数のオブジェクトを持っているときに、その片方だけを変更してレコード更新したような場合

```ruby
book1 = Book.find(1) #=> title: "Railsの教科書" 
book2 = Book.find(2) #=> title: "Railsの教科書"
book1.title = "Ruby超入門"
book1.save!
book2 #=> title: "Railsの教科書" 
book2.reload # 最新の"Ruby超入門"を使いたいときはreloadする必要がある
book2 #=> title: "Ruby超入門" 
```

- @ima1zumi pluck はどういう時に使うんだろう?
    - @Kyo18 pluck使ったことなかった・・・
    - @sanfrecce-osaka https://railsguides.jp/active_record_querying.html#pluck
    - @ima1zumi pluck は結果がRubyの配列で返る
        - select は ActiveRecord::Relation で返る

### 2-2-3
- @chiroru absence(値が空であること)はどういう時に使うのでしょうか？
  - 単体のカラムとしては値が必要でも、(何か別のカラムと組みあわせた時など)条件によって値が不要な場合に使えるのではないか
- @sanfrecce-osaka よくある勘違い => フロント側でバリデーションしているからサーバー側でバリデーションしなくてもよくない？
    - 実際はフロント・Rails・DBで役割が違うので全部バリデーションした方がいい(と以前指摘されたことがある)
    - フロント => ユーザーに入力エラーを伝えるため
        - 直接API等にリクエストを送ればすりぬけられるのでフロントだけでは不十分
    - Rails => アプリケーションでエラーの際の制御・処理をしやすくするためのもの
        - SQLを直接叩けばすり抜けてしまうのでフロント + Rails でも不十分
    - DB => 最後の砦
        - ここだけだと扱いにくいのでここだけでも不十分
- @chiroru フォールバックという言葉初めて聞きました・・
  - 処理が上手くいかなかった時に、機能制限や方法を変更して動く状態にすること(?)
      - @igaiga : 私もそんな理解です！「失敗したときの代替案」みたいな意味でつかってます。
- @sanfrecce-osaka `!`の意味はRailsとRubyで意味が違う
    - ActiveRecord: 例外が発生する可能性のあるメソッド
    - Ruby: 破壊的メソッド(とは限らないけどよく使われる)
    - c.f. https://qiita.com/tadsan/items/7baab2605a4d8ac1858e
- @masuyama13 「レースコンディション」の意味がわからなかった
    - レースコンディション（競合状態）。以下の理解でOK？
        - @snfrecce-osaka 自分もきちんと意味調べてなかったなぁ :eyes: 
        - @sanfrecce-osaka 複数DBを扱っている場面とかで使われる？
>システムや処理過程の問題であり、処理過程の出力結果がイベントなどの順序やタイミングと予期しない（かつ危険な）依存関係にある場合をいう。
[競合状態 \- Wikipedia](https://ja.wikipedia.org/wiki/%E7%AB%B6%E5%90%88%E7%8A%B6%E6%85%8B)

>レースコンディションは、ある状態が成立しているという前提でプログラムが処理を行ったところ、実際には他のプロセスやスレッドによって状態が変更されていて、意図した処理が失敗してしまう問題のことである。
[IPA ISEC　セキュア・プログラミング講座：C/C\+\+言語編　第9章 ファイル対策：ファイルレースコンディション対策](https://www.ipa.go.jp/security/awareness/vendor/programmingv2/contents/c803.html#:~:text=%E3%83%AC%E3%83%BC%E3%82%B9%E3%82%B3%E3%83%B3%E3%83%87%E3%82%A3%E3%82%B7%E3%83%A7%E3%83%B3%E3%81%AF%E3%80%81%E3%81%82%E3%82%8B%E7%8A%B6%E6%85%8B,%E5%95%8F%E9%A1%8C%E3%81%AE%E3%81%93%E3%81%A8%E3%81%A7%E3%81%82%E3%82%8B%E3%80%82)
- @hogucc 私もわからなくて調べていたのですが、この記事が参考になるかもです
  - [Rails におけるレースコンディションの例とその回避方法 - LukeSilvia’s diary](https://lukesilvia.hatenablog.com/entry/20100130/p1)
- @ima1zumi 「楽観ロック」で似たような話が出てきます
    - [「楽観的ロック」と「悲観的ロック」の違い｜「分かりそう」で「分からない」でも「分かった」気になれるIT用語辞典](https://wa3.i-3-i.info/diff514lock.html)

- @Kyo18 formatの「あるフォーマット」とは？
    - 正規表現のことだった。https://railsguides.jp/active_record_validations.html#format

### 2-2-4
- @chiroru `gsub(pattern) {|matched| .... } -> String`の書き方があるんですね
  - メモ：`gsub(pattern) -> Enumerator`
  - ほかに $1, $2... という呼び方もある
  - e.g. /(before)_(validation)/ # => $1: 'bofore', $2: 'validation'
  - c.f. https://docs.ruby-lang.org/ja/latest/method/Kernel/v/1.html
  - "book" =~ /(k)/
  - $1 #=> "k" 
  - "book".gsub(/k/)
  - $1 #=> "k"
  - `"book".gsub(/b/){|matched|  }`
  - $1 #=> "b" 
  - $1は使える範囲が広いので、ブロック変数matchedで受けてブロックの中で処理をした方がきれいなプログラムになります

```ruby
irb(main):005:0> 'abcabc'.gsub(/[bc]/) { |str| p str ; str }
"b"
"c"
"b"
"c"
=> "abcabc"

irb(main):006:0> 'abcabc'.gsub(/[bc]/) { |str| puts str }
b
c
b
c
=> "aa"

irb(main):007:0> 'abcabc'.gsub(/[bc]/) { |str| p str ; str.upcase }
"b"
"c"
"b"
"c"
=> "aBCaBC"
```

- @sanfrecce-osaka コールバックは便利だけど使い所と責務を誤るとつらい。。。
    - e.g. after_save でメール飛ばすとか => テスト時に毎回stubしないといけなくてつらい
        - after_save だと DB に COMMIT されない
        - COMMIT後 としたい場合は after_commit

- @hogucc コールバックが実行されないメソッドもあるのか...忘れてハマりそう...

- @Kyo18 beforeやafterは分かりやすいけどaroundはどういう時に使うんだろう？
    - c.f. https://railsguides.jp/action_controller_overview.html#after%E3%83%95%E3%82%A3%E3%83%AB%E3%82%BF%E3%81%A8around%E3%83%95%E3%82%A3%E3%83%AB%E3%82%BF
        - controller の方だけど 
    - aroundだけ書き味が違う模様。ほとんど使われていなさそう。
    - サンプルコードはこんな感じです

```ruby
class Book < ApplicationRecord
  around_save :around_method

  private
  def around_method
    puts "before!"
    yield # ここでsaveの処理が行われる
    puts "after!"
  end

  # yieldで呼べるので、ブロックで囲える
  # def around_method
  #   puts "before!"
  #   ActiveRecord::Base.transaction do
  #     yield
  #   end
  #   puts "after!"
  # end
end
```

- @ima1zumi コールバックが実行されない `delete` などのメソッドを使うと、 `dependent: destroy` を設定していても関連付け先が消えないということを知らなかったので知れてよかった。 [ActiveRecord::Persistence](https://api.rubyonrails.org/classes/ActiveRecord/Persistence.html#method-i-delete)
    - 本文中には書いていませんが、 `delete` と `destroy` の違いを調べて知りました

- @sanfrecce-osaka lambda(Proc)を渡す書き方もよくある
    - 名前をつけるまでもない1箇所しか使わない処理の場合とかに使われたりする

```ruby
before_validation -> { ... }

before_destroy -> { Rails .logger.info "..." }
```

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！
>

- @sanfrecce-osaka 質問たくさん出て盛り上がったのでよき :raised_hands: 
    - Rails だけじゃなくて Ruby の質問とかも出て面白い :laughing: 
- @sanfrecce-osaka `after_save` と `after_commit` の違いと注意点について知れた :100: 

- @chiroru 個人的にはgsubのこと詳しく知れて良かったです！みんな知ってるかも？と思ってもまずは質問してみること大事ですね！今日は「1つ以上質問する」という目標を自分の中で立てていたので達成できて良かった🙆‍♀️
    - > みんな知ってるかも？と思ってもまずは質問してみること大事ですね！
    - @sanfrecce-osaka :iihanashida:

- @hogucc 1つの疑問からいろんな知見を得られるので、とても有意義な勉強会だなぁと改めて思いました！gsubのことやコールバックのことなど勉強になりました！

- @Kyo18 聞きたいことが聞けたのでかなり満足！画面共有に関してHackMDのプレビュー画面って見てる方いるのかな？

- @universato 色々知れて良かったです。

- @masuyama13 ログの見方を今まで知らなかった。コールバック難しいのでみんなで勉強できてよかった

- @ima1zumi 今後ハマりそうな箇所を知ることができて良かったです。(コールバック呼ばれないメソッド、 after_save, reload, レースコンディションなど)

- @igaiga gsubのブロック渡すときの動きとか、モデルのaroundアクションとか、知らないことがいろいろあって勉強になりました
    - （特別な理由がなければ）delete(コールバックが呼ばれない)をつかわずにdestroy(コールバックが呼ばれる)を使おう
    - @sanfrecce-osaka delete は使わないように注意します〜

## チャット
09:18
Kyo18
結構特殊なケース？

09:30
sanfrecce_osaka
昨日のRactor
昨日じゃなかった

09:34
Kyo18
なにかの本で読んだ気がするけど何だったか思い出せない

09:36
ima1zumi
ちょっと電波悪くてちょいちょい接続切れていることがあります🙇‍♂️

09:36
sanfrecce_osaka
👍

10:16
ユニ@universato
😮
