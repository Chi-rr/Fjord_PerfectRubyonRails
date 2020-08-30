# 第4回パRails輪読会ノート(2020-08-30)
###### tags: `パRails`
- 時間：08:30〜10:30
- 範囲：2-1-2〜2-2-2

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
    - 一言
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴
    - 一言

- @masuyama13（マスヤマ）
    - プラクティス：オブジェクト指向（ボウリング）
    - ボウリング難しすぎる

- @hogucc（おぐち）
    - プラクティス：JavaScript（メモアプリ）
    - 非同期処理難しい...

- @chiroru (ちろる)
  - プラクティス：JavaScript(入門)
  - JS突入〜！

- @sanfrecce_osaka(もりつか)
- Rails歴
    - 実務2年前後
    - 学習期間含めると5年弱
- プラクティス: 来週金曜のMachida.rbの準備 & 再来週金曜の社内発表の準備
- タンク型の食洗機を買うか迷っているなう

- @universato(ユニ)
  - プラクティス: Rails に戻って kaminari 周りをやっています!
  - 好きなRuby のプラクティスを一通りやってしまった。

- @haruguchi-yuma
    - Railsの基本を理解する
    - 現在書籍でインプット中心の学習です！

- @igaiga
    - プラクティス: とちぎRubｙ会議の資料作成
    - 柚子シロップを漬けました

-@e6i24v
  プラクティス：Linux
  
- @Kyo18 
    - プラクティス：　オブジェクト指向のボーリングプログラム
    - いつもの2割増し眠いです。
  
- @ima1zumi
    - プラクティス：JSのメモアプリ
    - macbookが壊れた

- @imaharu 
	- メンター
	- 最近、サウナにハマってる
	- AWSのドキュメントを淡々と読んでます

## 疑問点・気づき
>### 書き込みサンプル
>@アカウント名 Rails楽しい

### 2-1-2
- @imaharu published_on
    - dateは、on // dateを使う機会がないので、定かでない
        - @igaiga あってますよー
    - datetimeは、at
- @imaharu 
	- date型からdatetime型に後から変更するの辛いので、初めからdatetimeにしておきたい派なんだけど、皆さんどうしてますか？
	    - @igaiga imaharuさんと同じで、無意識でdatetime型をつかってます。date型はタイムゾーンが難しいので。
- @imaharu migrationの中で、SQLを利用したくなった時のお作法を知りたい
    - パッと自分が思いつくのは、up/downで対称性を保つように実装する
        - @sanfrecce-osaka down?
        - @igaiga up/down対称性を保つくらいしか思いつかない
        - @sanfrecce-osaka @igaiga さんと同じく
    - ex. 照合順序を変更したい時とか
    - @imaharu 
    	- メモ: rakeタスクという手段を考えても良さそう
- @sanfrecce-osaka ↓で色々メソッドが生えるのは ApplicationRecord の親クラスの ActiveRecord::Base で色々と Module を extend や include しているため
```ruby
class Book < ApplicationRecord
end
```
- @sanfrecce-osaka 表2.1にupdateがないのは紙面上の都合かな？
    - 前の版から更新されていない可能性？
    - 前の版の時点ではまだupdateがなかった可能性が？
    - @igaiga updateメソッドがいつから入ったのかは追えていないが、Rails4.1で以下の変更が入ったので、updateメソッドが入ったのはRails4.0？
        - 「非推奨のActiveRecord::Generators::ActiveModel#update_attributesが削除されました。ActiveRecord::Generators::ActiveModel#updateをお使いください。」
        - 参考ポエム: https://esa-pages.io/p/sharing/4060/posts/404/c0a77802269ea10d000c.html


### 2-2-1
#### (1) scopeを定義する の前まで

- select
    - @sanfrecce-osaka `select` なしだと SELECT * で全カラムを取得する(Rails以外だとやったら怒られるやつ  :sweat_smile: )
    - @sanfrecce-osaka パフォーマンスチューニングのときに使う印象
    	- @igaiga Railsの場合は、ARオブジェクトが取れるからね ← :naruhodo:
    	- メモ: RubyのArrayに直すとメモリを節約できる場合がある
