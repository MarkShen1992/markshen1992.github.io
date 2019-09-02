## 第一节

### 极客时间算法课笔记

找男女朋友

工作任务安排

扑克游戏（德州）

比特币，区块链

### 内功：数据结构与算法 设计模式

### 编程语言：Java, Python etc.

### 国内互联网公司

- 快手， 头条，抖音，Airbnb Beijing, Snapchat深圳
- 微信，地平线机器人，第四范式，小米，Musically，Face++
- BAT，微软，Google，小红书，饿了么，网易等等
- 新美大，滴滴

### 硅谷公司面试

Phone Interview

<http://collabedit.com/>

<https://coderpad.io/> (要翻墙)

<https://leetcode.com/>

### 硅谷工作

留学 F1

外企中国到总部 L1

直接硅谷公司 H-1B

---

每条路径的难易

准备周期，时间节点

资金预算

### 有趣且实用的

![](D:\github\markshen1992.github.io\document\algorithm\link.png)



## 第二节

### 《异类—不一样的成功启示录》马尔科姆·格拉德威尔

10000小时定律

- Chunk it up （切碎知识点）
  - 知识树

![](D:\github\markshen1992.github.io\document\algorithm\datastructure_summary.png)

![](D:\github\markshen1992.github.io\document\algorithm\datastructure.png)



- Deliberate Practice （刻意练习）
- Feedback （反馈）
  - 及时反馈
  - 主动性反馈
    - 高手代码（github, LeetCode, etc.）
    - 第一视角直播
  - 被动式反馈 （高手给你指点）
    - code review
    - 教练看你打，给你反馈

### 切题四件套

1. 审题
2. 可能解法， 对比时/空间夫大度，加强，不断优化
3. 多写
4. 测试cases



## 第三节

![](D:\github\markshen1992.github.io\document\algorithm\summary_datastructure.png)

### 时间复杂度，空间复杂度

![](D:\github\markshen1992.github.io\document\algorithm\shikongfuzadu.png)

### 代码例子

$$
O(1)
$$

```java
int n=1000;
System.out.println(n);
```

$$
O(N)
$$

```java
for (int i=0; i<n; i++) {
    System.out.println(i);
}
```

$$
O(N^2)
$$

```java
for (int i=0; i<n; i++) {
	for (int j=0; j<n; j++) {
        System.out.println(i);
	}
}
```

$$
O(log(N))
$$

```java
for (int i=0; i<n; i=i*2) {
    System.out.println("Hey - I'm busy looing at:" + i);
}
```

$$
O(k^n)
$$

```java
for (int i=0; i<Math.pow(2, n); i++) {
    System.out.println("Hey - I'm busy looing at:" + i);
}
```

$$
O(N!)
$$

```java
for (int i=0; i<Math.pow(2, n); i++) {
    System.out.println("Hey - I'm busy looing at:" + i);
}
```

![](D:\github\markshen1992.github.io\document\algorithm\lecture3_0100.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture3_0200.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture3_0300.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture3_0400.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture3_0500.png)



## 第四节

### Deliberate Practicing

- 坚持，刻意练习
- 练习缺陷，弱的地方
- 不舒服，不爽，枯燥

### 练习网站

