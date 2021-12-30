---
title: 391. 完美矩形
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 391. 完美矩形 map哈希
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 391. 完美矩形 map哈希
## [查看原题](https://leetcode-cn.com/problems/perfect-rectangle/)
## 解题思路
### 只要满足两个条件就是完美矩形：
1.所有矩形总面积 == 恰好围住所有矩形的大矩形的面积
2.任意两个矩形都没有重叠。这种情况下由于所有矩形是镶嵌的，所以位于大矩形内（除了大矩形的四个角）的任何位置的小矩形顶点数只可能为0,2,4。其他任何情况都代表有重叠。而大矩形四个顶点处的小矩形顶点数量只能为1。

### 判断矩形总面积是否等于围住所有矩形的大矩形的面积
1. 先将大的数组拆开为四个小数组，每个数组表示左下和右上两个点的横纵坐标
2. 找出大矩形的左下和右上坐标
3. 求出大矩形的面积
4. 求出每个小矩形的面积求和
5. 判断是否相等，不相等直接返回 false 相等则进入下一判断

### 判断是否有重叠
1. 将每个小矩形的坐标存到一个大数组中
2. 循环数组，用map哈希将每个坐标点的重复次数映射
3.判断每个坐标点的情况（大矩形内（除了大矩形的四个角）的任何位置的小矩形顶点数只可能为0,2,4。其他任何情况都代表有重叠。而大矩形四个顶点处的小矩形顶点数量只能为1。）
3. 最后返回true ，此处返回说明前面的条件都满足

## 代码

```javascript
/**
 * @param {number[][]} rectangles
 * @return {boolean}
 */

//  只要满足两个条件就是完美矩形：
// 1.所有矩形总面积 == 恰好围住所有矩形的大矩形的面积
// 2.任意两个矩形都没有重叠。这种情况下由于所有矩形是镶嵌的，所以位于大矩形内（除了大矩形的四个角）的任何位置的小矩形顶点数只可能为0,2,4。其他任何情况都代表有重叠。而大矩形四个顶点处的小矩形顶点数量只能为1。
//  */
var isRectangleCover = function(rectangles) {
    let nums1 = [],
        nums2 = [],
        nums3 = [],
        nums4 = [];
    for (let i = 0; i < rectangles.length; i++) {
        nums1.push(rectangles[i][0]);
        nums2.push(rectangles[i][1]);
        nums3.push(rectangles[i][2]);
        nums4.push(rectangles[i][3]);
    }
    const minNum1 = Math.min(...nums1);
    const minNum2 = Math.min(...nums2);
    const maxNum1 = Math.max(...nums3);
    const maxNum2 = Math.max(...nums4);
    const maxArear = (maxNum2 - minNum2) * (maxNum1 - minNum1);
    let sum = 0;
    rectangles.forEach(item => {
        sum += ((item[3] - item[1]) * (item[2] - item[0]));
    })
    let a = []; //存放每个坐标的字符串
    if (sum === maxArear) {
        for (let i = 0; i < rectangles.length; i++) {
            // 将四个角的坐标加入
            a.push(nums1[i] + "," + nums2[i]);
            a.push(nums1[i] + "," + nums4[i]);
            a.push(nums3[i] + "," + nums4[i]);
            a.push(nums3[i] + "," + nums2[i]);
        }
        let map = new Map();
        for (let i = 0; i < a.length; i++) {
            if (map.has(a[i])) {
                map.set(a[i], map.get(a[i]) + 1);
            } else {
                map.set(a[i], 1);
            }
        }
        // 判断四个顶点是否重复一次
        // 四个顶点
        const leftBottom = minNum1 + ',' + minNum2;
        const leftTop = minNum1 + ',' + maxNum2;
        const rightBottom = maxNum1 + ',' + minNum2;
        const rightTop = maxNum1 + ',' + maxNum2;
        const four = [leftBottom, leftTop, rightBottom, rightTop];
        //遍历map对象判断
        for (const [key, value] of map) {
            if (value == 1) {
                if (four.indexOf(key) === -1) {
                    return false;
                }
            } else if (value == 2) {
                if (four.indexOf(key) != -1) {
                    return false;
                }
            } else if (value == 4) {
                if (four.indexOf(key) != -1) {
                    return false;
                }
            } else {
                return false;
            }
        }
        return true;
    } else {
        return false;
    }
};
```