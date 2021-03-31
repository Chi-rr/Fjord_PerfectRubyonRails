# 【第33回】パRails輪読会ノート(2021-3-28)
###### tags: `パRails`
## 時間
予定
- 08:30〜10:30
- 司会・タイマー
司会： @kyo
タイマー： @masuyama
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
    - 今日のテーマ：
> - メンター、OB
    - 名前(@username + 呼び名)
    - Rails歴/プラクティス
    - 今日のテーマ：

## ドライバーガチャ

モブプロのドライバーをしたい方は↓の一番最初の配列に名前を書いてください〜 :+1: :+1: :+1:

```ruby=
%w[sanfrecce_osaka igaiga masuyama13 ikuma-t hogucc chiroru].
  partition { |user| !%w[hogucc].include?(user) }.
  flat_map(&:shuffle)
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
p.398から

## 疑問点・気づき

### 割り込み推奨！
今回はモブプロになるので、見ていて疑問に思ったことはその場でどんどん質問してください。
（後からだと回答が難しくなることがあるため）
Rails以外の質問（GitHubなど）や「何をやってるのか全然わからない」など、なんでもOKです！

>### 書き込みサンプル
>@アカウント名 Rails楽しい

- @hogucc
  - https://developer.mozilla.org/ja/docs/Web/API/Console/log#logging_objects
- splice　の代わりに分割代入を使う

```javascript=
const [first, second, ...hoge] = ['Jan', 'Feb', 'April', 'June'];
const months = [first, second, "March", ...hoge]
console.log({ months })
```

```javascript=
const deleteWithoutEffect = (months) => {
  const [first, second, third, ...hoge] = months
  return [first, second, ...hoge]
}

const watasu = ['Jan', 'Feb', 'March', 'April', 'June']
const deleted = deleteWithoutEffect(watasu);
console.log({ deleted })
```

- @hogucc
  - https://lodash.com/

```javascript=
import Turbolinks from "turbolinks"

