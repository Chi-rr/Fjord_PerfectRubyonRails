# 【第10回】パRails輪読会ノート(2020-10-11)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
司会・タイマー
司会： @ima1zumi
タイマー： @masuyama
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
    - 例： @ima1zumi xxページのこの文がよくわかりませんでした。 

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



## 自己紹介の記入をお願いします！
> - フィヨルド生
    - 名前(@username + 呼び名)
    - 現在のプラクティス 
    - 今日のテーマ(今日1日の目標)
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ(今日1日の目標)

- @imaharu 
	- Rails歴: 1.5年
	- 今日のテーマ: Unicorn触ってみる

- @hogucc（おぐち）
    - プラクティス:システム開発
    - 今日のテーマ:企業研究（自分がどういう会社に入りたいか考える）

- @igaiga
    - Rails歴:10年 / プラクティス: フィヨルドのリモートワークブログを書く
    - 今日のテーマ: fall guysで1位を取る

- @Kyo18
    - システム開発/自作サービス
    - 野球に関する自作サービスを作っているのですが完成がシーズンオフになりそう… 

- @ima1zumi（いまいずみ）
    - プラクティス：システム開発/自作サービス
    - 今日のテーマ：Vue.jsでAPI叩けるようになりたい！
    - reline

- @uda(うだ)
    - Railsのkaminari
    - deviseの課題にとりかかる

- @chiroru(ちろる)
  - プラクティス：Vuejs(Todoアプリ)・npm
  - Vuejs課題提出・npm取り掛かる

- @sanfrecce-osaka(もりつか)
    - Rails歴
        - 実務2年前後
        - 学習期間含めると5年弱
    - プラクティス
        - 自作Gemの改修
    - 今日のテーマ
        - 自作Gemの0.2.0のリリース(までいきたい・・・)

## 疑問点・気づき
>### 書き込みサンプル
>@アカウント名 Rails楽しい

### 3-3-6

#### 「複数のDBに接続する」(10分)
- @ima1zumi 現在のRailsでは複数DBで出来る機能は限られている
    - primary-replica は 1:1 でしか作れない
        - primary 1つに replica いっぱい はできない
        	- @imaharu レプリケーション詳しくないんですが、複数必要なんですか？
        	    - @ima1zumi 負荷分散が目的だと複数欲しいのかも
        	    	- なるほど
        - @sanfrecce-osaka 複数 replica 作っている例がありました
            - c.f. https://note.com/tana_d/n/n8ba31f72732c
        - @igaiga imaizumiさんが言ってたreplica1つ制限はもしかしたらこれかもしれない。勉強になりました。
            - https://railsguides.jp/active_record_multiple_databases.html#replica%E3%81%AE%E3%83%AD%E3%83%BC%E3%83%89%E3%83%90%E3%83%A9%E3%83%B3%E3%82%B7%E3%83%B3%E3%82%B0
            - 勘ですが、「DB名+replica: trueの中に複数のDBを設定して負荷分散」ができないことで、「DB名+replica: trueをたくさん書く」はできるのかなー。未調査です。

- ↑ メモ
	- レプリケーションには、2つの目的がある
		- 冗長性確保
		- 負荷分散

- @ima1zumi 基底クラスは継承用の実体のないクラスという認識でいいのかな？
    - `self.abstract_class = true` を設定するやつ
    - モデルとDBが対応しないクラス？
        - インスタンス作っちゃいけないクラス？

- @sanfrecce-osaka migration を generate したら primary と sub どちらも生成されるのだろうか？ :thinking_face: 

- @ima1zumi この節で扱うのはモデルとDBを対応付けできる機能
    - Author モデルは DB1 を、 Book モデルは DB2 を使うみたいなことができる
    - DB分けて嬉しいかどうかはよくわからない
        - DB2だとDBは実体のない概念だった
        - DBごとにrole分けてる場合はいいかも
            - 古いDBから新しいDBに移行するときに便利

#### 「書き込みと読み込みを分離する」（10分）
- @ima1zumi 実際にやってみたけど、ちゃんと複数DBに振り分けできているか確かめる方法がわからなくて困っています :sob: 
    - https://note.com/tana_d/n/n8ba31f72732c に書いてありました！

