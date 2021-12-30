---
title: 563. 二叉树的坡度
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 563. 二叉树的坡度   树的深度优先搜索
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 563. 二叉树的坡度   树的深度优先搜索
## [查看原题](https://leetcode-cn.com/problems/binary-tree-tilt/)
## 解题思路
树的深度优先搜索

## 代码

```javascript
var findTilt = function(root) {
    let sum = 0;

    function dfs(node) {
        if (!node) {
            return 0;
        }
        const leftNum = dfs(node.left);
        const rightNum = dfs(node.right);
        sum += Math.abs(leftNum - rightNum);
        return leftNum + rightNum + node.val;
    }
    dfs(root);
    return sum;
};

```