# 【第45回】パRails輪読会ノート(2021-6-27)
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
%w[sanfrecce_osaka hogucc asya81].
  partition { |user| !%w[].include?(user) }.
  flat_map(&:shuffle)
  # => ["sanfrecce_osaka", "hogucc", "asya81"]
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
p.422



## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- @hogucc pre-commit(npm)
    - https://www.npmjs.com/package/pre-commit
- @sanfrecce-osaka
    - [husky](https://www.npmjs.com/package/husky)
    - [pre-commit gem](https://github.com/jish/pre-commit)
- @sanfrecce-osaka
    - rubocop 盲目的に 従うな
    - 575
- @sanfrecce-osaka
    - airbnb https://github.com/airbnb/ruby
    - cookpad https://github.com/cookpad/styleguide

- @asya81 コーディング規約は皆さん何を使ってるんだろう？
- @asya81 RoboCopのデフォルトの「The Ruby Style Guide」をそのまま使うでもよいのかな？
    - @asya81 RuboCopデフォルトの設定はかなり厳しいらしい。なるほど。
- @sanfrecce-osaka
    - https://github.com/testdouble/standard
    - https://qiita.com/takahashim/items/e51927d473f18c2bc73a
    - https://github.com/prettier/plugin-ruby
    - https://github.com/rubocop/ruby-style-guide
    - https://github.com/fjordllc/rubocop-fjord
    - https://docs.komagata.org/5750
- @hogucc RubyStyleGuide
    - https://rubystyle.guide/

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @asya81 RuboCopの実際の導入イメージができて良かった！
- @asya81 お仕事でもまずはtodoで導入してみて、チームでワイワイ設定を検討できると良さそう😊 やってみます！
  - @hogucc :+1: 
- @hogucc Gitのコミット前フック便利そう
- @hogucc RuboCopはプロジェクトの初期段階からいれておきたい
- @sanfrecce-osaka 途中から rubocop 入れるのはやっぱり大変 :sob: 
