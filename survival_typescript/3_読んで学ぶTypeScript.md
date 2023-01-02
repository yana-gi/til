# 2023/01/02

## 値・型・変数
### [constは可変オブジェクトを保護しない](https://typescriptbook.jp/reference/values-types-variables/let-and-const#const%E3%81%AF%E5%8F%AF%E5%A4%89%E3%82%AA%E3%83%96%E3%82%B8%E3%82%A7%E3%82%AF%E3%83%88%E3%82%92%E4%BF%9D%E8%AD%B7%E3%81%97%E3%81%AA%E3%81%84)
constは再代入不可な変数名を宣言するだけで、可変（ミュータブル）なオブジェクトのプロパティを普遍にする保護効果はない（！）

```ts
const obj = { a: 1 };
obj = { a: 2 }; //再代入は不可
obj.a = 2; //プロパティの変更はできる
```

TypeScriptでオブジェクトを不変にするには、プロパティを読み取り専用にする必要がある

配列もオブジェクトの一種なので同様。変数の再代入はできないが配列要素は変更できる
```ts
const arr = [1, 2];
arr = [3, 4]; // 再代入は不可
arr.push(3); // 要素の変更はできる
```
TypeScriptで配列を不変にするには読み取り専用配列を使う必要がある
```
const nums: readonly number[] = [1, 2, 3];
```

### 型推論
型推論はコンパイラが型を自動で判別する機能

型推論と動的型付けの違い
- コンパイルのタイミングで型が決定される。型をプログラマが書くかコンパイラが自動で決めるか
- 動的型付けでは実行時に型が決まるので、実行タイミングにより型が変化する

### プリミティブ型
JavaScriptのデータ型はプリミティブ型とオブジェクトの2つに分類される

#### プリミティブ型
- プリミティブ型はイミュータブル（値を直接変更できない）。
  - オブジェクトは値を後で変更できるミュータブル特性がある
- プロパティを持たない
  - 🤔プロパティってなんだろう
  - ただ、文字列や数値などのプリミティブ型はプロパティを持ったオブジェクトとして扱える
    -  JavaScriptにはプリミティブ型をオブジェクトに自動変換する機能がある（オートボクシング、自動ボックス化）

プリミティブ型の種類
- boolean
- number
- string
- undifined
- null
- symbol
- bigint

それ以外はJavaScriptにおいては全てオブジェクト（配列や正規表現もそう）

### 数値型
#### NaN
- 非数（not-a-number)を表す変数。
- JavaScriptでは、処理の結果数値にならない場合にNaNを返す
```ts
> parseInt("百円")
NaN
```
📝 rubyは文字列を `to_i`すると0になる
```
irb(main):003:0> "百円".to_i
=> 0
```
> 整数とみなせない文字があればそこまでを変換対象とします。変換対象が空文字列であれば 0 を返します。
[String\#to\_i](https://docs.ruby-lang.org/ja/latest/method/String/i/to_i.html)

NaNは等号比較では常に`false` になる（！）
```ts
console.log(NaN == NaN);
=> false
console.log(NaN === NaN);
=> false
```

### 小数計算の誤差
JavaScriptの少数計算には誤差が生じる
誤差問題を包括的に解決する場合はdecimal.jsのようなパッケージを使うのも手

### 文字列型

Prettierの使い分けの例

1. 基本的に"を使用する
2. 文字列の中に"が含まれる場合は'を使用する
3. 文字列展開する必要があるときは`を使用する

- 文字列型の方注釈は`string`を使う
  - stringとString型は異なるので注意

### null型
JavaScriptのnullは値がないことを示す値

### undefined型
JavaScriptのundefinedは未定義を表すプリミティブな値


```ts
// 変数に値がセットされてない時
let name;
console.log(name);
 
// 戻り値がない関数
function func() {}
console.log(func());
 
// オブジェクトに存在しないプロパティにアクセスしたとき
const obj = {};
console.log(obj.name);
 
// 配列に存在しないインデックスにアクセスした時
const arr = [];
console.log(arr[1]);

```

#### undefinedリテラル
undefinedにはリテラルはない。undefinedは変数（！）
グローバル定数なものと理解しても問題ない

### undefinedとnullの違い

