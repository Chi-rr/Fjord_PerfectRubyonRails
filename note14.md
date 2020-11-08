# 【第14回】パRails輪読会ノート(2020-11-08)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @ima1zumi
タイマー： @kyo
順番 @kyo → @masuyama → @hogucc → @chiroru → @ima1zumi

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
- 雑談タイム(15分くらい)

※休憩はなしでやってみます！


## 自己紹介の記入をお願いします！
> - フィヨルド生
    - 名前(@username + 呼び名)
    - 現在のプラクティス 
    - 今日のテーマ : 最近読んだ本or漫画or動画
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ : 最近読んだ本or漫画or動画


- @shibaaaa(柴田)
  - 自作サービス作り
  - 最近読んだ本:AWS紫本(まだ序盤ですが)

- @Kyo18(岸) 
  - スクラム開発/自作サービス作成/就活
  - 最近読んだ本:SOFT SKILLS 最近読んだ漫画:BLUE GIANT
      - @igaiga SOFT SKILLS、筋トレと不動産投資がしたくなる良い本

- @hogucc（おぐち）
  - スクラム開発
  - 最近読んだ本：TeamGeek、Rubyのしくみ（読み途中）
      - @igaiga HRT!
      - @ima1zumi 良さそう!私も読みます

- @masuyama13（マスヤマ）
    - スクラム開発
    - 最近読んだ本：Team Geek

- @chiroru (ちろる)
  - VueCLI
  - 最近観ている動画：李子柒(リー・ズーチー)さんの動画

