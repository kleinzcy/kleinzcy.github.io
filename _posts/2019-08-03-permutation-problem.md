---
title: 排列组合问题
layout: post
categories: STL
tags: summary
author: chuyuzhang
---
这一篇文章主要总结一下c++中排列组合函数，[next_permutation](http://www.cplusplus.com/reference/algorithm/next_permutation/)、[prev_permutation](http://www.cplusplus.com/reference/algorithm/prev_permutation/)。

## 字典序
字典序，顾名思义就是按照字典顺序排列。例如字符串adcb，它的字典序就是abcd。

## 函数用法
parameters:first last（两个迭代器）
return:bool类型，对于next_permutation,若存在下一个字典序（升序）排列，返回true，对于prev_permutation，若存在上一个字典序（降序）排列，返回true，否则为false。

具体细节参考它们官网。

## 算法分析
下面，我们分析[下一个最大的数Ⅲ](https://leetcode-cn.com/problems/next-greater-element-iii/)，来理解next_permutation的作用。
问题的分析参看链接，这里我直接给出代码。

使用next_permutation的解法：

<pre class="line-numbers language-javascript"><code>class Solution {
public:
    int nextGreaterElement(int n) {
        if(n < 12) return -1;
        string str = to_string(n);
        next_permutation(str.begin(), str.end());
        long val = stol(str);
        if(val > INT_MAX || val <= n) return -1;
        return val;
    }
};</code></pre>

不使用next_permutation的解法：

<pre class="line-numbers language-javascript"><code>class Solution {
public:
    int nextGreaterElement(int n) {
        if (n < 12){
            return -1;
        }
        string num = to_string(n);//将n转换为string型
        int numSize = num.size(), indexI = num.size() - 1, swapIndex;
        //第一步：从前往后扫描，定位到第一个降序的位置
        while (indexI > 0 && num[indexI] <= num[indexI - 1]){
            indexI -= 1;
        }
        //如果一直扫描到了首端，说明这个数已经是最大，比如“54321”
        if (indexI == 0){
            return -1;
        }
        //这里需要自减一，因为此时定位到的位置是寻找转换之前位置“12345643”第一个出现逆序的位置是字符'6'，下标需要前移一个单位定位到'5'
        indexI -= 1;
        //第二步：寻找到最小的且比num[indexI]大的元素，比如“12345643”中比'5'大的且在'5'后面的元素是'6'
        swapIndex = indexI + 1;
        while (swapIndex + 1 < numSize && num[swapIndex + 1] > num[indexI]){
            swapIndex += 1;
        }
        //第三步：将第一个逆序的元素与他后面最小的比他大的元素交换
        swap(num[indexI], num[swapIndex]);
        //第四步：将逆序位置之后的元素进行排序
        sort(num.begin() + indexI + 1, num.end());
        long long resNum = stol(num);//将结果转换为long型
        if (resNum > INT_MAX){//如果超过了int型的最大表示范围，返回-1
            return -1;
        }
        return resNum;
    }
};</code></pre>

感谢参考[sinstar](https://leetcode-cn.com/u/sinstar),[hestyle](https://blog.csdn.net/qq_41855420/article/details/89243466)

## Reference
http://www.cplusplus.com/reference/algorithm/next_permutation/

http://www.cplusplus.com/reference/algorithm/prev_permutation/

https://leetcode-cn.com/problems/next-greater-element-iii/

https://blog.csdn.net/qq_41855420/article/details/89243466