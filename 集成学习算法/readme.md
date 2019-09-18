# 集成学习算法
## 主要内容
* 实现基于决策树桩的Adaboost算法
* 实现损失函数为ls的GBDT算法
* 实现基于l2正则项的XGBoost算法

* 使用sklearn中的VotingClassifier和BaggingClassifier
* 使用sklearn中xgboostAPI和xgboost开源库
* 使用sklearn中的randomforest

* 案例：使用randomforest填补缺失值
* 案例：基于随机森林分类器的偏差方差调参

## 理论部分概述
### 常见的集成算法之间的关系
随机森林：Bagging + 决策树  
提升树：AdaBoost + 决策树  
GBDT：Gradient Boosting + 决策树   
XGBboost：是在GBDT上的改进  
