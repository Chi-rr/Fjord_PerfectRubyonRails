# 【第34回】パRails輪読会ノート(2021-4-4)
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

- chiroru(ちろる)
  - 最近どう？: 入社しました！

- @hogucc（おぐち）
    - プラクティス:自作サービス...
    - 最近どう？： 就職きまりました〜！5/1から働きます
        - ふーが：おめでとうございます！！！！！🎉🎉
        - ありがとうございます！！！

- @sanfrecce-osaka(もりつか)
    - Rails歴
        - トータル: 5年くらい？
        - 実務: 3年弱
    - 現在のプラクティス
        - rubocop-ast に PR 出す
    - 最近どう？
        - 会社のチャットツールが Chatwork から Slack に変わって絵文字職人業が捗る

- @misosoup（みそしる）
    - プラクティス：開発にはいったばっかり
    - 最近どう？：いろいろ考えないといけないことが増えてそわそわしています…

- @yu-kichi (ゆーきち)
　- プラクティス：開発に参加して一ヶ月半ちょっとです
　- zoomも今回の輪読会も初めてです!けど何も準備しないで入ってきてます。。今日は雰囲気になれることを目標に頑張りますー。　
　- 最近どう？　仕事やめたばっかでかなりのんびりしてます〜

- ふーが
    - プラクティス：Railsのomniauthを提出したところ
    - 最近どう？：やっとRailsを楽しめるようになってきました🐯

- @igaiga
    - Rails歴: 10年 / プラクティス: RHGという古い本を読んでいます
        - RHG、これですか？ -> https://i.loveruby.net/ja/rhg/book/
    - 最近どう？: フィヨルドのDiscordが盛況なのが嬉しいです


## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[sanfrecce_osaka igaiga hogucc chiroru fu-ga].
  partition { |user| !%w[hogucc].include?(user) }.
  flat_map(&:shuffle)
# => ["chiroru", "sanfrecce_osaka", "igaiga", "fu-ga", "hogucc"]
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
8-3から

## 疑問点・気づき

- mimemagic のバージョン一覧
    - https://rubygems.org/gems/mimemagic/versions
- Rails のアップグレードのときによむといいドキュメント
    - https://railsguides.jp/upgrading_ruby_on_rails.html
    - https://qiita.com/jnchito/items/0ee47108972a0e302caf
    - https://inside.pixiv.blog/sue445/4751

mimemagicのせいでbundleinstallできないので,まずrailsのバージョンをあげる必要がある。
gemfileでrails 6.0.3.6にあげる。
```bundle update rails```




### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい


## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @hogucc Railsのバージョンアップの作業の流れを追えたので良かった
- @hogucc 初参加の方がいらっしゃって嬉しい！
- @hogucc 休憩の時間を取り忘れた...

- @yu-kichi 環境構築やっぱり難しい。。自分の知識が足りてないと実感した。その分とても勉強になりました！！色々使い慣れてないコマンドをしっかり復習しておきたい。

- @fuga mimemagicの依存問題の解消を目の前で見れて勉強になりました。
- @fuga gitもまだまだ知識が足りないなーと思ったのでいろいろやって慣れていきたい。

- @misosoup　昨日gitの復習しててよかった。vscodeでgui操作ができることを知った。railsのupdate作業を見れたのすごくよかった。パrailsは必要なとこしか読めてないので次回までにすこし目を通しておきたい。

- @chiroru railsのバージョンアップ体験できてよかった。

- @imaharu discardから輪読会への導線を探すことができなかったので、slackのlearningから訪問した。新しい人は、どうやって輪読会の存在を知るのか気になった
  - @hogucc 気になる...


## チャット
Kuniaki Igarashiから皆様 (8:33 午前)
ここ
https://hackmd.io/JC8zzjn_T-GaIh-71clcKQ
Kuniaki Igarashiから皆様 (8:53 午前)
10時頃きますー
森塚真年から皆様 (8:57 午前)
https://rubygems.org/gems/rails/versions
hoguccから皆様 (9:00 午前)
https://hackmd.io/@mametter/mimemagic-info-ja
ryohta ochiから皆様 (9:02 午前)
ラジオ参加します
hoguccから皆様 (9:04 午前)
https://rubygems.org/gems/mimemagic/versions
hoguccから皆様 (9:25 午前)
https://weblog.rubyonrails.org/2021/3/26/marcel-upgrade-releases/
imaharuから皆様 (9:28 午前)
https://images-na.ssl-images-amazon.com/images/I/71EPv7vt0sL._AC_SY741_.jpg
私から皆様へ (9:34 午前)
https://github.com/fjordllc/awesome_events/blob/main/Gemfile
imaharuから皆様 (9:35 午前)
bin/rails test:system >> hoge.txt
imaharuから皆様 (9:42 午前)
git log --decorate --all --graph
hoguccから皆様 (9:43 午前)
https://note.com/odaillyjp/n/n50b8f737b878
hoguccから皆様 (9:51 午前)
https://github.com/rubocop/rubocop/pull/9646
森塚真年から皆様 (9:56 午前)
https://weblog.rubyonrails.org/2021/2/10/Rails-5-2-4-5-6-0-3-5-and-6-1-2-1-have-been-released/
hoguccから皆様 (10:12 午前)
https://qiita.com/uasi/items/86c3a09d17792ab62dfe
imaharuから皆様 (10:27 午前)
Ps aux | grep elastic