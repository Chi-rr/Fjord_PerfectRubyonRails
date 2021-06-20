# 【第44回】パRails輪読会ノート(2021-6-20)
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
%w[chiroru asya81　hogucc].
  partition { |user| !%w[hogucc].include?(user) }.
  flat_map(&:shuffle)
  # => ["chiroru", "asya81　hogucc"]
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

## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- @hogucc Renovate、初めて聞いた
    - https://github.com/apps/renovate
- @hogucc dependabot、会社によって入れる入れないはまちまちっぽい

- @asya81 Github DependabotだからGithub上でないと使えない？っぽい。
- @asya81 まめにGemを更新するのが大事。そのためにはテストも重要。
- @asya81 RuboCopは「る」ぼこっぷだと分かった！
    - @asya81 DependabotよりはRuboCop入れやすそうなので、お仕事でも導入してみたい。導入するのに必要な準備とかあるのかな？

- https://github.com/dependabot/feedback/issues/439

- @sanfrecce-osaka https://koic.hatenablog.com/entry/rubocop-safe-autocorrect-by-default

- Qiita だけど
  - https://qiita.com/kumashun/items/483fd7d73256c786d724
  - @hogucc Metrics cops、代入、メソッド呼び出し、条件をチェックしているっぽい
  - @hogucc https://docs.rubocop.org/rubocop/cops_metrics.html

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @hogucc dependabotのPRをマージする作業、属人化したくないなぁという気持ちが高まった
- @hogucc rubocop、lオプションは使ったことなかった

- @chiroru Github Actionsの件、何もできずに終わってしまった・・

- @asya81 Github Actionsの件の調査はあまり進まなかったけど、テストの部分が勉強になった
- @asya81 皆さんがDependabotやRuboCopをどう使っているのか知れてよかった！

- @sanfrecce-osaka dependabot 使いたいなー :sob:

- @sanfrecce-osaka ABCサイズ皆苦労してるんだなぁ :eyes: 