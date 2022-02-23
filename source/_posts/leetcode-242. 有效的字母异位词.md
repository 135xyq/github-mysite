---
title: 242. 有效的字母异位词
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 242. 有效的字母异位词 转为数组排序后比较
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 242. 有效的字母异位词 转为数组排序后比较
## [查看原题](https://leetcode-cn.com/problems/valid-anagram/)
## 解题思路
1. 先判断两个字符串长度是否一样，不一样则肯定不是有效的字母异位词，直接返回false
2. 执行这这以后说明字符串长度一样则将他们转为数组
3. 可将数组排序，可直接使用sort ，因为sort是按ASCII码排序，所以可以直接使用
4. 循环数组，判断两个数组的每一项是否相等，不相等则说明两个字符串中右的字母个数不一样

## 代码

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
    // 如果两个字符串长度不一样则不可能满足条件
    if (s.length !== t.length) {
        return false;
    }
    // 将字符串转为数组
    const arr1 = Array.from(s);
    const arr2 = Array.from(t);
    arr1.sort();
    arr2.sort();
    for (let i = 0; i < arr1.length; i++) {
        if (arr1[i] !== arr2[i]) {
            return false;
        }
    }
    return true;
};
```