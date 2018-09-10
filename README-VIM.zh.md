
# FZF Vim集成

此存储库仅启用与Vim的基本集成. 如果您正在寻找更多,请查看[fzf.vim](https://github.com/junegunn/fzf.vim)项目. 

 (注意: 要在GVim中使用fzf,需要外部终端仿真器. ) 

## `:FZF[!]`

如果你为Vim设置了fzf,`:FZF`命令将被添加. 

```vim
" Look for files under current directory
:FZF

" Look for files under your home directory
:FZF ~

" With options
:FZF --no-sort --reverse --inline-info /tmp

" Bang version starts fzf in fullscreen mode
:FZF!
```

与...相似[ctrlp.vim](https://github.com/kien/ctrlp.vim),使用回车键,`CTRL-T`,`CTRL-X`要么`CTRL-V`分别在当前窗口,新选项卡,水平分割或垂直分割中打开所选文件. 

注意环境变量`FZF_DEFAULT_COMMAND`和`FZF_DEFAULT_OPTS`也适用于此. 

### 组态

-   `g:fzf_action`
    -   可自定义的额外键绑定,用于以不同方式打开所选文件
-   `g:fzf_layout`
    -   确定fzf窗口的大小和位置
-   `g:fzf_colors`
    -   自定义fzf颜色以匹配当前颜色方案
-   `g:fzf_history_dir`
    -   启用历史记录功能
-   `g:fzf_launcher`
    -    (仅限GVim) 终端仿真器打开fzf
    -   `g:Fzf_launcher`用于功能参考

#### 例子

```vim
" This is the default extra key bindings
let g:fzf_action = {
  \ 'ctrl-t': 'tab split',
  \ 'ctrl-x': 'split',
  \ 'ctrl-v': 'vsplit' }

" An action can be a reference to a function that processes selected lines
function! s:build_quickfix_list(lines)
  call setqflist(map(copy(a:lines), '{ "filename": v:val }'))
  copen
  cc
endfunction

let g:fzf_action = {
  \ 'ctrl-q': function('s:build_quickfix_list'),
  \ 'ctrl-t': 'tab split',
  \ 'ctrl-x': 'split',
  \ 'ctrl-v': 'vsplit' }

" Default fzf layout
" - down / up / left / right
let g:fzf_layout = { 'down': '~40%' }

" You can set up fzf window using a Vim command (Neovim or latest Vim 8 required)
let g:fzf_layout = { 'window': 'enew' }
let g:fzf_layout = { 'window': '-tabnew' }
let g:fzf_layout = { 'window': '10split enew' }

" Customize fzf colors to match your color scheme
let g:fzf_colors =
\ { 'fg':      ['fg', 'Normal'],
  \ 'bg':      ['bg', 'Normal'],
  \ 'hl':      ['fg', 'Comment'],
  \ 'fg+':     ['fg', 'CursorLine', 'CursorColumn', 'Normal'],
  \ 'bg+':     ['bg', 'CursorLine', 'CursorColumn'],
  \ 'hl+':     ['fg', 'Statement'],
  \ 'info':    ['fg', 'PreProc'],
  \ 'border':  ['fg', 'Ignore'],
  \ 'prompt':  ['fg', 'Conditional'],
  \ 'pointer': ['fg', 'Exception'],
  \ 'marker':  ['fg', 'Keyword'],
  \ 'spinner': ['fg', 'Label'],
  \ 'header':  ['fg', 'Comment'] }

" Enable per-command history.
" CTRL-N and CTRL-P will be automatically bound to next-history and
" previous-history instead of down and up. If you don't like the change,
" explicitly bind the keys to down and up in your $FZF_DEFAULT_OPTS.
let g:fzf_history_dir = '~/.local/share/fzf-history'
```

## `fzf#run`

对于更高级的用途,您可以使用`fzf#run([options])`具有以下选项的功能. 

| 选项名称                       | 类型   | 描述                                           |
| -------------------------- | ---- | -------------------------------------------- |
| `source`                   | 串    | 用于生成fzf输入的外部命令 (例如`find .`)                  |
| `source`                   | 名单   | Vim列表作为fzf的输入                                |
| `sink`                     | 串    | Vim命令处理所选项目 (例如`e`,`tabe`)                   |
| `sink`                     | 函数引用 | 参考处理每个所选项目的功能                                |
| `sink*`                    | 函数引用 | 如同`sink`,但一次获取输出行列表                          |
| `options`                  | 串/名单 | fzf的选项                                       |
| `dir`                      | 串    | 工作目录                                         |
| `up`/`down`/`left`/`right` | 数/串  | 使用给定大小的tmux窗格 (例如`20`,`50%`)                 |
| `window` (Vim 8 / Neovim)  | 串    | 用于打开fzf窗口的命令 (例如`vertical aboveleft 30new`)  |
| `launcher`                 | 串    | 外部终端仿真器启动fzf (仅限GVim)                        |
| `launcher`                 | 函数引用 | 生成函数`launcher`字符串 (仅限GVim)                   |

`options`条目可以是字符串或列表. 对于简单的情况,字符串应该足够,但如果您担心在不同平台上转义问题,则更喜欢使用列表类型. 

```vim
call fzf#run({'options': '--reverse --prompt "C:\\Program Files\\"'})
call fzf#run({'options': ['--reverse', '--prompt', 'C:\Program Files\']})
```

## `fzf#wrap`

`fzf#wrap([name string,] [opts dict,] [fullscreen boolean])`是一个辅助函数,它修饰选项字典以便它理解`g:fzf_layout`,`g:fzf_action`,`g:fzf_colors`,和`g:fzf_history_dir`喜欢`:FZF`. 

```vim
command! -bang MyStuff
  \ call fzf#run(fzf#wrap('my-stuff', {'dir': '~/my-stuff'}, <bang>0))
```

## fzf在终端缓冲区内

最新版本的Vim和​​Neovim包括内置终端仿真器 (`:terminal`) 在下列情况下,fzf将在终端缓冲区中启动: 

-   在Neovim
-   在GVim上
-   在终端Vim上使用非默认布局
    -   `call fzf#run({'left': '30%'})`要么`let g:fzf_layout = {'left': '30%'}`

### 隐藏状态栏

当fzf在终端缓冲区中启动时,您可能希望隐藏包含缓冲区的状态行. 

```vim
autocmd! FileType fzf
autocmd  FileType fzf set laststatus=0 noshowmode noruler
  \| autocmd BufLeave <buffer> set laststatus=2 showmode ruler
```

## 的GVim

使用最新版本的GVim,fzf将在Vim的内置终端仿真器内启动. 请注意,Vim的这个终端功能仍然年轻且不稳定,您可能会遇到一些问题. 

如果你有一个旧版本的GVim,你需要一个外部终端模拟器来启动fzf. `xterm`默认情况下使用命令,但您可以使用它进行自定义`g:fzf_launcher`. 

```vim
" This is the default. %s is replaced with fzf command
let g:fzf_launcher = 'xterm -e bash -ic %s'

" Use urxvt instead
let g:fzf_launcher = 'urxvt -geometry 120x30 -e sh -c %s'
```

如果您在OSX上运行MacVim,我建议您使用iTerm2作为启动器. 参考[这个维基页面][macvim-iterm2]看看如何设置. 

[macvim-iterm2]: https://github.com/junegunn/fzf/wiki/On-MacVim-with-iTerm2

## [License](LICENSE)

麻省理工学院许可证 (MIT) 

版权所有 (c) 2017 Junegunn Choi
