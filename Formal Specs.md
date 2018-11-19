
## Formal Specification of the x86 instruction set architecture Digest
### Notations
A bitvector $x$ of length $n$ is denoted as $x \in \mathbb{B}^n$. 

$$\widetilde{\sigma\tau}f = \tilde{\sigma}(\tilde{\tau}f)$$
$$
\widetilde{\sigma\tau}f(x_1, \cdots, x_n) \\
= f(x_{(\sigma\tau)^{-1}(1)}, \cdots, x_{(\sigma\tau)^{-1}(n)})
= f(x_{\tau^{-1}(\sigma^{-1}(1))}, \cdots, x_{\tau^{-1}(\sigma^{-1}(n))})  \\
=(\tilde{\tau}f)(x_{\sigma^{-1}(1)}, \cdots, x_{\sigma^{-1}(n)})
=[\tilde{\sigma}(\tilde{\tau}f)](x_1, \cdots, x_n)
$$
因此$\widetilde{\sigma\tau}f = \tilde{\sigma}(\tilde{\tau}f)$(交换律)
设$n$元置换把$i$映射成$a_i(i = 1, 2, \cdots,n)$, 则通常把$\sigma$写成下述形式:
$$
\sigma = \begin{pmatrix}
1 & 2 & \cdots & n \\
a_1 & a_2 & \cdots & a_n
\end{pmatrix}
$$
称为n元置换
因为$\sigma$是双射, 因此$a_1 a_2 \cdots a_n$是$1, 2, \cdots,n$的一个$n$元置换.
更节省的方式:
$1 \rightarrow 2, 2 \rightarrow 3, 3 \rightarrow 4, 4 \rightarrow 1$写成$(1234)$
$1 \rightarrow 4, 2 \rightarrow 3, 3 \rightarrow 2, 4 \rightarrow 1$写成$(14)(23)$
如果一个$n$元置换$\sigma$把$i_1$映成$i_2$, 把$i_2$映成$i_3$, $\cdots$, 把$i_{r-1}$映成$i$, 把其称为一个r-轮换, 记作$(i_1 i_2 i_3 \cdots i_{r-1} i_r)$. 2-轮换也可称为对换.
两个轮换如果它们之间没有公共的元素, 则称它们不相交(disjoint). 例如, (134) 与 (25) 是不相交的两个轮换. 我们来计算它们的乘积, 轮换(25)把1, 3, 4分别保持不变, 而轮换(134)分别把2, 5保持不变.**不相交的两个轮换对乘法是可交换的**
**定理1**: 任何一个*非单位元的置换*都能表示成一些**两两不相交的轮换**的乘积, 并且*除了轮换的排列次序外, 表示法是唯一的*.
$(i_1, i_2, \cdots, i_{r-1}, i_r)^{-1} = (i_1, i_r, i_{r-1}, \cdots, i_2)$
推论2: 每一个置换都可以表示成一些对换的乘积. 其表示法不唯一
$(i_1, i_2, i_3, \cdots, i_{r-1}, i_r) = (i_1, i_r)(i_1, i_{r-1})\cdots (i_1,i_3)(i_1, i_2)$
$(134) = (14)(13)$
$(134)  = (12)(34)(24)(12)$
注意到两种分解中, 对换的个数都是偶数.
置换$\sigma$的对换分解式中出现的对换个数k的奇偶性是由$\sigma$本身决定的: 当$\sigma$为偶置换时, 对换个数为偶数;当$\sigma$为奇转换时, 对换个数为奇数.

2. $\neg, \to, \gets$





> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcyOTEzNTI3MiwtMTUwNDc2OTE0Nyw5OT
Y4OTE3ODRdfQ==
-->