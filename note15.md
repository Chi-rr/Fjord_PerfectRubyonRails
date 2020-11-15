# 【第15回】パRails輪読会ノート(2020-11-15)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @kyo
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
- 目的
- 輪読
  - 読書&hackmdに疑問点・気づきを記入(マイクオフ・[タイマー](https://timer.onl.jp/)使用)
  - 疑問点・気づきを確認(都度)
- 振り返り(10分くらい)

※休憩はなしでやってみます！

## 自己紹介の記入をお願いします！
> - フィヨルド生
    - 名前(@username + 呼び名)
    - 現在のプラクティス 
    - お気に入りの家電・ガジェットがあれば教えて下さい。
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - お気に入りの家電・ガジェットがあれば教えて下さい。


 - @ima1zumi
     - スクラム、就職活動
         - ransack と OOP と格闘中
     - お気に入りの家電
         - 人感センサーのライト
         - トラックボール
 
- @sanfrecce-osaka(森塚)
    - 現在のプラクティス
        - るりまへのプルリク
    - お気に入りの家電・ガジェットがあれば教えて下さい。
        - ルンバe5
        - シロカのお料理ケトル

- @yana-gi （やなぎ）
    - Rails devise（Rails難しい）
    - マキタのコードレスクリーナー
    - 見学参加です！

- @masuyama13 (マスヤマ)
    - スクラム開発
    - Kindle?

- @chiroru(ちろる)
  - プラクティス：スクラム開発
  - お気に入りの家電・ガジェット：卓上アロマディフーザー(加湿器？)

- @universato(ユニ)
  - プラクティス:スクラム開発の序盤
  - 久しぶりの参加。布団乾燥機をよく使っています。温かい。

- @kanazawa（かなざわ）
    - 卒業生（初参加）
    - 最近買ったAirpods Pro
 
- @hogucc（おぐち）
  - プラクティス：スクラム開発
  - お気に入りの家電・ガジェット：ホットクック
    
- @Kyo18 
  - スクラム開発、自作サービス開発、就活
  - SONYのノイズキャンセリングヘッドホンWH1000XM3

## ドライバーガチャ

モブプロのドライバーをしたい方は↓に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[ima1zumi masuyama13 hogucc sanfrecce-osaka chiroru Kyo18].shuffle
=> ["sanfrecce-osaka", "ima1zumi", "chiroru", "masuyama13", "hogucc", "Kyo18"]
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
>### 書き込みサンプル
>@アカウント名 Rails楽しい 

- @Kyo Railsのコマンドを実行すると毎回「使用しているbundlerが古い」的な警告が出るんだけど直し方が未だに分かっていない…

- @ima1zumi rails new を最小でやる方法: https://scrapbox.io/ima1zumi/rails_new_%E6%9C%80%E5%B0%8F

- @Kyo18 スキップオプションの省略形 [railsコマンド\(rails\) \| Railsドキュメント](https://railsdoc.com/rails)→非推奨サイト

- @hogucc [カレントディレクトリに rails new したい - ltcmdr927atenablog](https://ltcmdr927.hatenablog.jp/entry/2014/04/10/174333)

- @sanfrecce-osaka Ruby on Railsを使った開発で参照してもよいドキュメント
    - https://qiita.com/hanachin_/items/76a24bcef889edb59d19

- @universato ブランチ名の変更は、内部的にファイル名変更するのがメインで、かなり軽い作業のはず。
- 1度コミットすると、ブランチ名を変更できる。master -> main
- `.gitignore`に`/vendor/bundle`を入れる。`/.idea`はRubyMineのファイル。
- RubyMineは、⌘Eで最近参照したファイル
- @hogucc RubyMineは、⌘+option+Aでgit addできる

- 柴田さん曰く、引数なしの`bundle`コマンドは、今後ヘルプ表示になるらしい。
- [routes\.rb の読み方は「ルーツ」じゃない！！ \- Qiita](https://qiita.com/RyuGotoo/items/86e2e53cd3383bb0a618)
  - rootとroutesの区別のために違う読みにしているのでは、と書かれている。

- p.285 図6．3内の`Find me in ~`の文章が`index.html.haml`ではなく`index.html.erb`のままになっている。
  - p.287も誤り。p.296で直っている。



## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka 他の人の作業見たり聞いたりするのやっぱり楽しい :sparkles: 
- @sanfrecce-osaka ドライバーとして参加しなくても良くして気軽に参加できるようにしたのよかった :raised_hands: 
    - @sanfrecce-osaka 今後はドライバーも気軽にできるようにしていきたいなぁ :thinking_face: (今回見学枠だった人の感想とかを聞きたい)

- @chiroru いろんなエディタの小話なども聞けて面白かったです！
- @chiroru わいわいできて楽しかった！

- @hogucc RubyMineの便利機能が知れてよかったです！
- @hogucc ドライバーの二人とも作業がスムーズだったので、自分が作業するときこんなにうまくできるかちょっと心配になりました😅
    - @masuyama13 ググり方も見たい😁

- @masuyama13 本で作業の流れはわかると思いきや、人の作業を見ると知らないことがたくさんあって勉強になった！！ドライバーもやってみたい

- @yana-gi 他の方の作業をみるのが勉強になり楽しかったです！
- @yana-gi タグジャンプ切望していたので早速Rubymineダウンロードしてみました
    - @sanfrecce-osaka やったぜ :raised_hands: 

- @universato モブプロなんとなくでしか知らなかったけれど、今回初めて見て勉強になりました。もう少しzshやらVS Codeやら鍛えていきたいな(?)と思いました。ドライバーも楽しそうと思ったけれど、この先もっと難しくなるのかなと思うので、ドライバーもどんどん大変になりそうと思いました。

- @ima1zumi 他の人の作業が見られるの面白いし勉強になってすごく楽しいです！
- @ima1zumi RubyMineの便利機能をVimにも入れるぞ！！とやる気が出たのでよかったです
  - git commit するときに TODO を見る？っぽい機能とか気になった
  - Rubocop 自動で回す機能, end挿入, ctag を入れたい
  - ちなみに自分の shell は zsh です
- @ima1zumi git, GitHub のことについても質問できてよかった

- @kanazawa RubyMineの便利さを知れてよかったです（お試しダウンロードしました）。
    - @sanfrecce-osaka やったぜ :raised_hands: 

- @Kyo18 ここまでしっかり参加するモブプロは初めてだったので新鮮で面白かったです！RubyMineのショートカットだったり、Gitのコミットの粒度だったりモブプロならではの話が出てきて非常に勉強になりました！

- @Kyo18 ドライバーの交代のタイミングが結構むずかしいですね〜