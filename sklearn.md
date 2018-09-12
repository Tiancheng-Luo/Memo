###CV（变异系数缩写）

标准差与平均数的比值称为变异系数，记为C.V(Coefficient of Variance)。

用公式表示为：$C.V.=\frac{\sigma}{\mu}$ 。

### 1.1.1普通最小二乘法
$$
\tag{1-1} \underset{\omega}{\min}{||X\omega - y||_2}^2
$$
```python
from sklearn import linear_model
reg = linear_model.LinearRegresssion()
reg.fit([[0, 0], [1, 1], [2, 2]], [0, 1, 2])
print(reg.coef_)
```
### 1.1.2 岭回归
Ridge回归通过对系数的大小施加惩罚来解决普通最小二乘法的一些问题. 岭系数最小化的是带罚项的残差平方和.
$$
\underset{\omega}{min}{||X\omega - y||_2}^2 + \alpha{||\omega||_2}^2
$$
其中, $\alpha \geq 0$是控制系数收缩量的复杂性参数: $\alpha$的值越大, 收缩量越大, 这样系数对共线性的鲁棒性也更强.
与其他线性模型一样, Ridge用fit方法将模型系数$\omega$存储在其`coef_`成员中:
```python
from sklearn import linear_model
reg = linear_model.Ridge(alpha = 0.5)
reg.fit([[0, 0], [0, 0], [1, 1]], [0, 0.1, 1])
Ridge(alpha=0.5, copy_X=True, fit_intercept=True, max_iter=None,
		normalize=False, random_state=none, solver='auto',tol=0.001)
print(reg.coef)
reg.intercept_
```
#####   设置正则化参数: 广义交叉验证
RidgeCV通过内置的Alpha 参数的交叉验证来实现岭回归.
该对象对GridSearchCV的使用方法相同, 只是它默认为Generalized Cross-Validation(广义交叉验证GCV), 它是一种有效的留一验证方法(LOO-CV):
```python
from sklearn import linear_model
reg = linear_model.RidgeCV(alphas=[0.1, 1.0, 10.0])
reg.fit([[0, 0], [0, 0], [1, 1]], [0, 0.1, 1])
RidgeCV(alpha=[0.1,1.0,10.0],
		cv=None,fit_intercept=True,scoring=None, normalize=False)
print(reg.alpha_)
```

### 1.1.3 Lasso
The `Lasso`是估计稀疏系数的线性模型. 它在一些情况下是有用的, 因为它倾向于使用具有较少参数值的情况, 有效地减少给定解决方案所依赖变量的数量, 因此, Lasso及其变体是压缩感知领域的基础. 在一定条件下, 它可以恢复一组非零权重的精确集.
在数学公式表达上, 它由一个带有$l_1$先验的正则项的线性模型组成, 其最小化的目标函数是:
$$
\underset{\omega}{min}\frac{1}{2 n_{samples}}{||X \omega - y||_2}^2 + \alpha||\omega||_1
$$
lasso estimate解决了加上罚项$\alpha||\omega||_1$的最小二乘法的最小化, 其中, $\alpha$是一个常数, $||\omega||_1$是参数向量的$l_1-norm$范数
Lasso类的实现使用了coordinate descent(坐标下降算法)来拟合系数. 查看`最小角回归`, 这是另一种方法.
```python
from sklearn import linear_model
reg = linear_model.Lasso(alpha = 0.1)
reg.fit([[0, 0], [1, 1]], [0, 1]);
Lasso(alpha=0.1, # 参数$\alpha$ 
		copy_X=True, # 对是否修改数据的一个标记，如果True，即复制了就不会修改数据
		fit_intercept=True, #  是否计算截距(数据预处理可能已经centered)
		max_iter=1000, # 迭代最多次数
		normalize=False,#  
		positive=False, 
		precompt=False, 
		random_state=None,
		selector='cyclic', 
		tol=0.0001, 
		warm_start=False
		)
print(reg.predict([[1,1]])
```
对于较低级别的任务, 同样有用的是函数lasso_path, 它能够搜索所有可能路径上的值来计算函数.

### Gram矩阵
对称矩阵
欧氏空间半正定
-  如果  $v_1,v_2,…,v_n$  分别是随机向量，则 Gram 矩阵是协方差矩阵；
-   其实对于一个$X_N⋅d$（N 个样本，d 个属性）的样本矩阵而言，$X⋅X'X⋅X'$  即为 Gram 矩阵；

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU2MjE4MzY2Myw1NTk5OTU3NjgsLTIyNz
U0Nzg2NSwtMTQyNDI5MTgwMCw3NDE1NTkwMTksLTE0NDc3NzM1
ODQsNzc3MjA2NjcxXX0=
-->