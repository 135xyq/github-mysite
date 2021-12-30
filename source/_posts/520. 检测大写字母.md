---
title: 520. 检测大写字母
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 520. 检测大写字母   求出大小写字母的个数
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 520. 检测大写字母   求出大小写字母的个数
## 解题思路
1. 统计出单词中大写字母和小写字母的个数，使用（word.charAt(i) >= 'A' && word.charAt(i) <= 'Z'）判断是否是大写字母
2. 根据大小写字母的数量判断是否合法
    - 如果大写字母个数为0 或小写字母个数为0则合法
    - 如果大写字母的个数为1则继续判断单词的第一个字母是不是大写的，如果是则合法，不是就不合法
    - 其他情况均为不合法

## [原题](https://leetcode-cn.com/problems/detect-capital/)

## 代码

```javascript
/**
 * @param {string} word
 * @return {boolean}
 */
var detectCapitalUse = function(word) {
    const length = word.length;
    let upper = 0; //计算有多少个大写字母
    let lower = 0; //有多少小写字母
    for (let i = 0; i < length; i++) {
        if (word.charAt(i) >= 'A' && word.charAt(i) <= 'Z') {
            upper++;
        } else {
            lower++;
        }
    }
    if (lower === 0 || upper === 0) {
        return true;
    } else if (upper === 1 && (word.charAt(0) >= 'A' && word.charAt(0) <= 'Z')) {
        return true;
    } else {
        return false;
    }
};
```