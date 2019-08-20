数值最优化方法：
* 梯度下降法
  * Batch_gradient_descent
  * Stochastic_gradient_descent
  * mini_Batch_gradient_descent
 
* 牛顿法
* 坐标下降法

----
## 梯度下降法
迭代公式：$$X_{k+1}=X_{k}-\eta \nabla f(X)$$  
注意事项：  
使用前需要进行数值归一化  
实现细节问题：
* 初始值的设定
* 步长的选择
* 迭代终止的判定规则
