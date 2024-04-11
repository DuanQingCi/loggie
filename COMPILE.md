环境：go version go1.21.3
进入到cmd-loggie目录下

== windows下编译 ==
编译 Mac 可执行文件
SET CGO_ENABLED=0
SET GOOS=darwin
SET GOARCH=amd64
go build -tags "driver_badger" -o tonglog main.go
编译 Linux 可执行文件
SET CGO_ENABLED=0
SET GOOS=linux
SET GOARCH=amd64
go build -tags "driver_badger" -o tonglog main.go
编译 Windows 可执行文件
SET CGO_ENABLED=0
SET GOOS=windows
SET GOARCH=amd64
go build -tags "driver_badger" -o tonglog.exe main.go

== linux下编译 ==
export GOOS=windows  export GOARCH=amd64
/usr/local/go/bin/go build -tags "driver_badger" -o tonglog.exe   main.go
export GOOS=linux && export GOARCH=arm64
/usr/local/go/bin/go build -tags "driver_badger" -o tonglog-arm   main.go
export GOOS=linux && export GOARCH=amd64
/usr/local/go/bin/go build -tags "driver_badger" -o tonglog  main.go
执行启动
./tonglog -config.system=./loggie.yml -config.pipeline=./pipelines.yml -log.jsonFormat=false



go build -tags "driver_badger" -a -ldflags "-w -s" -gcflags "all=-N -l" -o tonglog main.go
go build -tags "driver_badger" -gcflags "all=-N -l" -o tonglog main.go
go build -tags "driver_badger" -gcflags "all=-N -l" -o tonglog.exe main.go

chmod +x tonglog
./tonglog --config es72ts.yaml
dlv --headless --api-version=2 --log --listen=:2345 exec ./tonglog -- --config test1.yaml 