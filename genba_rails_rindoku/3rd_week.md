## 2021/10/04
- Chapter2 2-6-2から3-1-1まで
    - 実装をどこから始めるかという話、みんなどうしているのか気になる
        - 自分は新規画面作成だったらルーティングから、既にある画面の機能追加だったらビューから着手していた
        - 3章でどう進めているのか意識してみよう
    - そういえばチーム開発でローカルのポスグレのバージョン気にしたことがなかったな……

## 2021/10/05
- Chapter3 3-1-2から 3-1-6 途中まで
    - production環境はこの間初めてherokuでデプロイしたときに触った。
    - development環境は開発者なら誰でも見たり触れるけど、production環境を見たり触れる人は限られている by komagataさん
    - 確かにステージング環境ってどこのDB見てるんだろう？
        - `database.yml` には書いてないhttps://github.com/fjordllc/bootcamp/blob/main/config/database.yml
        - [Bootcampのデプロイ方法 \| FJORD BOOT CAMP（フィヨルドブートキャンプ）](https://bootcamp.fjord.jp/pages/133)
    - 自分が雰囲気でRailsをやっていることが分かった

## 2021/10/08
- Chapter3 3-3-1-2 3-3-1-5の途中まで
    - GETとPOSTの違い、なんとなく分かっていたつもりだけど明確な使い分けは理解していなかった
    - [GETとPOSTの違いについて \- Qiita](https://qiita.com/kanataxa/items/522efb74421255f0e0a1#%E4%BD%BF%E7%94%A8%E7%94%A8%E9%80%94)
        - GETはリソースを取得するときに使うもの
            - 例) https://bootcamp.fjord.jp/questions?solved=true
        - POSTはリソースに対して特有の処理をするときに使うもの
            - 例) https://bootcamp.fjord.jp/reports/new
    - Rails5.1から`form_with`が推奨になったけど、Railsガイドのサンプルコードで`form_with`が使われていないという罠
