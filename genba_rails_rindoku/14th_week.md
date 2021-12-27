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
