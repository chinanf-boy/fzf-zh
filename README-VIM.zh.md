# FZF Vim 集成

此存储库仅与 Vim 的基本集成。 如果您正在寻找更多,请查看[fzf.vim](https://github.com/junegunn/fzf.vim)项目.

(注意: 要在 GVim 中使用 fzf,需要外部终端仿真器。 )

## `:FZF[!]`

如果你为 Vim 设置了 fzf,`:FZF`命令将被添加.

```vim
" 当前目录下，查找文件
:FZF

" 在你的 home 目录之下，查找文件
:FZF ~

" 带 options
:FZF --no-sort --reverse --inline-info /tmp

" 左边， 全屏模式开启fzf
:FZF!
```

与[ctrlp.vim](https://github.com/kien/ctrlp.vim)相似，使用回车键,`CTRL-T`,`CTRL-X`要么`CTRL-V`分别在当前窗口,新选项卡,水平分割或垂直分割中打开所选文件。

注意环境变量`FZF_DEFAULT_COMMAND`和`FZF_DEFAULT_OPTS`也适用于此。

### 配置

- `g:fzf_action`
  - 可自定义的额外键绑定,用于以不同方式打开所选文件
- `g:fzf_layout`
  - 确定 fzf 窗口的大小和位置
- `g:fzf_colors`
  - 自定义 fzf 颜色以匹配当前颜色方案
- `g:fzf_history_dir`
  - 启用历史记录功能
- `g:fzf_launcher`
  - (仅限 GVim) 终端仿真器打开 fzf
  - `g:Fzf_launcher`用于功能参考

#### 例子

```vim
" 这里是默认 给予的 按键绑定
let g:fzf_action = {
  \ 'ctrl-t': 'tab split',
  \ 'ctrl-x': 'split',
  \ 'ctrl-v': 'vsplit' }

" 选择行的过程中，可定义指定一个引用函数的动作
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

" fzf 默认布局
" - down / up / left / right
let g:fzf_layout = { 'down': '~40%' }

" 你可以设置 fzf 窗口使用 Vim command (需要: Neovim or latest Vim 8)
let g:fzf_layout = { 'window': 'enew' }
let g:fzf_layout = { 'window': '-tabnew' }
let g:fzf_layout = { 'window': '10split enew' }

" 自定义 fzf 颜色 to match your color scheme
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

" 启动 per-command 历史.
" CTRL-N 和 CTRL-P 会自动 载入 上下历史，而不是使用 down 和 up. 如果你不喜欢这样,
" 在 $FZF_DEFAULT_OPTS 明确绑定，你想要的按键
let g:fzf_history_dir = '~/.local/share/fzf-history'
```

## `fzf#run`

对于更高级的用途,您可以使用`fzf#run([options])`具有以下选项的功能.

| 选项名称                   | 类型          | 描述                                                     |
| -------------------------- | ------------- | -------------------------------------------------------- |
| `source`                   | string        | 用于生成 fzf 输入的外部命令 (例如`find .`)               |
| `source`                   | list          | Vim 列表作为 fzf 的输入                                  |
| `sink`                     | string        | Vim 命令处理所选项目 (例如`e`,`tabe`)                    |
| `sink`                     | funcref       | 参考处理每个所选项目的功能                               |
| `sink*`                    | funcref       | 如同`sink`,但一次获取输出行列表                          |
| `options`                  | string/list   | fzf 的选项                                               |
| `dir`                      | string        | 工作目录                                                 |
| `up`/`down`/`left`/`right` | number/string | 使用给定大小的 tmux 窗格 (例如`20`,`50%`)                |
| `window` (Vim 8 / Neovim)  | string        | 用于打开 fzf 窗口的命令 (例如`vertical aboveleft 30new`) |
| `launcher`                 | string        | 外部终端仿真器启动 fzf (仅限 GVim)                       |
| `launcher`                 | funcref       | 生成函数`launcher`字符串 (仅限 GVim)                     |

`options`项可以是字符串或列表. 对于简单的情况,字符串应该足够,但如果您担心在不同平台上转义问题，则更喜欢使用列表类型。

```vim
call fzf#run({'options': '--reverse --prompt "C:\\Program Files\\"'})
call fzf#run({'options': ['--reverse', '--prompt', 'C:\Program Files\']})
```

## `fzf#wrap`

`fzf#wrap([name string,] [opts dict,] [fullscreen boolean])`是一个辅助函数,它修饰选项字典，以便让`:FZF`之类能理解`g:fzf_layout`,`g:fzf_action`,`g:fzf_colors`,和`g:fzf_history_dir`。

```vim
command! -bang MyStuff
  \ call fzf#run(fzf#wrap('my-stuff', {'dir': '~/my-stuff'}, <bang>0))
```

## fzf 在终端缓冲区内

最新版本的 Vim 和 ​​Neovim 包括内置终端仿真器 (`:terminal`) 在下列情况下,fzf 将在终端缓冲区中，启动:

- 在 Neovim
- 在 GVim 上
- 在终端 Vim 上使用非默认布局
  - `call fzf#run({'left': '30%'})`要么`let g:fzf_layout = {'left': '30%'}`

### 隐藏状态栏

当 fzf 在终端缓冲区中启动时,您可能希望隐藏包含缓冲区的状态行.

```vim
autocmd! FileType fzf
autocmd  FileType fzf set laststatus=0 noshowmode noruler
  \| autocmd BufLeave <buffer> set laststatus=2 showmode ruler
```

## GVim

使用最新版本的 GVim，fzf 将在 Vim 的内置终端仿真器内启动。 请注意,Vim 的这个终端功能仍然年轻且不稳定,您可能会遇到一些问题.

如果你有一个旧版本的 GVim，你需要一个外部终端模拟器来启动 fzf. 默认情况下使用`xterm`命令，但您可以使用`g:fzf_launcher`进行自定义。

```vim
" 这是默认. %s 会替换成 fzf 命令
let g:fzf_launcher = 'xterm -e bash -ic %s'

" 用 urxvt 替换
let g:fzf_launcher = 'urxvt -geometry 120x30 -e sh -c %s'
```

如果您在 OSX 上运行 MacVim，我建议您使用 iTerm2 作为启动器。 参考[这个维基页面][macvim-iterm2]看看如何设置.

[macvim-iterm2]: https://github.com/junegunn/fzf/wiki/On-MacVim-with-iTerm2

## [License](LICENSE)

The MIT License (MIT)

版权所有 (c) 2017 Junegunn Choi
