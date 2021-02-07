# 【第26回】パRails輪読会ノート(2021-2-07)
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
    - 今日のテーマ：最近「これは知見！」と思ったこと
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：最近「これは知見！」と思ったこと

- @hogucc（おぐち）
    - スクラム開発、就活
    - 知見： yancan.fmで紹介されていたバグなどに出会ったときのフローチャート
      - [バグなどの謎の現象に立ち向かうも闇が濃く、どうしても沼から脱出できない時に見るフローチャート - Thanks Driven Life](https://gongo.hatenablog.com/entry/2017/01/04/233904) 
- @ikuma-t
    - オブジェクト指向プログラミング
    - 知見：午後会 > 朝会、夕会
- @sanfrecce-osaka(もりつか)
    - 現在のプラクティス: 勉強会の準備
    - 知見: https://twitter.com/ShinShinohara/status/1357699296829710337?s=20
- @masuyama13 (マスヤマ)
    - 自作アプリ
    - 知見：[括弧 \- Wikipedia](https://ja.wikipedia.org/wiki/%E6%8B%AC%E5%BC%A7#%E6%B3%A2%E6%8B%AC%E5%BC%A7%EF%BD%9B_%EF%BD%9D)
- @igaiga
  - プラクティス: 執筆
  - 知見:
    - Bundlerが標準添付されるようになったのってRuby2.6でまだ最近なんだなー
    - Enumerable#sumが入ったのってRuby2.4でまだ最近なんだなー
    - foo.method(:bar).source_location
- chiroru
  - プラクティス：就活、自作アプリ
  - 知見： https://twitter.com/matomesu

## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[sanfrecce_osaka igaiga masuyama13 ikuma-t hogucc chiroru].
  partition { |user| !%w[masuyama13 ikuma-t].include?(user) }.
  flat_map(&:shuffle)
# => ["igaiga", "sanfrecce_osaka", "hogucc", "chiroru", "ikuma-t", "masuyama13"]
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

7-5

## 疑問点・気づき


### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- @hogucc インテグレーションテストは複数のリクエストを組み合わせてテストできる。機能テストは1つのリクエストだけしかテストできない
- @hogucc RSpecのコントローラースペックはminitestのコントローラーテストとは別物。RSpecでminitestのコントローラーテストに相当するものはリクエストスペック
- @ikuma-t Macのテキスト入力系ショートカット
    - [知らないあなたは損してる。Macの必殺ショートカットキー \| 株式会社ZINE](https://zineinc.co.jp/hack/mac/mac-text-control/)
- コミットメッセージに実行したコマンドをそのまま記載する流儀がある
    - @a_matsuda さんもやっているっぽい？ c.f. https://fujimura.hatenablog.com/entry/2018/03/30/181715#f-b8bcd6cc

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka 自分のドライバーのタイミング、色々脱線多かったかな？ :sweat_smile: 
  - @hogucc 自分は気にならなかったです！他の人はどうなんだろう？ 
- @ikuma-t コントローラのテストは自分で書く時忘れそう（システムテストに比べてわかりにくい）
  - @sanfrecce-osaka API 書いたときはシステムテストの代わりにコントローラーのテストはきちんと書いておいた方がいいという話はありますね〜(逆に API 以外はコントローラーのテストは書かないことも多い気がしますね〜 :smile: (個人的所感))
- @hogucc 自己紹介のときの知見コーナーが思いのほか盛り上がってよかった
- @hogucc RubyMineのショートカットキー知らなさすぎるので慣れていきたい...
- @masuyama13 コントローラのテストはプラクティスのときちゃんと勉強しなかったので勉強になった
- @chiroru vim基本的な操作しか覚えていないからプラグイン入れていなかったけど、macにも便利なショートカットあるからそちらを利用しようかな