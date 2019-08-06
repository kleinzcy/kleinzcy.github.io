---
title: 检测单向链表上的环
layout: post
categories: Leetcode
tags: summary
author: chuyuzhang
math: 'true'
---
## 算法综述
检测单链表上的环有个很经典的算法叫做”弗洛伊德判圈算法”, 也叫”龟兔算法”,时间复杂度是O(n+m),空间复杂度是O(1),其中m为环的长度。另外有一个更加高效的算法，叫做brent判圈算法。

检测单链表中的环，还可以用无序集合来解决，将节点push到集合中，检测下一个节点是否在集合中，若在，说明有环，否则无，时间复杂度和空间复杂度都为O(n)。还有一个就是标记visited，如果这个节点被访问了，就令visited为true，否则为false，若下一个节点的visited为true，则说明有环，这种方法，需要修改原始数据结构，不怎么方便，可以利用hash表存储结点的地址，判断地址是否已在hash表中，这样做和第二种方法差不多,时间复杂度为O(n)，空间复杂度为O(n)。

算法实例和代码参考：[detect-loop-in-a-linked-list](https://www.geeksforgeeks.org/detect-loop-in-a-linked-list/)

## 龟兔算法的基本思路
### 原理
假设令龟、兔为指针，并且指向起点位置，兔子每次移动两个节点，乌龟每次移动一个节点。如果两者在起始节点外相遇，则说明有环。如果兔子在走到链表尾部还没有与乌龟相遇，说明无环。

### 环的长度
上述算法刚判断出存在环时, 龟和兔位于同一节点. 此时让兔不动, 而龟不断前进, 肯定又会相遇, 而这一次龟前进的步数显然就是环的长度length.

### 环的起点
还是之前所说龟兔相遇的节点, 首先兔保持原位, 而把龟置回链表起点, 然后龟和兔同时走, 每次都走一步, 经过time_b步最终再次相遇, 则这次相遇的节点就是环的起点start.

## 龟兔算法证明
如图所示，令起始节点为h， 起始节点到环起点距离为m， 龟兔相遇节点为p， p节点与环起点距离为n； 
当龟兔相遇时 
乌龟所跑距离为 S = m + n + aC（C 为环长度), 
兔子所跑距离为2S = m + n + bC（因为兔子速度为乌龟2倍） 
故得S = (b - a)C = m + n + aC ==> (b - 2a)C = m + n, 由此可知，m + n 为环C长度整数倍. 
那么令乌龟返回链表起始节点，兔子仍在相遇节点P，两者同时不断推进直至相遇，相遇节点为环起点。因为乌龟移动距离m, 则兔子也移动距离m， 原本p 节点距离环起点为n， 由于m + n 为环长整数倍，故兔子移动到了环起点，即相遇节点为环起点。 

## Brent判圈算法
### 原理
起始令乌龟兔子指向起始节点，让乌龟保持不动，兔子走2i2i 步， 即迭代一次，兔子走2步， 迭代2次，兔子走4步等等。在兔子走每一步后，判断龟兔是否相遇，如果没有相遇，则让乌龟的位置变成兔子所在的位置，否则如果乌龟不动，则乌龟永远无法进入环内，随后进入新的迭代。循环下去，直至相遇或到表尾。

### 环的长度
由于乌龟一直处于兔子更改步长上限时的位置，所以更改步长上线后，兔子走了几步与乌龟相遇，则环的长度就为多少。

### 环的起点
Flyod判圈算法利用了乌龟和兔子的距离是环长整数倍的性质求起点，所以可以让乌龟回到起点，兔子回到距离起点环长距离的节点，随后与Floyd算法一样。
<pre class="line-numbers language-javascript"><code>bool hasCycleBrent(ListNode *head) {
   ListNode *p1 = head;
   ListNode *p2 = head;
   int steps = 0;
   int limit = 2;
   while (p1 != NULL && p2 != NULL) {
      p1 = p1->next;
      if (p1 == p2) {
          return true;}
      ++steps;
      if (steps == limit) {
        p2 = p1;
        steps = 0;
        limit *= 2;
       }
     }
    return false;
}</code></pre>
 
## leetcode题目分析
直接参考这个题：[寻找重复数](https://leetcode-cn.com/problems/find-the-duplicate-number/solution/xun-zhao-zhong-fu-shu-by-leetcode/)

## Reference
https://www.geeksforgeeks.org/detect-loop-in-a-linked-list/
http://adam8157.info/blog/2015/08/why-does-tortoise-and-hare-algorithm-work/
https://blog.csdn.net/u011221820/article/details/78821464
http://zhengyhn.github.io/post/algorithm/brent.loop/