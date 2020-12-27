# 【第21回】パRails輪読会ノート(2020-12-27)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @masuyama
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
- 自己紹介
- 休憩挟みつつモブプロ(10:10~15くらいまで)
- 振り返り書く(3~5分くらい)
- 雑談(15分くらい)


## 自己紹介の記入をお願いします！
> - フィヨルド生
    - 名前(@username + 呼び名)
    - 現在のプラクティス 
    - 今日のテーマ：年越しの瞬間は何しますか？
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：年越しの瞬間は何しますか？

- @ima1zumi 
    - 自作サービス
    - 年越しの瞬間：こたつでぐだぐだテレビを見てそう
    - twitter

- @hogucc（おぐち）
    - スクラム開発、就活
    - 年越しの瞬間:テレビを見てると思います
- @masuyama13 
    - スクラム開発
    - テレビがないのでYouTubeとか見る？
- @ikuma-t
    - devise
    - カップ焼きそばを食べる

- @neutral 
    - Linux
    - いつもと変わらずのつもりでしたが、あらためて何しよう？と意識しました。猫とごろごろかな？ 私もテレビないです！

- @igaiga
    - なぜか最近書類仕事が多くて書類をいろいろ読んでます
    - 年越しの時間はtweetします

- @ksmxxxxxx 
    - Webアプリケーション
    - ゲームしているか、絵を書いてるか、プラクティスをしているかのどれかの予感がしてます（地元の友だち、多分今年は返ってこないので呼び出しはない気がする）

- @sanfrecce-osaka(もりつか)
    - 遅刻している記事の作成
    - 親と年越しそば(オンライン越し)

- @chiroru 
  - スクラム開発
  - 年越しの瞬間：初詣か麻雀・・？

## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[sanfrecce_osaka masuyama13 ikuma-t ima1zumi hogucc].
  partition { |user| !%w[ima1zumi hogucc Kyo18 igaiga chiroru].include?(user) }.
  flat_map(&:shuffle)
  #=> ["sanfrecce_osaka", "ikuma-t", "masuyama13", "hogucc", "ima1zumi"]
```

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
６−６−２から

## 疑問点・気づき
- hamlチートシート
    - https://morizyun.github.io/ruby/library-template-engine-haml.html
- @hogucc （誤字報告）p.328のリスト6.48の①の"data-toggle"の値
    - (誤)"model"
    - (正)"modal"
- @sanfrecce-osaka bootstrap のモーダルのドキュメント
    - https://getbootstrap.jp/docs/4.2/components/modal/
    - https://getbootstrap.com/docs/4.5/components/modal/#usage <-こっちがmodalの使い方です

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい


## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @hogucc （覚書）reviwerになってもらうためにbootcampのコラボレーターに参加していない人を追加しないとですね...
- @sanfrecce-osaka 初参加がお２人も！ :raised_hands: 
  - @chiroru 今日みたいに見学だけでもラフにしてもらえたらいいですね〜
- @sanfrecce-osaka localhost の説明ミスっていた :sweat_smile: 
    - 正しくは↓
    - https://qiita.com/1ain2/items/194a9372798eaef6c5ab
- @chiroru エラーとか一緒に解決していけるの、良い
- @hogucc モデルの関連付けの話とか結構難しいと思うので、初参加の方のために説明まじえつつもっとゆっくり進めたほうがよかったのかな...？
- @ikuma-t rubymineの起動設定で`http://0.0.0.0:3000`だとGithub認証が失敗するのは盲点（`http://localhost:3000`ならOK）。
    - @ikuma-t お手数おかけしました🙇‍♂️
    - @ikuma-t RubyMineでrails実行しているログから調査しようと思います
    - @ikuma-t 立ち上げ時のログは`Listening on tcp://0.0.0.0:3000`、GETは`GET "/" for 127.0.0.1`どういうこと...?
- @ikuma-t Bootstrapもよく知らんとエラーに立ち向かえない...。
    - `{}`の前の空白と`modal（✖️model）`
- @ima1zumi `0.0.0.0` と `localhost` の違いを意識したことがなかったので勉強になった
    - これ読んでたけどよくわからなかった [What is the Difference Between 127\.0\.0\.1 and 0\.0\.0\.0?](https://www.howtogeek.com/225487/)
- @masuyama13 `model`とか`localhost:3000`のやつとか、罠が多い日だった…一人だったら絶対気づけない。モブプロありがたい:pray:
- @ksmxxxxxx 
    - 前職でRailsのviewいじってたの懐かしくなった
    - モブプロ、初めて見たけどいいですね
    - Bootstrap、もう一年近く触ってないけど、覚えてるもんだな…( ºωº )

- @neutral  
    - 独学でRails チュートリアルをやっていた時に、Railsに関するものなのかBootstrapに関するものなのかが分からなくて困ったことがあったので、あることなのだなぁと思いました。
    - エラーが出た時にみなさんの考え方・向かい方がとても参考になりました。
    - 見学参加もとても有意義。恐れ多いと思っている人がいたら大丈夫と伝えたい。
    - やっぱり英語勉強した方がいいのでは。

