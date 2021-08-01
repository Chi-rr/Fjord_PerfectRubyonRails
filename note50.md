# 【第50回】パRails輪読会ノート(2021-8-1)
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
11-2から


## 疑問点・気づき

### 11-2 値オブジェクト〜11-2-2 いつ導入すべきか(７分)

- @sanfrecce-osaka 値オブジェクトは値自身をオブジェクトとして扱う
- @sanfrecce-osaka 値オブジェクトを使うことでドメインロジックを分割できる
- @hogucc 値オブジェクトを導入するのはある値に対する同じロジックを複数のモデルで共有したいとき

### 11-2-3 実装例(7分)


- @imaharu

```ruby=
class PhoneNumber
  attr_reader :value
  delegate :hash, to: :value

  def == (other)
    self.class == other.class && self.value == other.value
    # other.class == self.class && self.value == other.value こちらの方が意図と合っている気がする
  end
```

```ruby=
class User < ActiveRecord
  # roleカラムで、管理者、一般ユーザー
end

class Admin
  def initialize(user_object)
    raise ArgumentError if user_object.class != User.class
    raise ArgumentError if user_object.role != "admin"
    @admin = user_object
  end
  
  def hoge
    @admin.hoge
  end
end
```

そもそも論

```ruby=
class Account < ActiveRecord
  belongs_to :user
  belongs_to :admin
end

class User < ActiveRecord
  delegate :email, to: account
  has_one: account
  # has_many: accounts
end

class Admin < ActiveRecord
  delegate :email, to: account
  has_one: account
  # has_many: accounts
end
```


- @imaharu モデルの肥大化を防ぐためのValue Objectを利用するというよりは、以下が主目的では？
    - 値オブジェクトには、このような実装上の利点だけでなく、モデリングの上でも利点があります。質の高いアプリケーションを開発するには、ドメインモデルを正確に抽出することはもちろん、抽出したドメインモデルを実装に正確に反映させることも同じくらい重要です。2つの間に齟齬があると、両者を段階的に洗練していくことが難しくなるからです。
- @sanfrecce-osaka https://twitter.com/MinoDriven/status/1380773721032433674?s=20

- @imaharu メモ: composed_of, classify
    - https://api.rubyonrails.org/classes/String.html#method-i-classify
    - https://api.rubyonrails.org/classes/ActiveRecord/Aggregations/ClassMethods.html#method-i-composed_of

- @sanfrecce-osaka composed_of　、めっちゃ良く出来てる(実務ですぐ使えそう)
    - @sanfrecce-osaka AR の where とかに値オブジェクトをそのまま渡して使えるの便利。Rails 賢いなぁ
    - @sanfrecce-osaka ネームスペース切ったクラスを値オブジェクトとして使いたい場合は class_name を使う感じかな
    - @sanfrecce-osaka mapping で二次元配列で渡すのはどういうケースだろう？ :eyes:
        - @asya81 ドキュメントに例がありました〜
        - https://api.rubyonrails.org/classes/ActiveRecord/Aggregations/ClassMethods.html#method-i-composed_of
            - @sanfrecce-osaka 感謝 :pray: 
    - @sanfrecce-osaka constructor で 初期化時のメソッド名を指定できるの便利
    - @sanfrecce-osaka converter は便利そうだけど型のない世界だから使い所ミスるとわかりにくいコードになりそうな気もする :thinking_face: 

```ruby=
composed_of :address, mapping: [ %w(address_street street), %w(address_city city) ]
```        
    
```ruby=
# 値オブジェクト
class Address
  attr_accessor :street, :city
end

class Country < ApplicationRecord::Base
  # column: address_street
  # column: address_city
  composed_of :address, mapping: [ %w(address_street street), %w(address_city city) ]
end
```

