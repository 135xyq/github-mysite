---
title: 1614. 括号的最大嵌套深度
date: 2022-01-07 13:02:21
toc: true
comments: true
description: 1614. 括号的最大嵌套深度 栈的应用
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---

# 1614. 括号的最大嵌套深度 栈的应用

## [查看原题](https://leetcode-cn.com/problems/maximum-nesting-depth-of-the-parentheses/)

## 解题思路

寻找括号的最大嵌套深度，左括号和右括号构成一对，正好符号栈的特点（先进后出），可以构成一对。
1. 遍历字符串遇到 ')'将其push到栈中
2. 遇到'('比较当前栈中元素个数和最大值比较，不断更新最大值，并pop出一个元素

## 代码

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var maxDepth = function(s) {
	const stack = [];
	let max = 0;
	for(let i = 0;i < s.length;i++){
		if(s.charAt(i) === '('){
			stack.push(s.charAt(i))
		}else if(s.charAt(i) === ')'){
			max = stack.length > max ? stack.length : max;
			stack.pop()
		}
	}
	return max;
	
};
```