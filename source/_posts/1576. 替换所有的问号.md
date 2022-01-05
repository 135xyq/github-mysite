---
title: 1576. 替换所有的问号
date: 2022-01-05 13:47:30
toc: true
comments: true
description: 1576. 替换所有的问号 遍历扫描 多重条件判断 & 三种符号替换
categories: leetcode题解
tags: 
	- 算法
	- leetcode
	- js
---

# 1576. 替换所有的问号 遍历扫描 多重条件判断 & 三种符号替换

## [查看原题](https://leetcode-cn.com/problems/replace-all-s-to-avoid-consecutive-repeating-characters/)


## 解题思路（多重条件判断）

我的变换格式是：```String.fromCharCode((arr[i-1].charCodeAt() - 97 + 23) % 26 + 97```来保证前后不重复

1. 将字符串转为数组，因为js中字符串无法更改单独一项的值
2. 遍历数组，判断是否是'?'，如果是则分为三种情况
	1. 在开头：判断数组的长度是否为1 ，若为1，则直接返回'a',若不是则变换后面一个字符，填充到当前位置。
	2. 在结尾：变换前一个元素，填充到当前位置。
	3. 在中间：判断在前一个元素变换后是否和后一个元素相同，若相同，则使用后一个字符的变换，不相同直接使用。

## 代码

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var modifyString = function(s) {
	let arr = s.split('');
	for(let i = 0;i<arr.length;i++){
		if(arr[i] === '?'){
			if(i === 0){
				if(arr.length === 1){
					arr[i] = 'a';
				}else{
					if(arr[i+1] === '?'){
						arr[i] = 'b';
					}else{
						arr[i] = String.fromCharCode((arr[i+1].charCodeAt() - 97 + 23) % 26 + 97);
					}
					
				}
			}else if(i === arr.length -1){
				arr[i] = String.fromCharCode((arr[i-1].charCodeAt() - 97 + 23) % 26 + 97);
			}else{
				if(String.fromCharCode((arr[i-1].charCodeAt() - 97 + 23) % 26 + 97) === arr[i+1]){
					arr[i] = String.fromCharCode((arr[i+1].charCodeAt() - 97 + 23) % 26 + 97)
				}else{
					arr[i] = String.fromCharCode((arr[i-1].charCodeAt() - 97 + 23) % 26 + 97);
				}
			}
		}
	}
	return arr.join('')

};
```


## 解题思路

在替换时，实际不需要遍历所有的小写字母，只需要遍历三个互不相同的字母，就能保证一定找到一个与前后字符均不相同的字母，在此我们可以限定三个不同的字母为 ('a','b','c')

## 代码

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var modifyString = function(s) {
	const arr = [...s];
	for(let i =0;i<arr.length;i++){
		if(arr[i] === '?'){
			for(let j =0;j<3;j++){
				if ((i > 0 && arr[i - 1] === String.fromCharCode('a'.charCodeAt() + j)) || (i < arr.length - 1 && arr[i + 1] === String.fromCharCode('a'.charCodeAt() + j))) {
                    continue;
                }
                arr[i] = String.fromCharCode('a'.charCodeAt() + j);
                break;
			}
		}
	}
	return arr.join('')
};

```
