### 显示文件路径
https://vi.stackexchange.com/questions/104/how-can-i-see-the-full-path-of-the-current-file
命令行:f
<C-G> 显示当前buffer相对于当前路径的Path
1 <C-G> 显示全部路径
It seems `C-g` is default for `0C-g`, and 
`2C-g` shows **buffer** index number (starting from 1) as well in addition.等价于 :ls

register %里是文件名
```
:echo @%                |" directory/name of file
:echo expand('%:t')     |" name of file ('tail')
:echo expand('%:p')     |" full path
:echo expand('%:p:h')   |" directory containing file ('head')
```

statusline增加文件路径状态:
```
set laststatus=2
set statusline+=%F
```
In insert mode, type Ctrl-r then % to insert the name of the current file.
### 清空register
有两种方法。一种是 setreg()。具体来说用：

1

`:call setreg(``'a'``,` `''``)`

可以把 寄存器a 里的内容清空。如果是想清除某几个寄存器的话，这个方法就很好。如果是想清空所有的，用个循环即可，如下：

1

2

3

`for` `c` `in` `range(char2nr(``'a'``), char2nr(``'z'``)) + range(char2nr(``'0'``), char2nr(``'9'``))`

`call setreg(nr2char(c),` `""``)`

`endfor`

另一种方法是去删  [vim](https://www.baidu.com/s?wd=vim&tn=SE_PcZhidaonwhc_ngpagmjz&rsv_dl=gh_pc_zhidao)info 文件。
直接去操纵 viminfo 就可以了。但是由于 vim 加载的时候会加载 viminfo 里的内容，退出的时候会再写入。所以用 vim 来编辑 viminfo 是不行的，删掉的东西会再写回去。因此要退出所有正在运行的 vim，让其把相关的内容先都写到 viminfo 里，然后运行其它编辑器来删除 viminfo 里的有关内容。或者干脆把 viminfo 直接删了也行，相当于清空所有历史记录。

最后，如果你根本不喜欢 vim 在退出之后保留那么多没用的寄存器内容，那么在 .vimrc 里加上（请务必先看一下自己的 .vimrc 里是不是已经有 viminfo 的设置，如果有只需把 < 后面的数字改成 0 就好，其它的不要动）：

1

`set` `viminfo=100,<0,s10,h`

就可以禁止 vim 退出后保存寄存器的内容。
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI0OTg3OTMsLTMwMDI4OTEyMywtMTA3MT
M0Mjg1OCwzODU1MTkzMTMsNDQ3NjI4MTA1XX0=
-->