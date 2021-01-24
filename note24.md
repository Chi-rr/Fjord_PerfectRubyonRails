# 【第24回】パRails輪読会ノート(2021-1-24)
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
- 休憩挟みつつモブプロ(10:10~15くらいまで)
- 振り返り書く(3~5分くらい)
- 雑談(15分くらい)


## 自己紹介の記入をお願いします！
> - フィヨルド生
    - 名前(@username + 呼び名)
    - 現在のプラクティス 
    - 今日のテーマ：自分のお気に入りの作品
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：自分のお気に入りの作品


- @igaiga
  - 現在のプラクティス: 新しい本を書き始めました
  - 好きなマンガ: アルテ
    
- @sanfrecce-osaka(森塚)
    - プラクティス： 社内勉強会(TypeScript)の準備
    - お気に入りの作品(絞れない・・・汗)
        - ハイキュー
        - 暗殺教室
        - SHIROBAKO
        - ゆるキャン△
        - ガールズ&パンツァー
        - ロボットアニメ全般
        - 特撮ヒーロー全般

- @Kyo18 (岸)
  - プラクティス：発表準備
  - お気に入りの作品：
    - ピンポン
    - PSYCHO-PATH

- @hogucc（おぐち）
  - プラクティス：スクラム開発、就活
  - お気に入りの作品: ジャンプ系の漫画ならだいたい好き

- @chiroru (ちろる)
  - プラクティス：自作サービス、就活
  - お気に入りの作品：Just Add Magic

- @ikuma-t
    - プラクティス：コメントをつける
    - お気に入りの作品：SHIROBAKO、コンフィデンスマン JP

## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[sanfrecce_osaka ikuma-t hogucc Kyo18 igaiga chiroru].
  partition { |user| !%w[ikuma-t chiroru sanfrecce_osaka].include?(user) }.
  flat_map(&:shuffle)
```

["sanfrecce_osaka", "Kyo18", "igaiga", "hogucc", "ikuma-t", "chiroru"]


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

7-3(p.350)

## 疑問点・気づき

- @ikuma-t factory-botを導入すると、generateコマンドでfactory-bot用のファイル（`test/factories/XXX.rb`）が自動生成されるようになる。
    - fixturesの方は作成されなくなる。
- @hogucc Kernel#randメソッド
  - [Kernel.#rand (Ruby 3.0.0 リファレンスマニュアル)](https://docs.ruby-lang.org/ja/latest/method/Kernel/m/rand.html)
- @ikuma-t gitのリモートブランチをローカルから確認する方法（without RubyMine）
    - [ローカルgitリポジトリでリモートのリポジトリURL確認方法 \- Qiita](https://qiita.com/zhao-xy/items/a35add58575ef7d9d4dc)
- @ikuma-t GitHubCLIでPRを作成する&PRをWebで確認する

```bash
gh pr create --fill; gh pr view --web
```

- @chiroru `bin/rails test`は、デフォルトでシステムテストを実行しない
  - `bin/rails test:system`でシステムテストする
  - ※bootcampでは、`$ ./bin/test`で両方実行できる
  - Rails6.1.1~`all`で全て実行できる
```
By default, running bin/rails test won't run your system tests. Make sure to run bin/rails test:system to actually run them. You can also run bin/rails test:all to run all tests, including system tests.
```

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい


## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @Kyo18 久しぶりにfactory-botの復習ができてよかった❗Gitのブランチの森には自分もよく迷いこみます…
- @sanfrecce-osaka Git はむずかしい
- @hogucc git難しい...コミット履歴がおかしくなったときいつも慌ててしまう...
- @chiroru git難しいですね・・あと、 system testは別途やらないといけないのですね🤔
- @ikuma-t テスト初めて見ましたが、rubyのソースを読む感覚で内容が理解できていいなと思いました（細かいところは全然わからないけど）。Gitはカオスだ...