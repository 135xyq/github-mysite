---
title: 88. 合并两个有序数组
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 88. 合并两个有序数组 循环替换后排序
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 88. 合并两个有序数组 循环替换后排序
## 解题思路
注意不能改变num1的长度，不能能用pop
将nums2先插入到nums1的末尾，再用sort排序

[原题](https://leetcode-cn.com/problems/merge-sorted-array/)

## 代码

```javascript
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
var merge = function(nums1, m, nums2, n) {
    for (let i = m; i < m + n; i++) {
        nums1[i] = nums2[i - m]
    }
    nums1 = nums1.sort(function(a, b) { return a - b });
    // console.log(nums1)
};
```