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

`main.go`というファイルを作成し、以下のコードを入力してください。

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
'app'という名前のバイナリを作成
$ go build -o app main.go
```

```
# 生成したバイナリを実行
$ ./app
このコマンドも"Hello World!"と出力すれば、ビルドと実行が正常に行われています。
```
