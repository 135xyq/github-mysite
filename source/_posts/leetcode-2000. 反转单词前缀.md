---
title: 2000. 反转单词前缀
date: 2022-02-02 11:35:20
description: 2000. 反转单词前缀 字符串反转 & 数组reverse
comments: true
toc: true
categories: leetcode题解
tags: 
	- 算法
	- leetcode
	- js
---

# 2000. 反转单词前缀 字符串反转 & 数组reverse

## [查看原题](https://leetcode-cn.com/problems/reverse-prefix-of-word/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/1dfb07f73c284d37b1377a6a2c2aaaf5.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路(字符串反转)

先求出反转的下标;
新建一个空字符串，将要反转的前缀，倒叙存到字符串中，循环，最后加上不需要更改的部分。

## 代码

```javascript
/**
 * @param {string} word
 * @param {character} ch
 * @return {string}
 */
var reversePrefix = function(word, ch) {
	const index = word.indexOf(ch);
	let str = '';
	if(index === -1){
		return word;
	}else{
		for(let i = 0;i<=index;i++){
			str += word[index -i]
		}
		return str + word.slice(index + 1);
	}
};

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/54b500f3ad4b471482c1efecd20235aa.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路(数组reverse)

将字符串转为数组，使用reverse反转

## 代码

```javascript

/**
 * @param {string} word
 * @param {character} ch
 * @return {string}
 */
var reversePrefix = function(word, ch) {
	const index = word.indexOf(ch);
	if(index === -1){
		return word;
	}else{
		const arr =  word.split('');
		const arr1 = arr.splice(index+1)
		const temp = arr.splice(0,index+1).reverse()
		return temp.join('') + arr1.join('')
	}
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/94cd2ca0d0a24444b80a5ac3824ed5d6.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
