### A.Maximal-Binary-Matrix

考虑到(i,j)和(j,i)必然是同时填入的，所以我们在填充的时候不用严格地“先逐列再逐行”遍历，而是始终在右上角的区域进行遍历就行。
```cpp
if (j==N)
{
  i += 1;
  j = i;
}
```
即每填充完一行，自动跳转到下一行的对角线位置。每处理一个对角线位置，count自减1；每处理一个非对角线位置，count自减2（即同时对角线对称的两处位置）。

另外特别注意，如果count只剩下一个，那么接下来一定要填充的是下一行的对角线位置！
