## 2021/09/06
- 第10章 10.5.4から第11章 11.3.2 まで
    - `return`や`block`の挙動の違いからProc.newとlamdaどちらを使うか
        - > Proc.newやラムダの中でわざわざreturnやbreakを使おうとするな！！
        - > 「よし、落とし穴にはまらないように気を付けながらreturnやbreakを使うぞ」と思うのではなく、「うかつにreturnやbreakを使うと、わかりにくい不具合の原因になりそうだな」と思うようにしてくださいね。
        - [returnやbreakを使ったときのProc\.newとラムダの挙動の違い \- Qiita](https://qiita.com/jnchito/items/83410c0cda446efea582)
    - Proc.newとlambaの使い分けは引数の個数の柔軟性でするのかな
    - `did_you_mean`というgemがあることを初めて知った
- ふりかえり
    - ついにyeldとProcの章が終わった！チェリー本の終わりもついに見えてきた
    - 難しくて理解を避けてきた`Proc`は思った以上に身近なものだった

## 2021/09/07
- 第10章 11.3.3から 11.4.1 まで
    - デバッグの仕方は人によって大きくやり方が変わってきそう。人のデバッグ見てみたい
    - `pp`メソッドはRailsのデバッグで大活躍してます
        - [library pp \(Ruby 3\.0\.0 リファレンスマニュアル\)](https://docs.ruby-lang.org/ja/latest/library/pp.html)
    - `ApplicationRecord`ってクラス？モジュール？という疑問
        - `ApplicationRecord`はgem(module)
        - Modelクラスの継承関係は`XxxModel < ApplicationRecord < ActiveRecord::Base`
- 振り返り
    - デバッグを雰囲気ではなくできるようになりたい
    - 人のデバッグを見たり、ペアプロでデバッグするにはどうすればいいんだろう？
        - →デバッグ用の練習問題があればいいな
    - 11章以降は確認的な内容なので音読じゃなくて各自読む時間を設ける形にしてもいいのかも？
        - →明日形式変えてやってみましょう

## 2021\-09\-08
- 第10章 11.4.2から11.4.4 コラムまで
    - `tap`メソッド使いこなしたい！
        - [Object\#tap \(Ruby 3\.0\.0 リファレンスマニュアル\)](https://docs.ruby-lang.org/ja/latest/method/Object/i/tap.html)
    - Byebugを使いこなせそうにないのでこれからもRubyMineのデバッガーを使うことになりそう
    - 今回デバッグをしたコードはFizzBuzzだったけど、Railsのコードの方がデバッグのありがたみが分かりそう。Userインスタンスの中身を見れたり。

