---
title: 189. 轮转数组
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 189. 轮转数组 利用数组内置方法splice和unshift
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 189. 轮转数组 利用数组内置方法splice和unshift
## [查看原题](https://leetcode-cn.com/problems/rotate-array/)

## 解题思路
1. 判断出哪些部分是要向右轮转的，用 k % nums.length求出要轮转的长度
2. 找到第一个要轮转开始的地方 数组长度- 要轮转的长度
3. 截取整个部分再用 unshift方法插入到数组的最前面就行
## 代码

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
 var rotate = function(nums, k) {
    let length = nums.length;
    let k1 = k % length;
    nums.unshift(...nums.splice(length - k1))
    return nums
};
```