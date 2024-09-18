# Go 言語入門

独自コマンドの作成

## コマンド作成の基礎

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

`./app` コマンドも"Hello World!"と出力すれば、ビルドと実行が正常に行われています。

## ./app のバイナリファイルをコマンドとして設定しましょう

バイナリを作成した後、そのバイナリを使って独自のコマンドを作成することができます。以下の手順で進めます。

1. バイナリをシステムのパスに配置します。例えば、`/usr/local/bin`に配置します。

```
$ sudo mv app /usr/local/bin/
```

2. 配置したバイナリに実行権限を付与します。

```
$ sudo chmod +x /usr/local/bin/app
```

3. これで、`app`コマンドとして使用できるようになります。

```
$ app
Hello World!
```

このようにして、Go 言語で作成したバイナリを使って独自のコマンドを作成することができます。これにより、Go 言語で作成したプログラムを簡単に実行できるようになります。

## 自作コマンドを作ってみよう！

次に、ターミナルでソースコードをレビューする簡単なコマンドラインツールを作成してみましょう。
これにより、Go 言語のさらなる機能を学ぶことができます。

作業ディレクトリを作成し、そこに移動します。

```
$ mkdir review
$ cd review
```

次に、`code.go`というファイルを作成し、以下のコードを入力してください。

```
package review

import "fmt"

type CodeReviewService struct{}

func NewCodeReviewService() *CodeReviewService {
	return &CodeReviewService{}
}

func (s *CodeReviewService) ExecuteCodeReview() error {
	fmt.Println("ExecuteCodeReview が呼ばれました！")

	return nil
}

```

main.go で`code.go` で作成した `ExecuteCodeReview()` 関数を呼びます。

```main.go
package main

import (
	"fmt"
	"os"

	"github.com/ca-groupit/hrk-m/golang-handson/go-samples/review"
)

func main() {
	service := review.NewCodeReviewService()
	err := service.ExecuteCodeReview()
	if err != nil {
		fmt.Println("エラー:", err)
		os.Exit(1)
	}
}
```

`main.go` を実行してみましょう

```
$ go run main.go
```

`ExecuteCodeReview が呼ばれました！`というメッセージが出力されれば、プログラムは正常に動作しています。

<!-- TODO: これからかく -->

## 最後に

app ディレクトリを削除しましょう！

```
sudo rm -rf /usr/local/bin/app
```
