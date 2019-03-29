# fzf [![explain]][source] [![translate-svg]][translate-list]

[explain]: http://llever.com/explain.svg
[source]: https://github.com/chinanf-boy/Source-Explain
[translate-svg]: http://llever.com/translate.svg
[translate-list]: https://github.com/chinanf-boy/chinese-translate-list

「 fzf是一种通用的命令行模糊查找器 」

[中文](./readme.md) | [english](https://github.com/junegunn/fzf)


---

## 校对 ✅

<!-- doc-templite START generated -->
<!-- repo = 'junegunn/fzf' -->
<!-- commit = '8540902a35361dba217cc3ad86ff2215ae51918e' -->
<!-- time = '2018 9.4' -->
翻译的原文 | 与日期 | 最新更新 | 更多
---|---|---|---
[commit] | ⏰ 2018 9.4 | ![last] | [中文翻译][translate-list]

[last]: https://img.shields.io/github/last-commit/junegunn/fzf.svg
[commit]: https://github.com/junegunn/fzf/tree/8540902a35361dba217cc3ad86ff2215ae51918e

<!-- doc-templite END generated -->

- [x] readme
- [x] [README-VIM.md](README-VIM.zh.md)
- [x] [BUILD.md](BUILD.zh.md)


### 贡献

欢迎 👏 勘误/校对/更新贡献 😊 [具体贡献请看](https://github.com/chinanf-boy/chinese-translate-list#贡献)

## 生活

[If help, **buy** me coffee —— 营养跟不上了，给我来瓶营养快线吧! 💰](https://github.com/chinanf-boy/live-need-money)

---

# <img src="https://raw.githubusercontent.com/junegunn/i/master/fzf.png" height="170" alt="fzf - a command-line fuzzy finder"> [![travis-ci](https://travis-ci.org/junegunn/fzf.svg?branch=master)](https://travis-ci.org/junegunn/fzf)

fzf是一种通用的命令行模糊查找器.

<img src="https://raw.githubusercontent.com/junegunn/i/master/fzf-preview.png" width=640>

它是一个用于命令行的交互式Unix过滤器,可以与任何列表一起使用;文件,命令历史,进程,主机名,书签,git提交等.

## 优点

-   便携,无依赖性
-   非常快
-   最全面的功能集
-   布局灵活
-   自带的电池包括
    -   Vim/Neovim插件,按键绑定和模糊自动补全

## 目录

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [安装](#%E5%AE%89%E8%A3%85)
  - [使用Homebrew或Linuxbrew](#%E4%BD%BF%E7%94%A8homebrew%E6%88%96linuxbrew)
  - [用git](#%E7%94%A8git)
  - [作为Vim插件](#%E4%BD%9C%E4%B8%BAvim%E6%8F%92%E4%BB%B6)
  - [Arch Linux](#arch-linux)
  - [Fedora](#fedora)
  - [Windows](#windows)
- [升级fzf](#%E5%8D%87%E7%BA%A7fzf)
- [构建fzf](#%E6%9E%84%E5%BB%BAfzf)
- [用法](#%E7%94%A8%E6%B3%95)
- [例子](#%E4%BE%8B%E5%AD%90)
- [`fzf-tmux`脚本](#fzf-tmux%E8%84%9A%E6%9C%AC)
- [命令行的键绑定](#%E5%91%BD%E4%BB%A4%E8%A1%8C%E7%9A%84%E9%94%AE%E7%BB%91%E5%AE%9A)
- [bash和zsh的模糊完成](#bash%E5%92%8Czsh%E7%9A%84%E6%A8%A1%E7%B3%8A%E5%AE%8C%E6%88%90)
- [Vim插件](#vim%E6%8F%92%E4%BB%B6)
- [高级主题](#%E9%AB%98%E7%BA%A7%E4%B8%BB%E9%A2%98)
  - [性能](#%E6%80%A7%E8%83%BD)
  - [执行外部程序](#%E6%89%A7%E8%A1%8C%E5%A4%96%E9%83%A8%E7%A8%8B%E5%BA%8F)
  - [预览窗口](#%E9%A2%84%E8%A7%88%E7%AA%97%E5%8F%A3)
- [提示](#%E6%8F%90%E7%A4%BA)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## 安装

fzf项目包含以下组件:

-   `fzf`可执行文件
-   `fzf-tmux`用于在tmux窗格中,启动fzf的脚本
-   Shell扩展
    -   按键绑定 (`CTRL-T`,`CTRL-R`,和`ALT-C`)  (bash,zsh,fish)
    -   模糊自动补全 (bash,zsh)
-   Vim/Neovim插件

您可以仅[下载fzf可执行文件][bin],如果你不需要额外的东西的话.

[bin]: https://github.com/junegunn/fzf-bin/releases

### 使用Homebrew或Linuxbrew

您可以使用[Homebrew](http://brew.sh/)要么[Linuxbrew](http://linuxbrew.sh/)安装fzf.

```sh
brew install fzf

# 安装有用的 按键 绑定 和 模糊 补全:
$(brew --prefix)/opt/fzf/install
```

### 用git

或者,您可以用"git clone"此存储库到任何目录,并运行[install](https://github.com/junegunn/fzf/blob/master/install)脚本.

```sh
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

### 作为Vim插件

一旦安装了fzf,就可以在Vim中启用它,通过添加目录到在您的Vim配置文件中的`&runtimepath`,如下所示:

```vim
" If installed using Homebrew
set rtp+=/usr/local/opt/fzf

" If installed using git
set rtp+=~/.fzf
```

如果你使用[vim-plug](https://github.com/junegunn/vim-plug),同样可以写成:

```vim
" If installed using Homebrew
Plug '/usr/local/opt/fzf'

" If installed using git
Plug '~/.fzf'
```

但, 若你不在您的系统上单独安装`fzf` (使用Homebrew或"git clone") , 并在Vim上启用它 (将其添加到`&runtimepath`) ,你也可以使用`vim-plug`来做到这两点.

```vim
" PlugInstall and PlugUpdate will clone fzf in ~/.fzf and run install script
Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }
  " Both options are optional. You don't have to install fzf in ~/.fzf
  " and you don't have to run install script if you use fzf only in Vim.
```

### Arch Linux

```sh
sudo pacman -S fzf
```

### Fedora

fzf在Fedora 26及更高版本中可用,可以使用常用方法安装:

```sh
sudo dnf install fzf
```

默认情况下,启用shell补全和vim或neovim的插件. Shell按键绑定已安装,但默认情况下未启用. 有关更多信息,请参阅Fedora的软件包文档 (/usr/share/doc/fzf/README.Fedora) .

### Windows

可以下载用于Windows的预构建二进制文件[这里][bin]. 也可以用[choco][choco].

[choco]: https://chocolatey.org/packages/fzf

```sh
choco install fzf
```

但是,项目的其他组件可能无法在Windows上运行. 可以找到已知的问题和限制信息在[维基页面][windows-wiki]. 您可能会考虑安装[适用于Linux的Windows子系统][wsl]的fzf,一切都运行完美.

[windows-wiki]: https://github.com/junegunn/fzf/wiki/Windows

[wsl]: https://blogs.msdn.microsoft.com/wsl/

## 升级fzf

fzf正在积极开发中,您可能希望偶尔升级一次. 请根据按照以下说明进行操作对应安装方法.

-   git: `cd ~/.fzf && git pull && ./install`
-   brew: `brew update; brew reinstall fzf`
-   chocolatey: `choco upgrade fzf`
-   vim-plug: `:PlugUpdate fzf`

## 构建fzf

- [x] 看到[BUILD.md](BUILD.zh.md).

## 用法

fzf将启动交互式查找程序,从STDIN读取列表,并将所选项目写入STDOUT.

```sh
find * -type f | fzf > selected
```

如果没有STDIN管道,fzf将使用find命令获取除隐藏文件之外的文件列表.  (您可以用`FZF_DEFAULT_COMMAND`覆盖默认命令)

```sh
vim $(fzf)
```

#### 使用 finder

-   `CTRL-J`/`CTRL-K` (要么`CTRL-N`/`CTRL-P`) 上下移动光标
-   `Enter`键选择项目,`CTRL-C`/`CTRL-G`/`ESC`退出
-   在多选模式下 (`-m`), `TAB`和`Shift-TAB`标记多个项目
-   Emacs样式的按键绑定
-   鼠标: 滚动,单击,双击; 在多选模式下进行 `shift-点击` 和`shift-滚动`

#### 布局

默认情况下,fzf以全屏模式启动,但您可以使用`--height`选项,从光标下方开始的宽度.

```sh
vim $(fzf --height 40%)
```

还可以看看`--reverse`和`--layout`选项,如果您更喜欢"自上而下"布局,而不是默认的"自下而上"布局.

```sh
vim $(fzf --height 40% --reverse)
```

您可以将这些选项添加到`$FZF_DEFAULT_OPTS`这样他们就可以默认应用了. 例如,

```sh
export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border'
```

#### 搜索语法

除非另有说明,否则fzf以"扩展搜索模式"开始,您可以在其中键入由空格分隔的多个搜索项. 例如`^music .mp3$ sbtrkt
!fire`

|   例子    | 匹配类型       | 描述               |
| --------- | ---------- | ---------------- |
| `sbtrkt`  | 模糊匹配       | 匹配`sbtrkt`的项目    |
| `'wild`   | 完全匹配 (引号)  | 包含`wild`的项目      |
| `^music`  | 前缀精确匹配     | 以`music`开头的项目 |
| `.mp3$`   | 后缀精确匹配     | 以`.mp3`结尾的项目  |
| `!fire`   | 反精确匹配      | 不包含`fire`的项目     |
| `!^music` | 反前缀精确匹配    | 不以`music` 开头的项目  |
| `!.mp3$`  | 反后缀精确匹配    | 不以`.mp3`结尾的项目 |

如果您不喜欢模糊匹配,但由不希望"引号"每个单词,请启动fzf`-e`/`--exact`选项. 请注意,当`--exact`设定,`'`-前缀, 就变成了模糊匹配"unquotes"的意思.

有个单个条形字符可用作OR运算符. 例如,以下查询匹配以`core`开头,,且任何一个以`go`或`rb`, 或`py`结束的.

    ^core go$ | rb$ | py$

#### 环境变量

-   `FZF_DEFAULT_COMMAND`
    -   使用于tty时,使用的默认命令
    -   例如`export FZF_DEFAULT_COMMAND='fd --type f'`
-   `FZF_DEFAULT_OPTS`
    -   默认选项
    -   例如`export FZF_DEFAULT_OPTS="--layout=reverse --inline-info"`

#### 选项

请参见手册页 (`man fzf`) 获取完整的选项列表.

## 例子

[the wiki page](https://github.com/junegunn/fzf/wiki/examples)可以找到许多有用的例子. 也请随意添加自己的例子.

## `fzf-tmux`脚本

[fzf-tmux](bin/fzf-tmux)是一个bash脚本,在tmux窗格中打开fzf.

```sh
# usage: fzf-tmux [-u|-d [HEIGHT[%]]] [-l|-r [WIDTH[%]]] [--] [FZF OPTIONS]
#        (-[udlr]: up/down/left/right)

# select git branches in horizontal split below (15 lines)
git branch | fzf-tmux -d 15

# select multiple words in vertical split on the left (20% of screen width)
cat /usr/share/dict/words | fzf-tmux -l 20% --multi --reverse
```

即使你不在tmux上,它仍然会工作,默默无视`-[udlr]`选项,所以可以在你的脚本中经常使用`fzf-tmux`.

或者,您可以使用`--height HEIGHT[%]`选项不以全屏模式启动fzf.

```sh
fzf --height 40%
```

## 命令行的键绑定

安装脚本将为bash,zsh和fish设置以下键绑定.

-   `CTRL-T`- 将选定的文件和目录粘贴到命令行上
    -   设置`FZF_CTRL_T_COMMAND`覆盖默认命令
    -   设置`FZF_CTRL_T_OPTS`传递其他选项
-   `CTRL-R`- 将所选命令从历史记录粘贴到命令行
    -   如果要按时间顺序查看命令,请按`CTRL-R`再次按相关性切换排序
    -   设置`FZF_CTRL_R_OPTS`传递其他选项
-   `ALT-C`-  cd进入所选目录
    -   设置`FZF_ALT_C_COMMAND`覆盖默认命令
    -   设置`FZF_ALT_C_OPTS`传递其他选项

如果您正在使用tmux会话,通过设置FZF_TMUX`到1,则可以在拆分窗格中启动fzf`,并用`FZF_TMUX_HEIGHT` (例如. `20`,`50%`)更改窗格的高度 .

如果你在bash上使用vi模式,则在.bashrc中`source
~/.fzf.bash` *之前* 需要添加`set -o vi`,以便正确设置vi模式的按键绑定.

可以在[the wiki page](https://github.com/junegunn/fzf/wiki/Configuring-shell-key-bindings)找到更多提示.

## bash和zsh的模糊完成

#### 文件和目录

如果光标前的单词以默认的触发顺序结束,则可以触发文件和目录的模糊完成`**`.

-   `COMMAND [DIRECTORY/][FUZZY_PATTERN]**<TAB>`

```sh
# Files under current directory
# - You can select multiple items with TAB key
vim **<TAB>

# Files under parent directory
vim ../**<TAB>

# Files under parent directory that match `fzf`
vim ../fzf**<TAB>

# Files under your home directory
vim ~/**<TAB>


# Directories under current directory (single-selection)
cd **<TAB>

# Directories under ~/github that match `fzf`
cd ~/github/fzf**<TAB>
```

#### 进程ID

为kill命令提供PID的模糊完成. 在这种情况下,没有触发序列,只需在kill命令后按tab键.

```sh
# Can select multiple processes with <TAB> or <Shift-TAB> keys
kill -9 <TAB>
```

#### 主机名

对于ssh和telnet命令,提供了主机名的模糊完成. 名称从 /etc/hosts和 〜/.ssh/config  中提取.

```sh
ssh **<TAB>
telnet **<TAB>
```

#### 环境变量/别名

```sh
unset **<TAB>
export **<TAB>
unalias **<TAB>
```

#### 设置

```sh
# Use ~~ as the trigger sequence instead of the default **
export FZF_COMPLETION_TRIGGER='~~'

# Options to fzf command
export FZF_COMPLETION_OPTS='+c -x'

# Use fd (https://github.com/sharkdp/fd) instead of the default find
# command for listing path candidates.
# - The first argument to the function ($1) is the base path to start traversal
# - See the source code (completion.{bash,zsh}) for the details.
_fzf_compgen_path() {
  fd --hidden --follow --exclude ".git" . "$1"
}

# Use fd to generate the list for directory completion
_fzf_compgen_dir() {
  fd --type d --hidden --follow --exclude ".git" . "$1"
}
```

#### 支持的命令

在bash上,模糊完成,仅对预定义的一组命令启用 (`complete | grep _fzf`看清单) . 但您可以为其他命令启用它,如下所示.

```sh
complete -F _fzf_path_completion -o default -o bashdefault ag
complete -F _fzf_dir_completion -o default -o bashdefault tree
```

## Vim插件

- [x] 看[README-VIM.md](README-VIM.zh.md).

## 高级主题

### 性能

fzf很快,而且是[变得更快][perf]. 在大多数用例中,性能不应成为问题. 但是,您可能希望了解影响性能的选项.

-   `--ansi`告诉fzf提取,并解析输入中的ANSI颜色代码,它使初始扫描速度变慢. 因此不建议您将其添加到您的`$FZF_DEFAULT_OPTS`.
-   `--nth`使fzf变慢,因为fzf必须标记每一行.
-   `--with-nth`使fzf变慢,因为fzf必须标记化,并重新组合每一行.
-   如果您绝对需要更好的性能,可以考虑使用`--algo=v1` (默认为`v2`) 使fzf使用更快的贪心算法. 但是,此算法无法保证找到匹配的最佳排序,因此不建议这样做.

[perf]: https://junegunn.kr/images/fzf-0.17.0.png

### 执行外部程序

您可以设置按键绑定,以启动外部进程而无需离开fzf (`execute`,`execute-silent`) .

```bash
# Press F1 to open the file with less without leaving fzf
# Press CTRL-Y to copy the line to clipboard and aborts fzf (requires pbcopy)
fzf --bind 'f1:execute(less -f {}),ctrl-y:execute-silent(echo {} | pbcopy)+abort'
```

看手册页*KEY BINDINGS*部分,了解详细信息.

### 预览窗口

当设置了`--preview`选项,fzf会以当前行作为参数自动启动外部进程,并在拆分窗口中显示结果.

```bash
# {} is replaced to the single-quoted string of the focused line
fzf --preview 'cat {}'
```

由于预览窗口仅在过程完成后更新,因此快速完成命令非常重要.

```bash
# Use head instead of cat so that the command doesn't take too long to finish
fzf --preview 'head -100 {}'
```

预览窗口支持ANSI颜色,因此您可以使用语法高亮显示文件内容的程序.

-   Highlight: <http://www.andre-simon.de/doku/highlight/en/highlight.php>
-   CodeRay: <http://coderay.rubychan.de/>
-   Rouge: <https://github.com/jneen/rouge>

```bash
# Try highlight, coderay, rougify in turn, then fall back to cat
fzf --preview '[[ $(file --mime {}) =~ binary ]] &&
                 echo {} is a binary file ||
                 (highlight -O ansi -l {} ||
                  coderay {} ||
                  rougify {} ||
                  cat {}) 2> /dev/null | head -500'
```

您可以使用自定义预览窗口的大小和位置,通过`--preview-window`选项. 例如,

```bash
fzf --height 40% --reverse --preview 'file {}' --preview-window down:1
```

有关更高级的示例,请参阅[git与fzf的键绑定][fzf-git] ([code](https://gist.github.com/junegunn/8b572b8d4b5eddd8b85e5f4d40f17236)) .

[fzf-git]: https://junegunn.kr/2016/07/fzf-git/

## 提示

#### 关于`.gitignore`

您可以使用[fd](https://github.com/sharkdp/fd),[ripgrep](https://github.com/BurntSushi/ripgrep), 要么[the silver
searcher](https://github.com/ggreer/the_silver_searcher)替代默认的find命令遍历文件系统遵循`.gitignore`内容.

```sh
# Feed the output of fd into fzf
fd --type f | fzf

# Setting fd as the default source for fzf
export FZF_DEFAULT_COMMAND='fd --type f'

# Now fzf (w/o pipe) will use fd instead of find
fzf

# To apply the command to CTRL-T as well
export FZF_CTRL_T_COMMAND="$FZF_DEFAULT_COMMAND"
```

如果希望命令遵循符号链接,并且不希望它排除隐藏文件,请使用以下命令:

```sh
export FZF_DEFAULT_COMMAND='fd --type f --hidden --follow --exclude .git'
```

#### `git ls-tree`用于快速遍历

如果您在大型git存储库中运行fzf,`git ls-tree`可以帮你提高遍历的速度.

```sh
export FZF_DEFAULT_COMMAND='
  (git ls-tree -r --name-only HEAD ||
   find . -path "*/\.*" -prune -o -type f -print -o -type l -print |
      sed s/^..//) 2> /dev/null'
```

#### Fish shell

版本2.6.0之前的fish[不允许](https://github.com/fish-shell/fish-shell/issues/1362)在命令替换中从STDIN读取,这意味着简单`vim (fzf)`没有按预期工作. 2.5.0及更早版本的解决方法是使用`read`fish命令:

```sh
fzf | read -l result; and vim $result
```

或者,对于多个结果:

```sh
fzf -m | while read -l r; set result $result $r; end; and vim $result
```

全局系统在fish中是不同的,说明`**`完成不起作用. 但是,那`CTRL-T`命令将使用命令行的最后一个标记作为递归搜索的根文件夹. 例如,击中`CTRL-T`在以下命令行的末尾

```sh
ls /var/
```

将列出`/var/`下的所有文件和文件夹.

使用自定义`FZF_CTRL_T_COMMAND`时,使用注入的`$dir`变量以利用此功能. `$dir`默认为`.`,当最后一个标记不是有效目录时. 例:

```sh
set -g FZF_CTRL_T_COMMAND "command find -L \$dir -type f 2> /dev/null | sed '1d; s#^\./##'"
```

## [License](LICENSE)

(MIT)

版权所有 (c) 2017 Junegunn Choi
