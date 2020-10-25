# 【第12回】パRails輪読会ノート(2020-10-25)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @masuyama
タイマー： @ima1zumi
順番 @kyo → @masuyama → @chiroru → @ima1zumi


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
- 目的
- 輪読
  - 読書&hackmdに疑問点・気づきを記入(マイクオフ・[タイマー](https://timer.onl.jp/)使用)
  - 疑問点・気づきを確認(都度)
- 振り返り(10分くらい)

※休憩はなしでやってみます！


## 自己紹介の記入をお願いします！
> - フィヨルド生
    - 名前(@username + 呼び名)
    - 現在のプラクティス 
    - 今日のテーマ：最近読んでよかった本
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：最近読んでよかった本



- @Kyo18 (岸)
    - スクラム開発/自作サービス/就活
    - たたかう植物：植物が様々な状況で生き残るために身に着けた術を分かりやすく紹介している本です

- @hogucc（おぐち）
    - スクラム開発、自作サービスのペーパープロトタイプを作る
    - リファクタリングRubyエディション

- @igaiga(いがいが)
    - Rails歴: 10年 / プラクティス: 銀座Rails講演資料
    - パRails以外だと「人類と気候の10万年史」

- @shibaaaa(柴田)
    - 自作アプリ開発
    - 現場Rails


- @uda (うだ)
    - Railsでユーザーのプロフィールページを作成中
    - 『ぜんぶ、すてれば』中野善壽
    
- @chiroru (ちろる)
  - VueCLI
  - 『動物化するポストモダン』

- @masuyama13 (マスヤマ)
    - スクラム開発
    - 『王様の速読術』

- @sanfrecce-osaka(もりつか)
    - プラクティス
        - 月末の勉強会ラッシュ
    - 今日のテーマ：最近読んでよかった本
        - パRails
        - JavaScript Primar

## 疑問点・気づき
>### 書き込みサンプル
>@アカウント名 Rails楽しい

### 4-4-1〜4-4-3 (8分)

- > あくまで HTML はサーバから返すものである
    - @sanfrecce-osaka DHH のフロントエンドに対する考え方が現れてるなぁ :smirk: 
- data-controller・data-action・data-target
    - @sanfrecce-osaka 規約で縛るのが実に Rails らしい :eyes: 
    - 【NOTE】
        - data-controller => 読み込むエンドポイント(コントローラ)
        - data-action => 実行するコントローラのメソッド
        - data-target => 操作する対象

- @shibaaaa Stimulusを初めて聞いたけど現場ではどの程度使われている？
    - @sanfrecce-osaka 利用例はまだ少ない印象
    - @shibaaaa Turbolinksとも相性が良さそう
    - これからポスト jQuery として使われていくのでは
- @shibaaaa リスト4.19のファイル名が`hell_controller`になっている(helloのタイポ？)
    - @uda リスト4.18もindexのxがない
    - @igaiga ありがとうございます！
- @hogucc 一度規約を把握すればすごく使いやすそうな印象を受けました


### 4-4-4〜4-4-5 (12分)

- > コントローラは data-controller 属性を含む DOM とその子孫がスコープになります
    - @sanfrecce-osaka この仕組みは凝ったものを作るときに大変になりそう
        - スコープ内では命名をユニークにする必要がある(という認識)
        - スコープが大きくなってくると data-action や data-target で命名が重複しないように命名がどんどん冗長になっていきそうな印象
            - data-target はコントローラを指定できるから大丈夫そう？ :thinking_face: 
            - data-action もスコープとは別のコントローラのメソッドも呼べるので大丈夫そう？ :eyes: 
        - 小さくコンポーネントに切り分けるようなことはしにくそう

- @masuyama13  4-4-4 ■controller 3文目（P207）「そのため JavaScript 側ではは」になってます
    - @igaiga ありがとうございます！

- @shibaaaa リスト4.22のコード内の一行目、`mport`となっている（importのタイポ？）
    - @igaiga ありがとうございます！


### 5-1-1〜5-1-4 (12分)

- @sanfrecce-osaka async の読み方は、英語の読み方的には「エーシンク」
  - @hogucc awaitは「アウェイト」でしたっけ？これいつも読み方がわからなくなる... 
- > プロセスを再起動するとキュー中のジョブは失われる
    - @sanfrecce-osaka DB でキューを管理する Gem もあったような気がしたけど名前を忘れた・・・
        - DelayedJobだったっぽい
        - https://github.com/collectiveidea/delayed_job
- @sanfrecce-osaka キューとは
    - データ構造の1つ
    - c.f. http://e-words.jp/w/%E3%82%AD%E3%83%A5%E3%83%BC.html
- @sanfrecce-osaka bootcamp では Slack 通知に利用されている
    - https://github.com/fjordllc/bootcamp/blob/master/app/jobs/notice_slack_job.rb
- @sanfrecce-osaka Sidekiq の Web UI しらなかった :eyes: 

- @shibaaaa シリアライズ/デシリアライズとはなんですか？
    - @sanfrecce-osaka c.f. http://e-words.jp/w/%E3%82%B7%E3%83%AA%E3%82%A2%E3%83%A9%E3%82%A4%E3%82%BA.html

- @Kyo18 スレッドプールの説明を読んでも理解できない…
    - 【MEMO】 スレッドプール == スレッドをプール(ためておく)

### 5-1-5〜5-1-7 (9分)

- リスト5.7 の `self.`
    - @sanfrecce-osaka ここは `self.` は省略できない？
        - 省略できそう
- @sanfrecce-osaka テストする際にJobをモックすることもある
- @chiroru (一つ前で触れられたかもしれませんが)解説にsidekiqが選ばれたのはなぜでしょうか？
    - sidekiqがデファクトスタンダード(Resqueはほぼ見ないかも)
    - @chiroru 上記二つは、キューをredisで保存
    - @chiroru Delayed Jobは上記二つとは異なり、キューをDB上に保存できる
    - @sanfrecce-osaka fjord の kowabana では sucker_punch を使っている
        - c.f. https://github.com/fjordllc/kowabana/blob/master/Gemfile#L57
        - c.f. https://qiita.com/zephiransas/items/e2797a8202a1b07b7b68

### 5-2-1〜5-2-3 (10分)

- @sanfrecce-osaka ActiveStorage はサムネイル画像用の URL にアクセスしたタイミングでサムネイルを生成する
    - @sanfrecce-osaka 大量にアップロードした後に index アクションで大量に生成しないといけない場合とかパフォーマンスがかなりやばそうだけど大丈夫なのかな？ :thinking_face: 
        - やばくなるので要対応
            - e.g. ページング
            - また、サムネイル生成は非同期処理なのでサムネイルが生成されるまで一時的なサムネイルを表示する等の対応も必要
    - @sanfrecce-osaka 変換は初回アクセスのみ？毎回変換する？
    - @sanfrecce-osaka このあたりの画像変換とかは最近は lambda とかでやる方がいいのかな？ :thinking_face: 
        - :moneybag: でスペックを上げるのが一番よさそう

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @shibaaaa 初参加できました！集中して読み進められるのと、疑問をその場で回答頂けるのでとても有意義な時間でした。 ← @sanfrecce-osaka :raised_hands: 

- @shibaaaa ビデオチャットツールはZOOMを使うのはいかかでしょうか？Wherebyだと重くてMacのファンがうるさかったりしてしまうので...。フィヨルドでもZOOMの利用をしていてとても軽くて使い心地よかったです。
  - 特段wherebyにこだわりがあるわけではないので、検討してみたいと思います！！ご提案ありがとうございます😆

- @sanfrecce-osaka 非同期処理とかファイルアップロード周りはまだまだ弱いので @igaiga さんから知見を得られてよかった :laughing: 
- @sanfrecce-osaka Stimulus 知識を得られたので次から問題なく使えそう

- @hogucc Stimulusのコードを初めて見たので、後ほど自分で書いてみたいという気持ちになりました！
- @hogucc selfを書かないといけないケースは踏んでみたい


- @uda Active Storageは次の次のプラクティスで出てくるのでとても参考になりそう


- @masuyama13 JavaScript難しいけどいろんな便利機能があることがわかったので使ってみたい


- @chiroru 今日は初参加で@shibaaaaさんが来てくれた！udaさんもちょっと前から参加してくださっていて、嬉しい！！😊

- @Kyo18 @igaigaさんの声がすごく聞き取りやすくなっている！
    - @igaiga 新マイク導入しました！ ← @sanfrecce-osaka :raised_hands: 

- @Kyo18 ActiveJobによる非同期実行などは、意外と今まで触れてこなかった部分なのでもっと理解を深めたい