# 【第48回】パRails輪読会ノート(2021-7-18)
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
%w[sanfrecce_osaka hogucc asya81 fuga].
  partition { |user| !%w[asya81 sanfrecce_osaka hogucc].include?(user) }.
  flat_map(&:shuffle)
  # => ["sanfrecce_osaka", "hogucc", "asya81"]
  # partition のブロックの中の配列で空白文字が半角スペースになっていなくてひとつづきの文字列として認識されていたみたいです〜
```

### 今日のスタート
10章から


## 疑問点・気づき

### 10-1 Railsアプリケーションのインフラ概要（5分）
- @hogucc べき等の話、Webを支える技術でも出てきたけど、DSLに関しても意識しないといけなかったのだなーと思った
- @hogucc コンテナ技術自体は前からUnixやLinuxには存在していた
- @fuga コンテナは環境構築をする上で、冪等かつ自動的に構成を組めるようにしたもの
- https://docs.docker.com/get-started/
- [Amazon.co.jp: イラストでわかるDockerとKubernetes Software Design plus eBook : 徳永 航平: 本](https://www.amazon.co.jp/dp/B08PNMRXKN/ref=dp-kindle-redirect)
- [#マンガでわかるDocker ① 〜概念・基本コマンド編〜 【ダウンロード版】 #技術書典
](https://booth.pm/ja/items/825879) 
- [#マンガでわかるDocker ④ 〜Compose編〜（わかばちゃんと学ぶシリーズ）：湊川あいの、わかば家。](https://techbookfest.org/product/5283800311398400?productVariantID=5166605057130496)
- [#マンガでわかるRuby ② #オブジェクト指向 編 PDFダウンロード版 #技術書典 - 湊川あいの、わかば家。 #技術書典 #わかばちゃんと学ぶ シリーズ - BOOTH](https://booth.pm/ja/items/1573974)
- りあくと！ は別の方
    - https://oukayuka.booth.pm/

### 10-2 基本的なDockerイメージの構築(10分)

- @sanfrecce-osaka Dockerfile は雑にいうとほぼほぼシェルスクリプトのようなもの
- @sanfrecce-osaka ビルドステップキャッシュ便利
    - もう再ビルド時に bundle install で待たなくて済むぞわーい
- @fuga シェルスクリプトの積み重ねでDockerfileを作成することができる
    - @fuga 特別なことを覚えなくても使える
    - @fuga 同一性が担保できる
- @hogucc 関係あるかわからないけど、DockerFileのベストプラクティスが公式っぽいページに載っていた
    - https://docs.docker.jp/develop/develop-images/dockerfile_best-practices.html
- http://docs.docker.jp/v1.12/engine/reference/builder.html#from
- https://qiita.com/zembutsu/items/24558f9d0d254e33088f
- https://docs.docker.jp/engine/userguide/dockerimages.html
- 一つずつのイメージ(ruby, rails, node.js)を組み合わせて作成するのがイメージ
- 一つずつのイメージ(ruby, rails, node.js) = コンポーネント
- コンポーネントとは、再利用可能なもの
- dockerでdbのマイグレーションとかもやってくれる感じですか？
  - dockerfile内にRUNを書いておけば、できます

### 10-3 開発環境におけるDockerの活用(10分)

- @fuga コンテナとプロジェクトのディレクトリをマウントして、ソースコードの反映をリアルタイムにすることができる
- @fuga `docker-compose`は、複数のコンテナを組み合わせて一度に起動してくれる

--- ↑今日はここまで↑ ---
--- ↓次回は以下 :squid: から↓ ---

- @sanfrecce-osaka volume
- @sanfrecce-osaka ポートフォワーディング
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


### 10-5 ログ出力(7分)


### 10-6 HTTPサーバとの通信(7分)




## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka Docker の説明難しいなー :thinking_face: 
    - @sanfrecce-osaka 説明することも多いしふんわり理解のところもあるし :innocent: 
- @hogucc dockerの概念を説明するのが難しいし、説明できないということは理解できてないんだなということがわかった、、イラストでわかるDockerとKubernetesを読み直します
    - @fuga 僕も積んでいるので読んでみます

- @chiroru dockerのイメージが少しできるようになりました！

- ＠asya81 docker使ったことなくてよく分からなかったのが、皆さんのお話を聞いて少しイメージできました！

- @asya81　実際に使ってみてより理解したい！

- @fuga Dockerの用語の概念がとても難しくて理解がふんわりという感じ。
- @fuga 実際に使うともう少し腹落ちするのかなぁという気もする ← @sanfrecce-osaka :crab: 
    - @fuga ユースケースがあまりイメージできてないので、そのせいもありそう