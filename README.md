# Install protobuf compiler (protoc)

-   Download the windows zip [here](https://github.com/protocolbuffers/protobuf/releases)
-   Extract all to `C:\proto3`
-   Add `C:\proto3\bin` to PATH
-   To make sure, run `protoc` in cmd

## Add PATH to .bashrc

-   Open `.bashrc` file in nano or vim

```
nano .bashrc
```

-   Add protoc bin

```
export PATH=$PATH:/c/proto3/bin
```

-   Save and close

### protoc-gen-go

To compile the proto file to Go file we need the Protobuf Compiler(protoc) and also the protoc-gen-go plugin.

```
go install google.golang.org/protobuf/cmd/protoc-gen-go@latest
```

After executing this command, protoc-gen-go (compiler plugin)executable file will be installed in GOBIN path (`%USERPROFILE%\go\bin` in windows), add this path to the PATH (environmental variable) for the protoc to find it.

# Run protoc

-   First you need to run the following command to install the necessary tools:

```
go get -u google.golang.org/grpc
go get -u google.golang.org/protobuf/cmd/protoc-gen-go
go get -u google.golang.org/grpc/cmd/protoc-gen-go-grpc
```

The first command installs the gRPC package, the second installs the standard Go protocol buffer compiler plugin (`protoc-gen-go`), and the third installs the gRPC Go code generator plugin (`protoc-gen-go-grpc`).

-   Run the following command

```
protoc greet/greetpb/greet.proto --go_out=.
```

This command tells `protoc` to generate gRPC Go code for the specified `.proto` file using the `--go_out` flag. The `.` after the `=` specifies the output directory as the current directory.

Keep in mind that the `--go_out` and `--go-grpc_out` flags generate different types of Go code. The former generates standard protocol buffer Go code, while the latter generates gRPC-specific Go code, including service interfaces and implementations. If you need both types of code, you can use both flags in the same command:

```
protoc greet/greetpb/greet.proto --go_out=. --go-grpc_out=.
```
