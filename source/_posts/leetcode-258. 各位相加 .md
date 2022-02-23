---
title: 258. 各位相加
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 258. 各位相加  双层while循环
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 258. 各位相加  双层while循环
## [查看原题](https://leetcode-cn.com/problems/add-digits/)
## 解题思路
两层while循环控制，外层循环控计算结束，里层while控制将数字各项拆开计算求和；
每次循环计算求和都更新外层的num 为数字各项计算总和sum。

## 代码

```javascript
/**
 * @param {number} num
 * @return {number}
 */
var addDigits = function(num) {
    while (num > 9) {
        let sum = 0;
        while (num > 0) {
            sum += num % 10;
            num = Math.floor(num / 10)
        }
        num = sum;
    }
    return num;
};
```