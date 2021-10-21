## 2021/10/18
- Chapter 3-3-5から 4-1-3まで
    - マイグレーションはDBごとに適用する必要があることを知らなかった
    - マイグレーションを取り消す時（自分のイメージ）
        - 自分がさっき作成したmigrateを取り下げたい場合：`rails db:rollbask`
        - 過去のmigrateを変更/削除したい場合:changeやdownメソッドを書いて`rails db:migrate`
## 2021/10/19
- Chapter 4-1-3から　4-2-2 NOT NULL制約　まで
    - redo知らなかった。マイグレーション追加する時に習慣にしよう
        - 自分が書いたマイグレーションを`bin/rails db:migrate`してバージョンが上がること、また期待通りに動作することを確認する
        - `bin/rails db:migrate:redo`でバージョンを下げられることを動作確認する
    - マイグレーションファイルはmigrateした後にいじっては行けないものだと思っていたので、逆にpushしなければ変更してもいいことに気づいた
        - [GitHubにpushしたmigrationファイルは安易に修正してはいけません \- Qiita](https://qiita.com/jnchito/items/3525fd22973477b88411)
    - pushしなかったらマイグレーション変更してもいい？
        - 他の人がDBを反映していなかったら変更してもいい
        - むしろマイグレーションが複雑にならないように変更した方がいいケースもある
    - DBにNULL制約をつける理由
        - nullはnull
            - boolean型だったらtrue/falseのどちらでもない
            - countに含まれない

## 2021/10/20
- P133　4-2-3　文字列カラムの長さを指定する　から 4.3.3 必須かどうかの検証を追加する　まで
    - マイグレーションファイルの変更
        - バージョンを戻す際の処理を
            - `add_column`：自動生成してくれる（changeメソッドでOK）
            - `change_column`:自動生成してくれない（up/downメソッドを書く必要がある）
        - `bin/rails db:migrate:redo`をして確認をする
        - https://railsguides.jp/active_record_migrations.html#changeメソッドを使う
    - `save`と`save!`の違い
        - 検証（valid）エラーが発生した場合に`false`にするか例外が発生するかの違い
        - 自分は今までDB更新処理時のエラーも含まれているのかと思っていた（でも要検証かも）

## 2021/10/21
- P139 4.3.4 コントローラとビューで検証エラーに対応する　　から 4.3.4　から　4.3.5 まで（前半）
    - インスタンス作成時ではなく`save`の時に検証が走る
    - `rails c`で入力値を`'a' * 30`みたいに作成するの真似したい
- 4.3.6から 4.3.7 まで（後半）
    - 既存のvalidメソッドはテストをする必要がないとkomagataさんに言われたことがある
    - オリジナルの検証コードを書く場合
        - 検証を行うメソッドをモデルに追加・検証用のメソッドとして指定（手軽）
        - 自前のValidatorを作成する（共通利用できる）
    - Rails6.1で`update_attributes`などが削除されてたりする模様 :eyes: 
        - https://railsguides.jp/6_1_release_notes.html#active-record


