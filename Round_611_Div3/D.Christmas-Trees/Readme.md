### D.Christmas-Trees

题意是说给了一系列树的坐标。要求安排Ｎ个人的位置（不能重叠），希望最小化所有人与树的距离之和。

注意本题的objective function。要求是所有di的和的最小值，而不是最小化所有di的最大值。因此二分搜索法并不能确定这个数。

朴素的贪心法可以解这道题。思想是multi source BFS. 对于每棵树，我们都同时向两边扩展一步；然后第二回合从队列中取出元素，再往外扩展一步：注意这次是只能单向扩展。那么如何确定该往哪个方向扩展（避免重复）呢？我们需要使用一个hash表，记录一下x-1或者x+1是否曾经被扩展过，同时读取x对应（离最近的树）的距离。每扩展一步，说明就有一个新位置x-1（或者x+1)可以放一个人，并且这个新位置距离最近的树的距离就是```Map[x]+1```。不断BFS直到我们探索到m个新位置为止。
