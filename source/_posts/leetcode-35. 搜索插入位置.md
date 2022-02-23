---
title: 35. 搜索插入位置
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 35. 搜索插入位置 二分注意细分判断条件
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 35. 搜索插入位置 二分注意细分判断条件
## [查看原题](https://leetcode-cn.com/problems/search-insert-position/)
## 解题思路
二分算法，注意不同的判断条件
1. left 为左边界初始值为 0 ，right 为右边界 初始值为 nums.length - 1
2. 注意while的循环条件为 left<= right ， mid = Math.floor((left + right) / 2);
3. 开始判断nums[mid] 和target的关系
    1. 如果nums[mid] > target 
        - 继续判断mid是否在数组的第一项了
            1. 如果不是第一项则 right = mid - 1;
            2. 如果是第一项应该直接结束，说明此时数组中没有target，且小于nums[0],则应该插在第0位
    2. 如果nums[mid] < target
         - 继续判断mid是否在数组的最后一项了
            1. 如果不是最后一项则 left = mid + 1;
            2. 如果是最后一项应该直接结束，说明此时数组中没有target，且大于nums[nums.length -1],则直接插在第 nums.length 位
    3. 如果nums[mid] === target 
        - 直接返回 mid

## 代码

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var searchInsert = function(nums, target) {
    let left = 0,
        right = nums.length - 1;
    while (left <= right) {
        mid = Math.floor((left + right) / 2);
        if (nums[mid] > target) {
            if (mid != 0) {
                right = mid - 1;
            } else {
                return 0;
            }
        } else if (nums[mid] < target) {
            if (nums[mid + 1] > target) {
                return mid + 1;
            } else {
                if (mid != nums.length - 1) {
                    left = mid + 1;
                } else {
                    return nums.length;
                }
            }
        } else {
            return mid;
        }
    }
};

```