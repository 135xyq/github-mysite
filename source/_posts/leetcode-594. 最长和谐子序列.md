---
title: 594. 最长和谐子序列
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 594. 最长和谐子序列 Map对象
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 594. 最长和谐子序列 Map对象

## [查看原题](https://leetcode-cn.com/problems/longest-harmonious-subsequence/)

## 解题思路
1. 将数组映射到Map对象中，以数组的值为键，以数组值得个数为Map对象的值
2. 使用forof循环取出对象的每一项
3. ```const right = map.get(key + 1) ? map.get(key + 1) : 0;```
     ```const left = map.get(key - 1) ? map.get(key + 1) : 0;```
    将当前项得左右两项做出判断
4. 求出左右项得最大值
5. 判断是否要更新总的最大值（条件是左右两项至少存在一个，且两者之和大于当前的总最大值）



## 代码

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var findLHS = function(nums) {
    let result = 0; //返回结果
    const map = new Map();
    for (const num of nums) {
        if (map.has(num)) {
            map.set(num, map.get(num) + 1);
        } else {
            map.set(num, 1)
        }
    }
    for (const [key, value] of map) {
        const right = map.get(key + 1) ? map.get(key + 1) : 0;
        const left = map.get(key - 1) ? map.get(key + 1) : 0;
        let max = Math.max(left, right);
        if ((max + value) > result && max > 0) {
            result = max + value;
        }
    }
    return result;
};

`
``