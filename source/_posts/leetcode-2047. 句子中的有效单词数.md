---
title: 2047. 句子中的有效单词数
date: 2022-01-27 11:17:20
description: 2047. 句子中的有效单词数  正则&模拟所有条件求解
comments: true
toc: true
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---

# 2047. 句子中的有效单词数  正则&模拟所有条件求解

## [查看原题](https://leetcode-cn.com/problems/number-of-valid-words-in-a-sentence/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/a3689751ef404a5fa9e4f77ce0239add.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路(正则)

使用正则表达式来判断是否符合条件。
1. 将字符串经过trim,replace,split来去除两端的空格，并按空格将字符串转为一个个单词存放到数组arr中;
2. 写出两个正则语句```/^[a-z]*[!,.]{0,1}$/```(单词不包含-)；```/^[a-z]+-[a-z]+[!,.]{0,1}$/```(单词包含-);
3. 循环arr,判断每一个单词，使用test将单词与两个规则匹配，只有有一个满足就符合条件;

## 代码

```javascript
/**
 * @param {string} sentence
 * @return {number}
 */
var countValidWords = function(sentence) {
	/*
	仅由小写字母、连字符和/或标点（不含数字）。
	至多一个 连字符 '-' 。如果存在，连字符两侧应当都存在小写字母（"a-b" 是一个有效单词，但 "-ab" 和 "ab-" 不是有效单词）。
	至多一个 标点符号。如果存在，标点符号应当位于 token 的 末尾 。
	*/

	const arr =  sentence.trim().replace(/ +/g,' ').split(' ');
	let count = 0;
	const reg1 = /^[a-z]*[!,.]{0,1}$/;//无 - 
	const reg2 = /^[a-z]+-[a-z]+[!,.]{0,1}$/;//有 -
	arr.forEach(item=>{
		
		if(reg1.test(item)|| reg2.test(item)){
			count++;
		}
	})
	return count;
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/4ad97e7c8d0743cc871d9e5e9d759e75.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)


## 解题思路(模拟所有条件求解)

找出各种不符合条件的情况，来判断每一个单词

### 不符合条件的情况

1. 单词中包含数字
2. 多于一个连词符 -
3. 连词符左右两端不是小写字母
4. 单词中包含不至一个标点符号
5. 标点符号不在单词结尾


### 步骤

1. 使用split将字符串依照空格分为一个个单词，存到数组arr中；
2. 循环数组arr，遍历每个单词依照条件进行判断；

## 代码

```javascript

/**
 * @param {string} sentence
 * @return {number}
 */
var countValidWords = function(sentence) {
	const arr =  sentence.split(' ');
	let count = 0;
	arr.forEach(item=>{
		if(item !=''){
			let flag1  = 0;//连字符的个数
			let flag2 = 0;//标点符号的个数
			let i;
			for(i = 0;i<item.length;i++){
				if(item[i] >= '0' && item[i] <= "9"){
					break;
				}else if(item[i] === '-'){
					if(flag1 > 0 || i===0 || i ===item.length-1|| item[i-1] < 'a' || item[i-1]>'z' || item[i+1] <'a'||item[i+1] >'z'){
						break;
					}
					flag1++;
				}else if(item[i] === '!' || item[i]==="." || item[i] ===','){
					if(flag2 > 0 || i !== item.length-1){
						break;
					}
					flag2++;
				}
			}
			if(i === item.length){
				count++;
			}
		}
	})
	return count;
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/b8c114a45ba74de4805d0c2e735a53d4.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
