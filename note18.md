# 【第18回】パRails輪読会ノート(2020-12-06)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @chiroru
タイマー： @ima1zumi
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
    - 今日のテーマ：国内で行きたいところ
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：国内で行きたいところ

- @hogucc（おぐち）
    - スクラム開発、就活
    - 国内で行きたいところ:岐阜（白川郷）、金沢、どこかの温泉地

- @sanfrecce-osaka(森塚)
    - 現在のプラクティス
        - 来週日曜のRubyアドベントカレンダーの記事作成
    - 今日のテーマ：国内で行きたいところ
        - 北陸
            - ブリ :fish: が食べたい
        - 関西
            - 里帰りしたい

- @masuyama13 （マスヤマ）
    - スクラム開発
    - 国内で行きたいところ：松本

- @chiroru (ちろる)
  - スクラム開発
  - 国内で行きたいところ：岐阜県奥飛騨の温泉(名古屋から高速で3時間くらい)
 
- @ima1zumi 
    - 自作サービス
    - 国内で行きたいところ：富山、福井

- @Kyo18（岸）
  - スクラム開発/自作サービス
  - 国内で行きたいところ:銀山温泉(山形県)
  - http://www.ginzanonsen.jp/
  　　- @hogucc このフローチャートやったら銀山温泉でした
  　　　  - https://togetter.com/li/1629117 

## ドライバーガチャ

モブプロのドライバーをしたい方は↓に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[ima1zumi masuyama13 hogucc sanfrecce-osaka Kyo18 chiroru].
  reject { |user| %w[sanfrecce-osaka ima1zumi masuyama13 igaiga hogucc ikuma-t].include?(user) }.
  shuffle
=> ["chiroru", "Kyo18"]
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
6-3-6 から

## 疑問点・気づき
- @hogucc controllerとviewの両方で使いたいメソッドはcontrollerでhelper_methodとして定義する
  - viewだけで使う場合はhelperフォルダにxxx_helper.rbを作ってメソッドを定義する
  - [ControllerとViewの両方で使いたいメソッドの定義方法 - hogucc's box](https://scrapbox.io/ukuh1r8-86980398/Controller%E3%81%A8View%E3%81%AE%E4%B8%A1%E6%96%B9%E3%81%A7%E4%BD%BF%E3%81%84%E3%81%9F%E3%81%84%E3%83%A1%E3%82%BD%E3%83%83%E3%83%89%E3%81%AE%E5%AE%9A%E7%BE%A9%E6%96%B9%E6%B3%95)
- @hogucc true、falseのいずれかを返したい場合はnot演算子(!)を二つ重ねる
- @hogucc yarn installの--check-filesオプションをつけると、node_modules に既にインストールされたファイルが削除されていないことを確認する
  - [yarn install | Yarn](https://classic.yarnpkg.com/ja/docs/cli/install/)

- @chiroru
  - テーブルの「null:false」と、モデルの「presence:true」は役割が異なる。
    - 「null:false」は空文字を許容する
    - 「presence:true」は空文字を許容しない
  - ローカルブランチ削除：
    - `git branch -D branchname`(変更を無視)/`git branch -d branchname`
  - リモートブランチ削除：
    - `git push -d origin branchname`(=`git push origin :branchname`)
- @hogucc
  - PRの書き方についてはこちらも参考になるかもです
    - [レビューしてもらいやすいPRの書き方 - hydrakecat’s blog](https://hydrakecat.hatenablog.jp/entry/2018/06/30/%E3%83%AC%E3%83%93%E3%83%A5%E3%83%BC%E3%81%97%E3%81%A6%E3%82%82%E3%82%89%E3%81%84%E3%82%84%E3%81%99%E3%81%84PR%E3%81%AE%E6%9B%B8%E3%81%8D%E6%96%B9)

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- 

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！
- @chiroru 初のドライバー！緊張したけど楽しかったです！！
    - @sanfrecce-osaka :clap: 
- @masuyama13 gitがまだまだわかってない…😓毎回学びがあって勉強になります！！

- @hogucc gitの操作、細かい挙動がわかっていなかったりするので、みんなで知識を持ち寄って理解していく感じがすごく良かったです

- @ima1zumi `!!` で true/falseだけを返すようにするのよくわかってなかったので勉強になった！

- @ima1zumi main への push を防止した
    - [GitHubでmasterブランチへのダイレクトプッシュを防ぐ方法 – Memoteki](https://memoteki.net/archives/2592)

- @ima1zumi [File Icons for GitHub and GitLab \- Chrome Web Store](https://chrome.google.com/webstore/detail/file-icons-for-github-and/ficfmibkjjnpogdcfhfokmihanoldbfe/related?hl=en) かわいい

- @sanfrecce-osaka 今回もモブプロ楽しかった〜 :laughing: 

- @Kyo18 初ドライバーめちゃくちゃ楽しかったです！ドライバーをやりながらだとその都度出てきた疑問を聞きやすいので、モブプロの学習効率が良いと言われる理由がよくわかりました！