- @sanfrecce-osaka 【誤字】 P.151 リスト3.28 の後のサンプルコード と直前の文章で差異がある(どっちが正しいかはまだ未確認)
    - 直前の文章: connects_to
    - サンプルコード: connected_to
        - @ima1zumi この文脈では connected_to が正しそう
        - https://railsguides.jp/active_record_multiple_databases.html#%E3%82%B3%E3%83%8D%E3%82%AF%E3%82%B7%E3%83%A7%E3%83%B3%E3%82%92%E6%89%8B%E5%8B%95%E3%81%A7%E5%88%87%E3%82%8A%E6%9B%BF%E3%81%88%E3%82%8B
        - connets_to: https://api.rubyonrails.org/classes/ActiveRecord/ConnectionHandling.html#method-i-connects_to
        - connected_to: https://api.rubyonrails.org/classes/ActiveRecord/ConnectionHandling.html#method-i-connected_to
        - @igaiga ありがとうございます！

- @sanfrecce-osaka delay の設定値の判断は無限に難しそう :sweat_smile: 

- @imaharu 
	- データベースが違うので、トランザクションの扱いの考慮すると、途端に開発が辛くなりそうと予想
		- select for updateで、READ ONLYのデータベースは占有ロック対象にならないので
	- READ ONLYで取得するデータは、キャッシュデータで問題のないユースケースに絞られるのかな？
	- @ima1zumi 関係あるかも？な記事 https://blog.kamipo.net/entry/2019/06/26/102100
	    - 関係なかった

> 自動切り替え機能によって、アプリケーションはHTTP verbや直近の書き込みの有無に応じてprimaryからreplica、またはreplicaからprimaryへと切り替えます。

> アプリケーションがPOST、PUT、DELETE、PATCHのいずれかのリクエストを受け取ると、自動的にprimaryに書き込みます。書き込み後に指定の時間が経過するまでは、アプリケーションはprimaryから読み出します。アプリケーションがGETリクエストやHEADリクエストを受け取ると、直近の書き込みがなければreplicaから読み出します。

https://railsguides.jp/active_record_multiple_databases.html#%E3%82%B3%E3%83%8D%E3%82%AF%E3%82%B7%E3%83%A7%E3%83%B3%E3%81%AE%E8%87%AA%E5%8B%95%E5%88%87%E3%82%8A%E6%9B%BF%E3%81%88%E3%82%92%E6%9C%89%E5%8A%B9%E3%81%AB%E3%81%99%E3%82%8B

### 3-4-1〜3-4-6(15分)
#### 3-4-6

- @sanfrecce-osaka config 等の gem + 環境変数でやっているアプリケーションもまだま多いのかな？ :thinking_face: 
    - アプリによって保存方法が違うというのが現状
        - アプリのできた時期によって昔のまま管理している場合も結構ある
        - Rails の外で管理している場合も結構ある
    - 暗号化はしておいた方がいい

- @ima1zumi master.key はどこで管理されるんだろう？
    - 誰か1人のローカルに保存する？そんなわけはないか..
    - AWS上の秘密情報管理する場所とか

### 3-5-1(10分)

- @sanfrecce-osaka 【誤字】 3-5-1 の冒頭
    - 誤: 通常のリクスト
    - 正: 通常のリクエスト
    - @igaiga ありがとうございますー！

- @imaharu 
	- 「執筆時点で103に対応したメジャーなブラウザが存在しないこと、未対応ブラウザに103を含む複数レスポンスを送信するとセキュリティ上の問題があることから、現時点ではリバースプロキシを介してEarlyHintsを使うことが現実的」
		- セキュリティの問題、パッと思い浮かばなかった
			- これ？ [HTTPレスポンス分割攻撃](https://www.ipa.go.jp/security/vuln/websecurity-HTML-1_7.html) 初めて聞いた

- @ima1zumi 【誤字】p.160 図3.6の下
    - 誤：レスポンスを受診
    - 正：レスポンスを受信
    - ありがとうございますー！

- @Kyo18 nginxのプラクティスがはるか昔に感じるので、プロキシサーバー周辺の復習が必要だ・・・

- @ima1zumi これ知らなかった
> Chromeでアクセスした場合、自己証明書に対して警告画面を表示する場合があり、アプリケーション画面に遷移できないことが あります。執筆時点ではChromeの表示している画面に対して「thisisunsafe」とタイプすることで表示できるようになります。
（ページ163). 

