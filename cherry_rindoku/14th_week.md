## 2021/08/23
- 第9章 9.2.5から9.2.8 まで
    - `StandardError`：発生しやすいエラーのスーパークラス
    - rescue節に何も指定しない場合、捕捉されるのは`StandardError`とそのサブクラス
    - 複数のresucue節を指定する場合は、呼び出す順番に注意。スーパークラスは後の方に書く。
    - 他のプログラミング言語の`Exception`がRubyでいう`StandardError`

    - エラーが出てきたときはとりあえず文をそのまま検索していたけど、エラークラスをるりまで調べてみるのもよさそう
    - 後でbootcampアプリで例外を使っているところ調べてみよう

## 2021\-08\-24
- 第9章 9.3から9.4.4 まで
    - 異常終了と例外処理の違い
        - 異常終了 : エラーが発生したらそこで処理を終える
        - 例外処理 : エラーが発生したら例外処理をして次の処理に進む
        - yu-kichiさんの説明のおかげで理解できた
    - > if 式は、条件が成立した節(あるいは else 節)の最後に評価した式の結果を返します。else 節がなくいずれの条件も成り立たなければ nil を返します。
https://docs.ruby-lang.org/ja/latest/doc/spec=2fcontrol.html#if
        - 知らなかった！
    - 自分でrescueしようとせずフレームワークに例外処理を任せた方が安全。

## 2021/08/25
- 第9章 9.4.5から9.5.5 まで
    - できるだけ早い段階で例外を発生させてプログラムを停止させると、原因の調査と対策がしやすくなる
    - 文字列を返すメソッドを作ったつもりがnilが返ってくる処理を作ってしまった、というのはいつかやってしまいそう
    - Rubocopの忠告に~~歯向かえる~~自分たちで判断できるようになった
    - 例外処理は外部から入力を受け取るときによく使うのかなと思った
    - Javaだとメソッド定義時に引数と戻り値の型を指定するんだけど、今日の範囲を読んで静的型付けの良さが少し分かった

## 2021/08/26
- 第9章 9.6から 9.6.5 まで 
    - `File.open`はブロック付きでオープンすると、メソッドの実行後に自動的にクローズされる
    - `ensure`節にreturnを書くと例外が発生しなくてもメソッドの戻り値がensure節の値になる。普段Rubyではreturnを使わないけどガード節を書くときなどに注意かも
- 第9章 9.6.8 まで
    - メソッドの中身全体が例外処理で囲まれている場合は`begin`と`end`を省略することができる
    - 2.5以降ではメソッドだけでなく`do/end`ブロック内でも省略できるようになった by　伊藤さん
        - [do/endブロック内でbegin/endなしのrescue/else/ensureが書けるようになった](https://qiita.com/jnchito/items/f182b6f0093a6a3701a1#doend%E3%83%96%E3%83%AD%E3%83%83%E3%82%AF%E5%86%85%E3%81%A7beginend%E3%81%AA%E3%81%97%E3%81%AErescueelseensure%E3%81%8C%E6%9B%B8%E3%81%91%E3%82%8B%E3%82%88%E3%81%86%E3%81%AB%E3%81%AA%E3%81%A3%E3%81%9F)
