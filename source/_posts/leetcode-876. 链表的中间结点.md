---
title: 876. 链表的中间结点
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 876. 链表的中间结点 先找到链表的长度，再返回对应一半的值
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 876. 链表的中间结点 先找到链表的长度，再返回对应一半的值

## [查看原题](https://leetcode-cn.com/problems/middle-of-the-linked-list/)

## 解题思路
1. 遍历列表进行链表长度的统计
2. 返回链表的一半长度后面的数据

## 代码

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var middleNode = function(head) {
    let count = 0; //链表的长度
    let p = head;
    let n = head;
    while (p) {
        count++;
        p = p.next;
    }
    const mid = count % 2 ? Math.floor(count / 2) : Math.ceil(count / 2);
    while (mid--) {
        n = n.next;
    }
    return n;
};

```