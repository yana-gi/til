## 2021/09/28
    - RailsドキュメントはRailsはじめたばかりの頃に検索で引っかかりやすいので参照していた思い出。Railsドキュメントは著者不明なのでRailsガイドや公式APIドキュメントを参照した方がいい
    - [Ruby on Railsを使った開発で参照してもよいドキュメント \- Qiita](https://qiita.com/hanachin_/items/76a24bcef889edb59d19)

## 2021/09/29
- インストールで詰まったのでメモ
    - ruby 2.5.1 をインストールする
    - bundlerをインストールする
    - `bundle -v` をするとエラー
    ```
    ~/genba_rails on 🌱 main [$?⇕] via 💎 v2.5.1 took 18s 
    ❯ bundler -v         
    Traceback (most recent call last):
        2: from /Users/yana/.rbenv/versions/2.5.1/bin/bundler:23:in `<main>'
        1: from /Users/yana/.rbenv/versions/2.5.1/lib/ruby/2.5.0/rubygems.rb:308:in `activate_bin_path'
    /Users/yana/.rbenv/versions/2.5.1/lib/ruby/2.5.0/rubygems.rb:289:in `find_spec_for_exe': can't find gem bundler (>= 0.a) with executable bundler (Gem::GemNotFoundException)
    ```
    - gem listには入ってることを確認
    ```
    ❯ gem list | grep 'bundler'
    bundler (2.2.28, 2.0.2, 1.17.3)
    ```
    - bundlerのversionを`1.17.3` 以外削除するといいらしい
    - bundlerのuninstallができない
    ```
    ❯ gem uninstall bundler -v 2.2.28
    Gem 'bundler' is not installed
    ```
    - `Gemfile.lock` （自分の場合は実行ディレクトリの上の階層）を削除したら`bundle -v` でバージョンを確認できた
- 原因
    - [Bundler 2系しか入っていなくて既存アプリがbundle installできなかった… \| by Tatsuya Tobioka \| Ruffnote \| Medium](https://medium.com/ruffnote/bundler-2系しか入っていなくて既存アプリがbundle-installできなかった-dd03737d3866)
    - > Bundler 2系は .lockファイルを見て切り替えるようなので、切り替える先のBundlerが見つからずNotFoundエラーになるということでしょう。
    - 🤔 `.lockファイル`はどこまでみてるんだろう？
