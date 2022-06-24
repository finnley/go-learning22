# go-learning

## init cobra app

```shell
$ cobra init go-learning --pkg-name go-learning
Your Cobra applicaton is ready at
/Users/finnley/Coding/go-learning

$ go run main.go 
main.go:18:8: package go-learning/cmd is not in GOROOT (/Users/finnley/sdk/go1.18/src/go-learning/cmd)
$ go mod init go-learning
$ go mod tidy

$ go run main.go 
A longer description that spans multiple lines and likely contains
examples and usage of using your application. For example:

Cobra is a CLI library for Go that empowers applications.
This application is a tool to generate the needed files
to quickly create a Cobra application.
```

## cobra show command

```shell
go-learning
├── LICENSE
├── README.md
├── cmd
│   └── root.go
├── go.mod
├── go.sum
└── main.go
```

```shell
$ cobra add show
show created at /Users/finnley/Coding/go-learning
```

```shell
go-learning
├── LICENSE
├── README.md
├── cmd
│   ├── root.go
│   └── show.go
├── go.mod
├── go.sum
└── main.go
```

下面是 show.go 文件的初始代码：
```go
// showCmd represents the show command
var showCmd = &cobra.Command{
	Use:   "show",
	Short: "A brief description of your command",
	Long: `A longer description that spans multiple lines and likely contains examples
and usage of using your command. For example:

Cobra is a CLI library for Go that empowers applications.
This application is a tool to generate the needed files
to quickly create a Cobra application.`,
	Run: func(cmd *cobra.Command, args []string) {
		fmt.Println("show called")
	},
}
```

rootCmd.AddCommand(showCmd) 命令的添加，将命令添加到根命令
实现显示当前时间的逻辑：
在 &cobra.Command.Run 中添加获取当前时间逻辑 time.Now()：
```go
// showCmd represents the show command
var showCmd = &cobra.Command{
	Use:   "show",
	Short: "Displays the current time",
	Long: `You can use the time show command to view the current time. For example:

$ ./go-learning show
2021-03-19 14:34:20.9320241 +0800 CST m=+0.378845301`,
	Run: func(cmd *cobra.Command, args []string) {
		//fmt.Println("show called")

		fmt.Println(time.Now())
	},
}
```

运行
执行 show 命令：
```shell
$ go run main.go show
2022-05-08 16:29:50.269528 +0800 CST m=+0.000807241
```

执行 show –help 命令：
```shell
$ go run main.go show --help
You can use the time show command to view the current time. For example:

$ ./go-learning show
2021-03-19 14:34:20.9320241 +0800 CST m=+0.378845301

Usage:
  go-learning show [flags]

Flags:
  -h, --help   help for show

Global Flags:
      --config string   config file (default is $HOME/.go-learning.yaml)
```

## version command

```shell
cobra add version

go build -o main main.go

$ ./main version --help
version subcommand show git version info.

Usage:
  go-learning version [flags]

Flags:
  -h, --help   help for version

Global Flags:
      --config string   config file (default is $HOME/.go-learning.yaml)
      
$ ./main version       
git version 2.21.1 (Apple Git-122.3)

go build -o main main.go
```

## go-password-encoder

https://github.com/anaskhan96/go-password-encoder

```shell
go get github.com/anaskhan96/go-password-encoder
```