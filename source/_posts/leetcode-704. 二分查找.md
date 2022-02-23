---
title: 704. 二分查找 
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 704. 二分查找  二分
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 704. 二分查找  二分
## 解题思路
二分算法，
1. 求左右边界left 和 right 的中间值mid
2. 判断中心值对应的数组值 nums[mid] 与要比较的值target大小关系
    - 大，则更新右边界right = mid - 1
    - 小，则更新左边界left = mid +1
    - 相等，直接返回mid
3. 循环判断直到 left<= right
4. 直接返回-1，这里返回说明前面肯定没有返回，说明没找到对应的下标

## [原题](https://leetcode-cn.com/problems/binary-search/)

## 代码

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function(nums, target) {
    let left = 0;
    let right = nums.length-1;
    while (left <= right) {
        let mid = parseInt((left + right) / 2);
        if (nums[mid] > target) {
            right = mid - 1;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            return mid;
        }

    }
    return -1;
};

```