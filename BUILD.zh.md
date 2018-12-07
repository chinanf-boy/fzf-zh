# 建立 fzf

## 建立说明

### 先决条件

- `go`，\$PATH 中的可执行文件

### 使用 Makefile

Makefile 设好， 并在`$GOPATH`项目根目录下使用它。

```sh
# 根据你的平台，构建 fzf 二进制文件
make

# 构建 fzf 二进制文件，并复制到 bin目录
make install

# 构建 32-位 和 64-位 可执行文件，再压缩进target
make release

# 为所以定好的平台，压缩好发布版本
make release-all
```

### 运用`go get`

或者,您可以使用`go get`命令直接构建 fzf，而不手动克隆存储库.

```sh
go get -u github.com/junegunn/fzf
```

## 使用第三方库

- [mattn/go-runewidth](https://github.com/mattn/go-runewidth)
  - [MIT](http://mattn.mit-license.org)许可
- [mattn/go-shellwords](https://github.com/mattn/go-shellwords)
  - [MIT](http://mattn.mit-license.org)许可
- [mattn/go-isatty](https://github.com/mattn/go-isatty)
  - [MIT](http://mattn.mit-license.org)许可
- [tcell](https://github.com/gdamore/tcell)
  - [Apache License 2.0](https://github.com/gdamore/tcell/blob/master/LICENSE)许可

## 执照

[MIT](LICENSE)
