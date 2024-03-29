实现了三种决策树的建模和绘制，  
自己实现的CART分类树与sklearn中的CART树对比，在特征较少时，具有近似的效果。

# 决策树简介：
* 非参数学习算法
* 可以解决分类问题和回归问题
* 天然可以解决多分类问题
* 具有非常好的可解释性
* 在机器学习领域，决策树更重要的一个应用是使用集成学习的方式，创建随机森林的算法。  随机森林的算法可以得到非常好的学习结果。

# 决策树的局限性：
1. 生成的边界 横平竖直，所以数据如果有一点偏斜，决策树得到的决策边界可能就不能很好的反馈数据的分布情况。
2. 作为非参数学习算法，对个别数据样本点是非常敏感的。

# 决策树的关键：
* 每个节点在哪个维度做划分
* 某个维度在哪个值做划分
* 才能使得划分后，信息熵降低？

# ID3、C4.5、CART树之间的关系
ID3 (Iterative Dichotomiser 3)  
构建的树是多分类的样子，按照某一列进行切分。  
局限性：
* 分支度越高（分类水平越多）的离散变量往往子节点的总信息熵会更小，ID3是按照某一列进行切分，有一些列的分类可能不会对我们需要的结果有足够好的指示。极端情况下取ID作为切分字段，每个分类的纯度都是100%，但这样的分类方式是没有效益的
* 不能直接处理连续型变量，若要使用，则需要对连续性变量进行离散化
* 对缺失值较为敏感，使用ID3之前要提前对缺失值进行处理
* 没有剪枝的设置，容易导致过拟合。

C4.5 
在ID3的基础上进行改进：
1. 使用信息增益率（Gain Ratio）作为选取切分字段的参考指标
$$Gain Ratio = \frac{Information Gain}{Information Value}$$
其中$$Information Values = -\sum\limits_{i=1}^k P(v_i)log_2P(v_i)$$
$v_i$为子节点中样本量占父节点样本量的比例
我们选择 信息增益率最大的那一列，本质是信息增益最大，分支度又较小的列（也就是纯度提升很快，但又不是靠着把类别分 特别细 来提升 那些特征）

2. 添加连续变量处理手段
	如果输入特征字段是连续性变量，则有下列步骤：
	1. 算法首先对这一列数从小到大排序
	2. 选取相邻的两个数的中间数作为切分数据集的备选点，此时针对连续变量的处理并非将其转化为一个拥有N-1个分类水平的分类变量，而是将其转化为N-1个二分方案。

当连续变量的某中间点参与到 决策树的二分过程中，往往代表该点对最终分类结果有较大影响，也为我们对连续变量的分箱压缩提供了指导性意见。也这是决策树的最常见用途之一，指导模型分箱。

CART树
在C4.5的基础上再进一步改进  
现在被大量使用的是C4.5改进的CART树，CART树本质上和C4.5区别不大，只不过CART树的所有层都是二叉树，也就是每层只有两个分支。

# 决策树对比KNN算法：
对于KNN，我们假设，每一个特征对于我们的推断的重要性是一样的，这也是KNN最大的缺陷。  
而决策树天生就认为每个特征对于推断的重要性是不一样的，而CART则进一步认为，每个特征下的每个分类对于推断的重要性也是不一样的。
