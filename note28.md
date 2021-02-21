# 【第28回】パRails輪読会ノート(2021-2-21)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会：  @kyo
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
    - 今日のテーマ：最近買ってよかったもの
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：最近買ってよかったもの

- hogucc（おぐち）
    - スクラム開発、自作サービス、就活
    - 最近買ってよかったもの: Rubyレシピブック
      - [Rubyレシピブック 第3版 303の技](https://www.amazon.co.jp/Ruby%E3%83%AC%E3%82%B7%E3%83%94%E3%83%96%E3%83%83%E3%82%AF-%E7%AC%AC3%E7%89%88-303%E3%81%AE%E6%8A%80-%E9%9D%92%E6%9C%A8-%E5%B3%B0%E9%83%8E/dp/4797359986)

- @Kyo18 (岸)
    - Rspecの勉強、RubySilverの勉強
    - 最近買ってよかったもの:ニトリのワークチェア

- @ikuma-t
    - オブジェクト指向ボウリング
    - 最近買ってよかったもの：Webカメラ

- @sanfrecce-osaka(もりつか)
    - プラクティス: Machida.rb の準備
    - 最近買ってよかったもの： 吉野家の牛皿ファミリーパック(4人前)

- @masuyama13 
    - 自作アプリ開発
    - 最近買ってよかったもの：nosh

- @igaiga
  - プラクティス: 執筆
  - 最近買ってよかったもの: NeoChiPillOw https://www.crossmarche.jp/f/neochi

## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[hogucc sanfrecce_osaka Kyo18 ikuma-t igaiga masuyama13].
  partition { |user| !%w[sanfrecce_osaka igaiga masuyama13 ikuma-t chiroru].include?(user) }.
  flat_map(&:shuffle)
```

 ["hogucc", "sanfrecce_osaka", "Kyo18", "masuyama13", "igaiga", "ikuma-t"]

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
8章から


## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- https://api.rubyonrails.org/classes/ActionView/Helpers/FormBuilder.html#method-i-check_box
    - form_with から直接呼び出しているのはこっち
- https://api.rubyonrails.org/classes/ActionView/Helpers/FormHelper.html#method-i-check_box
    - FormBuilder のメソッドがこっちを呼び出している

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @Kyo18 久しぶりの参加でした！Gitの問題が起きていてドラーバーになったのにモブプロができませんでしたが、きちんと直してまた参加します！
- @hogucc 久しぶりにドライバーやったので緊張しました
- @hogucc とりあえず勉強会が終わったらmacを再起動します😭 
- @hogucc 個人的にフォームヘルパーをもっと勉強する必要がありそう...
- @chiroru githubの認証問題、自分にも起こり得るから気になる
- @ikuma-t Gitはカオス...。たまにしか設定しないから、自分にエラーが発生したときも？になりそう。
- @masuyama13 フォームヘルパーとか前勉強したのにまたわからなくなった😩勉強しなければ！
- @igaiga GitHubの認証、ちゃんと聞いてなかったのですがSSHプロトコルでも同じ問題起きますか？
- @sanfrecce-osaka 画像アップロード機能ができた〜 :tada: 