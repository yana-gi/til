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

## 2021\-02\-01
- Chapter 9-5-7-2から 9-5-7-4途中まで
    - updateやcreateなどの更新系は!をつけると例外が発生するのは知っていたけど、find_byなどの参照系でも同様の挙動になるのは初めて知った！（でもfindは結果が返って来なかったら例外になる）
    - `bin/rails r '処理'`でワンライナーでデータの内容を確認することができる。rって何の略だろう→runner
    - やつはしさんがsandbox使いこなしててなるほど〜と思った

## 2022\-02\-04
- Chapter 10から　 10-3 まで
    - 自作サービスのバージョンアップもこまめにやっていかないとな〜と思った😇
    - バージョンアップはこまめにやっておくと負担も小さくなる（一気にやろうとするとハードルが高くなる）
    - Dependabotは色々設定ができる

## 2021\-02\-09
- Chapter 10-9-1から10-10まで
    - ざっくりとした理解
        - ActiveSupport::Concernがあると親モデルの記述がシンプルになる
        - STIは継承関係にあるモデルはDB側ではすべて同じテーブルに格納される
    - 後で読む
        - ActiveSupport::Concernのあり/なしでの記述の違いは[\[Rails\] ActiveSupport::Concern の存在理由 \- Qiita](https://qiita.com/castaneai/items/6dc121ce6ff100614f42)に書いてあった
        - STI（単一テーブル継承）は独習Railsの方が分かりやすい（haruguchiさん情報）

## 2022\-02\-10
- Chapter 10-10-1から 10-10-3まで
    - viewの共通処理はhelperに、コントローラーの共通処理は下記の方法で書く
    - コントローラーの共通化には2つ方法がある
        - 基底クラスを追加してMix-inする
        - ApplicationControllerに共通機能を記述する（どのコントローラーからも呼び出せる）
    - bootcampの[ApplicationController](
https://github.com/fjordllc/bootcamp/blob/main/app/controllers/application_controller.rb)にもログインや認証・権限周りの共通処理が書いてあった👀

## 2022\-02\-11
- Chapter 10-10-4から　10-11-2 まで
    - コントローラーの処理を共通化する前にモデルに切り出せないか？を考える
    - P421に書かれている「>パーフォーマンスのオーバーヘッド」とは
        - 処理の負担がrenderを使わないで記述する <　eachで回してrenderを表示する と言ったように普段やるより処理の負担がかかること
        - 繰り返しパーシャルを呼び出すには`:collection`
    - P419の`all.max_by { |t| t.priority + t.volume}`をSQL側で呼び出せないか？と言う話
        - [maximum](https://api.rubyonrails.org/v7.0/classes/ActiveRecord/Calculations.html#method-i-maximum)メソッドには一つのカラムを指定するだけ（複数のカラムの合計値は指定できない）なのかな？
            - `maximxum('priority + volume')` とか書いたらいけないかなー (適当)
            - [calculate](https://api.rubyonrails.org/v7.0/classes/ActiveRecord/Calculations.html#method-i-calculate)で`Person.sum("2 * age")`しているからできるかも（適当）

## 2022\-02\-16
- Chapter 10-12-4から 10-12-4まで
    - 外部APIと連携した処理は、外部サービスに関連するロジックはクラスに閉じ込める
        - コントローラーがスッキリする
        - ダミー実装と入れ替えやすい（APIが未実装だったとしても実装を進めることができる
        - テストがしやすくなる
    - 本ではまずコントローラーで実装→クラスに切り分けるやり方でやっているので参考にしたい
