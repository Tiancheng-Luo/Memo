https://stackoverflow.com/questions/25867060/awk-warning-escape-sequence-treated-as-plain
## FS等转义一般字符常量需要转义两次\\\\ -> \, \\. -> .
不包括\n \t等特殊字符, 包括\\s,等reg表达式, 是因为C语言预处理. 
https://www.cyberciti.biz/faq/linux-unix-gnu-awk-warning-escape-sequence-treated-as-plain-soultion/

String literals as used in your `FS` setting get parsed twice, once when the script is read and again when executed so escapes need to be doubled up (google it and/or read the awk man page or book). In this case on the first pass `\\\\` gets converted to `\\` and on the second pass `\\` gets converted to `\` which is what you want.

-   The Open Group clarifies that the C-style string preprocessing applies to regular expression strings. It stops short of explicitly saying that awk interprets contents of all string variables (not just that of constants) before invoking the regex interpreter.  [pubs.opengroup.org/onlinepubs/009695399/utilities/…](http://pubs.opengroup.org/onlinepubs/009695399/utilities/awk.html#tag_04_06_13_04)  $ f='\\.(dll|exe)$' $ awk -v filemask="${f}" 'BEGIN { a = "foodll"; print (a ~ filemask); print filemask;}' 0 \.(dll|exe)$  – [eel ghEEz](https://stackoverflow.com/users/80772/eel-gheez "774 reputation")  [Mar 2 '16 at 21:21](https://stackoverflow.com/questions/25867060/awk-warning-escape-sequence-treated-as-plain#comment59189989_25867768)
> Written with [StackEdit](https://stackedit.io/).``
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzc4OTE1NTA4XX0=
-->