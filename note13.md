# 【第13回】パRails輪読会ノート(2020-11-01)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @chiroru
タイマー： @kyo
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
    - 今日のテーマ(ハロウィン何かしましたか？orマイブーム)
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ(ハロウィン何かしましたか？orマイブーム)

- @ima1zumi
    - 今日は諸事情でカメラマイクオフで参加します :pray:
    コメント読み上げていただけるとありがたいです！
    - プラクティス：スクラム、就活
    - ハロウィン:ハロウィンっぽい柄のお菓子をもらいました

- @chiroru 
  - VueCLI
  - ハロウィン+マイブーム：丁寧な暮らし系動画(ハロウィンver)を観ました

- @hogucc(おぐち) 
  - スクラム開発、自作サービスのペーパープロトタイプ作成
  - マイブーム: どうしよう...マイブームが無い...
  - 全然関係ないですが、ハウリングしそうなのでミュート率高めで参加します。イヤホン買わないと...

- @masuyama13 (マスヤマ)
    - スクラム開発
    - 身内の誕生日と重なっているのでハロウィンぽいことはしていません🎃
        - 無職なのにプレゼントを買わされたぐらい🎁

- @sanfrecce-osaka(もりつか)
    - プラクティス
        - 来週
            - Machida.rb の準備
            - Omotesando.rb での LT の準備
            - Ruby Gold 受験の準備
            - 参加する輪読会(Rubyの仕組み・メタプログラミングRuby)の準備
            - 家事全般
            - 確定申告(去年)
        - 再来週
            - 社内発表の準備
    - 今日のテーマ：ハロウィン何かしましたか？orマイブーム
        - ハロウィン
            - 404 Not Found
        - マイブーム
            - 日報的にYWTを使う
                - https://www.kikakulabo.com/tpl-ywt/#:~:text=YWT%E3%81%A8%E3%81%AF%E3%80%81%E3%80%8CY%EF%BC%9A,%E3%81%AE%E6%B5%81%E3%82%8C%E3%81%AF%E5%90%8C%E3%81%98%E3%81%A7%E3%81%99%E3%80%82

- @igaiga
  - Rails歴10年, プラクティス: 講演資料づくりx2
  - ハロウィンはfall guys(ゲーム)でハロウィンコスアバターが安かったので買って着ました


## 疑問点・気づき
>### 書き込みサンプル
>@アカウント名 Rails楽しい
### 5-2-4〜5-2-8 (8分)

- > cache の不足
    - @sanfrecce-osaka 再レンダリングされるから cache されない ActiveStorage だともう1度ファイルを添付し直さないといけないのか :eyes: 

- @masuyama13 ActiveStorageはプラクティスでやったときに簡単に導入できた覚えがあるが、問題点もあることがわかった

- @ima1zumi 自作サービスに入れようと思っていましたが、validationヘルパーが不足していることがわかってよかったです。いろいろ機能調べてから導入しようと思いました。
    - @sanfrecce-osaka 参考: 他の候補 => carrierwave・shrine ←ありがとうございます！！

### 5-3-1〜5-3-4(12分)

- @sanfrecce-osaka rails/mailers/:mailer_name/:method_name でプレビュー見れるの知らなかった、知見
- @sanfrecce-osaka 開発環境で実際に送信されたメールを確認するためによく使われる Gem
    - letter_opener + letter_opener_web
        - bootcamp では letter_opener
    - mailcatcher
    - c.f. https://qiita.com/k-shogo/items/d85905535a64e82a3b2b
- @hogucc メールのプレビューできるのは便利!
- @hogucc 非同期でメール送信するときメール送信以外の処理でこけた場合にメールを送らないようにする仕組みは必要そう

### 5-4-1~5-4-4(13分+α)

- @sanfrecce-osaka Action Mailbox は hey という Basecanp のサービスで使われている
    - c.f. https://gihyo.jp/lifestyle/clip/01/awt/202007/02
    - c.f. https://hey.com/
    - ~~これのために Rails に組み込まれたという噂も~~
- @sanfrecce-osaka Kaigi on Rails での Action Mailbox の発表
    - c.f. https://youtu.be/UkYxiGQT694
- @masuyama13 昔mixiで、メールを送るとその内容を日記として投稿できる機能があったけど、そういうときAction Mailboxを使うのだろうか
- 【NOTE】 メールを受けてそれをトリガーにして何か処理をする際に Action Mailbox を使えそう(@igaiga さん談)

### 5-4-5~5-4-6(6分+α)

- @sanfrecce-osaka Web UI が用意されているの便利そう :eyes: 
    - @sanfrecce-osaka このあたり API モードでも使えるのかな？ :thinking_face: 

### 5-5-1~5-5-4(11分+α)

- with_rich_text_xxxx_and_embeds
    - @sanfrecce-osaka embed => 埋め込む
- @masuyama13 「アンコメント」の意味がよくわからなくなる😓
    - アンコメント：コメントじゃない状態（コードとして有効な状態）にすること
    - **un**comment
- @hogucc with_rich_text_xxxxとwith_rich_text_xxx_and_embedsの使い分けが理解できていない...

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka 使用経験が少ない or まったくないところなので(想定通りだけど)あまり議論は盛り上がらなかった :sweat_smile: 
    - Action Mailbox の使えそうな場面に関してイメージが付いたので今後使用できそうな場面があれば使っていきたい :muscle: 
    - Action Text も使ってみたいが個人的には最近 React ばかりで Rails で View を書かn(ry
- @hogucc ActionMailboxやActionTextは存在自体初めて知った。プレビュー機能とか手軽に試せる手段を用意してくれているRailsは優しい
- @masuyama13 ActiveStorage にバリデーションやcacheがないことを知れてよかった
- @chiroru メール周りほとんど触ったことがなかったので、輪読会を通して知ることができてよかったです。

- @ima1zumi Railsが提供している標準機能について概要を知ることができて良かったです！

