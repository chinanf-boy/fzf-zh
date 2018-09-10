
# 建立fzf

## 建立说明

### 先决条件

-   `go`$ PATH中的可执行文件

### 使用Makefile

Makefile将设置并使用它自己的`$GOPATH`在项目根目录下. 

```sh
# Build fzf binary for your platform in target
make

# Build fzf binary and copy it to bin directory
make install

# Build 32-bit and 64-bit executables and tarballs in target
make release

# Make release archives for all supported platforms in target
make release-all
```

### 运用`go get`

或者,您可以直接构建fzf`go get`命令而不手动克隆存储库. 

```sh
go get -u github.com/junegunn/fzf
```

## 使用第三方库

-   [mattn/go-runewidth](https://github.com/mattn/go-runewidth)
    -   许可下[MIT](http://mattn.mit-license.org)
-   [mattn/go-shellwords](https://github.com/mattn/go-shellwords)
    -   许可下[MIT](http://mattn.mit-license.org)
-   [mattn/go-isatty](https://github.com/mattn/go-isatty)
    -   许可下[MIT](http://mattn.mit-license.org)
-   [tcell](https://github.com/gdamore/tcell)
    -   许可下[Apache License 2.0](https://github.com/gdamore/tcell/blob/master/LICENSE)

## 执照

[MIT](LICENSE)