- @sanfrecce-osaka まだまだ本格的に使えるのは先になりそう？

- HTTP1.1 リクエストに対して基本的にレスポンスを返す
    - ブラウザ側はリクエスト〜レスポンスの間に待機時間ができる
        - 図3.6
    - JS/CSSのダウンロードは先にできそう
    - 先にJS/CSSだけ返して、待機中の時間を有効活用したい！
        - Early Hints
    - https://blog.jxck.io/entries/2016-12-16/103-early-hints.html
        > 103 Early Hints は、レスポンス内の 既知のメタ情報 と 未知のコンテンツ を分離し、非同期に送達できる仕組みであると見ることができる。

### 3-5-2(15分)
> 　実際のWebアプリケーション開発ではさらにDBやHTTP、JSやCSSなどの知識やチーム開発を行うためにGitをはじめとするバージョン管理ツールなどの知識も必要です。それらを一気に学習するのは困難ですから、やれるところや必要になった部分から少しずつ自分の足場を固めていくと良いでしょう。
（ページ170).
- @ima1zumi やさしい言葉に安心する :sob: ← @sanfrecce-osaka :iihanashida:

> XSSの影響を軽減するためには、インラインでのJavaScript実行を禁止することが重要です。 ただし、アプリケーションの要件を満たすためにインラインでのJavaScriptが必要になることもあります。
- @ima1zumi インラインのJavaScriptとはなんだろう？
    - HTML で `<script>` タグを使ってJavaScriptを埋め込むことをインラインスクリプトと呼ぶ
        - `<script> alert('hello') </script>`
    - インラインでないJSは外部スクリプトと呼ぶ
        - `<script type="text/javascript" src="sample.js"></script>` のように別ファイルから呼び出しする
- [HTMLのonclick属性\(クリックイベント\)を使用してはダメな4つの理由 \| iwb\.jp](https://iwb.jp/javascript-html-onclick-attribute-dont-use/)
```
<script>
function hello() {
  alert('hello')
}
</script>
<button onclick="hello()">hello</button>
<button onclick="alert('hello')">hello</button> // たぶんこれもできちゃう
```

- @hogucc
> 許可リストによってドメインを指定する方式にも、それを迂回して特定のJSを実行する方法が存在するということがわかってきました

怖い...この手の問題ってどこまで対策するか決めるのが難しそう

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka @igaiga さん、毎度解説のフォローありがとうございます〜 :pray: :pray: :pray: 
- @sanfrecce-osaka 今日のところはだいぶ難しめ && あまり知見をもっていないトピックだったのであまりコメント書けなかった(´・ω・｀)
- @sanfrecce-osaka 3章完！次章は皆大好き(？)フロントエンドの話！

- @hogucc 3章まで終わった！3章の内容は後半が難しかったので、あとで読み返して咀嚼したいと思いました。
- @hogucc Railsがやっているセキュリティ対策が理解できれば、他のフレームワークを触ったときにも知識を活かせそう

- @chiroru 現在Vueのプラクティスでインラインスクリプトを使ってしまっていたので危ないところでした・・

- @imaharu
	- Railsが裏でやっていることを完全理解したら、強強になれそう。他のフレームワークなどに浮気せずに一つのことを極めるの大事

- @uda
    - 最後のほう難しかった。勉強しようという気になった。
    - 輪読会の流れがわかった！
    - とりあえずここまでの内容を読み返す

- @ima1zumi 難しい内容・初めて見聞きする内容が多くて難しかったけどその分学びも多かった
- @ima1zumi HTMLにあんなに気軽にJS埋め込めるとは知らなかった。セキュリティ意識が高まった
- @ima1zumi Railsは何でも準備してくれていて便利...

- @Kyo18 今日の内容はなかなか高度な話題が多かったので全ては理解しきれませんでしたが、credentialsやXSS対策などは自作アプリ開発の中で確実に必要になると思うのでしっかり復習して理解を深めておきたいです。
    - Railsは避けては通れない❗意図していない場面で処理がブロックされてしまって期待した挙動にならないということがよくある。

- @sanfrecce-osaka (ちなみに)複数DBの場合は rails g migration では --database で指定する必要がありました(後で上に移します :pray: )