- @sanfrecce-osaka composed_of 使ってみたいので bootcamp アプリで利用できる場所はないかなぁと考えている ~~(と思ったけど実際には現役生には難しいよなぁ :sweat_smile:)~~
- @hogucc classifyメソッド
    - https://api.rubyonrails.org/classes/String.html#method-i-classify
    - https://api.rubyonrails.org/classes/ActiveSupport/Inflector.html#method-i-classify
    - どっちを使っているかは実装見てみないとわからなそう

- @asya81 composed_of、初めて知りました〜👀

### 11-3 サービスオブジェクト〜11-3-2 いつ導入すべきか(7分)

- @sanfrecce-osaka 後述されているけど気をつけないとすぐ :god: になるサービスオブジェクトさん
    - @sanfrecce-osaka 後述されている部分読んでなるほど～となった
    - @sanfrecce-osaka サービスオブジェクトに対する理解が深まった
    - @sanfrecce-osaka この節は Rails を利用しているエンジニアは必読の節なのでは・・・
- @sanfrecce-osaka サービスオブジェクトは複数のオブジェクトを操作するロジックを実装する際に利用する

### 11-3-3 実装例〜11-3-4 導入時のポイント(10分)

- @sanfrecce-osaka リスト11.11 のコメントに typo
    - 誤: ②何らかのエラーが発生した場合、対応すモデルの属性...
    - 正: ②何らかのエラーが発生した場合、対応するモデルの属性...
- @sanfrecce-osaka サービスオブジェクトはイミュータブルで状態を持たない ← ここ重要
- @sanfrecce-osaka サービスオブジェクトはなんらかの共通のインターフェースを持つ(e.g. call)
    - @sanfrecce-osaka 【MEMO】 サービスオブジェクトはクラスメソッドを1つだけ公開するといい
- > よくある失敗 「#{ モデル名 }Service」
    - @sanfrecce-osaka わかる of わかる
- @sanfrecce-osaka モデルに実装すべき場合はモデルに実装する
    - ココに気をつけないとすぐ :god: が生まれそう :innocent: 
- @sanfrecce-osaka イベントを表現するモデル、なるほど
    - Rails の model は テーブルと 1 対 1 でない
- @sanfrecce-osaka イベントを表現するモデルかサービスオブジェクトかは一長一短なのでケースバイケース
- https://qiita.com/joker1007/items/25de535cd8bb2857a685
- @hogucc オブジェクトの値を直接参照・更新するのはModelに任せる。サービスオブジェクトでやると保守性が低下する
- @hogucc　サービスオブジェクトを導入する前にまずModel側でイベントが定義できないか考えてみようと思った
    - イベントが存在しないor存在しても記録する必要がない場合はサービスオブジェクトを導入する

#### 【オマケ】 reflect_on_aggregation のコードリーディング

##### reflect_on_aggregation

activerecord-6.1.3.2/lib/active_record/table_metadata.rb:61
↓
activerecord-6.1.3.2/lib/active_record/reflection.rb:66

> Account.reflect_on_aggregation(:balance) # => the balance AggregateReflection

```ruby=
      def reflect_on_aggregation(aggregation)
        aggregate_reflections[aggregation.to_s]
      end
```

##### aggregate_reflections

activerecord-6.1.3.2/lib/active_record/reflection.rb:12

ActiveRecord::Reflection の class_attribute として定義されている

https://railsguides.jp/active_support_core_extensions.html#class-attribute

##### add_aggregate_reflection

- 【MEMO】 @sanfrecce-osaka String#-知らなかった
    - https://docs.ruby-lang.org/ja/latest/class/String.html#I_--2D--40


aggregate_reflections に代入している add_aggregate_reflection 

```ruby=
      def add_aggregate_reflection(ar, name, reflection)
        ar.aggregate_reflections = ar.aggregate_reflections.merge(-name.to_s => reflection)
      end
```

は activerecord-6.1.3.2/lib/active_record/aggregations.rb:241 の composed_of で呼ばれている

