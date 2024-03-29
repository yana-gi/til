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

# 2023/01/03

### undefinedとnullの違い

- JavaScriptでは「値がない」に相当する表現にnullとundefinedの2通りがある
- undefined 
  - 値が代入されていないため、値がない
  - オブジェクトに存在しないプロパティや配列にない要素にアクセスした時もundefinedになる
    - ⚠️ JavaScriptはエラーにならない
  - 変数
- null 
  - 代入すべき値が存在しないため、値がない
  - nullは自然発生しない
  - リテラル

どちらを使えばいいのあｋ

- undefinedに統一する方が簡単
  - TypeScriptのガイドラインにも [nullは使わない](https://github.com/Microsoft/TypeScript/wiki/Coding-guidelines#null-and-undefined) と記載されている
  - undefinedは至る所で自然発生するので、nullで統一しようとするとundefinedを全てnullにしようとするのは大変


### シンボル型
JavaScriptのシンボル型はプリミティブの一種
- 倫理型や数値型は値が同じであれば等価比較が`true`になる
- シンボルはシンボル名が同じでも初期化した場所が違うとfalseになる

```ts
> const s1 = Symbol("foo");
undefined
> const s2 = Symbol("foo");
undefined
> console.log(s1 === s1);
true
undefined
> console.log(s1 === s2);
false
```

⚠️ Rubyはシンボル値が同じであればどこで書いたものでも等価比較が`true`になる

JavaScriptでシンボルを使って書く機会はあまり多くない

###　型強制

JavaScriptには型が異なる2つの値を処理する時に、暗黙的に別の型へ変換されることがある


```ts
// エラーにならず、stringの1が数値型として扱われる
> "1" - 1
0
```

📝
RubyはTypeErrorになる

```ruby
❯ irb  
irb(main):001:0> "1" + 1
(irb):1:in `+': no implicit conversion of Integer into String (TypeError)
	from (irb):1:in `<main>'
	from /Users/yana/.rbenv/versions/3.0.2/lib/ruby/gems/3.0.0/gems/irb-1.4.1/exe/irb:11:in `<top (required)>'
	from /Users/yana/.rbenv/versions/3.0.2/bin/irb:25:in `load'
	from /Users/yana/.rbenv/versions/3.0.2/bin/irb:25:in `<main>'
irb(main):002:0> 1 + "1"
(irb):2:in `+': String can't be coerced into Integer (TypeError)
	from (irb):2:in `<main>'
	from /Users/yana/.rbenv/versions/3.0.2/lib/ruby/gems/3.0.0/gems/irb-1.4.1/exe/irb:11:in `<top (required)>'
	from /Users/yana/.rbenv/versions/3.0.2/bin/irb:25:in `load'
	from /Users/yana/.rbenv/versions/3.0.2/bin/irb:25:in `<main>'
irb(main):003:0> 
```

# 2023/01/04

### プロトタイプベース

JavaScriptｔのオブジェクトの生成はプロトタイプベース。
クラスベースがクラスからオブジェクトを生成するのに対して、プロトタイプベースはオブジェクトを素にして新しいオブジェクトを生成する

# 2023/01/05

### object型, Object型、{}型

![image](https://user-images.githubusercontent.com/67262644/210780265-700bf3cc-3dab-4c07-a40c-3a22b6eff20f.png)

object型 : オブジェクトのみ代入可能
Object型・{}型 : オブジェクト　と　null、undefinedを除くプリミティブ型が代入可能

# 2023/01/07

## 分割代入
オブジェクトからプロパティを取り出す場合、分割代入をするとプロパティを2度書かなくて済む

```ts
const item = { price: 100 }
const price = item.price

// 分割代入をした場合
const item = { price: 100 }
const { price } = item

```

```ts
// 複数のプロパティを取り出す
const obj = { a: 1, b:2 }
const {a, b} = obj
```

- 入れ子のプロパティを取り出せる
- デフォルト値も指定できる

## Shorthand property names
オブジェクトのキーと変数名が同じ時にオブジェクトに値を代入する時に、オブジェクトのキーの記載を省略することができる

## オプショナルチェーン
- nullやundefinedのプロパティを参照してもエラーが発生しないようにする

- TypeScript でオプショナルチェーンを使った場合、最後のプロパティの方とundefinedのユニオン型になる
- Null合体子と相性がいい

```ts
let book: undefined　　|　{ title: string }
const title = book?.title ?? "デフォルトタイトル"
console.log(title)
```

# 2023/01/09

読み直す
- [オブジェクトをループする方法](https://typescriptbook.jp/reference/values-types-variables/object/how-to-loop-an-object)
- [構造的部分型 \(structural subtyping\) \| TypeScript入門『サバイバルTypeScript』](https://typescriptbook.jp/reference/values-types-variables/structural-subtyping)

## 配列
JavaScriptの配列はオブジェクト（リテラルじゃない）ため、配列の中身が同じでもインスタンスが異なると期待する比較ができない

```ts
const list1 = [1,2,3]
const list2 = [1,2,3]
console.log(list1 == list2) // => false
const list3 = list1
console.log(list1 == list3) // => true
```

配列同士の比較をするにはisEqualを使う
```ts
import _ from 'lodash';

const list1 = [1,2,3]
const list2 = [1,2,3]

console.log(_.isEqual(list1, list2))  // => true
```
