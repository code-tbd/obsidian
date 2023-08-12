# go
从 https://go.dev/dl/ 下载对应系统的二进制文件，并配置环境变量。推荐使用 gvm 管理 go 版本，相关链接： https://github.com/moovweb/gvm 。
# proto
从 https://github.com/protocolbuffers/protobuf/releases/ 下载对应系统的二进制文件，并配置环境变量。
# protobuf
使用命令`go install google.golang.org/protobuf/cmd/protoc-gen-go@latest`安装相关工具，安装路径为$GOPATH/bin，注意需要将其添加到环境变量。
# make
使用命令`sudo apt install -y make`安装 make 工具，用于依赖 Makefile 文件的构建。

