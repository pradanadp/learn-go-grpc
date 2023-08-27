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
