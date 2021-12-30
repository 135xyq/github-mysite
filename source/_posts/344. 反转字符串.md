---
title: 344. 反转字符串
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 344. 反转字符串 reverse&双指针&splice
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 344. 反转字符串 reverse&双指针&splice
# [查看原题](https://leetcode-cn.com/problems/reverse-string/)

## 解题思路
每次将数组最后一个pop再用splice插入到数组中

## 代码
```javascript
/**
 * @param {character[]} s
 * @return {void} Do not return anything, modify s in-place instead.
 */
var reverseString = function(s) {
    let len = s.length;
    for (let i = 0; i < len; i++) {
        s.splice(i, 0, s.pop());
    }
};
```

## 解题思路
双指针，找出交换后的位置进行交换

## 代码

```javascript
/**
 * @param {character[]} s
 * @return {void} Do not return anything, modify s in-place instead.
 */
var reverseString = function(s) {
    let len = s.length;
    for (let i = 0; i < Math.floor(len / 2); i++) {
        let temp = s[i];
        s[i] = s[len - 1 - i];
        s[len - i - 1] = temp;
    }
};
```

## 解题思路
使用reverse方法

## 代码
```javascript
/**
 * @param {character[]} s
 * @return {void} Do not return anything, modify s in-place instead.
 */
var reverseString = function(s) {
    s.reverse();
};
```