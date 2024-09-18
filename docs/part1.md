# Go 言語入門

## 初期設定

まず、作業ディレクトリを作成し、そこに移動します。

```bash
$ mkdir go-samples
$ cd go-samples
```

次に、Go のモジュール環境で開発を進めるため、`go mod init`を実行します。これにより、カレントディレクトリに`go.mod`ファイルが作成されます。

```bash
$ go mod init github.com/{あなたのGitHubアカウント名}/golang-handson/go-samples
```

## プログラムの動作確認

それでは、Go 言語で最初のプログラムを書いてみましょう。ここでは、"Hello World"を出力する簡単なプログラムを作成します。

`hello-world/main.go`というファイルを作成し、以下のコードを入力してください。

```bash
$ mkdir hello-world
$ cd hello-world
```

```go
package main

import (
    "fmt"
)

func main() {
    fmt.Println("Hello World!")
}
```

そして、以下のコマンドでプログラムを実行します。

```
$ go run main.go
```

"Hello World!"というメッセージが出力されれば、プログラムは正常に動作しています。

次に、このプログラムをビルドして、生成されたバイナリを実行してみましょう。

```
# 'app'という名前のバイナリを作成
$ go build -o app main.go
```

```
# 生成したバイナリを実行
$ ./app
```

このコマンドも"Hello World!"と出力すれば、ビルドと実行が正常に行われています。

## Go 言語の特徴

Go 言語は Google が開発した静的型付けのコンパイル言語で、シンプルな文法と高いパフォーマンスを持つことが特徴です。また、並行処理をサポートするための強力な機能を持っています。

### メリット

1. **シンプルな文法**: Go 言語の文法はシンプルで、学習コストが低いです。また、ソースコードが読みやすく保守しやすいため、大規模な開発でも効率的に作業を進められます。

2. **高パフォーマンス**: C++や Java と同等のパフォーマンスを持ちつつ、動的言語のような手軽さを持っています。

3. **並行処理のサポート**: 'goroutine'と'channel'という機能を用いて、効率的に並行処理を行うことができます。

4. **標準ライブラリが充実**: ネットワークプログラミングや文字列処理、テストなど、多くの機能が標準ライブラリとして提供されています。

### デメリット

1. **ジェネリクスの欠如**: Go 言語は現状、ジェネリクスをサポートしていません。このため、型ごとに関数やメソッドを作成する必要があります。

2. **エラーハンドリングの冗長性**: Go 言語では、エラーは明示的にハンドリングする必要があります。これはコードの安全性を高めますが、一方でコードが冗長になる可能性もあります。

## Go 言語の基本的な文法

### 変数宣言

Go 言語では、以下のようにして変数を宣言します。

```go
var x int = 10
```

また、以下のように型推論を利用して変数を宣言することもできます。

```go
x := 10
```

### 関数定義

Go 言語の関数は以下のように定義します。

```go
func add(x int, y int) int {
    return x + y
}
```

### 制御構文

if 文

```go
if x > 10 {
    fmt.Println("x は10 より大きい")
} else {
    fmt.Println("x は10 以下")
}

```

for 文

```go
for i := 0; i < 10; i++ {
    fmt.Println(i)
}
```

### 配列

配列は固定長の同一型のデータを格納するためのデータ構造です。

```go
var arr [5]int
```

値のセットは以下のように定義します。

```go
arr[0] = 1
```

※ Go 言語の配列は固定長で、append 関数を使用して要素を追加することはできません。要素を動的に追加するためには、スライスを使用する必要があります

### スライス

スライスは可変長の配列で、より柔軟な操作が可能です。

```go
var s []int = []int{1, 2, 3}
```

スライスは append を使って要素を動的に追加することが可能です。

```go
s = append(s, 4)
```

### Go 言語のマップ

マップはキーと値のペアを格納するデータ構造です。

```go
var m map[string]int = map[string]int{"apple": 100, "banana": 200}
```

### Go 言語の構造体

構造体は複数の異なる型のデータを一つにまとめるためのデータ構造です。

```go
type Person struct {
    Name string
    Age  int
}

var p Person = Person{"Bob", 20}
```

### Go 言語のポインタ

Go 言語では、ポインタを用いてメモリ上のアドレスを直接扱うことができます。

```go
var x int = 10
var p *int = &x
```

## Go 言語のメソッドとインターフェース

Go 言語では、構造体に対してメソッドを定義することができます。また、インターフェースを用いて抽象型を定義することも可能です。

### メソッド

Go 言語のメソッドは、特定の型に関連付けられた関数です。

```go
type Person struct {
    Name string
    Age  int
}

func (p Person) SayHello() {
    fmt.Printf("Hello, my name is %s and I am %d years old.\n", p.Name, p.Age)
}

var p Person = Person{"Bob", 20}
p.SayHello()
```

### インターフェース

Go 言語のインターフェースは、メソッドのシグネチャの集合を定義したものです。

```go
type Greeter interface {
    SayHello()
}

func Greet(g Greeter) {
    g.SayHello()
}

var p Person = Person{"Bob", 20}
Greet(p)
```

### エラーハンドリング

Go 言語では、エラーは明示的にハンドリングする必要があります。以下のようにエラーハンドリングを行います。

```go
func ErrFunc() error {
		return fmt.Errorf("エラーだよ")
}

err := ErrFunc()
if err != nil {
		log.Fatal(err)
}
```
