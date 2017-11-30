1. 特征抽取: 借鉴了Google AdSense反作弊的一些特征, 同时也参考了传统反作弊系统的一些研究成果, 因为移动广告反作弊还处于新兴阶段.
	1. 时间特征: 作弊方经常使用多种技巧隐藏自己的活动, 例如生成非常稀疏的点击序列, 改变IP地址, 从不同国家的计算机发出点击等等; 还有一些是坚持使用传统方法, 即只在给定时间间隔内产生最大点击次数. 反作弊系统需要识别出这两种方式. 作者选择1 min, 5 min, 1 hours, 3hours and 6 hours的时间间隔, 来统计他们的点击次数, 并综合所有的时间间隔的数据, 统计平均值, 最大值, 方差以及偏度作为特征.
	2. IP特征: 构造了最大同IP点击数, IP总数, 平均每IP点击数, IP点击的熵, IP点击的方差等特征.
	3. 对Agent, Country, Campaign ID等其他属性也做了类似的工作来抽取特征.
	4. 最终一共生成了41个特征, 完整列表在http://www.dnagroup.org/PDF/FDMA12_TeamMasdar_AppendixA.pdf.
2. 特征选择: 作者使用了Principal Component Analysis (PCA), Common Spatial Patterns (CSP), 以及wrapper subset evaluation做特征选择. 经过对比测试, 第三种方法相对前两种要好. (但是实际上特征选择没有真正发挥作用, 后面有讲到.)
3. 方法使用: 作者尝试了决策树, 回归树, 神经网络, 还有SVM. 每个方法都使用了不同的learning algorithm. 经过分析, 发现决策树算法是最好的. (决策树的结果也最容易解释, 正好适用于反作弊系统)
4. 样本数据是高度倾斜的, 其中包括2.336%的作弊者, 2.596%的不确定和95.068%的未作弊数据. 为了应对数据倾斜, 使用了Resampling和SMOTE. 具体结果在后面有讲到.
5. 作者使用了Bagging, Metacost, random subspace, 以及logiboost来进行集成学习.
6. 作者最终使用了6个模型取平均, 包括Bagging with J48, Bagging with Reptree, Bagging with Random Forest, Metacost with J48, Logiboost with J48, Random subspace with J48.
7. 结果分析
	1. 特征选择: 特征选择目的是避免over fitting, 但是经过对比, 发现经过特征选择的结果要比不做特征选择稍低一些, 这个现象在各种算法中都类似. 一个可能的解释是, 决策树算法本身就包含pruning步骤, 这可以算是一种特征选择, 因此额外增加特征选择环节的收益很有限, 甚至还会有降低.
	2. 采样: 因为数据高度倾斜, 所以作者尝试了Resampling and SMOTE. 两种方法在训练集表现都很好, 但是在验证集表现都很差. 最终不做采样要比做了采样的结果好20%.
	3. 2-class/3-class classifications: 作者对比了仅包含两个类别(Observation转化为OK vs Observation转化为Fraud), 以及保持三种类别的标注. 三种结果做对比, Observation转化为OK的效果是最好的.
	4. 多种算法做组合的结果比单一算法要好, 最终选择了六种算法的组合.
8. 结论: 90%的作弊者在各个时间间隔的点击量都比较小, 并且方差和斜度也非常低, 这种方式虽然让他们隐藏在合法用户中, 但是这种系统性的点击也可以作为一个标识. 对于Agent属性, 作者观察到在作弊媒体上的方差非常大, 表明很多作弊媒体使用大量的agent来模拟正常用户.
