## 2021/10/11
- Chapter 3-3-1-5から　3-3-1-6まで
    - PostgreSQLのアップデートは`brew update && brew upgrade`とはまた別にPostgreSQLのアップデートをしないといけない
        - `brew postgresql-upgrade-database` でHomebrewがまとめて行ってくれる
        - [PostgreSQL DB のアップグレードは brew postgresql\-upgrade\-database が便利 \- Qiita](https://qiita.com/yasulab/items/237c3f9634055d665745)（安川さんの記事だ）
    - `new`と`create`で両方オブジェクトを作成する理由
        - 前のリクエストで作成した変数は次のリクエストでっそのまま使うことができない。
        - createアクションの場合、わざわざDBなどに保存するよりもシンプルのため、新しくオブジェクトを作ることが多い

## 2021/10/12
- Chapter 3-3-1-7から　 3-3-1-6まで
    - `human_attribute_name`の機能になぜ`human`がついているのか気になってる
      - :washimo:
      - > Transforms attribute names into a more human format, such as “First name” instead of “first_name”.
      - https://api.rubyonrails.org/classes/ActiveModel/Translation.html#method-i-human_attribute_name
      - `human format`ってhuman-readable的な……？
  - Flashメッセージの情報はセッションで保存されていることを初めて知った

# 2021/10/13
- Chapter 3-3-3から 3-3-3-2まで
    - `simple_format` 初めて知った。便利
        - https://api.rubyonrails.org/classes/ActionView/Helpers/TextHelper.html#method-i-simple_format
    - 英語なので避けてたrails_apiのdocをあたるようになってきた
    - Rails側でXSS対策をしなくてもscriptやHTMLタグが実行されなかった。
        - Rails側でやってくれてるのかな？

