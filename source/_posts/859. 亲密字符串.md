---
title: 859. 亲密字符串
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 859. 亲密字符串 遍历比较
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 859. 亲密字符串 遍历比较

## [查看原题](https://leetcode-cn.com/problems/buddy-strings/)

## 解题思路
1. 先判断两个字符串长度是否相等或者长度都为1，如果不相等或者长度为1，则肯定不满足，直接返回false
2. 遍历字符串求出每一项的差值存到数组temp中
3. 先判断一下交换的数据是否相等
4. 过滤出temp中值为0的项
5. 判断比较temp的长度
    - temp的长度为2，则比较temp[0] + temp[1] === 0
    - temp的长度为0，则判断字符串的长度是否为一串一样的数字，且长度大于1
    - 以上情况返回true
6. 其他情况返回false
## 代码
```javascript
/**
 * @param {string} s
 * @param {string} goal
 * @return {boolean}
 */
 var buddyStrings = function(s, goal) {
    // 如果两个字符串长度不相等或者其中一个长度为1，则肯定不是亲密字符串
    if (s.length !== goal.length || s.length === 1) {
        return false;
    }
    let temp = []; //用来存放两个字符串的每一项的差值
    for (let i = 0; i < s.length; i++) {
        temp.push(s.charCodeAt(i) - goal.charCodeAt(i));
    }
    let a = -1;
    for (let i = 0; i < temp.length; i++) {
        if (temp[i] !== 0 && a === -1) {
            a = i;
        } else if (temp[i] !== 0 && a !== -1) {
            if (goal.charAt(a) !== s.charAt(i)) {
                return false;
            }
        }
    }
    temp = temp.filter(item => item);
    if (((temp.length === 2) && (temp[0] + temp[1] === 0)) || (temp.length === 0 && ((new Set(s.split('')).size === 1) || (new Set(s.split('')).size !== s.length)))) {
        return true;
    } else {
        return false;
    }
};
```