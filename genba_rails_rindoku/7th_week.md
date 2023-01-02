## 2021/11/01
- Chapter 4-6から 4-8まで
    - クエリー用のメソッドは実行部分に当たるメソッドを呼ぶことで実行される
        - `User.wehre(admin: true).first`だった`User.wehre(admin: true)`の時点では実行されない
    - `ActiveRecord::Relation`
        - https://api.rubyonrails.org/v6.1.4/classes/ActiveRecord/Relation.html
        - 配列っぽいけど配列ではない
        - `where`などのクエリメソッドや、`has_many` `belongs_to`などの関連の呼び出しができる
        - これらはただのuserオブジェクトの配列では使えない
    - Rails consoleにコードの変更を反映させたい場合は、`reload!`を実行する

## 2021/11/02
- Chapter 4-9から Chapter4の終わり まで
    - rails_autolinkは比較的コンパクトなgemなので頑張ったら読めそう
        - https://github.com/tenderlove/rails_autolink
    - 本中に紹介されているrinkuというgemと比較してみても面白そう
        - https://github.com/vmg/rinku
    - 伊藤さんのMinitestとRSpecのLT
        - [RSpecとMinitest、使うならどっち？ / \#kanrk06 \- Speaker Deck](https://speakerdeck.com/jnchito/number-kanrk06)