[leetcode](<https://leetcode.com/>)

leetcode支持Google, facebook, linkedin, github登录



## 第五节

### 数组，链表

![](D:\github\markshen1992.github.io\document\algorithm\Lecture4_0100.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture4_0200.png)

### Array

Access: O(1)

Insert, Delete: 平均O(n)



### Linked List

![](D:\github\markshen1992.github.io\document\algorithm\Lecture4_0300.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture4_0400.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture4_0500.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture4_0600.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture4_0700.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture4_0800.png)



## 第六节

### 数组与链表习题

![](D:\github\markshen1992.github.io\document\algorithm\Lecture5_0100.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture6_0100.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture6_0200.png)

链表是否有环

1. 硬做，尾节点为null
2. Set数据结构，存节点地址，直接判重
3. 两个指针，一个一次走一步，一个一次走两步，有环会有相遇。**快慢指针**。

## 第七节 栈，队列

Stack: First In Last Out (FILO)

​	Array or LinkedList

Queue: First In First Out (FIFO)

​	Array or Doubly Linked List

![](D:\github\markshen1992.github.io\document\algorithm\Lecture6_0300.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture6_0400.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture6_0500.png)

[算法性能比对](<http://www.bigocheatsheet.com/>)

### 题目实战

1. String，大中小括号是否合法？

   (){}[] 合法

   {)} 不合法

![](D:\github\markshen1992.github.io\document\algorithm\Lecture7_0100.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture7_0200.png)

leetcode: 232, 255

用Stack实现Queue的效果

用两个Stack来实现，输入栈，输出栈

## 第八节 优先队列

### 特性

   正常进，按优先级出

### 实现机制

1. Heap(Binary, Binomial, Fibonacci)

2. Binary Search Tree

![](D:\github\markshen1992.github.io\document\algorithm\Lecture8_0100.png)

二叉堆调整

![](D:\github\markshen1992.github.io\document\algorithm\Lecture8_0200.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture8_0300.png)

学会用Leetcode，wikipedia

### 题目实战

leetcode 703

![](D:\github\markshen1992.github.io\document\algorithm\Lecture8_0400.png)

leetcode 239

![](D:\github\markshen1992.github.io\document\algorithm\Lecture8_0500.png)

## 第九节 Hash table

1. HashTable Hash Function Collisions
2. Map vs Set
3. HashMap, HashSet, TreeMap, TreeSet
4. 查询和计数

![](D:\github\markshen1992.github.io\document\algorithm\Lecture9_0100.png)

### 哈希碰撞问题

![](D:\github\markshen1992.github.io\document\algorithm\Lecture9_0200.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture9_0300.png)

对速度要求高的时候，用HashMap, HashSet

如果要有序的结构，要使用TreeMap, TreeSet

### 题目实战

- leetcode 242 变位词
- leetcode 1 tow sum
- leetcode 15, 18 ; 3 sum, 4 sum



## 第十节 Tree & Graph

### 回顾链表内容

### 树

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_0100.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_0200.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_0300.png)

LinkedList 就是特殊化的树

Tree就是特殊化的图

链表 <-> 树 <-> 图

```java
public class TreeNode {
    public int val;
    public TreeNode left, right;
    public TreeNode(int val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}
```

### 二叉搜索树

是指一棵**空树**或者具有下列性质的二叉树：

**左子树**上所有节点的值据小于它的根节点的值；

**右子树**上所有节点的值据大于它的根节点的值；

Recursively, 左右子树也分别是二叉查找树。

平衡二叉搜索树，红黑树

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_0400.png)

### 题目实战

leetcode 98，235，236

### 二叉树遍历

- Pre order：根 左 右
- **In order**：左 根 右
- Post order：左 右 根

实际中用的非常少。

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_0500.png)

上图前中后序遍历结果如下：

前：A B D E C F G

中：D B E A F C G

后：D E B F G C A

**二叉搜索树的中序遍历结果是有序的数组。**

### 递归和分治

- Recursion

  1. 从前有座山
  2. 山里有个庙
  3. 庙里有个老和尚在讲故事

  《盗梦空间》计算阶乘，斐波那契数列

  计算n!.

  ![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_0600.png)

- Divide & Conquer

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_0700.jpg)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_0800.jpg)

### 题目实战

- leetcode 50, 169

### 贪心算法

在对问题求解时，总是做出在当前看来是最好的选择。

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_0900.png)

### 适用场景

问题能够分解成子问题来解决，子问题的最优解能递推到最终问题的最优解，这种子问题最优解成为最优子结构。

