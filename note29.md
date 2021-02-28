# 【第29回】パRails輪読会ノート(2021-2-28)
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
    - おすすめ（or 好きな）モバイルアプリ
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - おすすめ（or 好きな）モバイルアプリ

- @hogucc（おぐち）
    - スクラム開発、自作サービス
    - 好きなモバイルアプリ: Duolingo

- @ikuma-t
    - オブジェクト指向LSコマンド
    - 好きなモバイルアプリ：Fast Notion、Quizlet

- @masuyama13（マスヤマ）
    - 自作アプリ
    - 好きなアプリ：住信SBI

- @chiroru (ちろる)
  - 就活、自作サービス
  - 好きなモバイルアプリ： Focus To-Do

- @igaiga
  - プラクティス: 営業
  - モバイルアプリ: スマートニュースの花粉予報

- @sanfrecce-osaka(もりつか)
    - プラクティス: 家事
    - モバイルアプリ: FiNC・あすけん

## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[sanfrecce-osaka igaiga masuyama13 ikuma-t hogucc chiroru].
  partition { |user| !%w[].include?(user) }.
  flat_map(&:shuffle)
  #=> ["masuyama13", "sanfrecce-osaka", "chiroru", "igaiga", "hogucc", "ikuma-t"]
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
p.386 「サムネイルを作成する」から


## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- @hogucc
  - libvipsの処理性能についてのブログ
    - [薬局向けサービス”kakari”にruby-vipsを導入した話 - メドピア開発者ブログ](https://tech.medpeer.co.jp/entry/2020/07/30/100000)
- @ikuma-t
    - `rails restart`
    - https://github.com/rails/rails/blob/main/railties/lib/rails/tasks/restart.rake#L7
    - `tmp/restart.txt`を作成するコマンド。作成されたファイルのタイムスタンプを利用して再起動をするっぽい。

- @imaharu 
	- active_storage_validationsは、custom validationを定義しているだけ
	- なぜ、hoge.pngが通ってしまうかの考察
		- active_storage_validationsは、active_storageのcontent-typeを呼び出して、validationに定義したcontent-typeが存在するか確かめている
		- ここで、active-storageの実装を読むと、「MimeMagic.by_extension(format)」を読んでいそう
		- MimeMagic.by_extension(format)は、ファイルの中身を読むのではなく、拡張子をそのままcontent-typeとして返すので、保存できてしまうと思われる
	- 上記から発生する疑問
		- 書籍に記載されている、「画像は不正な画像です」という文言は、validatesの記述から出力されないと考えられる。
		- なぜなら、image_metadata_missingのcustom validationは、「AspectRatioValidator」と「DimensionValidator」でのみerrors.addされているから
- @masuyama13 `brew install`はマシンに依存するコマンドなので`bin/setup`には書かない

- @hogucc active_storage_validations メモ
    - Content-typeがgifの画像をイベント作成時に保存するとvalidationエラー(Content-typeが不正)になる
    - Content-typeがtxtでファイル名をxxx.pngに変えたものをイベント作成時に保存すると上記validationエラーにならない
        - txtファイルは中身に文字を入力した状態
        - Content-typeがgifでファイル名をxxx.pngに変えたものは上記validationエラーになる
    - gemの挙動が変わった...?

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！


- @sanfrecce-osaka file コマンドをはじめて知った、学びだ
- @sanfrecce-osaka 

- @hogucc active_storage_validationsの挙動が謎...
- @hogucc fileコマンドの使いどころがわかった
	- @imaharu CTFやると利用します

- @ikuma-t gemの挙動がカオス。GitHubのPRはテンプレを作ってもいいかもと思いました（規模感的になくても問題なさそうですが）

- @chiroru active_storage_validations、難しい。。

- @masuyama13 いろいろ難しかった。日本語のエラーメッセージがどこで定義されているかわかってよかった
