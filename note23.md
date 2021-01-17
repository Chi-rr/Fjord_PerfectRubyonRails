# 【第23回】パRails輪読会ノート(2021-1-17)
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
    - 今日のテーマ： 好きな動物アカウント
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ： 好きな動物アカウント

- @hogucc
    - プラクティス:スクラム開発、就活
    - 好きな動物アカウント
    　　- 動物アカウントではないですが、べこさんとメンターのbetaさんのお家のねこ画像のツイートをいつも楽しみに見ています
    　　- 好きな動物は猫、犬、海獣

- @chiroru 
  - プラクティス：スクラム開発、自作サービス、就活
  - 好きな動物アカウント
    - https://twitter.com/ayumi58908
    - [Momo Ten Kuuももと天空](https://www.youtube.com/channel/UCroloVlHKUnvOMn5MtuvyDg)

- @Kyo18 
  - プラクティス：自作サービス/社内発表の準備/スクラム開発
  - 好きな動物アカウント：「もんたの日常」
  - https://www.youtube.com/c/%E3%82%82%E3%82%93%E3%81%9F%E3%81%AE%E6%97%A5%E5%B8%B8

- @ikuma-t
    - プラクティス：Railsでコメントをできるようにする
    - 好きな動物アカウント：アドベンチャーワールドのパンダ→[Tiyon Tube](https://www.youtube.com/channel/UCekTPfHdjpbbu9gDOmhv_3Q)


- @masuyama13 (マスヤマ)
    - スクラム開発
    - 好きな動物はうさぎ

- @igaiga
  - プラクティス: Rubyの勉強
  - 好きな動物アカウント: カピバラが好きなので、インスタグラムで検索しまくった結果、カピバラタイムラインが完成しました

- @sanfrecce-osaka
  - プラクティス: 社内勉強会の準備
  - 好きな動物アカウント
      - 特にフォローしていないです :pray: 
      - 好きな動物は犬・猫

## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[sanfrecce_osaka hogucc igaiga].
  partition { |user| !%w[ikuma-t chiroru].include?(user) }.
  flat_map(&:shuffle)
  # => ["sanfrecce_osaka", "hogucc", "igaiga"]
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

6-8(p.337)

## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

# モブプロ
- @hogucc `throw(:abort)`でコールバックを停止する 
  - [Active Record コールバック - Railsガイド](https://railsguides.jp/active_record_callbacks.html#%E3%82%B3%E3%83%BC%E3%83%AB%E3%83%90%E3%83%83%E3%82%AF%E3%81%AE%E5%81%9C%E6%AD%A2)
- @hogucc `erros[:base]`
  - [Active Record バリデーション - Railsガイド](https://railsguides.jp/active_record_validations.html#errors-base) 

## 7-1

- @sanfrecce-osaka テストきちんと書くの大事 :+1: 
- @hogucc TDD経験したことがないので難しそうと思うけど、7-1-2に書いてあるとおり、E2Eのテストからならわりと書きやすそうと思った
    - @sanfrecce-osaka TDD は仕様がはっきりしているときはやりやすいですね〜
    - c.f. [【初心者向け】テストコードの方針を考える（何をテストすべきか？どんなテストを書くべきか？）](https://qiita.com/jnchito/items/2a5d3e15761fd413657a#tdd%E3%81%A7%E9%96%8B%E7%99%BA%E3%81%99%E3%82%8B%E3%81%8B%E3%81%A9%E3%81%86%E3%81%8B%E3%81%AB%E3%81%A4%E3%81%84%E3%81%A6)
- @masuyama13 *"テストコードの行数がプロダクトコードの行数の数倍になること"* もあるのか〜（感想）
- > まずはシステムテストで広範囲にテストを書き
    - @sanfrecce-osaka そうなんだろうか？ :thinking_face: 
    - @sanfrecce-osaka 既存のアプリケーションにテストを書く話だった(なのでそのとおりでした :pray: )
- @Kyo18 自作サービスでテストを全然書けていないので耳が痛い

## 7-2

- @masuyama13 ネット上の情報だとRSpecばかりなイメージがある
- @ikuma-t minitestに2種類書き方があるの初めて知った
- @Kyo18 これからminitestのシェアが増えてくるかも的な話を効いた覚えが…
- @sanfrecce-osaka c.f. [RSpecとMinitest、使うならどっち？ / #kanrk06](https://speakerdeck.com/jnchito/number-kanrk06)

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！


- @masuyama13 6章終わった！すごい:raised_hands:
- @hogucc 6章おわったー！だんだん終わりが見えてきましたね
- @ikuma-t もう少しでテストのプラクティスに入るので、ちょうどテストの章入れて嬉しいです。勉強になります！
- @chiroru 6章開始が11/15~だったので、およそ2ヶ月！
- @Kyo18 年末年始を挟んで久しぶりの参加でしたがやはりすごく勉強になりますね！次回からはテストのモブプロなのでかなり楽しみにしてます！ :+1:
- @sanfrecce-osaka テスト楽しみ〜 :smile_cat: 
- @sanfrecce-osaka (Tabnine 紹介し忘れた orz )