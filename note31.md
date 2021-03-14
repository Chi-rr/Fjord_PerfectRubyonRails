# 【第31回】パRails輪読会ノート(2021-3-14)
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

## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[sanfrecce_osaka igaiga masuyama13 ikuma-t hogucc chiroru].
  partition { |user| !%w[masuyama13 sanfrecce_osaka hogucc].include?(user) }.
  flat_map(&:shuffle)
# => ["chiroru", "ikuma-t", "igaiga", "masuyama13", "hogucc", "sanfrecce_osaka"]
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
p.392 8-2

## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- ActiveSupport の String#truncate
    - https://railsguides.jp/active_support_core_extensions.html#truncate
- @hogucc
    - [特殊文字リファレンス](http://www.htmq.com/text/)
- @ikuma-t
    - [kaminariのHelper](https://github.com/kaminari/kaminari#helpers)
- @hogucc
    - [VS Code：エディタの行折り返しをデフォルト設定にする | 電脳産物](https://dianxnao.com/vs-code%EF%BC%9A%E3%82%A8%E3%83%87%E3%82%A3%E3%82%BF%E3%81%AE%E8%A1%8C%E6%8A%98%E3%82%8A%E8%BF%94%E3%81%97%E3%82%92%E3%83%87%E3%83%95%E3%82%A9%E3%83%AB%E3%83%88%E8%A8%AD%E5%AE%9A%E3%81%AB%E3%81%99/)

- @chiroru 
```html
= paginate @events, window: 1, outer_window: 0
```

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @hogucc kaminariのソースコード読んでみるのおもしろそうだなと思いました
- @hogucc fixupのやり方を覚えた
- @hogucc `force push`のオプションはブランチ名の後につけても有効になることがわかった
- @sanfrecce-osaka 横道で色々と盛り上がれたのでよかった(ページ的にはあんまり進まなかったけど無問題)
  - @chiroru 🙇‍♀️✨
- @sanfrecce-osaka kaminari に bootstrap 用のテーマが用意されていることがわかった
    - そして tailwind や bootstrap5 のテーマがなければコントリビュートチャンスかも？ということもわかった
- @ikuma-t kaminariはさらっと触っただけだったので、中の仕組みが垣間見えて面白かったです。link_to_unless初めて知りました。
- @chiroru vscodeのcommit -m機能を積極的に使っていこう。gitgraphも色々できることがわかった
- @chiroru kaminari用のviewが用意されているの知らなかった
- @masuyama13 RubyMine に頼りっきりで rebase -i 全然わからん
  - https://chiroru-memo.hatenablog.com/entry/2020/12/30/190535
