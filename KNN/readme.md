# 代码总结
自己编码，实现了基于线性搜索和基于kd-tree的KNN算法，演示sklearn中GridSearchCV类的使用  
自己实现的线性搜索的效率较为低下，故学习了kd-tree算法  
但kd-tree算法对于高维数据来说还是有不足之处，以后有机会可以再学习关于kd-tree的进一步改进算法--ball-tree

# KNN算法的关键要素
对于KNN算法来说
k值的选择、距离度量及分类决策规则是k近邻法的三个基本要素。

1.k值选择：  
k太小，预测结果对近邻的实例点非常敏感，整体模型变得复杂，容易过拟合  
k太大，这时与输入实例较远的训练实例也会起预测作用，使预测发生错误，k值增大意味着整体模型变得简单，特别当K=N，无论输入实例是什么，都将简单地预测它属于在训练实例中最多的类。
一般k取一个比较小的数字，采用交叉验证的方法来选取k的值  


2.距离度量
对于明可夫斯基(Minkowski Distance)距离来说 $$\big(\sum\limits_{i=1}^n |X_i^{(a)}-X_i^{(b)}|^p\big)^{\frac{1}{p}}$$
p=1时 为曼哈顿距离
p=2时 为欧拉距离


3.分类决策规则  
uniform   
distance（一般权重选距离的倒数）  

# KNN分类算法的推广
对于k近邻算法解决回归问题，往往使用临近点的平均值或者加权平均值

# KNN分类算法的优缺点
优点：
* 简单好用，容易理解，精度高，理论成熟，既可以做分类也可以做回归  
* 可用于数值型数据和离散型数据  
* 无数据输入假定  
* 适合对稀有事件进行分类  

缺点：
* 计算复杂性高，空间复杂度高  
* 计算量太大，所以一般数值很大的时候不用这个，同时单个样本不能太少，否则容易发生误分  
* 可理解性比较差  
* 维数灾难：随着维数的增加，“看似相近”的2个点之间的距离越来越大  

# 参考内容：
《统计学习方法》——李航  
《机器学习实战》——Peter  
https://www.joinquant.com/community/post/detailMobile?postId=2843&page=&limit=20&replyId=&tag=&utm_source=wechat_session&utm_medium=social&utm_oi=662949217920880640
知乎上关于kdtree的原理的解释