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

![](D:\markshen1992.github.io\document\algorithm\link.png)



## 第二节

### 《异类—不一样的成功启示录》马尔科姆·格拉德威尔

10000小时定律

- Chunk it up （切碎知识点）
  - 知识树

![](D:\markshen1992.github.io\document\algorithm\datastructure_summary.png)

![](D:\markshen1992.github.io\document\algorithm\datastructure.png)



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

![](D:\markshen1992.github.io\document\algorithm\summary_datastructure.png)

### 时间复杂度，空间复杂度

![](D:\markshen1992.github.io\document\algorithm\shikongfuzadu.png)

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

![](D:\markshen1992.github.io\document\algorithm\lecture3_0100.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture3_0200.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture3_0300.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture3_0400.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture3_0500.png)



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

![](D:\markshen1992.github.io\document\algorithm\Lecture4_0100.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture4_0200.png)

### Array

Access: O(1)

Insert, Delete: 平均O(n)



### Linked List

![](D:\markshen1992.github.io\document\algorithm\Lecture4_0300.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture4_0400.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture4_0500.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture4_0600.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture4_0700.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture4_0800.png)



## 第六节

### 数组与链表习题

![](D:\markshen1992.github.io\document\algorithm\Lecture5_0100.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture6_0100.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture6_0200.png)

链表是否有环

1. 硬做，尾节点为null
2. Set数据结构，存节点地址，直接判重
3. 两个指针，一个一次走一步，一个一次走两步，有环会有相遇。**快慢指针**。

## 第七节 栈，队列

Stack: First In Last Out (FILO)

​	Array or LinkedList

Queue: First In First Out (FIFO)

​	Array or Doubly Linked List

![](D:\markshen1992.github.io\document\algorithm\Lecture6_0300.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture6_0400.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture6_0500.png)

[算法性能比对](<http://www.bigocheatsheet.com/>)

### 题目实战

1. String，大中小括号是否合法？

   (){}[] 合法

   {)} 不合法

![](D:\markshen1992.github.io\document\algorithm\Lecture7_0100.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture7_0200.png)

leetcode: 232, 255

用Stack实现Queue的效果

用两个Stack来实现，输入栈，输出栈

## 第八节 优先队列

### 特性

   正常进，按优先级出

### 实现机制

1. Heap(Binary, Binomial, Fibonacci)

2. Binary Search Tree

![](D:\markshen1992.github.io\document\algorithm\Lecture8_0100.png)

二叉堆调整

![](D:\markshen1992.github.io\document\algorithm\Lecture8_0200.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture8_0300.png)

学会用Leetcode，wikipedia

### 题目实战

leetcode 703

![](D:\markshen1992.github.io\document\algorithm\Lecture8_0400.png)

leetcode 239

![](D:\markshen1992.github.io\document\algorithm\Lecture8_0500.png)

## 第九节 Hash table

1. HashTable Hash Function Collisions
2. Map vs Set
3. HashMap, HashSet, TreeMap, TreeSet
4. 查询和计数

![](D:\markshen1992.github.io\document\algorithm\Lecture9_0100.png)

### 哈希碰撞问题

![](D:\markshen1992.github.io\document\algorithm\Lecture9_0200.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture9_0300.png)

对速度要求高的时候，用HashMap, HashSet

如果要有序的结构，要使用TreeMap, TreeSet

### 题目实战

- leetcode 242 变位词
- leetcode 1 tow sum
- leetcode 15, 18 ; 3 sum, 4 sum



## 第十节 Tree & Graph

### 回顾链表内容

### 树

![](D:\markshen1992.github.io\document\algorithm\Lecture10_0100.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture10_0200.png)

![](D:\markshen1992.github.io\document\algorithm\Lecture10_0300.png)

LinkedList 就是特殊化的树

Tree就是特殊化的图

链表 -> 树 -> 图

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

![](D:\markshen1992.github.io\document\algorithm\Lecture10_0400.png)

### 题目实战

leetcode 98，235，236

### 二叉树遍历

- Pre order：根 左 右
- **In order**：左 根 右
- Post order：左 右 根

实际中用的非常少。

![](D:\markshen1992.github.io\document\algorithm\Lecture10_0500.png)

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

  ![](D:\markshen1992.github.io\document\algorithm\Lecture10_0600.png)

- Divide & Conquer