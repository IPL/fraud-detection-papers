# Fraud Detection Papers

## Report
* [The Lane’s Gifts v. Google Report](/papers/Alexandr_Tuzhilin_Report.pdf) by Alexander Tuzhilin. 2006.

 	这是由Alexander Tuzhilin主导的对Google的无效点击检测系统的独立评估, 反映了当时(2006年)的Google反作弊系统的状态, 以及发展进程. 几个有意思的地方:
	1. 人员组成. Click Quality团队的工程部分有10多个人, Spam Operations有20多个人, 还可以获得很多其他团队的支持.
	2. Google主要使用Anomaly-based和Rule-based方法检测无效点击, 也会少量使用Classifier-based方法.
	3. Google使用Prevention和Detection达到目标. Detection有下列几个维度: Online filtering vs. Offline monitoring and analysis, Automated vs. Manual detection, Proactive vs. Reactive detection, Where were invalid clicks made.
	4. 检测阶段主要有: Pre-filtering, Online Filtering, Post-filtering.
	5. Google分析在线未检测出而离线检测出的无效点击, 开发新的filter或修正已有的filter.
	6. Click Quality团队使用非直接的证据证明系统确实在工作: 新添加的filter仅识别少量新的无效点击, 以及离线分析方法相对仅识别少量新的无效点击.
	7. 大多数的filter都非常简单. 系统工作良好的原因可能是: 多个filter组合, 部分filter比较复杂, 大多数攻击非常简单, 无效点击的长尾特性(这里有主观猜测).
	8. Google的filter中主要缺少: Deployment of Data Mining Methods, Using the Conversion Data in Filters, Developing More Advanced Types of Filters.
	9. 除了少数例外, 所有的filter和对应的阈值都是工程师引入和确定的, 目的是为了保护广告主, 未受到finance部门的影响.
	10. Google的无效点击检测的发展历程: 
		1. The Early Days (February 2002 – Summer 2003): AdWords投入使用, 当时仅有三条filter, 只能过滤初级的无效点击.
		2. The Formation Stage (Summer 2003 – Fall 2005): AdSense投入使用, Click Quality组建, 增加了三条filter, 除此之外, 开始整体架构开发. 无效点击问题在2005年年底"under control".
		3. The Consolidation Stage (Fall 2005 – present): 调优现有方法, 开发下一代filter, 为更复杂的攻击做好准备.

	报告反映的是2006年的状况, 相信现在Google的无效点击检测系统已经非常完善, 不过这篇报告还是有一定的参考价值.

* [Click Fraud Detection: Adversarial Pattern Recognition over 5 Years at Microsoft](/papers/ClickQualitySystems54_LNCSFormat_clean.pdf) by Brendan Kitts et al. Real World Data Mining Applications 2015.

## Bluff Ads
* [Fighting Online Click-Fraud Using Bluff Ads](/papers/10.1.1.471.8973.pdf) by Hamed Haddadi. ACM Computer Communication Review 2010.
* [Measuring and Fingerprinting Click-Spam in Ad Networks](/papers/sigcomm12-clickspam.pdf) by Vacha Dave et al. ACM SIGCOMM Conference on Data Communication 2012.

## Mobile Apps
* [DECAF: Detecting and Characterizing Ad Fraud in Mobile Apps](/papers/10.1.1.704.3668.pdf) by Bin Liu et al. Proc. 11th USENIX Conf. Netw. Syst. Des. Implementation 2014.
* [MAdFraud: Investigating Ad Fraud in Android Applications](/papers/mobisys2014.pdf) by Jonathan Crussell et al. Proc. 12th International Conference on Mobile Systems Applications and Services (MobiSys'14) 2014.

## Competition
* [Detecting Click Fraud in Online Advertising: A Data Mining Approach](/papers/JMLR'13.pdf) by Richard Oentaryo et al. JMLR 2014.
* [Feature Engineering for Click Fraud Detection](http://research.larc.smu.edu.sg/fdma2012/doc/FirstWinner-Starrystarrynight-Paper.pdf) by Clifton Phua et al. International Workshop on Fraud Detection in Mobile Advertising (FDMA) 2012.
* [A Novel Approach Based on Ensemble Learning for Fraud Detection in Mobile Advertising](http://research.larc.smu.edu.sg/fdma2012/doc/SecondWinner-TeamMasdar-Paper.pdf) by Kasun S. Perera et al. International Workshop on Fraud Detection in Mobile Advertising (FDMA) 2012.

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

* [Hybrid Models for Click Fraud Detection in Mobile Advertising](http://research.larc.smu.edu.sg/fdma2012/doc/ThirdWinner-DB2-Paper.pdf) by Chen Wei et al. International Workshop on Fraud Detection in Mobile Advertising (FDMA) 2012.
* [Random Forests for the Detection of Click Fraud in Online Mobile Advertising](http://research.larc.smu.edu.sg/fdma2012/doc/FirstRunnerUp-Tea-Paper.pdf) by Daniel Berrar et al. International Workshop on Fraud Detection in Mobile Advertising (FDMA) 2012.
* [Hierarchical Committee Machines for Fraud Detection in Mobile Advertising](http://research.larc.smu.edu.sg/fdma2012/doc/SecondRunnerUp-Kites-Paper.pdf) by S. Shivashankar et al. International Workshop on Fraud Detection in Mobile Advertising (FDMA) 2012.