---
title: 1816. 截断句子
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 1816. 截断句子 split方法和循环判断
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 1816. 截断句子 split方法和循环判断

## [查看原题](https://leetcode-cn.com/problems/truncate-sentence/)

## 直接调用内置方法

### 解题思路
1. 先将字符串用split转为数组
2. 用slice截取数组的0到k部分再用join连接

### 代码
```javascript
/**
 * @param {string} s
 * @param {number} k
 * @return {string}
 */
var truncateSentence = function(s, k) {
    // 将字符串转为数组后截取
    return s.split(' ').splice(0,k).join(' ')
};

```

## 循环判断

### 解题思路
1. 新定义一个空字符result，定义count=0用来存储找到了几个空格
2. 循环字符串，判断这一项是不是空格，如果是空格则count++
3. 判断count和k的关系，如果count===k说明单词已经找够，break退出循环，else则将当前项加到result中


### 代码
```
/**
 * @param {string} s
 * @param {number} k
 * @return {string}
 */
var truncateSentence = function(s, k) {
    const length = s.length;
    let result = '';
    let count = 0;
    for(let i = 0;i<length;i++){
        if(s.charAt(i)===' '){
            count++;
        }
        if(count === k){
            break;
        }else{
            result += s.charAt(i);
        }
        
    }
    return result;
};
```