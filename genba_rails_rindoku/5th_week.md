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
