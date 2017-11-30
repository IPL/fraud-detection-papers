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