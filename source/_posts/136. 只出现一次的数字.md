---
title: 136. 只出现一次的数字 循环利用indexOf求解
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 136. 只出现一次的数字 循环利用indexOf求解
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 136. 只出现一次的数字 循环利用indexOf求解

## [查看原题](https://leetcode-cn.com/problems/single-number/)

## 解题思路
这种方法时间复杂度较高
利用indexOf方法判断数组当前项在前后是否还能找到与他一样的数，如果不能找到，这个数即为所求。


## 代码

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    const length = nums.length;
    for (let i = 0; i < length; i++) {
        if (nums.indexOf(nums[i], i + 1) === -1 && nums.indexOf(nums[i]) === i) {
            return nums[i]
        }
    }
};
```

## 解题思路
1. 将数组转为set集合，set集合没有重复项
2. 对set集合每一项求和 sum1
3. 对数组求和 sum2
4. set集合的和sum1表示数组不重复项的和，乘以2再减去sum2即为那个只出现一次的数

## 代码

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    const set = new Set(nums); //将nums转为集合
    let sum1 = 0; //求set集合各项的和
    let sum2 = 0; //求数组的各项和
    for (const item of set) {
        sum1 += item;
    }
    nums.forEach(vaule => {
        sum2 += vaule;
    })
    return (2 * sum1) - sum2;
};
```