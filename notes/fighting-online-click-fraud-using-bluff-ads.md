## [Fighting Online Click-Fraud Using Bluff Ads](https://arxiv.org/pdf/1002.2353.pdf)

很短的一篇paper, 只有4页, 但是引用次数很多, 70多次, 主要还是因为思路的创造性.

Bluff Ad是专门设计可以被机器或者没有经过足够训练的作弊人力检测和点击的广告. 一种可能是广告的展示文本不相关, 另一种形式是定向到不相关的人群. 无论哪种形式, 正常的用户一般都不会去点击.

然后作者列举了4种作弊的方式, 并且介绍了bluff ad是怎么工作的. 4种作弊方式分别是Profiling the customer, Publisher fraud, Attacks on advertisers, 以及Attacks on publisher. Bluff/real比例高代表作弊可能高. 这里没有任何公式, 都是定性的文字描述.

作者做了很简单的一组实验, 分成一个正常的广告, 和三组bluff ads, 在Google Adword上投放, 以实际数据表明相对正常广告来说, bluff ad的点击率确实很低. 但是这个实验太过简单, 并且数据量很小, 也没有排除其他原因的干扰, 比如其中有两组广告根本没有获得曝光机会, 也就无从对比点击率.

总的来说, 是一篇很有创新的paper, 但是内容有限. 而且根据对作者的检索, 也没有发现后续有更深入的研究成果.