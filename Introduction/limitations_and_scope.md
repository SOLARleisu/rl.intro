# 1.4 限制与使用领域

从前面的讨论中，应该清楚增强学习严重依赖**状态（state）**的概念——状态作为策略和价值函数的输入，也作为模型的输入和输出。在非正式的情况下，我们可以把状态视为向代理传达在某种特定时间下”环境如何”的一种信号。我们在这里使用的状态的正式定义由第3章中介绍的马尔可夫决策过程的框架给出。然而，更一般地说，我们鼓励读者遵循非正式的含义，把状态看作是代理获得的任何有关其环境的信息。例如，我们假设状态信号是由一些预处理系统产生的，这些预处理系统名义上也属于代理的环境的一部分。本书不涉及构建，改变或学习状态信号的问题。我们采取这种做法不是因为我们认为状态表示不重要，而是为了充分关注决策问题。换句话说，我们主要关注的不是设计状态信号，而是在任何状态信号输入后，应该采取什么样的动作。（我们在第17.3节的最后一章中对于状态设计和构造做了简单的介绍。）

本书中我们所考虑的大多数强化学习方法都是围绕着价值函数构建的，但是这并不是解决增强学习问题所严格必须的。例如，遗传算法，遗传程序设计，模拟退火和其他优化方法等方法已经被用来处理强化学习问题，而没有采用价值函数。这些方法评估了许多非学习者的“终生”行为，每个非学习者使用不同的策略与环境进行交互，最后选择那些能够获得最大奖励的非学习者。我们把这些进化方法称为进化方法，因为它们的操作与生物进化产生具有熟练行为的生物体的方式类似，即使这些生物个体在它们的一生中并没有进行学习。如果策略空间足够小，或者可以结构化，那么很容易找到好的策略——或者如果有很多时间可以用于搜索——那么这种革命性的方法就可以是有效的。另外，演化方法在代理不能感知其环境的完整状态的问题上具有优势。

我们的重点是强化学习方法，与环境进行交互学习，这是进化方法所不具备的。在许多情况下，能够利用个体行为相互作用细节的方法比进化方法更有效。进化方法忽略了强化学习问题的许多有用的结构：他们不使用这样一个事实，他们正在寻找的策略是从状态到动作的函数;他们不会注意到一个个体在一生中经历了哪个状态，或者选择了哪个动作。在某些情况下，这些信息可能会引起误导（例如，当状态被误解时），但是更多的情况下，这些信息能够帮助进行更有效地搜索。虽然进化和学习有许多共同的特征，并且自然而然地联合起来，但是我们并不认为进化方法自身特别适合于解决加强学习的问题，因此我们在本书中没有涉及它们。

但是，我们确实包含了一些方法，像进化方法一样，不会引入价值函数。这些方法在由数值参数集合定义的策略空间中进行搜索。他们估计参数调整的方向，以便最快地改善策略的表现。然而，与进化方法不同的是，当代理与环境进行交互时，这些方法会产生估计值，以便利用个体行为交互的细节。像这样的方法在许多问题中被证明是有用的，而一些最简单的强化学习方法属于这一类（见第13章）。但是，最后，这种类型的最好的方法往往包含某种形式的价值函数。