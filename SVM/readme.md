参考李航老师的《统计学习方法》和《机器学习实战》完成SVM的个人代码整理

参考李航老师的《统计学习方法》写出来的代码效果并不是很好，主要在SMO中对于优化变量的更新中，容易陷入某几个变量改来改去，嗯，就把时间耗在修改这几个变量上了。
看过《机器学习实战》和最原始的Platt的论文后，进行了代码上的重新梳理，主要变化有：
* 提前判断，如果有些对alpha的修改是没有意义的，就不要修改
* 提前将kernel矩阵算出来，节约计算时间

最终的准确率和sklearn的svm还是相差不多的，调调参也是可以达到的，但是计算时间上还是有很大差距，就linearSVM就差了10倍。
看到一篇公众号里关于这个计算时间如何优化

例如：
* 在优化E的时候，对E的变化是线性的，所以并不需要再重新计算u(i)
* 核函数矩阵是对称的，故只需要存储一半

之后有机会再继续优化～

个人总结的SVM的推导原理博客链接,忘了可以再看看……
![这次一定要弄懂-SVM-1- Hard Margin SVM的原问题推导](https://blog.csdn.net/weixin_44264662/article/details/97151205)
![这次一定要弄懂-SVM-2-Hard Margin SVM的原问题转换为拉格朗日对偶问题](https://blog.csdn.net/weixin_44264662/article/details/97614757)
![这次一定要弄懂-SVM-3-Hard Margin SVM的对偶问题的求解（SMO算法）](https://blog.csdn.net/weixin_44264662/article/details/97673000)
![这次一定要弄懂-SVM-4-总结Hard Margin SVM的求解过程，并用python实现](https://blog.csdn.net/weixin_44264662/article/details/97900309)
![这次一定要弄懂-SVM-5-推广到soft margin svm和非线性的svm](https://blog.csdn.net/weixin_44264662/article/details/97952385)