- joins・includes
    - @sanfrecce-osaka N + 1 の解決のときによく使う
    - c.f. [ActiveRecordのjoinsとpreloadとincludesとeager_loadの違い](https://qiita.com/k0kubun/items/80c5a5494f53bb88dc58)
        - @sanfrecce-osaka 今更この記事の著者が @k0kubun さんだということに気づいた :sweat_smile: 
        - @igaiga これは名著
            - includesは自動でpreloadとeager_loadが選択されるので、できればpreloadとeager_loadを明示的に指定してほしい

- to_a
    - @sanfrecce-osaka これでSQLが発行されるのはEnumerator::Lazyを意識している感じかな？(もしくは使っている？)
    - メモ: 単純に配列に直すから、という意味あいかも
    - メモ: Lazyの方が後なので意識している、ということはなさそう

- @imaharu 「明示的に任意の箇所でSQLを発行したい場合は、to_aメソッドを呼び出して即座にSQLを発行するというテクニックがあります」
	- どのようなSQLが生成されているかデバックする時にしか利用したことがない。他のユースケースがあれば知りたい。
	- @igaiga AR::Relationオブジェクトつくる ➡️ SQL発行 ➡️ AR::Relationオブジェクト変更 ➡️ SQL発行　とか？

- @hogucc 即座にSQLが発行されないのはメソッドチェインでクエリを書けるようにするためだったのか
    - @sanfrecce-osaka Merbの件
        - c.f. https://www.itmedia.co.jp/enterprise/articles/0812/24/news080.html
        - c.f. https://essa.hatenablog.com/entry/20081225/p1
        - c.f. https://mag.osdn.jp/10/08/31/0458203
    - @igaiga Rails3.0でMarbが統合されて、（たまたま）同じタイミングでArelも入ったのかもしれない
        - 松田さんの記事 https://gihyo.jp/dev/serial/01/ruby/0043
- @imaharu findとfind_by！について
	- メンターでレビューしてる際に、idをfind_by!してるとfindに変更するようオススメしてるが、皆さんはコメントせずにApproveしますか？
	    - @igaiga 意味がなければ私もfindにしてもらいます
        - @sanfrecce-osaka idを指定する場合は例外で落ちてほしいと言う意味でもfindですかね〜(find_by!も一緒だった)

#### (2) COLUMNまで

- @sanfrecce-osaka `scope` とクラスメソッドの挙動の違い、なるほど〜 :eyes: 
    - @igaiga scopeはAR::Relationを返して欲しい、と考えると覚えるのが楽です
- @sanfrecce-osaka デフォルトスコープは悪い文化 :see_no_evil: 
	- @imaharu サービスから退会する際にユーザーを論理削除してる場合は、利用してもいいかもと思ってみたり (default_scopeの使い所を探そうと、頭を捻って考えた時の例)
		- @imaharu DeletedUserモデルを作る方がいい
        - メモ: ↑のようなケースは使いたくないけど使わざるをえないこともある

- @masuyama13 `where("price > 3000")`と書かないのはなぜ？
    - c.f. https://railsguides.jp/security.html#sql%E3%82%A4%E3%83%B3%E3%82%B8%E3%82%A7%E3%82%AF%E3%82%B7%E3%83%A7%E3%83%B3
    - @imaharu CTFのWeb問題とかやると勉強になりますよ！
    - 今回は静的な文章なのでSQLインジェクションは起きないが、将来的に誰かが3000を変数に書き換える可能性を考慮して最初からプレイスホルダで書く、と良さそうらしい。

- @imaharu Book.costly.written_about("java")
	- Rubyではなく、Javaなのが面白い ← :crab: 


### 2-2-2
#### (1) 多対多のリレーションを実現する の前まで

- @sanfrecce-osaka 既存のデータがあってmigrationで外部キー制約等の追加によって不整合が発生してしまう場合、どうするのがベストプラクティスなんだろう？ :thinking_face: 
    - @sanfrecce-osaka rakeタスク(もしくはrails runner)でデフォルト値を追加した後に制約追加？
        - igaigaさんはこれ派(というかこれしかなさそう？)
    - @sanfrecce-osaka 書籍にある通り、 `bin/rails db:reset` ？
- @sanfrecce-oska has_many、belongs_to、before_action等の多くのDSLは実はクラスメソッド



## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！
>
- @Kyo18 結構高度な話が多く、現時点では理解しきれない話もありましたが頭のインデックスに詰め込んどきます！Railsの機能の追加の経緯のお話が面白かったです！
- @sanfrecce-osaka 知見たくさん :raised_hands: 
- @hogucc 感想から話が広がって良かったな〜と思いました！
- @hogucc 実務だとどうしているという話が聞けるのはありがたいです
- @chiroru ActiveRecodeの歴史的な経緯を含め、メソッドチェインで検索できる理由が知れたのが面白かったです。勉強になりました。

- @imaharu 質問や気付きを書いてる人が固定化されてる気がする。実は、質問したいけどできてない人がいないか心配。
	- @igaiga 難しめの質問は、少し手前から「これはこういう機能で」って説明が入ると分かりやすくてよさそう
		- @imaharu 確かに！説明できなければ、自分がわかっていないことに気がつけるのでいいですね
		- @sanfrecce-osaka :crab: 
- @sanfrecce-osaka 現役生も疑問とかを書きやすいようにしていきたいなぁ :thinking_face: 
    - どうすればいいかは思いついていない(´・ω・｀)
- @igaiga 難しい質問が多くてなってきたので、初歩的な質問がしづらくなってないか心配（なんでも気軽にどうぞ〜）
- @masuyama13 scopeのことがわかってよかった。歴史の話面白い！司会難しい…グダグダですみません😓
- @universato 書く時に、カーソルと実際に書かれる行が行ズレることがある(辛い)。 だんだん難しくなってきた。途中で書くべきことだったかもしれないけれど、joinsやinlcudesの三人称単数形メソッドを見ると「Rubyじゃない!!」と思う。このあたり、最初のうちはごっちゃになる気がする。RubyはどうもMatz氏が原形派らしい。

- @haruguchi-yuma id検索のときに、findとfind_by!のどちらを使うか、プレイスホルダーで書く話など、ためになりました。まだ、何かを作ったことがないので、Railsでのアプリ制作の全体の見通しが頭に入っていなくて、難しい話もありました。

## チャット
08:37
sanfrecce_osaka
みんな🎳で悩んでいる

08:51
ima1zumi
macbook の調子が悪いので途中で失礼します👋

08:57
ユニ@universato
😮

08:58
Kyo18
知らなかった

09:03
chiroru
画面共有でmacが熱くなってきたのでカメラオフで行きます〜🙇‍♀️

09:03
sanfrecce_osaka
👍

09:32
ユニ@universato
😮
😍

09:53
ユニ@universato
😮

09:54
Kyo18
あとからコードを触る人のためにそう書いてるのか！
ｗ

09:55
ユニ@universato
😂

10:06
ユニ@universato
👍

10:11
ユニ@universato
😮

10:12
ユニ@universato
👍

10:12
おぐち
👍