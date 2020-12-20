# 【第20回】パRails輪読会ノート(2020-12-20)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @kyo
タイマー： @masuyama
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
    - 今日のテーマ：一度住んでみたい場所
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：一度住んでみたい場所

- @Kyo18 (岸)
  - プラクティス：スクラム開発/自作サービス開発/引っ越し
  - 今日のテーマ：広島市内に住みたい！

- @masuyama13 (マスヤマ)
    - スクラム開発
    - 海外…？

- @chiroru (ちろる)
　　- プラクティス：スクラム開発/自作サービス(?)
　　- 今日のテーマ：北海道か長野か鳥取

- @hogucc（おぐち）
  - プラクティス:スクラム開発/就活
  - 一度住んでみたい場所:鎌倉、西荻窪 

- @ikuma-t
  - プラクティス：Railsのi18nを理解する
  - 今日のテーマ：金沢に住みたい

- @sanfrecce-osaka(森塚)
    - 現在のプラクティス: 今週金曜の Advent Calendar の準備
    - 一度住んでみたい場所: 福岡

- @igaiga
    - プラクティス: 書類仕事
    - 一度住んでみたい場所: 丘の上

## ドライバーガチャ

モブプロのドライバーをしたい方は↓に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[masuyama13 hogucc sanfrecce-osaka Kyo18 igaiga chiroru ikuma-t].
  reject { |user| %w[ima1zumi chiroru].include?(user) }.
  shuffle
```

```ruby=
 ["Kyo18", "igaiga", "hogucc", "sanfrecce-osaka", "ikuma-t", "masuyama13"]
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
6-4-6から

## 疑問点・気づき

- @Kyo18 p.316 リスト6．33の文章が「i18n-rails」となってます！（本文ではrails-i18n）

- @Kyo18 `範囲選択+shift+>`でインデントの追加ができる(vim)
- @sanfrecce-osaka RubyMine のメモリ割り当てを増やす方法
    - https://pleiades.io/help/ruby/increasing-memory-heap.html

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- 

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！


- @sanfrecce-osaka RubyMine の GitHub連携 で Pull Request をレビューできた :raised_hands: 
- @sanfrecce-osaka View とかの長いコードは @igaiga さんみたいにコピペしてしまった方が良かったのかもしれない :thinking_face: 
- @hogucc RubyMineが重くなってしまったので対処したい...
- @masuyama13 モブプロは見ているだけで勉強になるし面白い
- @ikuma-t fjordのリポジトリのコントリビューターでないと、レビューができないので、可能であれば参加者は追加しておきたいと思いました！
    - @sanfrecce-osaka 次から参加者は全員 Collaborator に追加していく方針でやってみます〜 :pray: 
- @ikuma-t upstreamを反映する流れをまとめておくと、初参加の方がやりやすい気がします
    - @sanfrecce-osaka :+1: 
- @chiroru ：今日はいつもよりドライバーやってもらえた！igaigaさんのモブプロ見られたの嬉しい。zoomのが通信状態がやっぱり良い気がした。

- @Kyo18 @igaigaさんのモブプロを初めて拝見しましたが、エラーが起きた際にどこに原因があるのか目星をつけるのがとても早く、原因を見つける過程がとても勉強になりました！RubyMineの新たな知識も仕入れられたので満足です！
    - @masuyama13 @igaigaさんのエラー発見＞それ思いました！