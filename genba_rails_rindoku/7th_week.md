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
