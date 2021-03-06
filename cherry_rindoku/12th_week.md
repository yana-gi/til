## 2021-08-10
第7章 7.10.6から7.10.8まで
### 疑問点や気づき

- モンキーパッチはうまく使えば開発の効率を高められるけど、弊害にも注意
- オーバーライドとモンキーパッチの違い
  - オーバーライドは継承元の同名のクラスを上書きする
  - モンキーパッチはクラス自体を上書きしたりクラスを追加したりする

- クラスメソッドは特異メソッドの一種
- 自分の「クラスメソッド以外に特異クラスを使う場面はある？」という質問
  - object ENVは ENVclassがあるわけではなく、ENVというobjectにメソッドを定義している（ユニさんより）

## 2021/08/11
第7章 7.10.9から第7章 7.11まで（クラスの最後まで）
### 疑問点や気づき
- 動的型付け言語と静的型付け言語の違いいまだによくわかってない
- ダックタイピングはRailsのポリモーフィックのプラクティスでも出てきた

- クラスが終わった！
- いろんな話が出てきたけど覚えてはいないのでクラスを定義する際にチェリー本のクラスの章を読み返したい
- クラスの理解は深まったけど、オブジェクト指向とはあまり仲良くなれなかった。やっぱりコード書かないと身につかないかも

## 2021/08/12
- メソッドを`private`に設定する(include)のはモジュールの定義側で、クラスメソッドを定義する(extend)のはモジュールを呼び出す側なんだと思った
- `extend`で呼び出したクラスメソッドはクラス直下やクラスメソッド定義内、`クラス名.メソッド`で呼び出せる。インスタンスメソッド定義内や`インスタンス名.メソッド`では呼び出せない
```ruby
module Loggable
   def log(text)
     puts "[LOG] #{text}"
   end
 end

class Product
   extend Loggable
   def self.create_products(names)
     log 'create_products is called.' #=> 呼び出せる
   end

   def instance_products(names)
     log 'instance_products is called.' #=> 呼び出せない
   end

   log 'Defined Product class.' #=> 呼び出せる
 end

Product.log(‘hoge’) #=> 呼び出せる
Product.new.log(‘hoge’) #=> 呼び出せない
```
- クラス構文の直下ではクラスメソッドしか呼び出せない
- モジュールのテストの仕方が気になる。今回はモジュールをミックスインしたクラスを呼び出していたけど、テストクラスから直接モジュールを呼び出してテストすることもあるのかな。bootcamp見てみよう

## 2021/08/13
- 第8章 8.5から8.5.3まで

### 疑問点・気づき
- `is-a`の関係が成り立たなければ継承を使うべきではない（Moduleで定義するべき）
- モジュールをincludeしていれば`Object#is_a?`がtrueを返す
- という２つを混同しないようにしたい
- Enumerableはeachが実装されていることを前提としたモジュール。
- include先でeachを実装する必要がある。
