# 动态规划问题



### 最长上升子序列

![](/home/xinyue/Notes/pic/1.动态规划/最长上升子序列.png)



##### O(n^2) 方法

dp(i, j) = k

- 有 i 个数字，以第 j 位为结尾的长度


$$
dp(i, j) =  \begin{cases}
dp(i - 1, j) \\
max(dp(i, k) + 1)\\
\end{cases}
$$
