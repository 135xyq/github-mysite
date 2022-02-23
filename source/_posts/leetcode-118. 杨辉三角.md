---
title: 118. 杨辉三角 循环遍历，一层一层计算
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 118. 杨辉三角 循环遍历，一层一层计算
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 118. 杨辉三角 循环遍历，一层一层计算
## 解题思路
1. 定义一个空数组result存放返回值
2. 循环，定义一个新数组temp ，先将数组第一项赋值为1，在循环计算，再判断参数
    - 参数为1则不在temp最后一项push（1）
    - 不为1则push（1）
3. 将temp添加都result中

## [原题](https://leetcode-cn.com/problems/pascals-triangle/)
## 代码

```javascript
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
    let result = [];
    for (let i = 1; i <= numRows; i++) {
        let temp = [1];
        for (let j = 1; j < i - 1; j++) {
            temp.push(result[i - 2][j - 1] + result[i - 2][j]);
        }
        if (i !== 1) {
            temp.push(1);
        }
        result.push(temp);
    }
    return result;
};
```