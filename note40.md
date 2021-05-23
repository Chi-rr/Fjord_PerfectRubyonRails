# 【第40回】パRails輪読会ノート(2021-5-23)
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
%w[sanfrecce_osaka hogucc fuga asya81 isshi-hasegawa chiroru].
  partition { |user| !%w[asya81].include?(user) }.
  flat_map(&:shuffle)
  #=> ["sanfrecce_osaka", "chiroru", "fuga", "isshi-hasegawa", "hogucc", "asya81"]
```

### 今日のスタート
13-1-5(p504)


## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- @hogucc bin/rails/routesでgrepするときgオプションが使える
    - https://railsguides.jp/routing.html#%E3%83%AB%E3%83%BC%E3%83%86%E3%82%A3%E3%83%B3%E3%82%B0%E3%81%AE%E8%AA%BF%E6%9F%BB%E3%81%A8%E3%83%86%E3%82%B9%E3%83%88

- @hogucc
    - modelsフォルダの直下にあるのはARのクラスだけじゃなくても良い。関心事ごとのロジックを表現するクラスがあっても良い
        - 例）bootcampアプリのgenerationクラス


## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @hogucc コールバックオブジェクト難しかったけど、使い方はざっくり理解できたのでよかった
- @hogucc 森塚さん、前回に引き続きコード用意していただいてありがとうございます！！助かりました🙏
- @hogucc modelフォルダ以下にはARオブジェクトのクラス以外も定義してよいというのは大きな発見だった

- @sanfrecce-osaka bootcamp アプリで使われているから先にやったけど内容濃くてなかなか初学者には難しい内容だったなー :sweat_smile: 
- @sanfrecce-osaka ルーティングの concern は業務で使っていきたいなー
- @masuyama13 難しくて全部は理解できなかったが雰囲気がつかめてよかった。また数ヶ月後に読み直したい

- @asya81 今回も前回に引き続き、難しかった😓
- @asya81 ルーティングにconcernが使えるのを初めて知った
- @asya81 コールバックオブジェクトは、Modelを肥大化させないために使える、と理解した
- @asya81 テストしやすさを考慮したコードを書くことも大事。保守性を保つための色んな方法が用意されているので、まずは知るところから
- @asya81 電話番号の暗号化、現場でもやられてるのかな？どこまで暗号化するべきなんだろう？？🤔
    - @hogucc うーん、要件によりそうですね...電話番号が機密性の高い顧客情報として扱われる場合は必要ですし、そうでない場合はする必要ないのかなぁと思ったりします
        - @asya81 なるほど〜。ありがとうございます🙏

- @chiroru ルーティングのconcernはそのうち使えそう
- @chiroru 森塚さんの画面共有の説明が有り難かったです！！準備ありがとうございます！

- @isshi-hasegawa bootcampアプリで実装されている内容ということを知れました！
- @isshi-hasegawa やはり内容が難しかったけど森塚さんのおかげでなんとかコードを追えました
- @isshi-hasegawa Code with me なかなか入れなくてごめんなさい～



- @fuga 今回も難しかったですが、concernの使い所がなんとなく掴めたので良かったです。

- @imaharu CallBackクラスあるの初めて知った
	- https://railsguides.jp/active_record_callbacks.html#%E3%82%B3%E3%83%BC%E3%83%AB%E3%83%90%E3%83%83%E3%82%AF%E3%82%AF%E3%83%A9%E3%82%B9

## チャット
hoguccから皆様 (8:51 午前)
https://docs.ruby-lang.org/ja/latest/method/Hash/i/merge.html
森塚真年から皆様 (9:09 午前)
Imaharuさんおはようございます〜
hoguccから皆様 (9:11 午前)
おはようございますー！
ryohta ochiから皆様 (9:28 午前)
https://railsguides.jp/active_record_callbacks.html#%E3%82%B3%E3%83%BC%E3%83%AB%E3%83%90%E3%83%83%E3%82%AF%E3%82%AF%E3%83%A9%E3%82%B9
hoguccから皆様 (9:42 午前)
この話が終わったら休憩いれましょうー
森塚真年から皆様 (9:45 午前)
コーヒーin
hoguccから皆様 (10:17 午前)
https://railsguides.jp/active_record_callbacks.html#after-initialize%E3%81%A8after-find
私から皆様へ (10:30 午前)
すみませんちょっと離席します・・！
森塚真年から皆様 (10:30 午前)
👍
hoguccから皆様 (10:33 午前)
もし抜けたい方いらっしゃったら、抜けていただいて大丈夫ですー！ありがとうございました！
森塚真年から皆様 (10:36 午前)
@ぺろさん すみません、少しお待ちいただけると〜🙏🙏🙏
Kuniaki Igarashiから皆様 (10:37 午前)
https://railsguides.jp/active_record_callbacks.html#%E5%88%A9%E7%94%A8%E5%8F%AF%E8%83%BD%E3%81%AA%E3%82%B3%E3%83%BC%E3%83%AB%E3%83%90%E3%83%83%E3%82%AF
森塚真年から皆様 (10:40 午前)
find_by_sql
hoguccから皆様 (10:46 午前)
この話が一区切りついたら是非ぺろさんの話を伺いたいなーと思います！
森塚真年から皆様 (11:01 午前)
https://www.tehepero.co.jp/
hoguccから皆様 (11:02 午前)
https://route06.co.jp/
Kuniaki Igarashiから皆様 (11:02 午前)
https://note.com/rimomonga/n/n1fb576224805
ryohta ochiから皆様 (11:26 午前)
抜けます〜
森塚真年から皆様 (11:27 午前)
https://github.com/corocn/paternity-leave-in-japan
剛 國分から皆様 (11:30 午前)
所用のためお先に失礼しますーお疲れ様でした！
Kuniaki Igarashiから皆様 (11:31 午前)
https://www.ashita-team.com/jinji-online/labor/9816

