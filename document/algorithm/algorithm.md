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
2. 可能解法， 对比时/空间夫大度，加强
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

### 数组与链表先习题

![](D:\markshen1992.github.io\document\algorithm\Lecture5_0100.png)

