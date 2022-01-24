## 2021\-12\-21
- Chapter 7-4から 7-4-4途中まで
    - メール送信の処理は実装したことがなかったのでこうやって実装するんだ〜と思った
    - 動作確認用のgemは色々ある
        - mailcatcherはbundleではなく`gem install`する必要がある
        - letter_opener と letter_opener_webは違う
            - https://rubyandrails.hatenablog.com/entry/letter_opener_web
## 2021\-12\-23
- Chapter 7-4-5から 7-5-2 まで
    - メールのテストを今まで書いたことがなかったので勉強になった
    - メールの構造を理解しておく必要がありそう。HTTPレスポンスのようにheaderとbodyがあることは分かった
    - メールの構造自体と、RubyのMailクラスの理解が両方必要……？

## 2021\-12\-24
- Chapter 7-5-3から Chapter 7-5-4 まで
    - ActiveStorageをインストールすると2つのテーブルができる
    - ActiveStorage:Blob
        - ファイルの実体以外の情報を管理する。実体はDB以外で管理する
    - ActiveStorage:Attachment
        - ActiveStorage:Blobとアプリ内のモデルを関連づける中間テーブル

## 2021\-12\-27
- Chapter 7-6から7-6-1まで
    - コントローラーでhtml以外のformatを指定するのは初めてだった
    - はるぐちさんの説明のおかげでCSV出力の流れが分かった！
    - `send`メソッド便利〜

## 2021\-12\-28
- Chapter 7-6-2から 7-6-2まで
    - Hash#sliceは引数に指定したarray||Hashのkeyだけを取得する
    - [Hash\#slice \(Ruby 3\.0\.0 リファレンスマニュアル\)](https://docs.ruby-lang.org/ja/latest/method/Hash/i/slice.html)
    - `Hash#slice`はRubyのメソッドなのかな。Rails APIには`slice!`しかなかった
        - https://api.rubyonrails.org/classes/Hash.html
    - [ActiveSupport版とRuby 2\.5版の挙動の違い](https://qiita.com/_mmasaki/items/fc98bfb494b40273c4cb)

## 2022\-1\-4

- 第11章 11.5.1 第11章 11.5.2の終わりまで
    - 右代入はパターンマッチの要素の一つだったのか！（元は右代入単体で実装されたらしい）

## 2022/01/12
- Chapter 8-4-2-1途中から Chapter 8-4-2-2まで
    - `Webpacker::Manifest::MissingEntryError in` 
        - 解決するまでにやったこと
            - `bin/rails webpacker:install`
            - `bin/rails webpacker:compile`
        - 疑問：webpackerのコンパイルをしたらエラーが解消されて動いたけど、その理由が分からなかった。webpackerをinstallした時点でコンパイルしてくれなかった原因はなんだろう？
    - webpackerを入れたら削除ボタンが機能しなくなった。deleteアクションで指定しているのにGETアクションが動く。
        - `rails-ujs`がDELETEリクエストの発行や確認ダイアログを表示してくれるらしいので、そこが関係してるかも？

## 2022/01/13
- Chapter 8-5から  Chapter 8-4-2-2まで
    - webpackerを入れたら削除ボタンが機能しなくなった件が直った🎉
        - rails-ujsが読み込まれていなかったのが原因。rails-ujsをyarnインストールしてpacksファイルにimport&startをした。
        - 自分のアプリではそんなことをしていないと思ったらRails6ではWebpackerがデフォルトなので最初から読み込まれていた
            - https://zenn.dev/yukito0616/articles/f8420b87984917#ちなみにrails6だと

## 2021\-01\-17
- Chapter 9から 9-1-3まで
    - privateリポジトリが無料で作れることを知らなかった……！
    - 「GitHubさんのGitをメインのGitということにして、開発者たちが自分のGitとGitHubの間で変更のやりとりをする」
        - 人と人のGit間でやりとりをするのと、GitHubと人の間でやりとりをするのは同じことをやっているのか
    - 前職でSVN使ってたけど何も覚えていない。小さいアプリだとSVN使わずに過去のコードを日付とともにすべてコメントで囲ったりしていた……

## 2021\-01\-24
- Chapter 9-1-7の途中から  9-2-1まで
    - `git push --force-with-lease`は雰囲気で使ってたけど、「最新コミットが作者の時だけ`git push -f`のように作用する」という説明で納得できた
    - 個人サービス開発では`git push -f`をなんの躊躇いなくしていたので、チーム開発するときに事故らないかが不安😇
    - P369のコードレビューの視点は、実装する側としてもチェックしたい項目だった
