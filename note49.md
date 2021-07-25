# 【第49回】パRails輪読会ノート(2021-7-25)
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
%w[sanfrecce_osaka hogucc asya81 fuga].
  partition { |user| !%w[asya81 sanfrecce_osaka hogucc].include?(user) }.
  flat_map(&:shuffle)
  # => ["sanfrecce_osaka", "hogucc", "asya81"]
  # partition のブロックの中の配列で空白文字が半角スペースになっていなくてひとつづきの文字列として認識されていたみたいです〜
```

### 今日のスタート
10-3から


## 疑問点・気づき

### 10-3 開発環境におけるDockerの活用(10分)

- @fuga コンテナとプロジェクトのディレクトリをマウントして、ソースコードの反映をリアルタイムにすることができる
- @fuga `docker-compose`は、複数のコンテナを組み合わせて一度に起動してくれる

--- ↑今日はここまで

- @sanfrecce-osaka volume
    - https://qiita.com/aki_55p/items/63c47214cab7bcb027e0
- @sanfrecce-osaka ポートフォワーディング
    - cf. https://qiita.com/tatsuo-iriyama/items/e4bf2404411343116e3e
- > run コマンドを利用した時は --service-ports を指定していないと、〜
    - @sanfrecce-osaka へ〜 :eyes: 
- @sanfrecce-osaka -v $(pwd):/app:cached とすることである程度パフォーマンスの低下を緩和することができるの知見だ :laughing: 
- @sanfrecce-osaka ネイティブライブラリ
- @hogucc environmentのMYSQL_ALLOW_EMPTY_PASSWORDにtrueを設定すると、rootユーザーのパスワードが空でもコンテナを起動できるようになるっぽい
    - https://dev.mysql.com/doc/refman/8.0/ja/docker-mysql-more-topics.html#docker_var_mysql-allow-empty-password
- @hogucc `docker-compose up -d`の`-d`はバックグラウンドでコンテナを起動してくれるので、同じターミナルで作業ができる？
    - https://docs.docker.jp/compose/reference/up.html
- @sanfrecce-osaka イメージがゲシュタルト崩壊してきた :rolling_on_the_floor_laughing: 

### 10-4 環境によって可変する設定値や秘匿情報の管理（5分）

- @asya81 環境によって設定ファイルを分けるというのはコンテナにはなじまないので、環境変数で設定を可変にする等している。
- @asya81 秘匿情報の管理については、AWSやGCPを利用している場合は、Key Management Service（KMS）を利用すると、権限管理が一箇所にまとめられてよい。

### 10-5 ログ出力(7分)
- @hogucc 「新しくデータを保存しないことがコンテナ運用の鉄則」
    - 画像を保存したいときはS3などのオブジェクトストレージに保存する
    - ログもlogディレクトリではなく標準出力にする
- @sanfrecce-osaka エラートラッキングとかこの辺は prodcuction の話が主かな :eyes: 
- @sanfrecce-osaka mhさんのサービスでもSentry使ってましたね〜
    - https://mh-mobile.github.io/event_follow_slide/13

### 10-6 HTTPサーバとの通信(7分)
- @hogucc unicornは高速なクライアントからのアクセスを前提にしているので外部のインターネットから直接接続するとI/O待ちが発生してプロセスが長時間占有される
    - unicornの特性初めて知った

### 11-1 アーキテクチャパターンから見るRails(7分)
- @hogucc アクティブレコードはアーキテクチャパターンだった
- > 単一テーブル継承を用いる前に、そもそも対象のモデル群が継承関係にあるとみなすことが適切かを考えるとよいでしょう
    - @sanfrecce-osaka STI に限らず、安易に継承を使うのは本当に危険
        - リスコフの置換原則大事、超大事
        - これが守られていない継承を利用したコードのお守りは地獄やでぇ・・・
        - cf. [そろそろポリモーフィック関連について一言いっとくか](https://qiita.com/joker1007/items/9da1e279424554df7bb8)
- @hogucc typeというカラムを作ったらエラーになった記憶...
    - テーブルの各レコードが所属しているモデルのクラス名をtypeというカラムに保持しているので、このカラムと名前がぶつかるからエラーになる
- https://speakerdeck.com/daikimiura/upgrow
- https://speakerdeck.com/toshimaru/how-to-deal-with-fat-model
- https://speakerdeck.com/minodriven/railsdekao-erudomeinqu-dong-she-ji-falsekoadomein
- https://railsguides.jp/association_basics.html#%E3%82%B7%E3%83%B3%E3%82%B0%E3%83%AB%E3%83%86%E3%83%BC%E3%83%96%E3%83%AB%E7%B6%99%E6%89%BF-%EF%BC%88sti%EF%BC%89

いつからFat Modelになるのか？
下手に分割すると分割前より悪くなる
Fat Modelになったと気づいたときにはそれに対応する余裕がなくなっている
Fat Modelになる前に対処したいが、YAGNI...

Fat Modelの限界点
  - Validationを複数の用途で使い出すとやばい
  - FormのValidationを複数使ってたりとか
  - このあたりにくわしく書かれている
    - https://speakerdeck.com/yasaichi/what-is-ruby-on-rails-and-how-to-deal-with-it
    - https://anchor.fm/textafm

### 11-2 値オブジェクト〜11-2-2 いつ導入すべきか(７分)


### 11-2-3 実装例(7分)


### 11-3 サービスオブジェクト〜11-3-2 いつ導入すべきか(7分)


### 11-3-3 実装例〜11-3-4 導入時のポイント(10分)


## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka Rails で決められた規約以外で type 使ったらだめダゾ☆
- @sanfrecce-osaka 昔は完全にはピンときていなかった joker さんの記事やリスコフの置換原則の話を今はできるようになったんで皆そのうちわかるようになるはず :laughing: 

- @hogucc typeカラムの話、過去に自分でエラーを踏んだのにどのタイミングで起きたのかわすれていたので良い復習になった！
- @hogucc パRails発売１周年おめでとうございます～！！！🎉🎉🎉
                - @sanfrecce-osaka :tada
- @hogucc 10章が終わった！

- @asya81 企業によってアプリもインフラもやるという場合もあれば、分かれているという場合もあることを知った。
    - @asya81 スタートアップとか人数が少ないと必要にせまられてやらざるを得ない。
    - @asya81 私もよく分からないけどインフラ触っているので、不安。Docker化までは道のりが果てしなさそう。
- @asya81 継承とかよく分かってなかったので、これを機に色々知りたい。

- @masuyama13 継承は難しいのであまり使いたくないなと思った
- @masuyama13 typeカラムのエラーが出るタイミングが勉強になった

- @fuga `type`は使わない！というのを今のうちに知れて良かった
- @fuga 今はあまりピンとこない話が多いけれど、いざ使うという時のために心に留めておくといつか役立つ日が来そう
