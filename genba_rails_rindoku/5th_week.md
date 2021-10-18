## 2021/10/18
- Chapter 3-3-5から 4-1-3まで
    - マイグレーションはDBごとに適用する必要があることを知らなかった
    - マイグレーションを取り消す時（自分のイメージ）
        - 自分がさっき作成したmigrateを取り下げたい場合：`rails db:rollbask`
        - 過去のmigrateを変更/削除したい場合:changeやdownメソッドを書いて`rails db:migrate`
