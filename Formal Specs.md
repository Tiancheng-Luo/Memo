
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

[问题](http://blog.sina.com.cn/s/blog_6be26cc7010115hg.html)
```
给一个 n 长的数组，判断它是否为一个 1, 2, ..., n 的全排列，
要求在线性时间，常数空间内实现。
```
```
每个全排列都可以视为 1, 2, ..., n 上的一个置换。
问题就转化为检测该数组是不是一个 1, 2, ..., n 的置换。
由本文开头提到的定理可知，我们只需要检查该置换是不是由不相交的轮换构成的即可。

如何保证检查的高效以及所有轮换都不相交呢？
我们每次检查完一个数，就将它置负，这样遇到负值，循环就终止了。
如果终止前检查的那个数与起始的数相同，那么我们就发现了一个轮换，否则它就不是一个轮换，说明P不是一个置换。
由于检查过的轮换中的数字都被置为负值，所以第二个轮换肯定不会与第一个轮换相交。
如果到最后所有的数都被置为负值，且循环正常终止，那么说明它们都在不相交的轮换里，那么P 就是一个置换。

如果想要查找过程不影响最终数组的值，到最后把所有置负的元素都重新置正即可。
```
```c
int test_perm(int *a, int n)
{
  int i, j;
  if (a == NULL)  return 0;     
  a[0] = 1;
  for (i = 1; i <= n; ++i)      
    if (a[i] < 1 || a[i] > n) { 
      a[0] = 0;
      return a[0];
    }

  for (i = 1; i <= n; ++i)
    if (a[i] > 0) {
      j = i;
      while (a[j] > 0) {        
        a[j] = -a[j];
        j = -a[j];
      }
      if (j != i)  a[0] = 0;    
    }

  for (i = 1; i <= n; ++i)
    a[i] = a[i] > 0 ? a[i] : -a[i];

  return a[0];
}
```

$P=1-\frac{1}{100!}\sum_{k=51}^{100}\binom{100}{k}(k-1)!(100-k)!=1-\sum_{k=51}^{100} \frac{1}{k}=1-(H_{100}-H_{50})$
$P \approx 1-(\ln (100)$ - 
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzY4NzAwODQzLC01MjM0MjUyMjUsLTE1MD
Q3NjkxNDcsOTk2ODkxNzg0XX0=
-->