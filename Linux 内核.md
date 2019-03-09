## Linux 内核



阅读linux内核过相关malloc实现策略，

实现过malloc相关功能

- 建立双向链表
- 操作系统实现malloc 
  - prev：合并操作



#### /kernel/vsprintf.c

- goto repeat:  回到repeat 
- `-` ：左对齐
- 153 line : 位宽 初始化为-1
- 230 line : x,16进制（小写字母）
- 239: 判断整型是有符号整型还是无符号整型



#### /lib/malloc.c





#### /include/linux/string.h

用汇编语言实现的，

- 265 line: 汇编语言实现for循环，

---------



- 数值信息才是计算机里的本质信息



- 将人的脸部特征参数提取，用tansorflow在pc端搭建结构
- 特征判断：余弦距离

- 训练模型 放进机器里，机器判定
- tansorflow lite  提取人脸特征进行匹配





## 面试算法



- 动态规划问题：本质就是递推问题
- 符号推导



- 定义递推状态（符号说明）

  f(n) = k，n 是状态，就是第几种可能，k是答案（方法总数）

  

  

  #### 爬楼梯

  上到第n层楼的方法总数是k

- f(n) = f(n - 3) + f(n - 2)





墙壁涂色

- 首尾记录下来，求第一块是i,zui