# 【第27回】パRails輪読会ノート(2021-2-14)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @chiroru
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
    - 今日のテーマ： 趣味(または好きなもの)
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：

- @ikuma-t
    - オブジェクト指向ボウリング
    - 趣味：クラシックギター・ツール漁り・デュエマ（公式）、パワポ作り（非公式）

- @hogucc
    - スクラム開発、自作サービスペーパープロトタイプ作成、就活 
    - 趣味：水族館、温泉

- @masuyama13 
    - 自作アプリ作り
    - 趣味：音楽（洋楽、Superfly、ひげだん）

- @chiroru 
  - プラクティス：就活、自作サービス
  - 趣味： 温泉、麻雀、F1

- @igaiga
    - Rails歴: 10年 / プラクティス: 執筆
    - 今日のテーマ: エオルゼアで麻雀にたどり着いた & "slay the spire" というswitchで買ったカードゲーム風RPGにはまってます

## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[igaiga masuyama13 ikuma-t hogucc chiroru].
  partition { |user| !%w[sanfrecce_osaka igaiga masuyama13 ikuma-t].include?(user) }.
  flat_map(&:shuffle)
  
  => ["chiroru", "hogucc", "igaiga", "masuyama13", "ikuma-t"]
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
7-6


## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

バリデーションが実行されるメソッド
>以下のメソッドではバリデーションがトリガされ、オブジェクトが有効な場合にのみデータベースに保存されます。
>- create
>- create!
>- save
>- save!
>- update
>- update!

バリデーションのタイミング
>Railsは、Active Recordオブジェクトを保存する直前にバリデーションを実行します。バリデーションで何らかのエラーが発生すると、オブジェクトを保存しません。
>[Active Record バリデーション \- Railsガイド](https://railsguides.jp/active_record_validations.html#valid-questionmark%E3%81%A8invalid-questionmark)

`valid?`でバリデーションを手動で実行できる。
>Active Recordでバリデーションが行われた後は、errors.messagesインスタンスメソッドを使うと、発生したエラーにアクセスできます。

>errors[:attribute]を使うと、特定のオブジェクトの属性が有効かどうかを確認できます。このメソッドは、:attributeのすべてのエラーの配列を返します。指定された属性でエラーが発生しなかった場合は、空の配列が返されます。
>[Active Record バリデーション \- Railsガイド](https://railsguides.jp/active_record_validations.html#%E3%83%90%E3%83%AA%E3%83%87%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%81%AE%E6%A6%82%E8%A6%81-errors)

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @masuyama13 バリデーションの部分、今までなんとなくやっていたので細かいところを理解できてよかった

- @hogucc minitestのモックとスタブはほとんど使ったことなかったので勉強になりました！自分でも後で書いてみようと思います

- @ikuma-t テストのプラクティスの時にモックの部分読んだんですが、よくわからなかったので、今日理解できてよかったです。

- @chiroru モックとスタブ、こういう風に使うんだと勉強になりました。