---
title: 119. 杨辉三角 II 排列组合
date: 2021-12-30 18:24:47
comments: true #是否可评论
description: 119. 杨辉三角 II 排列组合
toc: true #是否显示文章目录
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 119. 杨辉三角 II 排列组合
## 解题思路
找出排列组合关系题就写出来了

[原题](https://leetcode-cn.com/problems/pascals-triangle-ii/)
## 代码

```javascript
/**
 * @param {number} rowIndex
 * @return {number[]}
 */
var getRow = function(rowIndex) {
    const result = []; //存放结果

    result.push(1); //第一个特殊处理
    for (let i = 1; i <= rowIndex; i++) {
        let t = 1; //分子
        let b = 1; //分母
        for (let j = 0; j < i; j++) {
            t *= (rowIndex - j);
        }
        for (let j = 1; j <= i; j++) {
            b *= j;
        }


        result.push(t / b);
    }
    return result;
};
```