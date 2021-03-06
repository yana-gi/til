## 2021\-09\-13
- 第12章 12.5まで
    - irbの補完機能、自分が定義した変数もサジェストしてくれて便利
    - `open-uri`の仕様が2.6以前とその後で変わっていた。こういう仕様の変更ってどのドキュメントを見ればわかるんだろう？
        - 森塚さんから共有して貰った！GitHubのリポジトリを見ればよかったのか
            - https://github.com/ruby/open-uri/commit/53862fa35887a34a8060aebf2241874240c2986a
    - > `example.com`はソフトウェアドキュメンテーションやドメイン名の例示のために予約されているセカンドレベルドメイン

## 2021/09/14
- 第12章 12.5.1から12.6のコラムまで
    - lsコマンドの課題のテストで、我流で`ruby ls.rb`をバッククォートリテラルで実行した結果を比較していた。伊藤さんからレビューで「コマンドの実行結果は端末によって値が変わる可能性があるため、端末によって結果が変わらないテストが望ましい」と指摘を受けたことがある。


## 2021\-09\-1５
- 第12章 12.7から12.7のコラムまで
    - `rails db:migrate`などのなどのマイグレーション処理はrakeだったのか……！
    - `test/**/*_test.rb`の `**`はディレクトリを再帰的に表現する
        - [Rubyで使われる記号の意味（正規表現の複雑な記号は除く） \(Ruby 3\.0\.0 リファレンスマニュアル\)](https://docs.ruby-lang.org/ja/latest/doc/symref.html#ast)
    - RakefileやRBSはDSL（ドメイン固有言語）

- 疑問点・気づき
    - rakeはほとんど覚えていなかったので、bootcampアプリの実用例などと一緒に復習できてよかった
    - rake taskの他にrails runnerもある
        - [Railsでバッチを書く時によく使うrails runnerとrake taskの違い \- Qiita](https://qiita.com/rllllho/items/672e336a03335cba6b34)
    - 伊藤さんが「最後まで読み切ると思ってなかった」とおっしゃいたけど、自分もそう思う


## 2021\-09\-16
- 第12章 12.8から12.9まで
    - Gemfileにかかれている`~>`の正体が分かってよかった
    - [セマンティック バージョニング 2\.0\.0 \| Semantic Versioning](https://semver.org/lang/ja/)
    - 確かにRailsでは`require`を書いたことがほとんどなかった。Railsが自動で読み込んでくれるため。
- 付録 A.2まで
        - Rails 6.0からZeitwerkが導入された[定数の自動読み込みと再読み込み \(Zeitwerk\) \- Railsガイド](https://railsguides.jp/autoloading_and_reloading_constants.html)
    - 素のRubyの知識の基礎ができていればRubyとRailsそれぞれがやってくれることの切り分けができるようになるのかな、と思った