```ruby=
        def composed_of(part_id, options = {})
          options.assert_valid_keys(:class_name, :mapping, :allow_nil, :constructor, :converter)

          unless self < Aggregations
            include Aggregations
          end

          name        = part_id.id2name
          class_name  = options[:class_name]  || name.camelize
          mapping     = options[:mapping]     || [ name, name ]
          mapping     = [ mapping ] unless mapping.first.is_a?(Array)
          allow_nil   = options[:allow_nil]   || false
          constructor = options[:constructor] || :new
          converter   = options[:converter]

          reader_method(name, class_name, mapping, allow_nil, constructor)
          writer_method(name, class_name, mapping, allow_nil, converter)

          reflection = ActiveRecord::Reflection.create(:composed_of, part_id, nil, options, self)
          Reflection.add_aggregate_reflection self, part_id, reflection
        end
```

ActiveRecord::Reflection.create や Reflection.add_aggregate_reflection に渡している self は ActiveRecord::Aggregations が ActiveRecord::Base で extend されているので AR オブジェクトのインスタンス

##### ActiveRecord::Reflection.create

```ruby=
      def create(macro, name, scope, options, ar)
        reflection = reflection_class_for(macro).new(name, scope, options, ar)
        options[:through] ? ThroughReflection.new(reflection) : reflection
      end
```

##### ActiveRecord::Reflection.reflection_class_for

```ruby=
        def reflection_class_for(macro)
          case macro
          when :composed_of
            AggregateReflection
          when :has_many
            HasManyReflection
          when :has_one
            HasOneReflection
          when :belongs_to
            BelongsToReflection
          else
            raise "Unsupported Macro: #{macro}"
          end
        end
```

##### AggregateReflection

```ruby=
    class AggregateReflection < MacroReflection #:nodoc:
      def mapping
        mapping = options[:mapping] || [name, name]
        mapping.first.is_a?(Array) ? mapping : [mapping]
      end
    end
```

##### MacroReflection#initialize

```ruby=
      def initialize(name, scope, options, active_record)
        @name          = name
        @scope         = scope
        @options       = options
        @active_record = active_record
        @klass         = options[:anonymous_class]
        @plural_name   = active_record.pluralize_table_names ?
                            name.to_s.pluralize : name.to_s
      end
```

##### つまり

```ruby=
self.class.reflect_on_aggregation(:money).mapping.each do |attribute, _|
```

の

```ruby=
self.class.reflect_on_aggregation(:money)
```

は composed_of で定義した値オブジェクトの mapping を返している

### 12-1 ユースケースとモデル(5分)


### 12-2 データベースと紐づかないモデルを作る(12分)


### 12-3 フォームオブジェクト(10分)


### 12-4 プレゼンター(7分)



## 振り返り(よかった点・次回に向けての改善点等)
>※ より良い勉強会にするため、FBお願いします！

- @sanfrecce-osaka 値オブジェクト(composed_of)便利
- @sanfrecce-osaka サービスオブジェクトに対する理解が深まった
- @sanfrecce-osaka 予習しておいたおかげで色々書けた
    - @hogucc ありがとうございます！
- @sanfrecce-osaka この章以降皆読んでほしい。オブジェクト指向を理解していれば Rails はまだまだ戦える子だと感じた

- @chiroru 値オブジェクト、サービスオブジェクト、なんとなくわかった

- @asya81 値オブジェクトやサービスオブジェクトがどういうものかが何となくわかった。
- @asya81 まずはオブジェクト指向を理解する必要があると思ったので、「オブジェクト指向設計実践ガイド」を読むところからやります！
    - @hogucc :+1: 
    - @sanfrecce-osaka :+1: 
- @asya81 どう設計するかがイメージできるようになったら、いろんな手段を知っていると便利そう。

- @hogucc モデルとサービスオブジェクト、どっちに何を書くかが明確になってよかった
- @hogucc 11章終わった！個人的にはすごく興味がある内容だった
- @hogucc オブジェクト指向、理解するの大事と痛感した
- @imaharu 11章は楽しい
    - @sanfrecce-osaka わかりみ
    - @hogucc わかる...