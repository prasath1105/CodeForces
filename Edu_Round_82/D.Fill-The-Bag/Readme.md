### D.Fill-The-Bag

题意描述：给一系列盒子box，每个box[i]都是2的次幂（可能相同）。现在要求取其中的一些盒子，使得其总和恰好为n。为了完成这个目的，你可以将部分盒子拆分成两个一半大小的，或者持续拆分下去直至是1. 问最少需要多少次拆分能够完成任务。

我们先考虑如果没有box的限制，想要恰好装满n最少需要多少个盒子？其实只要将n做二进制分解，看有几个bit上是1。第i个bit位是1，那么说明只需要一个2^i的盒子即可。所以我们必然会把所有的box按照i的幂次分类统计，放入power[i]中。

我们考虑如果n的第i个bit位是0，那么皆大欢喜，似乎我们不需要做什么。但是不然，假设这个时候box里面有4个2^i，不用岂不是可惜了？这4个盒子可以冲抵2个2^(i+1)的盒子来用。因此我们需要```power[i+1]+=power[i]/2```.

然后我们考虑如果n的第i个bit位是1，那么我们就看power[i]是否已经存在。1. 如果已经存在，自然也不需要任何拆分的操作，直接拿来用即可。注意如果剩下来若干个2^i的盒子，同样也要把它们数量折半计入2^(i+1)的盒子数。2. 如果power[i]一个都没有，那么我们就需要向前借位，将power[i+1]的个数减一（也就是做一次拆分），来提供所需要的这一个2^i。如果power[i+1]也没有，那么就要不断往前寻找（同时也不断拆分）直至找到一个高位的power[j]可以拆分为止。

那么是否一定能找到高位的j来提供拆分呢？其实我们可以预先做一个判断。只要盒子的总容量大于n，那么就一定会有解，因为只要把所有的盒子都拆分为1的容量，最终总能恰好装n。所以```sum(box)>=n```的时候只管往前借位（直到借到为止），否则可以直接输出-1.
