# fzf-zh [![explain]][source] [![translate-svg]][translate-list]

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

### 贡献

欢迎 👏 勘误/校对/更新贡献 😊 [具体贡献请看](https://github.com/chinanf-boy/chinese-translate-list#贡献)

## 生活

[help me live , live need money 💰](https://github.com/chinanf-boy/live-need-money)

---

# <img src="https://raw.githubusercontent.com/junegunn/i/master/fzf.png" height="170" alt="fzf - a command-line fuzzy finder"> [![travis-ci](https://travis-ci.org/junegunn/fzf.svg?branch=master)](https://travis-ci.org/junegunn/fzf)

fzf是一种通用的命令行模糊查找器. 

<img src="https://raw.githubusercontent.com/junegunn/i/master/fzf-preview.png" width=640>

它是一个用于命令行的交互式Unix过滤器,可以与任何列表一起使用;文件,命令历史,进程,主机名,书签,git提交等. 

## 优点

-   便携式,无依赖性
-   非常快
-   最全面的功能集
-   布局灵活
-   包括电池
    -   Vim / Neovim插件,键绑定和模糊自动完成

## 目录

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## 安装

fzf项目包含以下组件: 

-   `fzf`可执行
-   `fzf-tmux`用于在tmux窗格中启动fzf的脚本
-   Shell扩展
    -   键绑定 (`CTRL-T`,`CTRL-R`,和`ALT-C`)  (bash,zsh,fish) 
    -   模糊自动完成 (bash,zsh) 
-   Vim / Neovim插件

您可以[下载fzf可执行文件][bin]如果你不需要额外的东西,那就独自一人. 

[bin]: https://github.com/junegunn/fzf-bin/releases

### 使用Homebrew或Linuxbrew

您可以使用[Homebrew](http://brew.sh/)要么[Linuxbrew](http://linuxbrew.sh/)安装fzf. 

```sh
brew install fzf

# To install useful key bindings and fuzzy completion:
$(brew --prefix)/opt/fzf/install
```

### 用git

或者,您可以将此存储库"git clone"到任何目录并运行[install](https://github.com/junegunn/fzf/blob/master/install)脚本. 

```sh
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install
```

### 作为Vim插件

一旦安装了fzf,就可以通过添加目录来在Vim中启用它`&runtimepath`在您的Vim配置文件中,如下所示: 

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

但不是在您的系统上单独安装fzf (使用Homebrew或"git clone") 并在Vim上启用它 (将其添加到`&runtimepath`) ,你可以使用vim-plug来做到这两点. 

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

### Fedora的

fzf在Fedora 26及更高版本中可用,可以使用常用方法安装: 

```sh
sudo dnf install fzf
```

默认情况下启用shell完成和vim或neovim的插件. Shell密钥绑定已安装但默认情况下未启用. 有关更多信息,请参阅Fedora的软件包文档 (/usr/share/doc/fzf/README.Fedora) . 

### 视窗

可以下载用于Windows的预构建二进制文件[这里][bin]. fzf也可以作为[巧克力包][choco]. 

[choco]: https://chocolatey.org/packages/fzf

```sh
choco install fzf
```

但是,项目的其他组件可能无法在Windows上运行. 可以找到已知的问题和限制[维基页面][windows-wiki]. 您可能需要考虑安装fzf[适用于Linux的Windows子系统][wsl]一切都运行完美. 

[windows-wiki]: https://github.com/junegunn/fzf/wiki/Windows

[wsl]: https://blogs.msdn.microsoft.com/wsl/

## 升级fzf

fzf正在积极开发中,您可能希望偶尔升级一次. 请根据使用的安装方法按照以下说明进行操作. 

-   混帐: `cd ~/.fzf && git pull && ./install`
-   酿造: `brew update; brew reinstall fzf`
-   巧克力味: `choco upgrade fzf`
-   VIM插头: `:PlugUpdate fzf`

## 建立fzf

- [ ] 看到[BUILD.md](BUILD.zh.md). 

## 用法

fzf将启动交互式查找程序,从STDIN读取列表,并将所选项目写入STDOUT. 

```sh
find * -type f | fzf > selected
```

如果没有STDIN管道,fzf将使用find命令获取除隐藏文件之外的文件列表.  (您可以使用覆盖默认命令`FZF_DEFAULT_COMMAND`) 

```sh
vim $(fzf)
```

#### 使用取景器

-   `CTRL-J`/`CTRL-K` (要么`CTRL-N`/`CTRL-P`) 上下移动光标
-   `Enter`键选择项目,`CTRL-C`/`CTRL-G`/`ESC`退出
-   在多选模式下 (`-m`) `TAB`和`Shift-TAB`标记多个项目
-   Emacs样式键绑定
-   鼠标: 滚动,单击,双击;在多选模式下进行shift-click和shift-scroll

#### 布局

默认情况下,fzf以全屏模式启动,但您可以使用它从光标下方开始`--height`选项. 

```sh
vim $(fzf --height 40%)
```

还可以看看`--reverse`和`--layout`选项,如果您更喜欢"自上而下"布局而不是默认的"自下而上"布局. 

```sh
vim $(fzf --height 40% --reverse)
```

您可以将这些选项添加到`$FZF_DEFAULT_OPTS`这样他们就可以默认申请了. 例如,

```sh
export FZF_DEFAULT_OPTS='--height 40% --layout=reverse --border'
```

#### 搜索语法

除非另有说明,否则fzf以"扩展搜索模式"开始,您可以在其中键入由空格分隔的多个搜索项. 例如`^music .mp3$ sbtrkt
!fire`

| 代币        | 比赛类型       | 描述               |
| --------- | ---------- | ---------------- |
| `sbtrkt`  | 模糊匹配       | 匹配的项目`sbtrkt`    |
| `'wild`   | 完全匹配 (引用)  | 包含的项目`wild`      |
| `^music`  | 前缀精确匹配     | 以...开头的项目`music` |
| `.mp3$`   | 后缀精确匹配     | 以...结尾的项目`.mp3`  |
| `!fire`   | 逆精确匹配      | 不包含的项目`fire`     |
| `!^music` | 逆前缀精确匹配    | 不以开头的项目`music`   |
| `!.mp3$`  | 反后缀精确匹配    | 不以...结尾的项目`.mp3` |

如果您不喜欢模糊匹配并且不希望"引用"每个单词,请启动fzf`-e`要么`--exact`选项. 请注意,当`--exact`已设定,`'`-prefix"unquotes"这个词. 

单个条形字符用作OR运算符. 例如,以下查询匹配以...开头的条目`core`并以任何一个结束`go`,`rb`, 要么`py`. 

    ^core go$ | rb$ | py$

#### 环境变量

-   `FZF_DEFAULT_COMMAND`
    -   输入为tty时使用的默认命令
    -   例如`export FZF_DEFAULT_COMMAND='fd --type f'`
-   `FZF_DEFAULT_OPTS`
    -   默认选项
    -   例如`export FZF_DEFAULT_OPTS="--layout=reverse --inline-info"`

#### 选项

请参见手册页 (`man fzf`) 获取完整的选项列表. 

## 例子

可以找到许多有用的例子[the wiki
page](https://github.com/junegunn/fzf/wiki/examples). 随意添加自己的. 

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

即使你不在tmux上,它仍然会工作,默默无视`-[udlr]`选项,所以你总是可以使用`fzf-tmux`在你的脚本中. 

或者,您可以使用`--height HEIGHT[%]`选项不以全屏模式启动fzf. 

```sh
fzf --height 40%
```

## 命令行的键绑定

安装脚本将为bash,zsh和fish设置以下键绑定. 

-   `CTRL-T`- 将选定的文件和目录粘贴到命令行上
    -   组`FZF_CTRL_T_COMMAND`覆盖默认命令
    -   组`FZF_CTRL_T_OPTS`传递其他选项
-   `CTRL-R`- 将所选命令从历史记录粘贴到命令行
    -   如果要按时间顺序查看命令,请按`CTRL-R`再次按相关性切换排序
    -   组`FZF_CTRL_R_OPTS`传递其他选项
-   `ALT-C`-  cd进入所选目录
    -   组`FZF_ALT_C_COMMAND`覆盖默认命令
    -   组`FZF_ALT_C_OPTS`传递其他选项

如果您正在使用tmux会话,则可以通过设置在拆分窗格中启动fzf`FZF_TMUX`到1,并用更改窗格的高度`FZF_TMUX_HEIGHT` (例如. `20`,`50%`) . 

如果你在bash上使用vi模式,则需要添加`set -o vi` *之前* `source
~/.fzf.bash`在.bashrc中,以便正确设置vi模式的键绑定. 

可以找到更多提示[the wiki page](https://github.com/junegunn/fzf/wiki/Configuring-shell-key-bindings). 

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

对于ssh和telnet命令,提供了主机名的模糊完成. 名称从/ etc / hosts和〜/ .ssh / config中提取. 

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

在bash上,模糊完成仅对预定义的一组命令启用 (`complete | grep _fzf`看清单) . 但您可以为其他命令启用它,如下所示. 

```sh
complete -F _fzf_path_completion -o default -o bashdefault ag
complete -F _fzf_dir_completion -o default -o bashdefault tree
```

## Vim插件

- [ ] 看到[README-VIM.md](README-VIM.zh.md). 

## 高级主题

### 性能

fzf很快,而且是[变得更快][perf]. 在大多数用例中,性能不应成为问题. 但是,您可能希望了解影响性能的选项. 

-   `--ansi`告诉fzf提取并解析输入中的ANSI颜色代码,它使初始扫描速度变慢. 因此不建议您将其添加到您的`$FZF_DEFAULT_OPTS`. 
-   `--nth`使fzf变慢,因为fzf必须标记每一行. 
-   `--with-nth`使fzf变慢,因为fzf必须标记化并重新组合每一行. 
-   如果您绝对需要更好的性能,可以考虑使用`--algo=v1` (默认为`v2`) 使fzf使用更快的贪心算法. 但是,此算法无法保证找到匹配的最佳排序,因此不建议这样做. 

[perf]: https://junegunn.kr/images/fzf-0.17.0.png

### 执行外部程序

您可以设置键绑定以启动外部进程而无需离开fzf (`execute`,`execute-silent`) . 

```bash
# Press F1 to open the file with less without leaving fzf
# Press CTRL-Y to copy the line to clipboard and aborts fzf (requires pbcopy)
fzf --bind 'f1:execute(less -f {}),ctrl-y:execute-silent(echo {} | pbcopy)+abort'
```

看到*关键的约束力*手册页的部分详细信息. 

### 预览窗口

什么时候`--preview`如果设置了选项,fzf会以当前行作为参数自动启动外部进程,并在拆分窗口中显示结果. 

```bash
# {} is replaced to the single-quoted string of the focused line
fzf --preview 'cat {}'
```

由于预览窗口仅在过程完成后更新,因此命令快速完成非常重要. 

```bash
# Use head instead of cat so that the command doesn't take too long to finish
fzf --preview 'head -100 {}'
```

预览窗口支持ANSI颜色,因此您可以使用语法高亮显示文件内容的程序. 

-   突出: <http://www.andre-simon.de/doku/highlight/en/highlight.php>
-   CodeRay: <http://coderay.rubychan.de/>
-   胭脂: <https://github.com/jneen/rouge>

```bash
# Try highlight, coderay, rougify in turn, then fall back to cat
fzf --preview '[[ $(file --mime {}) =~ binary ]] &&
                 echo {} is a binary file ||
                 (highlight -O ansi -l {} ||
                  coderay {} ||
                  rougify {} ||
                  cat {}) 2> /dev/null | head -500'
```

您可以使用自定义预览窗口的大小和位置`--preview-window`选项. 例如,

```bash
fzf --height 40% --reverse --preview 'file {}' --preview-window down:1
```

有关更高级的示例,请参阅[git与fzf的键绑定][fzf-git] ([code](https://gist.github.com/junegunn/8b572b8d4b5eddd8b85e5f4d40f17236)) . 

[fzf-git]: https://junegunn.kr/2016/07/fzf-git/

## 提示

#### 关于`.gitignore`

您可以使用[fd](https://github.com/sharkdp/fd),[ripgrep](https://github.com/BurntSushi/ripgrep), 要么[the silver
searcher](https://github.com/ggreer/the_silver_searcher)而不是默认的find命令来尊重时遍历文件系统`.gitignore`. 

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

如果您在大型git存储库中运行fzf,`git ls-tree`可以提高遍历的速度. 

```sh
export FZF_DEFAULT_COMMAND='
  (git ls-tree -r --name-only HEAD ||
   find . -path "*/\.*" -prune -o -type f -print -o -type l -print |
      sed s/^..//) 2> /dev/null'
```

#### 鱼壳

版本2.6.0之前的鱼壳[doesn't allow](https://github.com/fish-shell/fish-shell/issues/1362)在命令替换中从STDIN读取,这意味着简单`vim (fzf)`没有按预期工作. 鱼2.5.0及更早版本的解决方法是使用`read`鱼命令: 

```sh
fzf | read -l result; and vim $result
```

或者,对于多个结果: 

```sh
fzf -m | while read -l r; set result $result $r; end; and vim $result
```

全球系统在鱼类中是不同的`**`完成不起作用. 但是,那`CTRL-T`命令将使用命令行上的最后一个标记作为递归搜索的根文件夹. 例如,击中`CTRL-T`在以下命令行的末尾

```sh
ls /var/
```

将列出所有文件和文件夹`/var/`. 

使用自定义时`FZF_CTRL_T_COMMAND`,使用未展开的`$dir`变量以利用此功能. `$dir`默认为`.`当最后一个令牌不是有效目录时. 例: 

```sh
set -g FZF_CTRL_T_COMMAND "command find -L \$dir -type f 2> /dev/null | sed '1d; s#^\./##'"
```

## [License](LICENSE)

麻省理工学院许可证 (MIT) 

版权所有 (c) 2017 Junegunn Choi

## License

MIT © [chinanf-boy](http://llever.com)
