# 【第16回】パRails輪読会ノート(2020-11-22)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会：@masuyama
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
- ドライバーガチャ
- モブプロ(10:10まで)
    - 途中で5分休憩を入れます (9:30頃)
    - 疑問はその場でどんどん出してください！
- 振り返り記入 (3〜5分)
- 振り返り・雑談 (10:30まで)


## 自己紹介の記入をお願いします！
> - フィヨルド生
    - 名前(@username + 呼び名)
    - 現在のプラクティス 
    - 最近よくやっていること（趣味）
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 最近よくやっていること（趣味）

- @masuyama13 (マスヤマ)
    - スクラム開発
    - 最近よくやっていること：YouTube大学を見る

- @igaiga
    - Rails歴: 10年 / プラクティス: 講演資料つくり
    - 最近よくやっていること（趣味）: 経理をする、本を読む

- @ima1zumi 
    - スクラム、就職活動
    - 最近よくやっていること：ゲーム（ペルソナ5R）

- @hogucc
  - スクラム開発、就活
  - 最近よくやっていること（趣味）：リングフィットアドベンチャー、読書

- @ikuma-t
    - Railsの基本を理解する
    - 最近よくやっていること：筋トレ動画をみる

- @sanfrecce-osaka(森塚)
- 現在のプラクティス 
    - GitHub Actions
- 最近よくやっていること（趣味）
    - 404 暇 is not found
    - 勉強会参加
    - 自炊のレパートリー増やし

- @yana-gi
    - Rails ユーザー認証が終わってomniauthでGitHub認証に入るところ
    - ポケモン盾　冠の雪原
        - ima1zumi DLC買ったのにやってない..やろう
        - yana-gi ストーリー面白いので是非！

## ドライバーガチャ

モブプロのドライバーをしたい方は↓に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
# ドライバーをしたい方は↓の配列に名前を書いておいてください〜
%w[sanfrecce-osaka ima1zumi hogucc masuyama13 igaiga].
  select { |user| !%w[sanfrecce-osaka ima1zumi].include?(user) }. # 前回ドライバーをした人を除くための処理
  shuffle
=> ["masuyama13", "igaiga", "hogucc"]
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


## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

### 気づき・雑談

- Gemfile の ~> はメジャーバージョンを上げないようにインストールする
- 認証は Rack ミドルウェアをよく使う
- omniauth は外部のサービスに認証を移譲する
- credentials を編集するには config/master.key が必要
- ログイン > GitHub上で認証 > Rails 側の /auth/github/callback が呼ばれる
- peco

### 質問

- 

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @masuyama13 モブプロは楽しい！igaigaさんのエディタとか興味あったので見られてよかったです。エイリアスとかもかっこよかったです！
    - @igaiga Emacsっていう最新エディタをつかってます！
    - @sanfrecce-osaka Vim ではないんですね (っ'-')╮ =͟͟͞͞ :bomb: 
- @ima1zumi `gh` 便利そうで入れようと思いました！
    - @igaiga https://github.com/cli/cli
- @ima1zumi `master.key` push してるから私のclient-secretが見える状態なのが気になるけど解決方法も思い当たらない
    - Callbackを `http://localhost:3000/auth/github/callback` に設定しているから漏れてもlocalhost以外で動かなさそうだからいいか、と思った
    - @igaiga いま思いついたのですが、masker.keyをリポジトリから外して、その内容をFjord Slackで共有する方がマイルドになるかもですね

- @sanfrecce-osaka GitHub のところは準備不足でした(反省) :bow: 
- @sanfrecce-osaka GitHub CLI :yosasou:

- @igaiga 3億年ぶりにViewのコード書けて楽しかったです！

- @ikuma-t 他の人がコードを書いているところがみられて勉強になりました！omniAuthぶっつけだったので、キャッチアップが若干厳しかったです。
- @ikuma-t localhost:3000を自動で開く設定はRubyMineでもたしかできたような... 

- @hogucc igaigaさんが使われていたコマンドのエイリアスが便利そうで、自分も登録してみようという気持ちになりました
- @hogucc モブプロ、前回以上にみんなでわいわい感が出ていてよかったと思います！

- @yana-gi OAtuh認証のプラクティスに入る前に最初の流れをみることができてラッキーでした！
- @yana-gi forkしてPR送る流れがよく分かってないので復習しておきたい
