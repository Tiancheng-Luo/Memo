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
The `Lasso`是估计

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMjk4MTM3NzUsLTE0NDc3NzM1ODQsNz
c3MjA2NjcxXX0=
-->