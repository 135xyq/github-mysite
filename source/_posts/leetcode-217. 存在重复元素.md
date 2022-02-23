---
title: 217. 存在重复元素
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 217. 存在重复元素 利用set来和数组长度比较&排序比较
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 217. 存在重复元素 利用set来和数组长度比较&排序比较

## [查看原题](https://leetcode-cn.com/problems/contains-duplicate/)
## 解题思路
利用集合set来保证传入的数字元素唯一，再比较set的长度和数组的长度，如果两者长度一样则说明，数组转为集合时没有取出重复元素，也即数组中的元素都是不重复的，返回false，否者返回true


## 代码

```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
    const set = new Set(nums);
    let sum1 = 0,
        sum2 = 0;
    if (set.size === nums.length) {
        return false;
    } else {
        return true;
    }
};
```

## 解题思路
1. 可以先讲数组从小到大排序，则重复的数字会相邻。
2. 循环判断数组的当前项是否等于下一项
    - 等于则直接返回
    - 不等于就继续判断
3. 循环结束return false，到此还没返回说明数组里面不会有重复值

## 代码

```javascript

/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
    nums.sort((a, b) => a - b); //将数组排序
    // 如果数组中存在重复元素，则排序后应该相邻
    for (let i = 0; i < nums.length; i++) {
        if (nums[i] === nums[i + 1]) {
            return true;
        }
    }
    return false;
}
```