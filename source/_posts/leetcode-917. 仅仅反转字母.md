---
title: 917. 仅仅反转字母
date: 2022-02-23 10:24:47
description: 917. 仅仅反转字母 双指针
comments: true #是否可评论
toc: true #是否显示文章目录
categories: "leetcode题解" #分类
tags:   #标签
	- js
	- leetcode
	- 算法
---


# 917. 仅仅反转字母 双指针

## [查看原题](https://leetcode-cn.com/problems/reverse-only-letters/)

![在这里插入图片描述](https://img-blog.csdnimg.cn/adb44c1c233840048d14f8f29587efd1.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
## 解题思路

双指针，两端同时向中间判断，遇到非字母就跳过，遇到字母的交换位置。

## 代码

```javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseOnlyLetters = function(s) {
    const chars = s.split('')
    for(let l = 0, r = s.length - 1; l < r;) {
        while(l < r && !((chars[l] >= 'a' && chars[l] <= 'z') || (chars[l] >= 'A' && chars[l] <= 'Z')))
            l++
        while(r > l && !((chars[r] >= 'a' && chars[r] <= 'z') || (chars[r] >= 'A' && chars[r] <= 'Z')))
            r--
        if(l < r) {
            const tmp = chars[l]
            chars[l++] = chars[r]
            chars[r--] = tmp
        }
    }
    return chars.join("")
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/ba96f37c65b8428493c515e571f76abd.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
