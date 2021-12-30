---
title: 283. 移动零 
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 283. 移动零 
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 283. 移动零 
## [查看原题](https://leetcode-cn.com/problems/move-zeroes/)
## 解题思路
1. 将right赋值为nums.length-1,代表当前连续0开始的位置
2. lef赋值为 0 表示当前数组扫描的位置
3. 从左到右扫描数组，如果当前项是 0 则将从数组当前项到连续0开始位置之间的数组项都向前移动一位，然后在后面补0，同时更新 right-- ,不在更新left，防止有连续的0，再次回到这个位置
4. 如果当前项不是0 则更新left++

## 代码
```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    let left; //左指针，开始循环
    let length = nums.length;
    let right = length - 1; //右指针的最开始位置
    for (left = 0; left <= right;) {
        // 如果当前项是0则将当前项之后的数值向前移一位
        if (nums[left] === 0) {
            for (let j = left + 1; j <= right; j++) {
                nums[j - 1] = nums[j]
            }
            nums[right] = 0;
            right--;
        } else {
            left++;
        }
    }
};
```