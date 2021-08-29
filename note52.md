# 【第52回】パRails輪読会ノート(2021-8-29)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @chiroru
タイマー： @hogucc
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
- 輪読会
- 振り返り書く(3~5分くらい)
- 雑談(15分くらい)
 

### zoom の画面共有について

- zoom で画面共有ができるか確認しておいてください。
    - 画面共有できない場合、 システム設定 > セキュリティとプライバシー > プライバシー > 画面の録画で zoom.usにチェックを入れます。
    - https://support.zoom.us/hc/ja/articles/201362153-%E7%94%BB%E9%9D%A2%E3%82%92%E5%85%B1%E6%9C%89


### 今日のスタート
12-3から

### 12-3 フォームオブジェクト(10分)

- @sanfrecce-osaka Rails にデフォルトで組み込まれているバリデーションは ActiveModel::EachValidator を継承して実装されている
- @sanfrecce-osaka options は ActiveModel::EachValidator の親クラスの ActiveModel::Validator の initialize で初期化されている
- @sanfrecce-osaka Rails にデフォルトで組み込まれているバリデーションも ActiveModel::Validator の例と同じく validates_with で　ActiveModel::Validator を継承したクラスを引数に渡して実装されている　
- @hogucc フロントとサーバーを分離して、RailsをAPIとしてしか使わなくする場合、フォームオブジェクトの恩恵は受けられなくなるってことなのかな...？
    - API側でフォームオブジェクトを利用するのが良さそう
- @fuga ちょうどフォームオブジェクトを使用したいと思っていたので、良いタイミング
- @fuga コントローラーやモデルの肥大化を防ぐためにフォームオブジェクトに分離するというユースケース
- @hogucc Reactのテストのライブラリ（メジャーなのはJestとReact Testing Library?)
    - https://ja.reactjs.org/docs/testing.html

### 12-4 プレゼンター(7分)

- @masuyama13 Bootcamp は ActiveDecorator を使っている
    - @hogucc https://github.com/fjordllc/bootcamp/tree/main/app/decorators
- @sanfrecce-osaka Active Decorator 以外に Draper という Gem もある
    - https://nishisuke.hateblo.jp/entry/2018/01/01/215459
- @sanfrecce-osaka API でも プレゼンター層は有効
    - https://qiita.com/ledsun/items/66bbdaa9af70fac20f2e
- @fuga helperやpresenterに切り出す線引きがよくわかっていない
    - あまりにも長いロジックは「切り出した方が良さそう」とわかる
    - 1行で書けるけど、チェインが続いているなどはどうなんだろう？
- @hogucc active_decorator
    - https://github.com/amatsuda/active_decorator
    - full_nameとか使えそう

## 振り返り(よかった点・次回に向けての改善点等)

- @hogucc モデルにいろいろ書いているなーと思ったらフォームオブジェクトやデコレーターの存在を思い出そうと思った
- @hogucc パRails読み終わりましたね！！！！！！！！！！！
- @hogucc 毎回参加してくださっていたigaigaさん、ありがとうございました！
    - @sanfrecce-osaka 感謝感謝です :pray: :pray: :pray:
- @masuyama13 ついに輪読会が終わった！もう一度読みたいところがたくさんあるいい本だった
- @fuga フォームオブジェクトもデコレーターもすぐに使えそうな感じがするので、さっそく使っていきたい
- @fuga どちらも責務の分離につながることなので、意識して利用したい
- @fuga 輪読会完走おめでとうございます🎉🎉🎉
    - @fuga 途中からでしたが、たくさん勉強させていただきました。ありがとうございました！！
- @chiroru  フォームオブジェクト、デコレーター、使ったことはないので概要がつかめてよかった
- @chiroru パRails、読了！！輪読会完走できたの感慨深い🎉😂
    - @sanfrecce-osaka :tada: :tada: :tada:
    - @hogucc chiroruさんが声を上げなければこの会は立ち上がってなかったはずです！本当にありがとうございました！
- @sanfrecce-osaka パRails輪読会、完！
- @sanfrecce-osaka ActiveDecorator のコード、勉強になるのでまたじっくり読みたい
- @asya81 今回も難しかったですが、フォームオブジェクトやデコレーターを知ることができて良かったです。また次出会った時は、パRails本やこのhackmdを見返そうと思います。
- @asya81 パRails輪読会、完走おめでとうございます！ありがとうございます！！🎉🥳