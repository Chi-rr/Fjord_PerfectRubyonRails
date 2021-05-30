# 【第41回】パRails輪読会ノート(2021-5-30)
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
    - 今日のテーマ：最近どう？
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：最近どう？
 

### zoom の画面共有について

- zoom で画面共有ができるか確認しておいてください。
    - 画面共有できない場合、 システム設定 > セキュリティとプライバシー > プライバシー > 画面の録画で zoom.usにチェックを入れます。
    - https://support.zoom.us/hc/ja/articles/201362153-%E7%94%BB%E9%9D%A2%E3%82%92%E5%85%B1%E6%9C%89

### 順番ガチャ

```ruby=
%w[sanfrecce_osaka chiroru hogucc fuga asya81 masuyama].
  partition { |user| !%w[sanfrecce_osaka hogucc chiroru masuyama].include?(user) }.
  flat_map(&:shuffle)
  # => ["asya81", "fuga", "hogucc", "sanfrecce_osaka", "masuyama", "chiroru"]
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
９章から


## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- @sanfrecce-osaka 今は亡き Travis CI。。。(サービス自体はまだあるけど)
- https://note.com/llminatoll/n/n423296287697
- @hogucc pullのオプションいろいろあることがわかった
    - https://git-scm.com/docs/git-pull

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @hogucc @asya81 さん、モブプロありがとうございましたー！
- @hogucc GitHubActions普通に仕事でも使えそうだけど、まだ全然理解できていない...
- @sanfrecce-osaka @asya さん、初コントリビュートおめでとうございます〜 :tada: :tada: :tada: 
- @sanfrecce-osaka モブプロやっぱり楽しいな〜 :waiwai:
- @sanfrecce-osaka GitHub Actions ﾁｮｯﾄﾘｶｲﾃﾞｷﾀ

- @isshi-hasegawa 遅れてしまったので概要の把握に手こずりましたが、RubyMineのGit操作講座みたいで勉強になりました！

- @asya81 RubyMineの使い方を色々知ることができた！モブプロ、勉強になってよい。
- @asya81 git rebase等、gitコマンドについてもっと理解したいと思った。
- @asya81 初コントリビュート、嬉しい ☺️ ありがとうございます〜！ 

- @chiroru git pullにオプション必要になったの知らなかった、勉強になります！
- @chiroru @asya81さんも環境構築を乗り越えついにモブプロデビュー！

- @masuyama13 GitHub Actions 前うまくできなかったので次回楽しみ

- @fuga RubyMineのGit操作便利！
- @fuga GitHub Actionsがとても楽しみ。

- @misosoup 最近出れてなかったのですが、今日も遅れてしまいましたー。来週本格的にGithubActionsのところに入るということで楽しみにしてます。次はちゃんとでたい〜。