# 【第19回】パRails輪読会ノート(2020-12-13)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @ima1zumi
タイマー： @kyo
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
    - 今日のテーマ：12月中にやりたいこと
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：12月中にやりたいこと



- @masuyama13 (マスヤマ)
    - スクラム開発
    - スクラム開発を終わらせる！
    - 自作サービスを作り始める

- @ima1zumi 
    - 自作サービス
    - reline の PR
    - 12月中にやりたいこと
        -　自作キーボード組みたい
        -　自作サービス..

- @hogucc（おぐち）
    - スクラム開発、就活
    - １２月中にやりたいこと
      - スクラム開発のプラクティスを終わらせたい
      - 就活で自分に合う企業と出会いたい...

- @chiroru (ちろる)
  - 現在のプラクティス：スクラム開発/自作サービス(?)
  - 12月中にやりたいこと
    - エアコンの掃除
    - 扇風機を片付ける

- @sanfrecce-osaka(モリツカ)
    - 現在のプラクティス
        - **今日** の Ruby Advent Calendar の記事作成
    - 今日のテーマ：12月中にやりたいこと
        - お料理ケトルが壊れてお湯が沸かせないのでお湯を沸かせる環境に戻すこと

- @Kyo18(岸)
  - 現在のプラクティス
    - スクラム開発/自作サービス/引っ越し準備
  - 今日のテーマ
    - 引っ越しを終わらせたい！


- @igaiga
    - 現在のプラクティス: 冬眠
    - 12月中にやりたいこと: 冬眠
        - @sanfrecce-osaka :sleeping: 

## ドライバーガチャ

モブプロのドライバーをしたい方は↓に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[ima1zumi masuyama13 hogucc sanfrecce-osaka kyo18 chiroru igaiga].
  reject { |user| %w[].include?(user) }.
  shuffle
```
["ima1zumi", "chiroru", "sanfrecce-osaka", "kyo18", "hogucc", "igaiga", "masuyama13"]

## 環境

- ruby 2.6.6

```bash
$ rbenv versions | grep 2.6.6
# 2.6.6が表示されることを確認する。表示されなければ以下実行
$ rbenv install 2.6.6
```

- rails 6.0.3
```bash
$ gem i -v 6.0.3 rails
```

c.f. [Rails Girls インストール・レシピ](https://railsgirls.jp/install)

## 本編の進め方

- 6章以降はモブプロで進めます
- コラム等のテキスト部分は本編中に読む時間を設けないので各自で読んでおいてください〜 :pray: 

### Pull Request の送り方

OSS の開発を体験するために、Fork してから Pull Request を送る方法でやります

### zoom の画面共有について

- zoom で画面共有ができるか確認しておいてください。
    - 画面共有できない場合、 システム設定 > セキュリティとプライバシー > プライバシー > 画面の録画で zoom.usにチェックを入れます。
    - https://support.zoom.us/hc/ja/articles/201362153-%E7%94%BB%E9%9D%A2%E3%82%92%E5%85%B1%E6%9C%89

### アプリケーションのリポジトリ

https://github.com/fjordllc/awesome_events

memo
`git remote add origin https://github.com/fjordllc/awesome_events.git`

### （初回のみ） `master.key` をローカルに作成する
`master.key` は秘密情報で GitHub や HackMD に上げるのはよろしくないため、 secret gist 管理にしています。 gist の URL は運営が管理しています。
ローカルに `config/master.key` を新規作成して、 gist から貼り付けてください。

**HackMDにgistを貼らないでくださいね!**

### 今日のスタート
6-4-3から

## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい


- @sanfrecce-osaka [RubyとRailsにおけるTime, Date, DateTime, TimeWithZoneの違い](https://qiita.com/jnchito/items/cae89ee43c30f5d6fa2c)

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka Discord、画質・音質がやっぱり不安定かなぁ？ :thinking_face: 
  - @chiroru zoomのが良さそうですかね・・？
- @chiroru PR書くの難しかった・・あとSJR初めて知りました！
- @ima1zumi innerHTML, どこかでなるべく使わないほうがいいと聞いたような気がしたけどソースが見当たらない...こういう場合は仕方ないのかな
    - @sanfrecce-osaka [この辺](https://developer.mozilla.org/ja/docs/Web/API/Element/innerHTML#Security_considerations)の話ですかね？
- @ima1zumi yarn install で時間かかって申し訳なかった :sob: `bundle` と `yarn install` を先にしておこうと思った
- @hogucc discordで画面共有したことないのですが、今日ドライバーだった方はやりづらいとかあったんでしょうか？
    - @ima1zumi 私は広いディスプレイ使ってて画面全体共有すると小さくなりすぎるので window ごとに表示してました。でも、macbook の小さい画面に表示させて、ちろるさんみたいに全画面共有すれば楽だったなーと思いました!
    - @chiroru そうですね！全画面共有だったので、その点に関しては全く問題ありませんでした！🙆‍♀️
- @masuyama13 バリデーションエラーはjs（SJR）で対応するといいと知らなかった
    - モデルの関連づけも勉強になりました
    - @ima1zumi 細かいところですが、AjaxだからJSでやってるのかなと思いました
- @masuyama13 Discordは声がよく途切れる、画面共有の小さい字が読めないという問題があった
- @Kyo18 やはりモブプロは見ている側でもかなり勉強になりますね！バリデーションエラーの際に`views/model`下に`.js.erb`ファイルを置くという方法は初めて知ったので、もう少し理解を深めたいと思います。

- @Kyo18 turbolinksとかAjax通信の復習をしなければ…
