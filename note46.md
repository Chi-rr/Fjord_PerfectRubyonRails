# 【第46回】パRails輪読会ノート(2021-7-4)
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
%w[sanfrecce_osaka hogucc asya81 chiroru fuga].
  partition { |user| !%w[sanfrecce_osaka].include?(user) }.
  flat_map(&:shuffle)
  # =>  ["asya81", "chiroru", "fuga", "hogucc", "sanfrecce_osaka"]
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
9-3-2 brakeman



## 疑問点・気づき
### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- `brakeman -w1`
  - [Brakeman
Ruby on Rails Static Analysis Security Tool](https://brakemanscanner.org/docs/options/ja.html)

>Confidenceレベル（自信レベル）
Brakemanは各警告にconfidenceレベルを設定しています。これは出力された警告がどれくらい問題なのか、大まかに見積もった値です。当然ながら、この値を絶対的なものとして信用するのはよくありません。

>指定したconfidenceレベル以上の警告だけを受け取りたい場合は、次のオプションを使います。

>-wスイッチには1から3までの数字を指定できます。1は低レベル（全警告を出力）で、3は高レベル（confidenceレベルが最高の警告のみ出力）です。

- https://github.com/fjordllc/awesome_events/pull/43

- https://brakemanscanner.org/docs/options/ja.html

- https://kanji.reader.bz/english/coveralls#:~:text=%E3%80%8C%E3%82%AB%E3%83%90%E3%83%BC%E3%82%AA%E3%83%BC%E3%83%AB%E3%82%BA(coveralls)%E3%80%8D%E3%81%A8%E3%81%AF%EF%BC%9F

- https://github.com/fjordllc/bootcamp/blob/0a85e5ea3a334b1756f54e717b70e9704475b035/test/application_system_test_case.rb#L21

`$ HEADED=1 rails test:all`

- https://github.com/fjordllc/awesome_events/pull/45/files

- https://coveralls.io/pricing

- カバレッジはどのくらいを目標にするべき？
    - 80%くらいを目指すとちょうど良さそうとのこと。 @igaiga さん、ありがとうございます！
    - 100%までやるとすると、validateとかbelongs_toとかRails自身のテストをすることになる。

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @hogucc 仕事のコードのカバレッジあげていきたい...
    - @sanfrecce-osaka :wakaru:
    - @sanfrecce-osaka jest にもあったはずだからフロントのカバレッジ測定もやっていきたいなぁ
- @hogucc 9章あとちょっと！
    - @sanfrecce-osaka :laughing: 
- @hogucc brakemanのオプションいろいろあることがわかった

- @chiroru simplecov見やすくてよかった！仕事でも使ってみよう

- @asya81 久しぶりに？ドライバーできて良かった！
    - @sanfrecce-osaka :raised_hands: 
- @asya81 gitともっと仲良くなりたい。RubyMineとも。
- @asya81 SimpleCovはお仕事でもテストコード整備とあわせてやりたい。
    - @sanfrecce-osaka やっていき！ :muscle: 

- @masuyama13 9章終わらせたかった〜
    - @sanfrecce-osaka :sob: 
- @fuga カバレッジの測定が自動でされるのはとても便利
- @fuga 見落としに気づきやすくなりそうなので、時がきたらぜひ使いたい
- @sanfrecce-osaka 【MEMO】 test:all についてあとで調べる

- 【メモ】 来週、Kyoto.rb のるりま読書会があるのでそれを避けて 11:00〜12:00開催です :pray: 