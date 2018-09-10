
# CHANGELOG

## 0.17.4

-   添加`--layout`带有新布局的选项`reverse-list`. 
    -   `--layout=reverse`是...的同义词`--reverse`
    -   `--layout=default`是...的同义词`--no-reverse`
-   如果任何占位符表达式 (例如,任何占位符表达式) 与查询不匹配,则预览窗口将更新. `{q}`,`{+}`) 计算为非空字符串. 
-   更多绑定键: `shift-{up,down}`,`alt-{up,down,left,right}`
-   fzf现在可以开始了`/dev/tty`通过做出有根据的猜测是不可用的. 
-   更新了Windows的默认命令. 
-   bash / zsh完成的修复和改进
-   安装和卸载脚本现在支持生成文件`XDG_CONFIG_HOME`上`--xdg`旗. 

看到<https://github.com/junegunn/fzf/milestone/12?closed=1>获取完整的更改列表. 

## 0.17.3

-   `$LINES`和`$COLUMNS`导出到预览命令,以便命令知道预览窗口的确切大小. 
-   默认命令或更好的错误消息`$FZF_DEFAULT_COMMAND`失败. 
-   当find命令检测到文件系统循环时,恢复#1061以避免列表中出现重复条目​​ (#1120) . 现在,默认命令需要find支持`-fstype`选项. 
-   fzf现在区分鼠标左键单击和右键单击 (#1130) 
    -   右键单击现在绑定到`toggle`默认情况下的操作
    -   `--bind`理解`left-click`和`right-click`
-   添加`replace-query`行动 (#1137) 
    -   用当前选择替换查询字符串
-   添加`accept-non-empty`行动 (#1162) 
    -   与accept相同,除了它阻止fzf退出而没有任何选择

## 0.17.1

-   修复了预览窗口的自定义背景颜色 (#1046) 
-   修复了Windows二进制文件的背景色问题
-   修复了使用cmd.exe执行命令的Windows二进制文件,没有解析和转义 (#1072) 
-   增加了对支持`window`使用Vim 8终端在Vim 8上进行布局 (#1055) 

## 0.17.0-2

辅助脚本的维护版本. fzf二进制文件未更新. 

-   对Vim 8内置终端的实验支持
    -   fzf现在可以在GVim中运行
-   更新了Vim插件以更好地处理`&shell`关于鱼的问题
-   修复了生成无效输出的fzf-tmux的错误
-   修复了fzf-tmux甚至可以工作的问题`tput`不起作用

## 0.17.0或更新版本

-   性能优化
-   可以在扩展搜索模式中将文字空间与反斜杠前面的空格匹配. 
-   `--expect`现在是添加剂,可以多次指定. 

## 0.16.11

-   性能优化
-   修复了缺少的预览更新

## 0.16.10

-   修复了预览窗口中ANSI颜色的无效处理问题
-   进一步改善`--ansi`性能

## 0.16.9

-   内存和性能优化
    -   一般用例的性能提升约20%
    -   处理速度提高了5倍`--ansi`
    -   内存使用量减少高达50%
-   错误修复和可用性改进
    -   固定处理括号粘贴模式
    -   [错误]在默认命令失败时在信息行上
    -   更有效地渲染预览窗口
    -   `--no-clear`针对重复重新启动方案进行了更新

## 0.16.8

-   新`change`事件和`top`行动`--bind`
    -   `fzf --bind change:top`
        -   每当更改查询字符串时,将光标移动到顶部结果
    -   `fzf --bind 'ctrl-w:unix-word-rubout+top,ctrl-u:unix-line-discard+top'`
        -   `top`结合`unix-word-rubout`和`unix-line-discard`
-   修正了不一致的抢七分数`--nth`用来
-   正确显示选项卡中的字符`--prompt`
-   固定不到`--cycle`在页面向上/向下翻页以防止过冲
-   Git修改版`--version`产量
-   对Cygwin环境的基本支持
-   Windows / Cygwin上的Vim插件中有很多修复 (感谢@janlazo) 

## 0.16.7

-   增加了对支持`ctrl-alt-[a-z]`关键和弦
-   CTRL-Z (SIGSTOP) 现在可以使用fzf
-   fzf将导出`$FZF_PREVIEW_WINDOW`以便脚本可以使用它
-   Vim插件和shell扩展中的错误修复和改进

## 0.16.6

-   小错误修复和改进
-   添加`--no-clear`用于编写脚本的选项

## 0.16.5

-   修正了一些小错误
-   添加`toggle-preview-wrap`行动
-   使用Go 1.8构建

## 0.16.4

-   添加`--border`选择在取景器上方和下方绘制边框
-   错误修复和改进

## 0.16.3

-   修复了当跨越制表符被剪裁时fzf错误地显示行的错误
-   用于的占位符表达式`--preview`和`execute`行动可以选择`+`用于多个选择的标志
    -   例如`git log --oneline | fzf --multi --preview 'git show {+1}'`
-   添加`execute-silent`静默执行命令而不切换到备用屏幕的操作. 当过程是短暂的并且您对其输出不感兴趣时​​,这很有用. 
    -   例如`fzf --bind 'ctrl-y:execute!(echo -n {} | pbcopy)'`
-   `ctrl-space`被允许进入`--bind`

## 0.16.2

-   丢弃ncurses依赖
-   freebsd,openbsd,arm5,arm6,arm7和arm8的二进制文件
-   官方24位色彩支持
-   添加了对复合操作的支持`--bind`. 可以使用链接多个动作`+`分隔器. 
    -   例如`fzf --bind 'ctrl-y:execute(echo -n {} | pbcopy)+abort'`
-   `--preview-window`允许大小为0. 这用于在后台执行fzf执行预览命令而不显示结果. 
-   小错误修复和改进

## 0.16.1

-   固定`--height`用背景颜色正确填充窗口的选项
-   添加`half-page-up`和`half-page-down`行动
-   添加`-L`标志为默认的find命令

## 0.16.0

-   *添加`--height HEIGHT[%]`选项*
    -   fzf现在可以显示取景器而不占用全屏
-   预览窗口默认会截断长行. 换行可以启用`:wrap`国旗`--preview-window`. 
-   拉丁字母字母将在匹配前进行标准化,以便更容易与重音字母匹配. 例如`sodanco`可以匹配`Só Danço Samba`. 
    -   可以通过禁用标准化`--literal`
-   添加`--filepath-word`做出有意义的动作/动作 (`alt-b`,`alt-f`,`alt-bs`,`alt-d`) 尊重路径分隔符

## 0.15.9

-   修复了0.15.8中引入的渲染毛刺
-   默认的转义延迟减少到50毫秒,可以通过配置`$ESCDELAY`
-   当溢出时,始终显示预览窗口右上角的滚动指示器
-   现在可以使用ncurses 6或tcell构建,以支持额外的功能
    -   *ncurses 6*
        -   支持超过256种颜色对
        -   支持斜体
    -   *T细胞*
        -   24位颜色支持
    -   看到<https://github.com/junegunn/fzf/blob/master/BUILD.md>

## 0.15.8

-   更新了ANSI处理器以处理更多VT-100转义序列
-   添加`--no-bold` (和`--bold`)  选项
-   改进了WSL的转义序列处理
-   增加了对支持`alt-[0-9]`,`f11`,和`f12`对于`--bind`和`--expect`

## 0.15.7

-   修复了禁用颜色且标题行包含ANSI颜色时的混乱

## 0.15.6

-   Windows二进制文件! (@ kelleyma49) 
-   修复了切换预览窗口时清除标题行的问题
-   修复了不在屏幕上显示^ N和^ O的问题
-   通过在ESC之后使fzf等待额外的击键来修复WSL上的光标键 (或以ESC开头的任何键序列) ,最长100ms

## 0.15.5

-   设置前景色将不再将背景颜色设置为黑色
    -   例如`fzf --color fg:153`
-   `--tiebreak=end`将考虑相对位置而不是绝对距离
-   更新`fzf#wrap`尊重的功能`g:fzf_colors`

## 0.15.4

-   在预览和执行操作中添加了对范围表达式的支持
    -   例如`ls -l | fzf --preview="echo user={3} when={-4..-2}; cat {-1}" --header-lines=1`
    -   `{q}`将被替换为当前查询的单引号字符串
-   修复以正确处理unicode空白字符
-   在预览窗口中显示滚动指示器
-   反向搜索词将默认使用精确匹配器
    -   这是一个突破性的变化,但我相信它更有意义. 由于模糊逆项,几乎不可能预测哪些条目将被过滤掉. 你仍然可以通过前置来执行逆模糊匹配`!'`这个词. 

## 0.15.3

-   添加了对更多ANSI属性的支持: 暗淡,下划线,闪烁和反向
-   固定的比赛条件`toggle-preview`

## 0.15.2

-   预览窗口现在可以滚动
    -   使用鼠标滚动或可绑定操作
        -   `preview-up`
        -   `preview-down`
        -   `preview-page-up`
        -   `preview-page-down`
-   更新了ANSI处理器以支持高强度颜色并忽略一些与VT100相关的转义序列

## 0.15.1

-   在第2 ^ 15列之后发生模式时修复了恐慌
-   修复了显示极长行时的渲染延迟

## 0.15.0

-   改进的模糊搜索算法
    -   添加`--algo=[v1|v2]`因此,人们仍然可以选择旧算法,该算法将搜索性能与结果质量相区分
-   高级评分标准
-   `--read0`读取由ASCII NUL字符分隔的输入
-   `--print0`打印由ASCII NUL字符分隔的输出

## 0.13.5

-   内存和性能优化
    -   高达2倍的性能和一半的内存

## 0.13.4

-   性能优化
    -   ascii字符串的内存占用减少了60%
    -   查询性能提高15%到20%
    -   性能提升高达45%`--nth`与非正则表达分隔符
-   修复了无效处理问题`hidden`的财产`--preview-window`

## 0.13.3

-   修复了预览窗口中最后一行的重复渲染

## 0.13.2

-   修复了未正确清除预览窗口的竞争条件

## 0.13.1

-   修复了大的UI问题`--preview`输出有许多ANSI代码

## 0.13.0

-   添加了预览功能
    -   `--preview CMD`
    -   `--preview-window POS[:SIZE][:hidden]`
-   `{}`in execute action现在被替换为当前行的单引号 (而不是双引号) 字符串
-   已修复以忽略括号粘贴模式的控制字符

## 0.12.2

-   256色功能检测不需要`256`在`$TERM`
-   添加`print-query`行动
-   更多命名的绑定键;<kbd>F1</kbd>〜<kbd>F10</kbd>,<kbd>ALT-/</kbd>,<kbd>ALT-空间</kbd>,和<kbd>ALT-进入</kbd>
-   添加`jump`和`jump-accept`实施的行动[在EasyMotion][em]像运动![][jump]

[em]: https://github.com/easymotion/vim-easymotion

[jump]: https://cloud.githubusercontent.com/assets/700826/15367574/b3999dc4-1d64-11e6-85da-28ceeb1a9bc2.png

## 0.12.1

-   现在普遍应用0.12.0中引入的排名算法
-   修复了精确模式下的无效缓存引用
-   Vim插件和shell扩展的修复和改进

## 0.12.0

-   增强排名算法
-   修正了一些小错误

## 0.11.4

-   添加`--hscroll-off=COL`选项 (默认值: 10)  (#513) 
-   Vim插件和shell扩展中的一些修复

## 0.11.3

-   SIGTERM优雅退出 (#482) 
-   `$SHELL`代替`sh`对于`execute`行动和`$FZF_DEFAULT_COMMAND` (#481) 
-   模糊完成API的变化
    -   [`_fzf_compgen_{path,dir}`](https://github.com/junegunn/fzf/commit/9617647)
    -   [`_fzf_complete_COMMAND_post`](https://github.com/junegunn/fzf/commit/8206746)用于后期处理

## 0.11.2

-   `--tiebreak`现在接受以逗号分隔的排序条件列表
    -   每个标准应仅在列表中出现一次
    -   `index`只允许在列表的末尾
    -   `index`未指定时隐式附加到列表中
    -   默认是`length` (或等同地`length,index`) 
-   `begin`在计算索引时,criteria将忽略前导空格
-   添加`toggle-in`和`toggle-out`行动
    -   切换方向取决于`--reverse`-ness
    -   `export FZF_DEFAULT_OPTS="--bind tab:toggle-out,shift-tab:toggle-in"`
-   减少了初始延迟时间`--tac`没有给出
    -   如果输入流正在进行中,fzf将屏幕的初始渲染推迟到100ms,以防止在初始阶段进行不必要的重绘. 但是,100毫秒的延迟是非常明显的,可能会给人一种fzf不够活泼的印象. 此提交将最大延迟减少到20毫秒`--tac`未指定,在这种情况下,输入列表会快速填充整个屏幕. 

## 0.11.1

-   添加`--tabstop=SPACES`选项

## 0.11.0

-   为扩展搜索模式添加了OR运算符
-   添加`--execute-multi`行动
-   修复了使用unicode宽字符时光标位置不正确的问题`--prompt`
-   shell扩展中的修复和改进

## 0.10.9

-   现在默认启用扩展搜索模式
    -   `--extended-exact`我们已经弃用了`--exact`用于正交控制搜索的"准确性"
-   修复了不显示不可打印字符的问题
-   添加`double-click`对于`--bind`选项
-   更强大的SIGWINCH处理

## 0.10.8

-   在禁用颜色后尝试设置颜色时修复了恐慌 (#370) 

## 0.10.7

-   修复了执行操作期间的非序列化中断处理,这通常会导致无效的内存访问和崩溃
-   变`--tiebreak=length` (默认) 使用修剪长度时`--nth`用来

## 0.10.6

-   更换`--header-file`同`--header`选项
-   `--header`和`--header-lines`可以一起使用
-   更改退出状态
    -   0: 好的
    -   1: 没有比赛
    -   2: 错误
    -   130: 中断
-   64位Linux二进制文件与ncurses静态链接,以避免兼容性问题. 

## 0.10.5

-   `'`-prefix取消引用该术语`--extended-exact`模式
-   向后扫描时`--tiebreak=end`已设定

## 0.10.4

-   修复了从输出中删除ANSI代码的问题`--with-nth`已设定

## 0.10.3

-   修复了慢性能`--with-nth`与...一起使用时`--delimiter`
    -   Golang的正则表达式引擎到目前为止非常慢,因此固定版本会将给定的分隔符模式视为普通字符串而不是正则表达式,除非它包含特殊字符并且是有效的正则表达式. 
    -   更简单的正则表达式用于分隔符以获得更好的性能

## 0.10.2

### 修复和改进

-   提高查询的感知响应时间
    -   热切,高效的符文阵列转换
-   无法初始化ncurses时无法正常退出 ($ TERM无效) 
-   改进排名算法时`--nth`选项已设置
-   当存在名称以dash开头的文件时,更改默认命令不会失败

## 0.10.1

### 新功能

-   添加`--margin`选项
-   添加了粘贴标头的选项
    -   `--header-file`
    -   `--header-lines`
-   添加`cancel`当输入已经为空时清除输入或关闭取景器的动作
    -   例如`export FZF_DEFAULT_OPTS="--bind esc:cancel"`
-   添加`delete-char/eof`区分的行动`CTRL-D`和`DEL`

### 小改进/修复

-   已修复以允许绑定冒号和逗号键
-   固定ANSI处理器以处理跨越多行的颜色区域

## 0.10.0

### 新功能

-   更多行动`--bind`
    -   `select-all`
    -   `deselect-all`
    -   `toggle-all`
    -   `ignore`
-   `execute(...)`在不离开fzf的情况下运行任意命令的操作
    -   `fzf --bind "ctrl-m:execute(less {})"`
    -   `fzf --bind "ctrl-t:execute(tmux new-window -d 'vim {}')"`
    -   如果该命令包含括号,请使用以下任何替代符号以避免解析错误
        -   `execute[...]`
        -   `execute~...~`
        -   `execute!...!`
        -   `execute@...@`
        -   `execute#...#`
        -   `execute$...$`
        -   `execute%...%`
        -   `execute^...^`
        -   `execute&...&`
        -   `execute*...*`
        -   `execute;...;`
        -   `execute/.../`
        -   `execute|...|`
        -   `execute:...`
            -   这是一种特殊形式,可以使您从解析错误中解脱出来,因​​为它不期望结束字符
            -   问题是它应该是逗号分隔列表中的最后一个
-   添加了对可选搜索历史的支持
    -   `--history HISTORY_FILE`
        -   使用时,`CTRL-N`和`CTRL-P`会自动重新映射到`next-history`和`previous-history`
    -   `--history-size MAX_ENTRIES` (默认值: 1000) 
-   可以启用循环滚动`--cycle`
-   修复了微调器没有在空闲输入流上旋转的错误
    -   例如`sleep 100 | fzf`

### 小改进/修复

-   添加了可以为其指定的键名的同义词`--bind`,`--toggle-sort`,和`--expect`
-   修复了当前行上多选标记的颜色
-   固定允许`^pattern$`在扩展搜索模式下

## 0.9.13

### 新功能

-   颜色定制与扩展`--color`选项

### Bug修复

-   修复了存在长行超过64KB的Reader过早终止的问题

## 0.9.12

### 新功能

-   添加`--bind`自定义键绑定的选项

### Bug修复

-   修复了在终端调整大小后立即更新"内联信息"的问题
-   固定ANSI代码偏移计算

## 0.9.11

### 新功能

-   添加`--inline-info`保存屏幕区域的选项 (#202) 
    -   在Neovim里面很有用
    -   例如`let $FZF_DEFAULT_OPTS = $FZF_DEFAULT_OPTS.' --inline-info'`

### Bug修复

-   大小写转换时输入的无效变异 (#209) 
-   扩展搜索模式中每个术语的智能案例 (#208) 
-   修正滚动偏移为正时双击结果

## 0.9.10

### 改进

-   性能优化
-   不太积极的memoization来限制内存使用

### 新功能

-   为浅色背景添加了颜色方案: `--color=light`

## 0.9.9

### 新功能

-   添加`--tiebreak`选项 (#191) 
-   添加`--no-hscroll`选项 (#193) 
-   视觉指示`--toggle-sort` (#194) 

## 0.9.8

### Bug修复

-   修复了Unicode案例处理 (#186) 
-   修复了在RuneError上终止 (#185) 

## 0.9.7

### 新功能

-   添加`--toggle-sort`选项 (#173) 
    -   `--toggle-sort=ctrl-r`适用于`CTRL-R`shell扩展

### Bug修复

-   固定打印空行if`--expect`已设置并且fzf已完成`--select-1`要么`--exit-0` (#172) 
-   修复以允许逗号字符作为参数`--expect`选项

## 0.9.6

### 新功能

#### 添加`--expect`选项 (#163) 

如果您提供以逗号分隔的键列表`--expect`选项,fzf将允许您选择匹配并在按下任何键时完成取景器. 此外,fzf将打印作为输出第一行按下的键的名称,以便您的脚本可以根据信息决定下一步操作. 

```sh
fzf --expect=ctrl-v,ctrl-t,alt-s,f1,f2,~,@
```

更新的vim插件使用此选项来实现[ctrlp](https://github.com/kien/ctrlp.vim)兼容的键绑定. 

### Bug修复

-   修复忽略ANSI转义码`\e[K` (#162) 

## 0.9.5

### 新功能

#### 添加`--ansi`选项 (#150) 

如果你给`--ansi`fzf的选项,fzf将解释输入中的ANSI颜色代码,使用ANSI颜色显示项目 (不支持真彩色) ,并从输出中删除代码. 默认情况下,此选项处于关闭状态,因为它需要一些开销. 

### 改进

#### 减少初始内存占用 (#151) 

通过删除不必要的指针副本,fzf在启动时将使用少得多的内存. 当输入非常大时,差异非常明显.  (例如. `locate / | fzf`) 

### Bug修复

-   修复恐慌`--no-sort --filter ''` (#149) 

## 0.9.4

### 新功能

#### 添加`--tac`用于反转输入顺序的选项. 

有人可能认为这个选项是不必要的,因为我们已经可以放了`tac`要么`tail -r`在命令管道中实现相同的结果. 但是,优点`--tac`是在输入完成之前它不会阻塞. 

### *向后不兼容的变化*

#### 改变了行为`--no-sort`

`--no-sort`选项将不再反转finder中的显示顺序. 您可能想要使用新的`--tac`选项`--no-sort`. 

    history | fzf +s --tac

### 改进

#### `--filter`禁用排序时不会阻止

当fzf在过滤模式下工作时 (`--filter`) 并且排序被禁用 (`--no-sort`) ,在输入完成之前无需阻塞. 新版本的fzf将在满足以下条件时即时打印匹配: 

    --filter TERM --no-sort [--no-tac --no-sync]

或者干脆: 

    -f TERM +s

此更改消除了以下用例中不必要的延迟: 

    fzf -f xxx +s | head -5

但是,在这种情况下,fzf按顺序处理行,因此它不能使用多个内核,并且fzf将比先前的执行模式运行稍慢,其中在加载整个输入之后并行完成过滤. 如果用户担心此性能问题,可以添加`--sync`重新启用缓冲的选项. 

## 0.9.3

### 新功能

-   添加`--sync`多阶段过滤选项

### 改进

-   `--select-1`和`--exit-0`当条件无法满足时,将立即启动查找程序