document.addEventListener("turbolinks:load", function(event) {
    const forms = document.querySelectorAll("form[method=get][data-remote=true]")
    for (const form of forms) {
        form.addEventListener("ajax:beforeSend", function({ detail: [,{url: requestUrl}] }) {
            Turbolinks.visit(requestUrl)
            event.preventDefault()
        })
    }
})
```
- ransackはバージョンアップが大変らしい

## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @hogucc オブジェクトリテラル関連の話すごく勉強になりました！今すぐ使えるTipsなのでこれからたくさん使っていこうと思います
- @sanfrecce-osaka JS 談義が盛り上がった :raised_hands: 
    - [追加情報] 社内発表のスライド: [今どきのなういJavaScriptの書き方](https://esa-pages.io/p/sharing/14573/posts/87/28eae192afbbec94d1ce.html)
    - [追加情報] elasticsearch の normalization: https://www.elastic.co/guide/en/elasticsearch/plugins/current/analysis-icu-normalization-charfilter.html
- @chiroru 森塚さんのJS講座、とても勉強になりました。分割代入、使いこなせるようになりたい
- @chiroru Elasticsearch良さそう。
- @masuyama13 JavaScript めっちゃ勉強になった

## チャット
森塚真年から皆様 (8:36 午前)
https://developer.mozilla.org/ja/docs/Web/HTML/Element/main
森塚真年から皆様 (9:14 午前)
https://developer.mozilla.org/ja/docs/Web/API/Console/log
森塚真年から皆様 (9:22 午前)
https://jp.vuejs.org/v2/guide/reactivity.html#%E9%85%8D%E5%88%97%E3%81%AB%E9%96%A2%E3%81%97%E3%81%A6
https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/splice
森塚真年から皆様 (10:51 午前)
https://rubygems.org/gems/mimemagic/versions
https://weblog.rubyonrails.org/2021/3/26/marcel-upgrade-releases/
森塚真年から皆様 (11:00 午前)
https://github.com/mimemagicrb/mimemagic/search?q=nokogiri&type=issues
https://ja.wikipedia.org/wiki/Ruby%E3%83%A9%E3%82%A4%E3%82%BB%E3%83%B3%E3%82%B9
私から皆様へ (11:10 午前)
https://github.com/carrierwaveuploader/carrierwave/issues/2548
hoguccから皆様 (11:11 午前)
https://hackmd.io/yjvOXmPPRBeZ241pn-hZZw?view
森塚真年から皆様 (11:11 午前)
https://github.com/carrierwaveuploader/carrierwave/issues/2553
Kuniaki Igarashiから皆様 (11:13 午前)
https://www.ruby-lang.org/en/about/license.txt
森塚真年から皆様 (11:15 午前)
https://hackmd.io/@mametter/mimemagic-info-ja#mimemagic%E3%81%AB%E4%BE%9D%E5%AD%98%E3%81%97%E3%81%A6%E3%81%84%E3%82%8BRails%E4%BB%A5%E5%A4%96%E3%81%AEgem
森塚真年から皆様 (11:48 午前)
https://andpad.connpass.com/event/208366/
H Masuyamaから皆様 (11:55 午前)
https://bootcamp.fjord.jp/practices/135
森塚真年から皆様 (11:59 午前)
https://zaitakushigoto.com/techacademy/#:~:text=%E3%81%AE%E6%B1%82%E4%BA%BA%E4%B8%80%E8%A6%A7-,%E8%87%AA%E5%88%86%E3%81%A7%E6%99%82%E9%96%93%E3%82%92%E6%B1%BA%E3%82%81%E3%81%A6%E3%80%81%E3%82%B9%E3%82%AD%E3%83%AB,%E6%B4%BB%E3%81%8B%E3%81%97%E3%81%A6%E6%99%82%E7%B5%A62%2C500%E5%86%86&text=%E8%AC%9B%E5%B8%AB%E3%81%AF%E3%83%A1%E3%83%B3%E3%82%BF%E3%83%BC%E3%81%A8%E5%91%BC%E3%81%B0,%E6%96%B9%E5%90%91%E3%81%91%E3%81%AE%E4%BB%95%E4%BA%8B%E3%81%A7%E3%81%99%E3%80%82
H Masuyamaから皆様 (11:59 午前)
一瞬外します
森塚真年から皆様 (12:01 午後)
irb(main):001:0> 8 * 20
=> 160
irb(main):002:0> 800_000 / 160
=> 5000
H Masuyamaから皆様 (12:02 午後)
戻りました〜
森塚真年から皆様 (12:15 午後)
https://japanese.engadget.com/jp-2019-04-23-landroid.html?guccounter=1&guce_referrer=aHR0cHM6Ly93d3cuZ29vZ2xlLmNvbS8&guce_referrer_sig=AQAAAKGR0paaCnzs96LxEdJRfIZF6aZh03AigT4zf4KhIsL0kOMB7Zwmn7Q7cZfcSYF2v-lIOoKq9qP2F1DiF-6HAhPZTxfk09_1Yy2SyM7atXkc7KjIYNxl_Pdl-9DOGzj5epDPVqe7wFKYaOB4zmt3mpoJJsmu7TPxKOnsOZEpmRSH
https://news.livedoor.com/article/detail/15839731/
Kuniaki Igarashiから皆様 (12:17 午後)
https://pocketti.me/?p=3255
hoguccから皆様 (12:23 午後)
https://www.jorudan.co.jp/time/rosenzu/%E4%B8%AD%E5%A4%AE%E3%83%BB%E7%B7%8F%E6%AD%A6%E7%B7%9A%E5%90%84%E5%81%9C/
森塚真年から皆様 (1:01 午後)
https://aws.amazon.com/jp/elasticsearch-service/pricing/
https://www.elastic.co/jp/what-is/elasticsearch
https://aws.amazon.com/jp/elasticsearch-service/
森塚真年から皆様 (1:06 午後)
https://aws.amazon.com/jp/elasticsearch-service/features/