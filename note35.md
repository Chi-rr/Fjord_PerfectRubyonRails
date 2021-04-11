# 【第35回】パRails輪読会ノート(2021-4-11)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @chiroru 
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
    - 今日のテーマ：最近どう？？
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：最近どう？？

- @hogucc（おぐち）
    - プラクティス：自作サービス？
    - 最近どう？？：DMMのキャンペーンで本を9冊買いました
      - https://prtimes.jp/main/html/rd/p/000003737.000002581.html

- @sanfrecce-osaka(もりつか)
    - 現在のプラクティス: 家事
    - 最近どう？
        - 昨日は Hirakata.rb に参加後、Developer eXperience Day CTO/VPoE Conference 2021 とふりかえりカンファレンスを並行参加していた
        - その後 1:00 くらいに目が覚めてふりかえりカンファレンスのアフタートーク的な雑談を Discord でやっていたので 3:00 頃まで参加していた
        - ふりかえりカンファレンスのアフタートーク的な雑談で[komagata さんを知っている方](https://twitter.com/pokotyamu) と会った
        - c.f. [エンジニアの人材不足について本気で考える 〜増やし、育てるためのDeveloper eXperienceとは〜](https://dxd2021.cto-a.org/program/time-table/d-4)

- @chiroru (ちろる) 
  - プラクティス：残すは自作サービス
  - 最近どう：仕事でRails書くことになった

- @masuyama13 （マスヤマ）
    - 最近どう？：昨日SQLドリルを50ページやった

- @fuga 
    - プラクティス：Railsのユーザーフォロー機能
    - 最近どう？：ActiveRecordに苦戦しています。

- @asya81(かわかみ)
	- 現在のプラクティス：CSS上級
	- 今日のテーマ：最近どう？
	    - 輪読会とかモブプロがどんな感じか知りたくて初参加しました！
          業務でRailsを使用していて分からないことばかりなので参加させてもらいました〜。
        - 昨日は鋼鉄婚式でしたが、ふりかえりカンファレンスにも少し参加しました。よろしくお願いします。
        - https://ja.wikipedia.org/wiki/%E7%B5%90%E5%A9%9A%E8%A8%98%E5%BF%B5%E6%97%A5

- @igaiga
    - Rails歴: 10年/プラクティス: Rubyのbacktraceのコードを調べています
    - 最近どう？？: iTerm2のSemantic History機能をつかったら、ターミナルのパスぽいものをcmd+clickしてEmacsが起動するようになって便利


## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[sanfrecce_osaka hogucc chiroru].
  partition { |user| !%w[hogucc chiroru].include?(user) }.
  flat_map(&:shuffle)
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
書籍は8-3から

## 疑問点・気づき
### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- fork元と同じリポジトリ名でなくても、remoteの設定が合っていれば問題ない
- @hogucc `rails db:prepare`はDBが存在すればマイグレーション実行、存在しなければDBのセットアップを実行する
- [Railsアプリケーションにおけるエラー処理（例外設計）の考え方](https://qiita.com/jnchito/items/3ef95ea144ed15df3637)
- @hogucc via: :allを指定すると、すべてのHTTP動詞にマッチする特別なルーティングを作成できます。
  - https://railsguides.jp/routing.html


## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @asya81 初めての参加でしたが、楽しかったです！
- @asya81 RubyMineの使い方も知れて、よかった。見た目変えてみたい。
- @asya81 Railsの例外処理、むずかしかったので、もうちょっと色々触ってみたい
- @sanfrecce-osaka rails むずかしい :innocent: 
- @sanfrecce-osaka @fuga さんにドライバーを経験してもらえた :raised_hands: 
- @sanfrecce-osaka @asya81 さん、初参加ありがとうございます :laughing: 
- @chiroru rescue_from勉強になりました
- @chiroru 司会久しぶりにやると、色々抜け漏れが・・みなさんフォローありがとうございます！ 
- @hogucc 初参加の方がいらっしゃって嬉しい！
- @hogucc 休憩ちゃんととった
    - @sanfrecce-osaka  :+1: 
- @hogucc 時間管理をちゃんとしたい...
- @masuyama13 難しかった。最近あまり参加できてなかったので参加できてよかった
- @fuga はじめてドライバーをやらせていただきとても勉強になりました。
- @fuga 難しい問題に遭遇しましたが、みなさんがどのように解決していくのかを垣間見ることができてよかったです。
- @misosoup 途中参加になってしまいました😇今日のところなんとなくわかったけど難しい〜。こういうときこそ輪読会が生きるな〜と思いました。
- @igaiga 最後の404の問題をまとめたのでこちらにも。ご協力ありがとうございました。🙏 https://esa-pages.io/p/sharing/4060/posts/2337/c5029b78a24f0b93b1ac.html
  - @hogucc まとめありがとうございます🙏