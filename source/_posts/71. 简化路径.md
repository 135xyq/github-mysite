---
title: 71. 简化路径
date: 2022-01-06 14:09:21
toc: true
comments: true
description: 71. 简化路径 栈的应用
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---

# 71. 简化路径 栈的应用

## [查看原题](https://leetcode-cn.com/problems/simplify-path/)

## 解题思路

我们首先将给定的字符串 path 根据/分割成一个由若干字符串组成的列表，记为names。根据题目中规定的「规范路径的下述格式」，names 中包含的字符串只能为以下几种：

- 空字符串。例如当出现多个连续的 \texttt{/}/，就会分割出空字符串；

- 一个点 .

- 两个点 ..

- 只包含英文字母、数字或 _ 的目录名。

对于「空字符串」以及「一个点」，我们实际上无需对它们进行处理，因为「空字符串」没有任何含义，而「一个点」表示当前目录本身，我们无需切换目录。

对于「两个点」或者「目录名」，我们则可以用一个栈来维护路径中的每一个目录名。当我们遇到「两个点」时，需要将目录切换到上一级，因此只要栈不为空，我们就弹出栈顶的目录。当我们遇到「目录名」时，就把它放入栈。

这样一来，我们只需要遍历names中的每个字符串并进行上述操作即可。在所有的操作完成后，我们将从栈底到栈顶的字符串用 / 进行连接，再在最前面加上 / 表示根目录，就可以得到简化后的规范路径。

## 代码

```javascript
/**
 * @param {string} path
 * @return {string}
 */

// 始终以斜杠 '/' 开头。
// 两个目录名之间必须只有一个斜杠 '/' 。
// 最后一个目录名（如果存在）不能 以 '/' 结尾。
// 此外，路径仅包含从根目录到目标文件或目录的路径上的目录（即，不含 '.' 或 '..'）。

var simplifyPath = function(path) {
    const names = path.split("/");
    const stack = [];
    for (const name of names) {
        if (name === "..") {
            if (stack.length) {
                stack.pop();
            } 
        } else if (name.length && name !== ".") {
            stack.push(name);

        }
    }
    
    return "/" + stack.join("/");
};