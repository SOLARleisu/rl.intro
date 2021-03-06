# 2.2 行动-价值方法

首先我们更加深入的来观察一些用于估计行动价值以及如何利用这些估计来做决策的简单方法。回想一个行动的真实价值就是这一行动被选择后的平均奖励。一个自然的方式就是通过实际获得奖励的平均值来估计：

Q_t(a) = \frac{行动a在t时刻前的奖励总和} {行动a在t时刻前被执行的次数} =
$$
\frac{\sum_{i=1}^{t-1}{R_i \cdot \mathbb{1}_{A_i=a}}}{\sum_{t=1}^{t-1}{\mathbb{1}_{A_i=a}}} 
$$

其中变量$$ \mathbb{1}_{predicate}$$表示如果$$predicate$$为真则变量为1，否则为0。如果分母为0，那么我们会定义 $$Q_t(a)$$ 为一个默认值，比如说0。只要分母的趋近无穷大，根据大树定律， $$ Q_t(a) $$会收敛到 $$q_*(a)$$. 这一方法叫做 **采样平均** 法，因为是通过相应奖励的采样平均来估计行动的价值。当然，这只是其中的一种估计方法，而且不一定是最好的一个。不过，现在就先用这个简单的估计方法来说明如何将估计的结果用来选择行动。

最简单的行动选择的规则就是选估计的价值最高的那个，也就是之前一节所说的贪婪行动。如果有多于一个的贪婪行动，可以用一种比较简单的方法来选择其中一个，比如说随机选择。**贪婪**行动的选择法可以记做：

$$
A_t = \arg\max_a Q_t(a),
$$

其中 $$\arg\max_a$$表示$$a$$是可以最大化后续表达式的某一行动（如果有多个可能可以用一些简单的方法来处理）。贪婪行动的选择永远都是开发现有知识来最大化即时的奖励，而不会尝试那些比较不好的行动来确认是否这些行动会比当前贪婪行动的结果更好。一种简单的改进就是大部分情况下贪婪，而每过一段时间，比如说以$$\epsilon$$的概率，从所有可能行动中随机选择一个而不考虑当前的行动价值估计。这类方法称为近贪婪行动选择规则，或者是 **$$\epsilon$$-greedy**方法。这类方法的优点在于随着时间的积累，每个行动都会被采样无限次，就保证了所有的 $$Q_t(a)$$都会收敛到$$q_*(a)$$。所以最终最优行动选择的概率会收敛到大于 $$1-\epsilon$$，基本接近确定了。当然，这些只是渐进保证，而非这类方法的实际效果。

*练习 2.1* 在 $$\epsilon$$-greedy行动选择中，如果有两种行动，而且$$\epsilon=0.5$$，贪婪行动被选择的概率是多少？

*练习 2.2* **赌博机例子** 一个多臂赌博机问题中，有 k=4 种行动，记做 1,2,3,4。如果使用$$\epsilon$$-greedy行动选择法，采样平均的行动-价值估计，对于所有的行动a，最初的估计都为Q_1(a)=0。如果最初的行动和奖励的序列是 A_1=1, R_1=1,A_2=2,R_2=1,A_3=2, R_3=2, A_4=2, R_4=2, A_5=3, R_5=0。这些步骤中，有些是$$\epsilon$$概率引起的随机选择。那么，这些步骤中，哪些肯定是随机选择？哪些可能是？




