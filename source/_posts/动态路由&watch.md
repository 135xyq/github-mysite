---
title: vue2中的动态路由
date: 2022-01-01 14:02:47
description: 动态路由的使用
comments: true #是否可评论
toc: true #是否显示文章目录
categories: 
  - 前端学习笔记 
  - vue
tags:   #标签
  - vue2
  - 前端
---


# 文章列表页逻辑

## 路由跳转逻辑

![动态路由-路由跳转逻辑](/images/vue2/动态路由-路由跳转逻辑.jpg)

## 组件逻辑

![动态路由-组件逻辑](/images/vue2/动态路由-组件逻辑.jpg)

### BlogList

![动态路由-BlogList](/images/vue2/动态路由-BlogList.jpg)

### BlogCategory

![动态路由-BlogCategory](/images/vue2/动态路由-BlogCategory.jpg)

# 知识

## 动态路由

我们希望下面的地址都能够匹配到`Blog`组件

- `/article`，显示全部文章
- `/article/cate/1`，显示分类`id`为`1`的文章
- `/article/cate/3`，显示分类`id`为`3`的文章
- ...

第一种情况很简单，只需要将一个固定的地址匹配到`Blog`组件即可

```js
{
  path: "/article",
  name: "Blog",
  component: Blog
}
```

但后面的情况则不同：匹配到`Blog`组件的地址中，有一部分是动态变化的，则需要使用一种特殊的表达方式：

```js
{
  path: "/article/cate/:categoryId",
  name: "CategoryBlog",
  component: Blog
}
```

在地址中使用`:xxx`，来表达这一部分的内容是变化的，在`vue-router`中，将变化的这一部分称之为`params`，可以在`vue`组件中通过`this.$route.params`来获取

```js
// 访问 /article/cate/3
this.$route.params // { categoryId: "3" }
// 访问 /article/cate/1
this.$route.params // { categoryId: "1" }
```

### 动态路由的导航

```vue
<router-link to="/article/cate/3">to article of category 3</router-link>

<router-link :to="{
   name: 'CategoryBlog',
   params: {
       categoryId: 3           
   }                    
}">to article of category 3</router-link>
```

## 编程式导航

除了使用`<RouterLink>`超链接导航外，`vue-router`还允许在代码中跳转页面

```js
this.$router.push("跳转地址"); // 普通跳转
this.$router.push({ // 命名路由跳转
  name:"Blog"
})

this.$router.go(-1); // 回退。类似于 history.go
```

## watch

利用`watch`配置，可以直接观察某个数据的变化，变化时可以做一些处理

```js
export default {
  // ... 其他配置
  watch: {
    // 观察 this.$route 的变化，变化后，会调用该函数
    $route(newVal, oldVal){
      // newVal：this.$route 新的值，等同 this.$route
      // oldVal：this.$route 旧的值
    },
    // 完整写法
    $route: {
      handler(newVal, oldVal){},
      deep: false, // 是否监听该数据内部属性的变化，默认 false
      immediate: false // 是否立即执行一次 handler，默认 false
    }
    // 观察 this.$route.params 的变化，变化后，会调用该函数
    ["$route.params"](newVal, oldVal){
      // newVal：this.$route.params 新的值，等同 this.$route.params
      // oldVal：this.$route.params 旧的值
    },
  	// 完整写法
    ["$route.params"]: {
      handler(newVal, oldVal){},
      deep: false, // 是否监听该数据内部属性的变化，默认 false
      immediate: false // 是否立即执行一次 handler，默认 false
    }
  }
}
```

