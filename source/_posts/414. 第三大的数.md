---
title: 414. 第三大的数
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 414. 第三大的数  利用set数组去重和sort排序
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 414. 第三大的数  利用set数组去重和sort排序

## [查看原题](https://leetcode-cn.com/problems/third-maximum-number/)
## 解题思路
1. 将数组转为set 集合去除重复值，再转为数组
2. 将数组降序排序
3. 判断数组的长度
    - 长度大于 3 则直接返回数组的第3大的数
    - 长度小于 3 直接返回数组的最大值即最大项

## 代码

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var thirdMax = function(nums) {
    //将数组去重
    const newNums = [...new Set(nums)];
    newNums.sort((a, b) => b - a);
    if (newNums.length >= 3) {
        return newNums[2];
    } else {
        return newNums[0]
    }
};

```