- @ima1zumi 
    - スクラム開発,就活
    - 最近読んだ本: [プログラマのための文字コード技術入門 \(WEB\+DB PRESS plus\) \(WEB\+DB PRESS plusシリーズ\) \| 矢野 啓介 \|本 \| 通販 \| Amazon](https://www.amazon.co.jp/dp/477414164X)
    - Rubyのしくみ

- @sanfrecce-osaka(もりつか)
    - 現在のプラクティス
        - 社内発表の準備
    - 最近読んだ本or漫画or動画
        - パーフェクトRuby on Rails(輪読会参加中)
        - Rubyのしくみ(輪読会参加中)
        - メタプログラミングRuby(輪読会参加中)
        - [読まずにわかる こあら式英語のニュアンス図鑑](https://www.amazon.co.jp/dp/B08LG665Z4)

- @koheitakahashi
    - Rails歴: 1年/ プラクティス: TypeScript + Vue.js の勉強しています
    - 最近読んだ本:『リファクタリング Ruby』(読み中)・ドクターストーンの新巻が熱い!!

- @igaiga
    - Rails歴: 10年/プラクティス: 年末調整
    - 2020年igaigaマンガランキング暫定1位「プリンタニア・ニッポン」 http://matogrosso.jp/printania/01.html


## 疑問点・気づき
>### 書き込みサンプル
>@アカウント名 Rails楽しい

### 5-6-1〜5-6-2(15分)

- @sanfrecce-osaka エントリポイントがchannels配下なのでpacks配下には何も作成しない
    - デフォルトだと packs/application.js 内で `require("channels")` している
- @sanfrecce-osaka generate に渡すのはチャネル名とメソッド名
- @sanfrecce-osaka window.App = ...
    - グローバル変数 window にとして App を登録している

- @koheitakahashi クライアントから、サーバー側に定義されたメソッドを呼び出せるというのが凄いですよね!!
    - @ima1zumi ref:p.264 リスト5.44,5.45
    - 書き方分かってしまえば、簡単な処理はすんなり書けてしまうので、素晴らしいと思いました!!(書き方分かるまでが私は苦労していました...)
    - 少しでも参考になれば幸いです → https://docs.koheitakahashi.com/entry/2020/08/20/124333
        - 訂正: WebSocket の概念として data channel consumer があると説明しておりますが、これらの概念は ActionCable が採用している pub/sub モデルの概念でしたmm(あとでブログを修正しますmm)

- @igaiga WebSocketやServer-Sent EventsなどのHTTP1.1の機能についてはWEB+DB PRESS 71の記事がわかりやすくてお勧め
    - @koheitakahashi WebSocket があまり理解できてなくて、Action Cable を理解するのに時間がかかっていたので、とても有り難いですmm
    - @sanfrecce-osaka :eyes: 

- polling
    - ときどき「どうなってる？」と問い合わせる
- server sent events
    - httpはヘッダにこれから何バイト送ります！を送る必要がある
        - 常時通信は難しい
        - 何バイト送ります！ に 0 を入れることで永遠に送り続ける裏技がある
        - HTTP1.1
        - (たぶん）これをlong pollingと呼ぶのだと思う

- websocket
    - HTTP1.1
    - HTTP 101を返す status changes
    - 違うプロトコルにかえるよ！のステータスコード
    - ここからはwebsocketに切り替えますよ、のネゴシエーション

- http は単方向通信
    - websocket は双方向常時通信

- @sanfrecce-osaka insertAdjacentHTML
    - c.f. https://developer.mozilla.org/ja/docs/Web/API/Element/insertAdjacentHTML

- @igaiga
    - ここの原稿を書くために3億年ぶりにjs書きました

### 5-6-3(7分+α) 9:14〜9:21
- @ima1zumi サーバの話になり、よくわからなくなってきた。。

- @shibaaaa スタンドアローンとはなんですか？
    - 他のサーバから独立したサーバとして構成する、という意味？

- @koheitakahashi ↑の話とも関連しますが、Action Cable 専用のサーバーを立てたらどんな感じなるのかが、あまり理解できていない感じがあります
    - 書いている内容は理解できたと思いますが、実際にやってないので実感が沸いていないという感じです。
    - @igaiga フィヨルドだと「ふつうのpumaだけで運用」という理解であっていますか？（運用したことないので知見があると嬉しいなと）
        - フィヨルドでは今後運用開始
            - @koheitakahashi PR がそのままマージされないということも…(分報機能の実装自体が取りやめになるかも…)

- @hogucc アダプタが具体的になにを指しているのかよくわかっていない...
    - @koheitakahashi broadcast(channelにメッセージを送る)などのタスクを一時的に保管しておくための場所を指していると認識してました🤔(違うかも？)
    - memo: ActionCable では送信内容が非同期に来るため、送信内容をキューにためて順に処理していく

- @sanfrecce-osaka ws と wss、log で見かけていたけど WebSocket 用の URI スキーマだったのか

- @ima1zumi ActionCableを本番で運用しているところはある？
    - @ima1zumi GitLab
        - @koheitakahashi ここら辺ですかね → https://github.com/gitlabhq/gitlabhq/blob/0b4bb101ea/app/channels/issues_channel.rb

### 5-6-4〜5-6-5(6分+α) 9:32〜9:38

- @ima1zumi ワーカーとは？
> ある作業所の話です。ここでは作業者がプラモデルを組み立てています。作業を依頼する人が、プラモデルの箱をたくさん作業所に持ってきて、机の上に並べます。
届けられたプラモデルは、作業者が1つ1つ組み立てなければなりません。作業者は、まず机に並べられたプラモデルの箱を取りにいきます。そして、箱の中に入っている説明書を読んで組み立てはじめます。作り終えた作業者は、また次の箱を取りにいきます。箱がなかったら、新しいプラモデルの箱が届くまで待ちます…
workerというのは「仕事をする人」「作業者」という意味です。Worker Thread パターンでは、ワーカースレッド（worker thread：作業者スレッド）が仕事を1 つずつ取りにいき、処理を行います。仕事がなかったら、ワーカースレッドは、新しい仕事が届くまで待ちます

らしい http://www.hyuki.com/dp/dp2_ch08.pdf

- @ima1zumi スレッドとはどう違うんだろう？
    - 違うレイヤの話

- @ima1zumi プロセスとスレッドの違い
    - プロセス
        - ps でプロセス一覧表示
        - 独立している
        - kill コマンドで停止できる
    - スレッド １つのプロセスの中に複数のスレッドを作ることができる
        - 分身の術
        - ちょっと関係した状態で動く
            - クラス変数とか共有したり
        - 並行処理
            - 一部共有して、一部共有していない。各スレッドが独立しているわけではない
        - Ractor はスレッドのライバル
            - 説明はしなかったですが、Fiberという道具もあります
    - Railsのdefaultアプリケーションサーバ puma
        - puma はスレッドをワーカーとして使う
            - ちなみに、pumaはプロセスをワーカーにするモードもあります
        - クラス変数共有とかの問題が起きるかも
        - スレッドなので使うメモリは少ない
        - スレッドを停止させるのはちょっと大変
    - Unicorn
        - プロセスベースでワーカーを使う
        - クラス変数とかの問題はおきない
        - メモリは大きめ
        - kill コマンドでワーカー1つ単位で停止できるので停止がかんたん
    - アプリケーションレベルでpumaとunicornの違いを意識することはあまりない
        - Railsがうまくやってくれている
        - クラス変数共有問題は起きるかも（ふだんクラス変数を使わないので意識していないけど）
    

### 5-6-6(7分+α) 9:48〜9:55

- @sanfrecce-osaka 必要そうな assertion や helper が用意されていてテストが書きやすそう

- @ima1zumi 改めて、こんな複雑な処理がかんたんにかけるRailsすごいなと思いました
- @masuyama13 分報機能早く使いたい！
    - @koheitakahashi 本番にマージされないかも…
    - [該当PR](https://github.com/fjordllc/bootcamp/pull/1527)

- @koheitakahashi `subscribe`や`connect` でその状態に持っていけるの凄いですよね!!

- @sanfrecce-osaka さっきのプロセスとかスレッドの話の関連で永和さんの idobata の発表資料が見つかったので共有しておきます〜 :pray: 
    - https://docs.google.com/presentation/d/1ccgvApLkeScQ5GDSIiq31Ij5hL1oFbvU-RNFdi4eSY0/htmlpresent
    - あとで上の章に移します〜 :pray: 

### 6章以降の進め方について

- モブプロでやる？
    - モブプロなら予習なしで今まで通り参加しやすそう
    - ドライバーがただひたすら手を動かすだけにならない？
        - エディタの使い方とか共有できることは色々あるので大丈夫だと思っている
    - 読んでいるだけだと手を動かすだけで終わってしまいそう
    - モブプロでやってみますか〜 :raised_hands: 
- ドライバーは1人あたり何分？
    - 作業(節)単位で区切る？
- ドライバーはどう決める？
    - 本当の最初は決める？
        - これに関しては決めなくても良さそう
    - 毎回 Array#shuffle で当日決める
    - やったことがない人を優先する
    - ゲスト呼んでみても面白そう
- リポジトリはどうする？
    - フィヨルド内で立てる？
        - machidaさん・komagataさんに確認する
    - private？public？
        - 同上
    - publicの場合著作権的に大丈夫？
        - パーフェクトRuby on Rails のサンプルコードのリンクを README に貼っておけば良さそう
        - https://github.com/perfect-ruby-on-rails/awesome_events
- 見学枠があると気軽に参加しやすそう
    - Slack のリアクションで事前に分けると当日効率が良さそう
- To Do
  - 輪読会のDocs、Slack投稿の文言にモブプロに関する記述を追加。
  - 見学枠OKを書いておく

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka 高橋さんから分報機能の現状とか苦労した話とかリアルな話を聞けて面白かった :raised_hands: 
- @sanfrecce-osaka @igaiga さんの WebSocket の話もすごく勉強になった！ :smile: 
- @sanfrecce-osaka 来週からモブプロ楽しみ :grin: 
- @shibaaaa 高橋さんによるAction Cableの解説・ブログが勉強になりました。ありがとうございました！
- @hogucc 分報機能のコード読んでみたいという気持ちになりました！高橋さん、igaigaさんによる解説、大変勉強になりました！
- @shibaaaa プロセスやスレッドについて勉強になりました！igaigaさんありがとうございます。
- @koheitahakashi igaiga さんの説明(WebSocket以外のプロトコルの話や、プロセス・スレッドの話など)がとても分かりやすくて勉強になりました。
- @koheitakahashi なんか皆さんと一緒に勉強して「やっていこう」と前向きな気持ちになりました。

- @chiroru 分報機能使ってみたい！実装された高橋さんのお話、ブログと勉強になりました！！

- @masuyama13 高橋さんのブログわかりやすい！ありがとうございます。WebSocketの勉強もしたい

- @ima1zumi プロセスとスレッドの違い、ずっと気になっていたので今回説明していただけてすごく勉強になりました！ありがとうございました！
- @ima1zumi 高橋さんのブログがすごく分かりやすくてActionCableのイメージがわきました!

- @Kyo18 ActionCableは高橋さんのLTで初めて知りました❗今日はその高橋さんにお越しいただき説明を聞けたため、かなり理解が深まりました❗ありがとうございました❗

- @igaiga (連絡)来週は実家へ行くので欠席します
    - @sanfrecce-osaka :ok_woman:
    - (なんで ok_**woman** しかないんだろう :thinking_face:)
        - @ima1zumi 人間の絵文字ってperson/man/woman の３種類の実装があるんですが、personなemojiだけ実装してるとwomanで表示される環境があるかも。でもなぜ ok_person じゃないのか分からない
        - https://emojipedia.org/person-gesturing-ok/
        - :sasuga: :clap: 
