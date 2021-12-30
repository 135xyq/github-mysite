---
title: 557. 反转字符串中的单词 
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 557. 反转字符串中的单词 III 转为数组逆序在转为字符&循环交换
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 557. 反转字符串中的单词 III 转为数组逆序在转为字符&循环交换
## [查看原题](https://leetcode-cn.com/problems/reverse-words-in-a-string-iii/)

## 解题思路
1. 将字符串按空格使用split分割为数组
2. 遍历数组每一项，再用split转为数组，使用reverse逆序，再使用join合并为字符串
3. 将数组使用join(' ')转为字符串

## 代码

```javascript
/**
 * @param {string} 
 * @return {string}
 */
var reverseWords = function(s) {
    const arr = s.split(' '); //将字符串转为数组
    let result = arr.map(item => item.split('').reverse().join(''))
    return result.join(' ')
};
```

## 解题思路
1. 新开一个数组，用来存放结果
2. 遍历原数组，计算每一个单词的长度，方法如下：判断当前项是不是 ' '
    - 是，则sum++（sum统计单词的长度）
    - 不是则新定义一个临时数组temp，将根据刚才计算的单词的长度，push到temp中，再将其转为字符串后加入到大数组中，最后判断当前项是不是最后一个单词，如果不是最后一个则需要再给大数组push一个' ' ,
    最后将大数组转为字符串，返回。

## 代码

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function(s) {
    const length = s.length;
    let result = [];
    let sum = 0; //一个单词的长度
    // 要多处理一个判断长度
    for (let i = 0; i <= length; i++) {
        // 如果不等于空格则说明是一个单词，统一处理
        if (s[i] !== ' ' && i !== length) {
            sum++;
        } else {
            // 将一个单词翻转
            let temp = [];
            for (let j = sum - 1; j >= 0; j--) {
                temp.push(s[i - sum + j]);
            }
            sum = 0;
            result.push(temp.join(''));
            if (i !== length) {
                result.push(' ')
            }
        }
    }
    return result.join('');
};
```
