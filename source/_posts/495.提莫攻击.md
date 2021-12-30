---
title: 495.提莫攻击
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 495.提莫攻击
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 495.提莫攻击
## 解题思路
1. 根据题意肯定是根据不同的情况加上不同的数值，先定义一个存储结果的变量；
2. 循环数组判断当前项是不是数组的最后一项
    - 如果是最后一项则不需要判断，直接加上中毒持续时间duration即可
3. 如果不是最后则分两种情况判断
    - 这次中毒结束完还没开始下一次的中毒，则需要加上中毒的持续时间爱duration
    - 这次中毒还没结束下次就开始了，则需要用下次的开始时间减去这次的时间即为本次中毒时间

## [原题](https://leetcode-cn.com/problems/teemo-attacking/)
## 代码

```javascript
/**
 * @param {number[]} timeSeries
 * @param {number} duration
 * @return {number}
 */
var findPoisonedDuration = function(timeSeries, duration) {
    let sum = 0;
    const length = timeSeries.length;
    for (let i = 0; i < length; i++) {
        if ((i !== length - 1) && ((timeSeries[i] + duration - 1) < timeSeries[i + 1])) {
            sum += duration;
        } else if ((i !== length - 1) && ((timeSeries[i] + duration - 1) >= timeSeries[i + 1])) {
            sum += (timeSeries[i + 1] - timeSeries[i]);
        } else if (i === length - 1) {
            sum += duration;
        }
    }
    return sum;
};
```