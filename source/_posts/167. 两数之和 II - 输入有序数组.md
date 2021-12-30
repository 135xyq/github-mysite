---
title: 167. 两数之和 II - 输入有序数组  
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 167. 两数之和 II - 输入有序数组  双重循环暴力求解&二分求解
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 167. 两数之和 II - 输入有序数组  双重循环暴力求解&二分求解
## 解题思路
两层循环暴力求解

##[原题](https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/)
## 代码

```javascript
/**
 * @param {number[]} numbers
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(numbers, target) {
    const length = numbers.length;
    let result = [];
    for (let i = 0; i < length; i++) {
        for (let j = i + 1; j < length; j++) {
            if (numbers[j] + numbers[i] === target) {
                result.push(i + 1, j + 1);
                return result;
            }
        }
    }

};
```

## 解题思路
二分法求解
1. 循环数组假设当前下标 i 为其中一个正确的值计算出另一个值，
2. 在 i+1 到 数组长度length-1 的这段距离中二分查找，找到符合条件的直接返回
3. 这种方法比直接双重暴力循环时间复杂度降低，从(N^2)  降为（NlogN）
```javascript
/**
 * @param {number[]} numbers
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(numbers, target) {
    const length = numbers.length;
    let left = 0,
        right = 0; //左右边界
    for (let i = 0; i < length; i++) {
        let target1 = target - numbers[i]; //另个数的大小
        right = length - 1;
        left = i + 1;
        let mid = Math.floor((left + right) / 2);
        while (left <= right) {
            if (target1 < numbers[mid]) {
                right = mid - 1;
            } else if (target1 > numbers[mid]) {
                left = mid + 1;
            } else {
                return [i + 1, mid + 1]
            }
            mid = Math.floor((left + right) / 2)
        }
    }

};
```