---
title: 318. 最大单词长度乘积 
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 318. 最大单词长度乘积 暴力循环
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 318. 最大单词长度乘积 暴力循环
## [查看原题](https://leetcode-cn.com/problems/maximum-product-of-word-lengths/)

## 解题思路
直接双层循环判断两项是否有字符一样，如果不一样则计算长度的乘积，并与最大值比较，不断更新最大值
## 代码
```javascript
function maxProduct(words) {
    let i, j;
    let max = 0;
    for (i = 0; i < words.length; i++) {
        for (j = i + 1; j < words.length; j++) {
            let flag = 0; //表示有无重复
            const set = new Set(words[i]);
            const set1 = new Set(words[j]);
            for (const item of set1) {
                if (set.has(item)) {
                    flag = 1;
                    break;
                }
            }
            if (!flag) {
                if ((words[i].length * words[j].length) > max) {
                    max = words[i].length * words[j].length
                }
            }
        }
    }
    return max;
}
```