---
title: 202. 快乐数
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 202. 快乐数  while循环找到结束条件
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 202. 快乐数  while循环找到结束条件
## [查看原题](https://leetcode-cn.com/problems/happy-number/)
## 解题思路
首先要明白一个数不是快乐数，则其中的计算过程会出现循环，要以此为结束条件
1. 先将数字的每一项取出来，存到一个数组中，因为会反复用到，所以建议写成一个方法 getEachNumber
2. 根据得到的数字每一项计算平方和，将其存放到一个数组中 temp
3. 先判断结果是否为 1
    - 为 1 则证明是快乐数，返回 true 
    - 不为1 则继续判断temp 是否出现过该数（判断是否出现了循环）
        - 如果出现了则返回false ，循环结束
        - 没出现过讲 n 值更新为上一次计算的各项平凡和，继续循环

## 代码

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {

    let temp = []; //存放每一次计算的结果，如果一个数不是快乐数说明到后面会形成循环
    while (1) {
        const nums = getEachNumber(n); //将数字每一项放在数组里;
        let result = nums.map(item => item ** 2); //将数字每一项平方
        let sum = 0; //每一次计算的各项平方和结果
        result.forEach(item => sum += item);
        if (sum === 1) {
            return true;
        }
        if (temp.indexOf(sum) != -1) {
            // 结果形成了循环不会再等于 1 了
            return false;
        }
        temp.push(sum);
        n = sum;
    }
};
/**
 * 取出数字的每一项
 * @param {number} n 传入要处理的数字
 * @param {Array}
 */
function getEachNumber(n) {
    let nums = [];
    while (n > 0) {
        nums.push(Math.floor(n % 10))
        n = Math.floor(n / 10)
    }
    return nums;
}
```