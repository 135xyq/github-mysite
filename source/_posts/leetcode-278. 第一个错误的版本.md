---
title: 278. 第一个错误的版本
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 278. 第一个错误的版本  二分法，注意判断结束条件
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 278. 第一个错误的版本  二分法，注意判断结束条件
## [查看原题](https://leetcode-cn.com/problems/first-bad-version/)
## 解题思路
二分算法判断
如果当前项不是错误版本，说明错误版本在后面更新 right = mid + 1
如果当前是错误版本，则需要继续判断当前是不是第一个错误版本
    - 如果当前是错误版本且第 mid - 1 不是错误版本，则说明mid是第一个错误版本
    - 如果当前是错误版本且第 mid - 1 是错误版本，则继续循环

## 代码

```javascript
/**
 * Definition for isBadVersion()
 * 
 * @param {integer} version number
 * @return {boolean} whether the version is bad
 * isBadVersion = function(version) {
 *     ...
 * };
 */

/**
 * @param {function} isBadVersion()
 * @return {function}
 */
var solution = function(isBadVersion) {
    /**
     * @param {integer} n Total versions
     * @return {integer} The first bad version
     */
    return function(n) {
        let left = 1;
        let right = n;
        while(left <= right) {
            mid = Math.floor((left + right) / 2)
            if(!isBadVersion(mid)){
                left = mid+1;
            }else if(isBadVersion(mid)){
                if(isBadVersion(mid - 1)){
                    right = mid-1;
                }else{
                    return mid;
                }
            }
        }
    };
};
```