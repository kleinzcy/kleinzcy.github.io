---
title: 龟兔算法
layout: post
categories: Leetcode
tags: summary
author: chuyuzhang
math: 'true'
---
## 什么是龟兔算法
检测单链表上的环有个很经典的算法叫做”弗洛伊德判圈算法”, 也叫”龟兔算法”.

## 龟兔算法的基本思路
### 是否有环
我们让龟(tortoise)和兔(hare)从单链表的起点出发, 每次龟走一步, 兔走两步, 如果time_a步之后龟兔相遇, 则该链表有环.

### 环的长度
上述算法刚判断出存在环时, 龟和兔位于同一节点. 此时让兔不动, 而龟不断前进, 肯定又会相遇, 而这一次龟前进的步数显然就是环的长度length.

### 环的起点
还是之前所说龟兔相遇的节点, 首先兔保持原位, 而把龟置回链表起点, 然后龟和兔同时走, 每次都走一步, 经过time_b步最终再次相遇, 则这次相遇的节点就是环的起点start.

## 龟兔算法证明
假设兔每次走step步, 那么只要单链表中存在环, 而且龟到达环的起点之后, 龟和兔之间的路程差能够是环长度length的整数倍, 则二者就能相遇. 即:

$$ ((step - 1) * time_a) % length == 0  && time_a >= start $$

其中start和length是固定的, time_a却无限增长, 所以总会有机会整除, 所以龟兔算法可以判断是否有环.

略过显而易见的长度计算, 接着说查找环的起点. 当仅当step为2, 即兔每次走两步时, 根据前面的条件得知time_a能被length整除. 于是我们接着假设time_b为龟到达环的起点start后绕了n圈再次到达起点, 即time_b == start + n * length, 则兔此时的位置(假设绕了m圈)是time_a + time_b - m * length, 代入后为time_a + start + (n - m) * length, 因为step为2时time_a能被length整除, 所以兔此时正好也在起点start处, 所以龟兔算法可以找到环的起点.


https://www.geeksforgeeks.org/detect-loop-in-a-linked-list/
http://adam8157.info/blog/2015/08/why-does-tortoise-and-hare-algorithm-work/