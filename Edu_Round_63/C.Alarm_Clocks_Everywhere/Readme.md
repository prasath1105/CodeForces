### C. Alarm Clocks Everywhere

https://codeforces.com/contest/1155/problem/C

很明显，我们需要以event[0]为起始时间。这个闹钟间隔p需要足够小，使得每两个事件之间的时间间隔gap需要是这个p的整数倍。

所以，我们所需求的就是这些事件时间间隔gap1,gap2,...,gap_n的最大公约数GCD。

最后检查这些periods里面是否存在甚至是GCD的约数的，有的话就是它了。

