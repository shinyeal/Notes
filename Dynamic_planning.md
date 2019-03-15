# 动态规划问题



### 最长上升子序列

![](/home/xinyue/Notes/pic/1.动态规划/最长上升子序列.png)



##### O(n^2) 方法

dp(i, j) = k

- 有 i 个数字，以第 j 位为结尾的长度

$$
dp(i, j) =  \begin{cases}
dp(i - 1, j) [j != i] \\
max(dp(i, k) + 1)  [j == i]\\
\end{cases}
$$

可以看出 j 在这里并没有太大的用，可以对问题进行降维处理

```c
#include<stdio.h>
#define MAX 1000
int num[MAX + 5];
int dp[MAX+ 5];

int main() {
    int n, ans = 1;
    scanf("%d", &n);
    for(int i = 0; i < n; i++) {
        scanf("%d", &num[i]);
    }
    dp[0] = 1;
    for(int i = 0; i < n; i++) {
        //当前本身就是一个长度
        dp[i] = 1;
        for(int j = i - 1; j >= 0; j--) {
            if(num[j] > num[i]) continue;
            if(dp[j] + 1 > dp[i]) dp[i] = dp[j] + 1;
        }
        if(dp[i] > ans) ans = dp[i];
    }
    printf("%d\n", ans);
    return 0;
}
```



##### O(nlogn) 方法

- 有 i 个数字，以第 i 个数字作为结尾的长度(val[j] < val[i] , j < i)

$$
dp(i) = max(dp(j) + 1)
$$

```c
#include <stdio.h>
#include <string.h>
#define MAX 100000
int arr[MAX + 5];
int dp[MAX + 5];
int len[MAX + 5];

int binary_serch(int *num, int n, int x) {
    int head = 0, tail = n, mid;
    while(head < tail) {
        mid = (head + tail) >> 1;
        if(num[mid] >= x) tail = mid;
        else head = mid + 1;
    }
    return head;
}

int main() {
    memset(len, 0x3f, sizeof(len));
    int n, ans = 1;
    scanf("%d", &n);
    for(int i = 0; i < n; i++) {
        scanf("%d", arr[i]);
    }
    dp[0] = 1;
    len[dp[0]] = arr[0];
    len[0] = -1;
    for(int i = 1; i < n; i++) {
        dp[i] = binary_serch(len, ans + 1, arr[i]);
        len[dp[i]] == arr[i];
        if(dp[i] > ans) ans = dp[i];
    }
    printf("%d\n", ans);
    return 0;
}
```



- 相关博客：https://www.cnblogs.com/GodA/p/5180560.html



### 切割回文

方法一：

















###  和为0的最长子串长度

>  一个一维维数组中只有1和-1，实现程序，求和为0的最长子串长度，并在注释中给出时间和空间复杂度。

#### 思路：

```
核心思路 dpi表示从array[i]一直加到array[j]的和
递推式：dpi = dpi+1 + array[i] + array[j];
判定：if(dpi == 0) max = max(max, j-1+1);
```



