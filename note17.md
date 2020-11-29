# 【第17回】パRails輪読会ノート(2020-11-29)
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
    - 今日のテーマ：おすすめの防寒対策グッズ
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：おすすめの防寒対策グッズ

- @Kyo18(岸)
　　- スクラム開発/自作サービス開発/引っ越しの諸々 
　　- 最近はスープにしょうがをたっぷりすりおろして入れています！

- @igaiga
    - Rails歴: 10年 / プラクティス: 経理作業と講演資料づくり
    - 足が冷えるのでアンカがあったかくて良いです

- @ima1zumi 
    - 自作サービス作成(スクラム、就活終わった 🙌 )
        - @sanfrecce-osaka :tada: :tada: :tada:
    - 貼るホッカイロ、ホットマット、もこもこした上着、保温性の高いマグカップに温かい飲み物を入れる、足の冷えない不思議な靴下

- @ikuma-t
    - Railsの基本を理解する
    - 鍋食べるのがいいです、柚子醤油鍋がおすすめ
    - [コク旨スープがからむ 至福のゆず醤油鍋用スープ｜商品情報｜モランボン](https://www.moranbong.co.jp/product/detail/id=3356)

- @hogucc（おぐち）
    - スクラム開発、就活
    - 電気ひざかけ

- @masuyama13 (マスヤマ)
    - スクラム開発
    - 防寒対策：毛布

- @sanfrecce-osaka(もりつか)
    - 現在のプラクティス 
        - Machida.rb 準備
    - おすすめの防寒対策グッズ
        - 毛布を膝にかける
        - 靴下を履く
        - ヒートテック
        - 白湯を飲む
        - 最終兵器エアコン

- @Saki(さき)
  - DB設計(Railsにまだ行ってないです)
  - 防寒対策:エアコンよりオイルヒーターのほうが足元もあったまって良いです
  - 見学させていだだきます。よろしくお願いします!
      - @sanfrecce-osaka ようこそ〜 :raised_hands: 

- @chiroru (ちろる)
  - スクラム開発
  - 白湯！
  - (本日見学枠でお願いします🤲)
　    - @sanfrecce-osaka :+1: 

## ドライバーガチャ

モブプロのドライバーをしたい方は↓に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[ima1zumi masuyama13 hogucc sanfrecce-osaka Kyo18 ikuma-t].
  reject { |user| %w[sanfrecce-osaka masuyama13 igaiga].include?(user) }.
  shuffle
```
=> ["hogucc", "ikuma-t", "Kyo18"]

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

6-3-5 のコントローラの作成から

## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- credentialsを表示して現在の内容をコピペください
    - $ bin/rails credentials:show
    - secret_key_baseは作り直すので捨ててください
- credentials editで credentials.yml.enc作り直してください
    - $ rm config/credentials.yml.enc
    - $ bin/rails credentials:edit
    - GitHubで発行されたトークンを再発行
- master.keyを.gitignoreに追加、rmしてgitリポジトリから外してください
  - `$ git rm --cached [ファイル名] `
- 動作確認


- bin/rails s -p 3001
    - これでポート番号を変えれる

- [Rails 4\.1以降のコンソールコマンドは必ず bin/ を付けなきゃいけないの？ \- Qiita](https://qiita.com/jnchito/items/c5a0848144203dce6e26)

- [Active Record の基礎 \- Railsガイド](https://railsguides.jp/active_record_basics.html#%E3%83%90%E3%83%AA%E3%83%87%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%EF%BC%88%E6%A4%9C%E8%A8%BC%EF%BC%89)

- Pull Request のテンプレートのサンプル
    - https://dev.classmethod.jp/articles/pull-request-template/

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka @igaiga さんによる Pull Request の書き方指南、参考になる！ :laughing: 
    - @sanfrecce-osaka 仕事での書き方見直そう :thinking_face: 
- @sanfrecce-osaka ログイン処理が追加された！ :tada: 

- @ikuma-t 1人でやっていると曖昧にしがちなコミットメッセージ、プルリクの書き方がとても参考になりました！
    - @ikuma-t プルリクをちゃんと書くためには、「動いた！直った！」ではなくて、事象とやるべきことを整理してコードに望むべき。
    - @ikuma-t 1人で写経する時にもこのマインドでよんだら良さそう
- @ikuma-t はじめてキードライバーで緊張しましたが、内容を読み上げてもらえるのでとてもやりやすかったです


- @ima1zumi igaigaさんのPRの書き方講座参考になりました！ レビューする側の視点で考えられるようになりました。
    - 「目的」「変更前はどうだったか」「変更後にどうなるのか」を書く
        - チームによっては「このPRはビジネス的に（顧客に）どういう価値を提供できるのか」を書く
- @ima1zumi `master.key` がGitHubに上がってるの気になっていたので、解決できてスッキリしました。
- @ima1zumi （連絡） `master.key` を毎週 bot に投稿させるのもどうかと思ったため、 bot に仕込むのはやめました。運営側で都度zoomのチャットでリンク共有できればと思います。
    - HackMDには貼らないでくださいね！（編集履歴に残ってしまうため）
    - @sanfrecce-osaka :+1: 
    - @hogucc :+1: 

- @masuyama13 コミットメッセージやPRの書き方、Git・RubyMineの使い方など全部が勉強になりました！モブプロやると毎回自分が知らなかったことをたくさん学べるのでうれしいです

- @hogucc PRの書き方すごく参考になりました！（自分のターンのときdescriptionを書いてなかったので反省...）
- @hogucc master.keyの書き換えは初めてやった作業だったので勉強になりました

- @Saki モブプロ初めて参加させていただきましたが、一人でコードを書くときよりも、フィードバックをその場ですぐいただけるので、とても勉強になると感じました。
- @Saki 自分がPRするときにどんなことに注意すればいいのか、とても参考になりました
- @Saki HackMD初めて使いましたが、一人で黙々とまとめることしかしたことが無かったので、参加者みんなで一つのドキュメントをリアルタイムで作り上げていくのがとても良いなと思いました。

- @chiroru hoguccさん初の司会お疲れ様でした！！
    - @hogucc ありがとうございます！
- @chiroru PRの書き方とても勉強になりました。

- @Kyo18 今まで自分があまり考えずにコミットメッセージを作っていたことを痛感しました・・・。これから読む人が状況を理解しやすいようなコミットメッセージを心がけたいと思います！
- @Kyo18 RubyMineユーザーが多くて、ショートカットの情報がすごくありがたい！ちゃんと使ってなれるようにします！