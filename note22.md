# 【第22回】パRails輪読会ノート(2021-1-10)
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
    - 今日のテーマ：今年やりたいこと
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：今年やりたいこと

- @hogucc（おぐち）
  - スクラム開発、就活
  - 今年やりたいこと
    - 就職&フィヨルドブートキャンプ卒業
    - コロナがおさまったら旅行がしたい
    - duolingoを継続する
    - OSSに貢献したい

- @masuyama13 (マスヤマ)
    - スクラム開発
    - 就職、帰省、飲み会

- @igaiga
    - 最近はRubyの勉強をしています
    - 今年やりたいこと: Rubyに詳しくなってPR投げる

- @ikuma-t
    - ユーザフォロー
    - 今年やりたいこと：Rubyコミュニティ参加、寿司打TOP100、FJORD卒業

- @chiroru (ちろる)
  - スクラム開発
  - 今年やりたいこと：就職して実家を出る

- @kazuyasai10
    - データーベース設計
    - フィヨルドブートキャンプを卒業する
    - 今回初参加で見学のために参加させていただきました。よろしくおねがいします。

- @sanfrecce-osaka(もりつか)
    - ツール作成して手作業自動化
    - 今年やりたいこと: Rails にコントリビュートする

## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[masuyama13 ikuma-t hogucc chiroru igaiga].
  partition { |user| !%w[ikuma-t chiroru].include?(user) }.
  flat_map(&:shuffle)
  # => ["ikuma-t", "chiroru", "masuyama13", "hogucc", "igaiga"]
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
６−7−1 「イベント参加処理の作成」から

## 疑問点・気づき

- ActiveRecord::Associations::CollectionProxy#buildにnewがaliasされてる
  - https://github.com/rails/rails/blob/914caca2d31bd753f47f9168f2a375921d9e91cc/activerecord/lib/active_record/associations/collection_proxy.rb#L316-L319
  - @hogucc ありがとうございます！
- [ActiveRecordのjoinsとpreloadとincludesとeager_loadの違い](https://qiita.com/k0kubun/items/80c5a5494f53bb88dc58)
  - @hogucc preloadはテーブルをJOINしないので、SQLの発行回数は１回増えるけどテーブルの件数の増加がパフォーマンスに大きく影響することはなさそう
  - @hogucc includesはRailsがeager_loadにするかpreloadにするかの挙動をよしなに選択してくれる
- [link_to](https://api.rubyonrails.org/v6.1.0/classes/ActionView/Helpers/UrlHelper.html#method-i-link_to)
- 式全体が真または偽であることが決定するまで、左辺から順に式を評価する

```rb
 1 && 2 && 3      #=> 3
 1 && nil && 3    #=> nil
 1 && false && 3  #=> false
 
 nil || false            #=> false
 false || nil            #=> nil
 nil || false || 2 || 3  #=> 2
```

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい


## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @hogucc （覚書）スクラム開発に入っていない人にreviwerになってもらうために、bootcampのコラボレーターに追加したい
  - komagataさんにスクラム開発に入っていない人をコラボレーターに追加することが問題ならないか確認する
  - なければ、やりたい人本人からkomagataさんへコラボレーターへの追加を依頼してもらう
  - ↑　@hogucc すみません、すっかり忘れてました...
- @hogucc 今まではあまり考えずにincludesを使っていたけど、preloadやeager_loadとの使い分けがとても勉強になった
- @hogucc ikuma-tさん、継続的に参加していただいて嬉しいです！！
    - @ikuma-t ✌️
- @sanfrecce-osaka N + 1 の件や Git の使い方等、色々とディスカッションや知見共有ができた
- @chiroru 初参加された方がdestroyよくわからなかったと言われていたのが申し訳なかったです・・ドライバーとしてもっと話しやすい雰囲気にできればよかった・・
- @ikuma-t 自分もhamlとかわからないままモブプロやっているので、もっといろんな人に参加して欲しい
- @ikuma-t モブプロ、ドライバーは入力待ちにすべきか悩む。ズンズン書いていって、あとで話す時間を増やした方がいいのかな
- @masuyama13 includes全然わかってなかった…
- @kazuyasai10 Git等の使い方やプログラミングしている画面が見れて勉強になりました！
