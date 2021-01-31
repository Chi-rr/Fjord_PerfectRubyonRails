# 【第25回】パRails輪読会ノート(2021-1-31)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @masuyama
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


## 自己紹介の記入をお願いします！
> - フィヨルド生
    - 名前(@username + 呼び名)
    - 現在のプラクティス 
    - 今日のテーマ：ストレス発散法
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：ストレス発散法


- @hogucc（おぐち）
    - プラクティス:スクラム開発、就活
    - ストレス発散法:お菓子を食べる、人としゃべる、動物の画像・動画を見る

- @kamiokan(かみおか)
    - プラクティス:UNIX・Linux について知る
    - ストレス発散法：おいしいもの食べる、飲む、寝る、千鳥の番組を見て笑う

- @ikuma-t（いくま）
    - test-unitの基本を理解する
    - モルカーをみる
- @masuyama13 (マスヤマ)
    - プラクティス：スクラム開発
    - ストレス発散法：ジャンクフードを食べる

- @sanfrecce-osaka(もりつか)
    - プラクティス: 仕事・Machida.rb・社内勉強会の準備
    - ストレス発散法
        - リファクタリング
        - コミュニティ・勉強会
        - 外食
        - ゆるキャン△
        - ゲーム(最近は桃鉄・スマブラ)
        - カラオケ(いきたい・・・)
        - 寝る

- @igaiga
    - Rails歴:10年 プラクティス: 執筆
    - ストレス発散法: マンガを読む、カピバラを見る

- @chiroru 
  - プラクティス：就活、自作サービス
  - ストレス発散法：美味しいものを食べる、山に行く、温泉に入る


## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[sanfrecce_osaka igaiga masuyama13 ikuma-t hogucc chiroru].
  partition { |user| !%w[sanfrecce_osaka igaiga hogucc].include?(user) }.
  flat_map(&:shuffle)
  #=> ["masuyama13", "ikuma-t", "chiroru", "hogucc", "sanfrecce_osaka", "igaiga"]
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

7-4-5「ログインヘルパーを作る」

## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- @hogucc OmniAuthのモック化についてはこちらの記事も参考になりそうです
    - [[Devise How-To] OmniAuth: 結合テスト（翻訳）｜TechRacho（テックラッチョ）〜エンジニアの「？」を「！」に〜｜BPS株式会社](https://techracho.bpsinc.jp/hachi8833/2017_05_22/40297)

- @hogucc test/helperはhelperファイルをテストするファイルを置くためのディレクトリ
    - なのでパRailsのsign_in_helper.rbはtest/helperではなくtest直下に置かれている

- @ikuma-t helperを別のディレクトリにまとめるのは、3つ以上ファイルができてから。
    - リファクタリングの時の考えた方と同じ
    - helperにするとややこしい+Rails的にもデフォルトの名前はないので、適当な名前をつける（Bootcampはsupports）

## 時刻を制御するテスト

- https://github.com/fjordllc/bootcamp/pull/2268

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka 今日は色々とずれていたり間違っていたりする説明をしてしまっていた OTL
    - @igaiga さん、色々と補足ありがとうございます :pray: 
- @masuyama13 本を見ながらコードを書いているだけだと簡単に思えてしまうけど、ちゃんと理解できていないところもあるので復習しておきたい
- @ikuma-t helpersはテスト用のヘルパー（これも言葉としては厳密ではない）を置く場所ではない、ということが発見でした。なんでそこに配置するのかはよく考えて書かないと×。

- @hogucc 時刻のテスト難しいなぁという印象...時刻をどう設定するかはちゃんと考えてからテスト書かないと後々そこが問題になって困る未来が見えました
- @hogucc kamiokanさん初参加ありがとうございます！！！
    - @sanfrecce-osaka :raised_hands: 

- @kamiokan 初参加でした！これまでチーム開発した経験とかゼロだったので、他の方がコード書いてるの見るのとか新鮮で、学びも多かったです。githubも一人でコミットしてプッシュしかしたことないので、プルリクとか覚えてドライバー参戦できるように整えてきます！ありがとうございました！
    - @sanfrecce-osaka ヤッター :raised_hands: ぜひぜひドライバー参戦してみてください〜 :+1: :+1: :+1: 

- @chiroru ミートアップでお話したkamiokanさんが参加してくださった！！
    - @sanfrecce-osaka :raised_hands: 