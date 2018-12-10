### 显示命令路径
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
In insert mode, type Ctrl-r then % to insert the name of the current file.
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU4NDI1OTEzNCwzODU1MTkzMTMsNDQ3Nj
I4MTA1XX0=
-->