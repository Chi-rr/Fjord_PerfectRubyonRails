# 【第32回】パRails輪読会ノート(2021-3-21)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @hogucc
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
    - 今日のテーマ：最近どう？
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：最近どう？

- もりつか(@sanfrecce-osaka)
    - Rails歴: 5年くらい(実務は3年くらい)
    - 現在のプラクティス: Gem作成
    - 最近どう？
        - スマブラの本気度9.9クリアを昨日成し遂げた
        - 枕買いたい

- おぐち（@hogucc）
    - プラクティス：自作サービス、就活
    - 最近どう？: 2月末くらいから始めたアルバイトに慣れてきた

- chiroru(ちろる)
  - プラクティス：自作サービス
  - 最近どう？： 先日輪読会後から腰痛が悪化してましたが、整骨院に通っていたら調子が良くなってきました！！
    - @hogucc おおー！よかったです！！自分も気をつけよう...
    - @sanfreccce-osaka :tada: :tada: :tada:
    - @igaiga よかった〜！

- ふーが（@fuga__ch)
    - プラクティス：Railsのdevise
    - Rails歴：１ヶ月くらい
    - 最近どう？：Railsの歩き方がわからず苦戦しています😅

- @igaiga
    - Rails歴: 10年 / プラクティス: 執筆
    - 2冊並行でコツコツ執筆しています。


## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[sanfrecce_osaka hogucc chiroru].
  partition { |user| !%w[chiroru].include?(user) }.
  flat_map(&:shuffle)
# => ["hogucc", "sanfrecce_osaka", "chiroru"]
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
p.394 8-2-2 Searchkickでイベント検索機能を作成する

## 疑問点・気づき
- >Homebrew では、いわゆるパッケージ名のことを formula と呼ぶ。
  - [Homebrew使い方まとめ](https://qiita.com/vintersnow/items/fca0be79cdc28bd2f5e4)

- kuromoji
  - [kuromoji](https://www.atilika.com/ja/kuromoji/)

- URLの上限
  - クエリパラメータ除いて2000文字(2048)くらい

- [Rails 6.1で form_withのデフォルトが「remoteなし」になった](https://techracho.bpsinc.jp/hachi8833/2021_01_22/103256)

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい


## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！
- @chiroru Kuromoji初めて聞いたけど、形態素解析すごそう

- @hogucc Elasticsearch使ったことがなかったので導入の手順を知れてよかった
- @hogucc ふーがさん初参加ありがとうございます！！！
- @hogucc 最近人が減ってきていて寂しい...
    - @sanfrecce-osaka :wakaru: (´・ω・｀)

- @fuga 
    - 質問の時間を設けていただいてありがとうございました。
    - 書籍の内容はまだ全然追いつけていませんが、これがわかるように今後頑張っていきたいと思います。
    - こうした一緒に勉強できる機会はとても勉強になるので、また参加させていただきたいです😊
      - @chiroru ぜひぜひ！！
      - @hogucc 是非ー！！！

- @sanfrecce-osaka @fuga さん初参加 :tada: :tada: :tada: :tada: :tada: 
- @sanfrecce-osaka Elasticsearch 完全理解した