它与动态规划的不同在于它对每个子问题的解决方案都做出选择，不能回退。动态规划则会保存以前的运算结果，并根据以前的运算结果对当前进行选择，有回退功能。

### 题目实战

leetcode 122

### 广度优先搜索

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_1000.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_1100.png)

用**队列**数据结构来解决，用队列来存每层的数据。不仅适用于树，也适用于图，状态机。访问过的节点要被标记。



### 深度优先搜索

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_1200.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_1300.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_1400.png)

DFS-递归写法

### 习题实战

leetcode 102, 104, 111, 22

### 剪枝

搜索中用到的。

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_1500.png)

解决问题：

1. 现实中很多搜索问题，状态集合非常大。
2. 很多在分叉的时候，已经得到优先级的判断。优胜劣汰的判断之后。

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_1600.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_1700.png)

搜索 + 剪枝

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_1800.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_1900.png)

### 题目实战

leetcode 51, 52 N queens

leetcode 36, 37 数独



### 二分查找

特点

1. Sorted(单调递增，单调递减)
2. Bounded(存在上下界)
3. Accessible by index(可通过索引访问)

适用数据结构: 数组

### 题目实战

leetcode 69



### 字典树

Trie的数据结构

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_2000.png)

Trie的核心思想

空间换时间，利用字符串的公共前缀来降低查询时间的开销以达到提高效率的目的。

Trie的基本性质

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_2100.png)

### 习题实战

leetcode 208

leetcode 79, 212



### 位运算

介绍

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_2200.png)

常用操作

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_2300.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_2400.png)

应用

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_2500.png)

### 题目实战

leetcode 191, 231, 338, 52



### 动态规划

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_2600.png)

### 斐波那契数列

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_2700.png)

### DP vs 回溯 vs 贪心

回溯（递归）——重复计算

贪心——永远局部最优

DP——记录局部最优子结构/多种记录值

### 习题实战

leetcode 70, 120, 152, 121, 122, 123, 309, 188, 714, 300, 322, 72



### 并查集

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_2800.png)

#### 现实中要解决的问题

老大，小弟之间的关系，组织结构架构

帮派识别

两种优化方式

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_2900.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_3000.png)

### 题目实战

leetcode 200



### LRU Cache

记忆

钱包-储物柜

代码模块（背下来）

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_3100.png)

<https://www.sqlpassion.at/archive/2018/01/06/understanding-the-meltdown-exploit-in-my-own-simple-words/> （需翻墙）

<https://www.sqlpassion.at/blog/>

1. Least Recent Used(最近最少使用)
2. Double LinkedList
3. O(1) 查询
4. O(1) 修改，更新

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_3200.png)

### LFU

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_3300.png)

习题实战

leetcode 146



### Bloom Filter(布隆过滤器)

在网络中，分布式系统中用到的非常多

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_3400.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_3500.png)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_3600.png)

## 第十一节 课程重点回顾

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_3700.png)

《指导生活的算法》简述·[兔妈在美国](<https://www.jianshu.com/u/a31ae0dc0acf>)

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_3800.png)

### 代码模板

递归模板

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_3900.png)

DFS代码-递归写法

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_4000.png)

BFS代码

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_4100.png)

二分查找

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_4200.png)

DP模板

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_4300.png)

### 练习和切题

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_4400.png)

题目至少要做三遍。

### 面试答题四件套

![](D:\github\markshen1992.github.io\document\algorithm\Lecture10_4500.png)

[算法与数据结构，你一定要知道的](<https://mp.weixin.qq.com/s?__biz=MjM5ODYxMDA5OQ==&mid=2651961961&idx=1&sn=dbb9c041bd2210ba91374715ce91eefe&chksm=bd2d0fb58a5a86a3c96a6a0ba9330e123d8039f2477654593af0a4088362ee4c9aaab287f911&scene=21#wechat_redirect>)

斐波那契数列-矩阵相乘的方式



## 第十二节 最后的最后

### 环境准备

### 切题姿势