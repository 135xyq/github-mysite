---
title: 牛客网-JS能力测评1
date: 2022-01-27 16:31:20
description: 
	 JS1 直角三角形 |  JS2 文件扩展名 | JS3 分隔符 | JS4 单向绑定 | JS5 创建数组 | JS6 判断版本 | JS7 无重复数组 | JS8 数组排序 | JS9 新数组 | JS10 计数器 | JS11 列表动态渲染 | JS12 模板字符串 | JS13 类继承 | JS14 参数解析器 | JS15 生成页码 | JS16 总成绩排名 | JS17 子字符串频次 | JS18 继承 | JS19 判断斐波那契数组 | JS20 数组扁平化 | JS21 数组过滤 |JS22 判断质数 | JS23 验证是否是身份证 | JS24 Symbol | JS25 相同的Set | JS26 Getter | JS27 控制动画 | JS28 Map保存节点 | JS29 全选 | JS30 回文字符串
comments: true
toc: true
categories: 
	- 牛客
	- JS能力测评
tags: 
	- 前端
	- js
	- 牛客
---


## JS1 直角三角形

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style>
            pre{
                font-size:20px;
            }
        </style>
    </head>
    <body>
        <pre>
        请补全JavaScript代码，要求在页面上渲染出一个直角三角形，三角形换行要求使用"br"实现。三角形如下：
        *
        **
        ***
        </pre>
        <hr>
        <div class='triangle'></div>

        <script>
            var triangle = document.querySelector('.triangle');
            for(let i = 0;i<3;i++){
                for(let j = 0;j<=i;j++){
                    const span = document.createElement('span');
                    span.innerHTML = "*";
                    triangle.appendChild(span);
                }
                triangle.appendChild(document.createElement('br'))
            }
            
        </script>
    </body>
</html>

```

## JS2 文件扩展名

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style>
            pre{
                font-size:20px;
                text-align: center;
            }
        </style>
    </head>
    <body>
        <pre>
            请补全JavaScript代码，要求以字符串的形式返回文件名扩展名，文件名参数为"filename"。
        </pre>
        <hr>
        <script>
            const _getExFilename = (filename) => {
                // 补全代码
                return '.' + filename.split('.')[1];
                
            }
        </script>
    </body>
</html>
```

## JS3 分隔符

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style>
            pre{
                font-size:20px;
                text-align: center;
            }
        </style>
    </head>
    <body>
        <pre>
            请补全JavaScript代码，要求返回参数数字的千分位分隔符字符串。
        </pre>
        <hr>

        <script type="text/javascript">
            function _comma(number) {
                // 补全代码
                if(number > 1000){
                    const arr = (number +'').split('');
                    for(let i = arr.length;i>3;i-=3){
                        arr.splice(i-3,0,',');
                    }
                    return arr.join('')
                }else if(number < -1000){
                    number = -number;
                    const arr = (number +'').split('');
                    for(let i = arr.length;i>3;i-=3){
                        arr.splice(i-3,0,',');
                    }
                    return '-' + arr.join('')
                } else{
                    return number+'';
                }
                
            }
            console.log(_comma(-123))  
        </script>
    </body>
</html>
```

## JS4 单向绑定

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style>
            pre{
                font-size:20px;
                text-align: center;
            }
        </style>
    </head>
    <body>
        <pre>
            请补全JavaScript代码，要求每当id为"input"的输入框值发生改变时触发id为"span"的标签内容同步改变。

            注意：必须使用DOM0级标准事件（onchange）
        </pre>
        <hr>
    	<input id="input" type="text" />
        <span id="span"></span>

        <script type="text/javascript">
            // 补全代码
            input.onchange =()=>{
                span.innerHTML =input.value;
            }
        </script>
    </body>
</html>
```

## JS5 创建数组

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style>
            pre{
                font-size:20px;
                text-align: center;
            }
        </style>
    </head>
    <body>
        <pre>
            请补全JavaScript代码，要求返回一个长度为参数值并且每一项值都为参数值的数组。
        注意：请勿直接使用for/while
        </pre>
        <hr>
    	
        <script type="text/javascript">
            const _createArray = (number) => {
                // 补全代码
                return new Array(Math.abs(number)).fill(number)
            }

            // console.log(_createArray(4))
        </script>
    </body>
</html>
```

## JS6 判断版本

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，该函数接收两个参数分别为旧版本、新版本，当新版本高于旧版本时表明需要更新，返回true，否则返回false。
注意：
1. 版本号格式均为"X.X.X"
2. X∈[0,9]
3. 当两个版本号相同时，不需要更新
        </pre>
        <hr>
    	
        <script type="text/javascript">
            const _shouldUpdate = (oldVersion, newVersion) => {
                // 补全代码
                const oldArr = oldVersion.split('.');
                const newArr = newVersion.split('.');
                let oldNumber = 0;
                let newNumber = 0;
                for(let i =0;i<3;i++){
                    oldNumber += 10 * oldNumber + parseInt(oldArr[i]);
                    newNumber += 10 * newNumber + parseInt(newArr[i]);
                }
                if(newNumber > oldNumber){
                    return true;
                }
                return false;
                
            }
            console.log(_shouldUpdate('0,0,0','0,0,2'))
        </script>
    </body>
</html>
```

## JS7 无重复数组

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，实现一个函数，要求如下：
1. 根据输入的数字范围[start,end]和随机数个数"n"生成随机数
2. 生成的随机数存储到数组中，返回该数组
3. 返回的数组不能有相同元素
注意：
1. 不需要考虑"n"大于数字范围的情况
        </pre>
        <hr>
        <script>
            const _getUniqueNums = (start,end,n) => {
                // 补全代码
                const arr = [];
                for(let i = 0;i<n;i++){
                   const temp = Math.ceil(Math.random()*(end - start)) + start;
                   if(!arr.includes(temp)){
                    arr.push(temp)
                   }
                }
                return arr;
            }
            console.log(_getUniqueNums(2,10,4))
        </script>
    </body>
</html>
```

## JS8 数组排序
```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
                <pre>
描述
请补全JavaScript代码，根据预设代码中的数组，实现以下功能：
1. 列表只展示数组中的name属性
2. 实现点击"销量升序"按钮，列表内容按照销量升序重新渲染
3. 实现点击"销量降序"按钮，列表内容按照销量降序重新渲染
注意：
1. 必须使用DOM0级标准事件（onclick）        
        </pre>
        <hr>
        <button class='up'>销量升序</button>
        <button class='down'>销量降序</button>
        <ul></ul>

        <script>
            var cups = [
                { type: 1, price: 100, color: 'black', sales: 3000, name: '牛客logo马克杯' },
                { type: 2, price: 40, color: 'blue', sales: 1000, name: '无盖星空杯' },
                { type: 4, price: 60, color: 'green', sales: 200, name: '老式茶杯' },
                { type: 3, price: 50, color: 'green', sales: 600, name: '欧式印花杯' }
            ]
            var ul = document.querySelector('ul');
            var upbtn = document.querySelector('.up');
            var downbtn = document.querySelector('.down');
            // 补全代码
            render(cups)
            function render(cups){
                ul.innerHTML= ''
                cups.forEach(cup=>{
                    const li = document.createElement('li');
                    li.innerHTML = i=cup.name;
                    ul.appendChild(li)
                })
            }
            upbtn.onclick = ()=>{
                cups = cups.sort((a,b)=>a.sales - b.sales)
                render(cups)
            }
            downbtn.onclick=()=>{
                cups = cups.sort((a,b)=>b.sales - a.sales)
                render(cups)
            }

        </script>
    </body>
</html>
```

## JS9 新数组

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，该函数接受两个参数分别为数组、索引值，要求在不改变原数组的情况下返回删除了索引项的新数组。
        </pre>
        <hr>
    	
        <script type="text/javascript">
            const _delete = (array,index) => {
                // 补全代码
                const newArr = [...array];
                newArr.splice(index,1);
                return newArr
            }

            console.log(_delete([1,2,3,4],2))
        </script>
    </body>
</html>
```

## JS10 计数器

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，要求每次调用函数"closure"时会返回一个新计数器。每当调用某个计数器时会返回一个数字且该数字会累加1。
注意：
1. 初次调用返回值为1
2. 每个计数器所统计的数字是独立的        
        </pre>
        <hr>
    	
        <script type="text/javascript">
            const closure = () => {
                // 补全代码
                let count = 1;
                return ()=>{
                    return count++;
                }
            }
        </script>
        <br>
        <br>
        <br>
        <hr>
        <pre>
            闭包的应用
        </pre>
    </body>
</html>
```


## JS11 列表动态渲染

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，将预设代码中的"people"数组渲染在页面中。实现下面的列表：
牛油1号 20岁
牛油2号 21岁
牛油3号 19岁
        </pre>
        <hr>
        <ul></ul>

        <script>
            var people = [
                { name: '牛油1号', id: 1, age: 20 },
                { name: '牛油2号', id: 2, age: 21 },
                { name: '牛油3号', id: 3, age: 19 },
            ]
            var ul = document.querySelector('ul');
            // 补全代码
            for(let i = 0;i<people.length;i++){
                const li = document.createElement('li');
                const spanName = document.createElement('span');
                const spanAge = document.createElement('sapn');
                spanName.innerText = people[i].name;
                spanAge.innerText = " "+ people[i].age + "岁";
                li.appendChild(spanName)
                li.appendChild(spanAge)
                ul.appendChild(li)
            }
        </script>
    </body>
</html>
```

## JS12 模板字符串

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，实现以下功能：
1.根据已有的person对象的注册时间求出距离当前时间的天数（天数向下取整）。
2. 将获得的天数和person数据拼接成字符串，作为h2标签的内容。
注意：
使用模板字符串进行字符串拼接，字符串最终内容如：尊贵的牛客网2级用户小丽您好，您已经注册牛客网3天啦~
        </pre>
        <hr>
        <h2></h2>

        <script>
            var person = {
                level: '2',
                name: '小丽',
                registTime: '2021-11-01',
            }
            var h2 = document.querySelector('h2');
            // 补全代码
            const registDate = new Date(person.registTime);
            const registMilTime = registDate.valueOf();
            const nowMilTime = new Date().valueOf();
            const days = Math.floor((nowMilTime - registMilTime) / (1000 * 60 * 60* 24));
            const str = `尊贵的牛客网${person.level}级用户${person.name}您好，您已经注册牛客网${days}天啦~`
            document.getElementsByTagName('h2')[0].innerText = str;

            
        </script>
    </body>
</html>
```

## JS13 类继承

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，完成类的继承。要求如下：
1. "Chinese"类继承于"Human"类
2. "Human"类实现一个函数"getName"，返回该实例的"name"属性
3. "Chinese"类构造函数有两个参数，分别为"name"、"age"
4. "Chinese"类实现一个函数"getAge"，返回该实例的"age"属性
        </pre>
        <hr>
        
        <script type="text/javascript">
            class Human {
                constructor(name) {
                    this.name = name
                    this.kingdom = 'animal'
                    this.color = ['yellow', 'white', 'brown', 'black']
                }
                // 补全代码
                getName(){
                    return this.name;
                }
            }

            // 补全代码
            class Chinese extends Human{
                constructor(name,age){
                    super(name)
                    this.age = age;
                }
                getAge(){
                    return this.age;
                }
            }
        </script>
    </body>
</html>
```

## JS14 参数解析器

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
描述:
请补全JavaScript代码，要求将字符串参数URL中的参数解析并以对象的形式返回。

示例1
输入：
getParams('https://nowcoder.com/online?id=1&salas=1000')

输出：
{id:1, salas: 100}      
        </pre>
        <hr>

        <script>
            // 第一种
            // const _getParams = (url) => {
            //     // 补全代码
            //     const index = url.indexOf('?');
            //     const str = url.slice(index+1)
            //     const arr = str.split('&');
            //     const obj = {};
            //     arr.forEach(item=>{
            //         const temp  =item.split('=');
            //         obj[temp[0]] = temp[1];
            //     })
            //     return obj;
                
            // }

            // 第二种
            const _getParams = (url) => {
                // 补全代码
                const arr = url.split('?')[1].split('&');
                const obj = {};
                arr.forEach(item=>{
                    const temp  =item.split('=');
                    obj[temp[0]] = temp[1];
                })
                return obj;
                
            }

            console.log(_getParams('https://nowcoder.com/online?id=1&salas=1000'))
        </script>
    </body>
</html>
```

## JS15 生成页码

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
描述:
请补全JavaScript代码，要求根据参数动态生成"li"标签页码并插入"ul"标签下。要求如下：
1. "allItem"为总数据项个数，"pageItem"为每页的数据项个数
2. "li"标签内容为当前页码数，页码从1开始

示例1
输入：
_createPage(13,2)
输出：
"li"长度为7，"li"内容依次为"1","2","3","4","5","6","7"
        </pre>
        <ul id="ul">
            
        </ul>
        <script type="text/javascript">

            // 第一种
            // const _createPage = (allItem, pageItem) => {
            //     // 补全代码
            //     const pageNum = Math.ceil(allItem / pageItem);
            //     const container = document.querySelector('#ul');
            //     for(let i = 1;i<=pageNum;i++){
            //         const li = document.createElement('li');
            //         li.innerText = i;
            //         container.appendChild(li)
            //     }
            // }


            const _createPage = (allItem, pageItem) => {
                // 补全代码
                const pageNum = Math.ceil(allItem / pageItem);
                let html = '';
                for(let i = 1;i<=pageNum;i++){
                    html += '<li>' + i + '</li>'
                }
                ul.innerHTML = html;
            }

            _createPage(13,2)
        </script>
    </body>
</html>
```

## JS16 总成绩排名

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，要求将数组参数中的对象以总成绩(包括属性"chinese"、"math"、"english")从高到低进行排序并返回。  
        </pre>
        <hr>
        
        <script type="text/javascript">
        const _rank = array => {
            // 补全代码
            return array.sort((a,b)=>(b.chinese +b.math +b.english)-(a.chinese +a.math +a.english))
        }

        console.log(_rank([
        {
            chinese:1,
            math:2,
            english:3
        },
        {
            chinese:1,
            math:3,
            english:3
        },
        {
            chinese:3,
            math:3,
            english:3
        }
        ]))
        </script>
    </body>
</html>
```




## JS17 子字符串频次

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style type="text/css">
            pre{
                font-size: 20px;
                text-align: center;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，该函数接受两个参数分别为字符串、子字符串，要求返回子字符串在字符串中出现的频次。
        </pre>

        <script>

            // 第一种
            const _searchStrIndexOf = (str, target) => {
                // 补全代码
                let fromIndex  = 0;
                let count = 0;
                while(str.indexOf(target,fromIndex) !== -1){
                    count++;
                    fromIndex = str.indexOf(target,fromIndex) + target.length;
                }
                return count;
            }

            console.log(_searchStrIndexOf("abcdeabfghabisdsa",'ab'))
        </script>
    </body>
</html>
```

## JS18 继承

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size:20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，实现以下功能：
1.给"Human"构造函数的原型对象添加"getName"方法，返回当前实例"name"属性
2. 将"Chinese"构造函数继承于"Human"构造函数
3. 给"Chinese"构造函数的原型对象添加"getAge"方法，返回当前实例"age"属性
        </pre>
        <hr>
        
        <script type="text/javascript">
            function Human(name) {
                this.name = name
                this.kingdom = 'animal'
                this.color = ['yellow', 'white', 'brown', 'black']
            }
            
            function Chinese(name,age) {
                Human.call(this,name)
                this.age = age
                this.color = 'yellow'
            }

            // 补全代码
            Human.prototype.getName = function(){
                return this.name;
            }
            Chinese.prototype = new Human();
            Chinese.prototype.constructor = Chinese;
            Chinese.prototype.getAge = function(){
                return this.age
            }
            
        </script>
    </body>
</html>
```

## JS19 判断斐波那契数组

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，要求以Boolean的形式返回参数数组是否为斐波那契数列。在数学上，斐波那契数列以如下方法定义：F(0)=0，F(1)=1, F(n)=F(n - 1)+F(n - 2)（n ≥ 2，n ∈ N）

注意：
1. [0,1,1]为最短有效斐波那契数列
        </pre>
        <hr>
        
        <script type="text/javascript">
            const _isFibonacci = array => {
                // 补全代码
                if(array.length < 3) return false;
                for(let i =0;i<array.length-2;i++){
                    if(array[i] + array[i+1] != array[i+2]){
                        return false;
                    }
                }
                return true;
            }

            console.log(_isFibonacci([0,1,1,2,3,4]))
        </script>
    </body>
</html>
```

## JS20 数组扁平化

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，要求将数组参数中的多维数组扩展为一维数组并返回该数组。

注意：
1. 数组参数中仅包含数组类型和数字类型

示例1
输入：
[1,[2,[3,[4]]]]
输出：
[1,2,3,4]
        </pre>
        <hr>
        
        <script>
            const _flatten = arr => {
                // 补全代码
                const str = String(arr);
                return str.split(',').map(item=>+item)
            }

            console.log(_flatten([1,[2,[3,[4]]]]))
        </script>
    </body>
</html>
```

## JS21 数组过滤

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，要求根据下拉框选中的条件变换重新渲染列表中展示的商品，且只展示符合条件的商品。
注意：
1. 必须使用DOM0级标准事件（onchange）
2. 建议使用ES6的filter方法   
        </pre>
        <hr>
        <select name="" id="">
            <option value="0">请选择销量范围</option>
            <option value="1">&lt100</option>
            <option value="2">100~500</option>
            <option value="3">&gt500</option>
        </select>
        <ul>
            <li>牛客logo马克杯</li>
            <li>无盖星空杯</li>
            <li>老式茶杯</li>
            <li>欧式印花杯</li>
        </ul>

        <script>
            var cups = [
                { type: 1, price: 100, color: 'black', sales: 60, name: '牛客logo马克杯' },
                { type: 2, price: 40, color: 'blue', sales: 100, name: '无盖星空杯' },
                { type: 4, price: 60, color: 'green', sales: 200, name: '老式茶杯' },
                { type: 3, price: 50, color: 'green', sales: 600, name: '欧式印花杯' }
            ]
            var select = document.querySelector('select');
            var ul = document.querySelector('ul');
            // 补全代码
            select.onchange = function(e){
                ul.innerHTML = ""
                const value = e.target.value;
                let filterCups;
                switch(value){
                    case '1': 
                        filterCups = cups.filter(item=>item.sales < 100)
                        break;
                    case '2':
                        filterCups = cups.filter(item=>(item.sales <= 500) && (item.sales >= 100))
                        break;
                    case '3':
                        filterCups = cups.filter(item=>item.sales > 500)
                    default:
                        break;
                }
                let str = '';
                filterCups.forEach(cup=>{
                    str += '<li>' + cup.name + '</li>'
                })
                ul.innerHTML = str;
            }
            
        </script>
    </body>
</html>
```

## JS22 判断质数

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，要求在Number对象的原型对象上添加"_isPrime"函数，该函数判断调用的对象是否为一个质数，是则返回true，否则返回false。
        </pre>
        <hr>
        <script type="text/javascript">
            // 补全代码
            Number.prototype._isPrime = function(){
                const value = this.valueOf();
                if(value < 2){
                    return false;
                }
                for(let i = 2;i<value;i++){
                    if(value % i === 0){
                        return false;
                    }
                }
                return true;
            }


            console.log((2)._isPrime())
            
        </script>
    </body>
</html>
```

## JS23 验证是否是身份证

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，要求以Boolean的形式返回字符串参数是否符合身份证标准。

注意：
1. 无需考虑地区信息、出生日期、顺序码与校验码的验证

示例1
输入：
_isCard('21062319980907888X')
输出：
true

        </pre>
        <hr>

        <script>
            const _isCard = number => {
                // 补全代码
                const length = number.length;
                if(length !== 18){
                    return false;
                }
                for(let i = 0;i < length-1; i++){
                    if(number[i] > '9' || number[i] < '0'){
                        return false;
                    }
                }
                if(number[length-1]=== 'X' || number[length-1]=== 'x'  || (number[length -1] > '0' && number[length-1] < '9')){
                    return true;
                }else{
                    return false;
                }
            }


            console.log(_isCard('21062319980907888X'))
        </script>
    </body>
</html>
```

## JS24 Symbol

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，要求以键/值对的对象形式返回参数数组。要求如下：
1. 键名的数据类型为Symbol
2. 键值为当前数组项
3. Symbol的描述为当前数组项
4. 返回普通对象
        </pre>
        <hr>
        
        <script type="text/javascript">
            const _symbolKey = array => {
                // 补全代码
                const obj = {}
                array.forEach(item=>{
                   obj[Symbol(item)] = item; 
                })
                return obj;
            }

            console.log(_symbolKey([121,1,2,23,]))
        </script>
    </body>
</html>
```


## JS25 相同的Set

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <style type="text/css">
            pre{
                font-size: 20px;
                text-align: center;
            }
        </style>
    </head>
    <body>
        <pre>
            请补全JavaScript代码，要求以boolean的形式返回两个Set对象参数是否一样，是则返回true，否则返回false。
        </pre>
        <hr>
        
        <script>
            const _isSameSet = (s1, s2) => {
                // 补全代码
                if(s1.size !== s2.size){
                    return false;
                }
                for (const key of s1){
                    if(!s2.has(key)){
                        return false;
                    }
                }
                return true;
            }

            console.log(_isSameSet(new Set([1,21,32,3]),new Set([1,32,21,3])))
        </script>
    </body>
</html>
```

## JS26 Getter

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
            }
        </style>
    </head>
    <body>
        <pre>
请补全JavaScript代码，完成名为"Rectangle"的矩形类。要求如下：
1. 构造函数只包含两个参数，依次为"height"、"width"
2. 设置Getter，当获取该对象的"area"属性时，返回该对象"height"与"width"属性的乘积

示例1
输入：
new Rectangle(12,12).area
输出：
144    
        </pre>
        <hr>
        
        <script type="text/javascript">
            class Rectangle {
                // 补全代码
                constructor(height,width){
                    this.height = height,
                    this.width = width
                }

                get area(){
                    return this.height * this.width;
                }
            }


            console.log(new Rectangle(12,12).area)
        </script>
    </body>
</html>
```

## JS27 控制动画

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
            }
            #rect {
                width: 120px;
                height: 100px;
                background-color: black;
                /*补全代码*/
                animation:rect 10s infinite;
                
            }
            @keyframes rect {
                from {
                    transform: rotate(0deg);
                }
                to {
                    transform: rotate(360deg);
                }
            }
        </style>
    </head>
    <body>
        <pre>
请补全代码，要求当滑动id为"range"的滑块控件时可以改变id为"rect"的矩形旋转速度。要求如下：
1. id为"rect"的矩形初始动画周期为10秒
2. id为"range"的滑块控件默认值为1、最小值为、最大值为10、滑动间隔为1
3. 当滑动滑块值为1时，矩形动画周期为10秒、当...，为...、当滑动滑块值为10时，矩形动画周期为1秒
注意：
1. 必须使用DOM0级标准事件（onchange）
        </pre>
        <hr>
        <!-- 补全代码 -->
        <div id="rect"></div>
        <input id="range" />
        
        <script type="text/javascript">
            // 补全代码
            range.onchange = function(){
                console.log(this.value)
                let value = Number(this.value);
                if(value >=1 && value <=10){
                    rect.style.animation = `rect ${10 - value + 1}s infinite`
                }
                
            }
            
        </script>
    </body>
</html>
```

## JS28 Map保存节点

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
                text-align: center;
            }
        </style>
    </head>
    <body>
        <pre>
            请补全JavaScript代码，要求将页面中的"p"标签以键名的形式保存在Map对象中，键名所对应的键值为该"p"标签的文字内容。
        </pre>
        <hr>
        <p>1</p>
        <script type="text/javascript">
            const _elementKey = () => {
                // 补全代码
                const map = new Map();
                const p = document.getElementsByTagName('p')[0];
                map.set(p,p.innerText);
                return map;
            }

            console.log(_elementKey())
        </script>
    </body>
</html>
```

## JS29 全选

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
    </head>
        <style>
            pre{
                font-size: 20px;
            }
            ul {
                list-style: none;
            }
        </style>
    <body>
        <pre>
请补全JavaScript代码，实现以下效果：
1. 选中"全选"框，以下所有选项全部勾选。
2. 把"全选"框从选中状态勾选成未选中状态，其他复选框全部取消选中效果。
3. 当其他复选框全部选中，"全选框"为选中状态。
4. 当其他复选框有一个未选中，"全选框"取消选中状态。

注意：
1. 必须使用DOM0级标准事件（onchange）
        </pre>
        <hr>
        <ul>
            <li>全选<input type='checkbox' id='all'></li>
            <li>Java<input type='checkbox' class='item'></li>
            <li>javaScript<input type='checkbox' class='item'></li>
            <li>C++<input type='checkbox' class='item'></li>
            <li>python<input type='checkbox' class='item'></li>
            <li>.net<input type='checkbox' class='item'></li>
        </ul>

        <script>
            // 第一种方法，不知道为啥，本地调试没问题，就是过不了
            // 补全代码
            const items = [...document.getElementsByClassName('item')];
            const all = document.getElementById('all');
            let arr = new Array(items.length).fill(false);
            items.forEach((item,index)=>{
                item.onchange=function(e){
                    if(this.checked){
                        arr[index] = true;
                    }else{
                        arr[index] = false;
                    }
                    render()  
                }
                                  
            })
            all.onchange = function(){
                if(this.checked){
                    arr = arr.map(item=>item=true)
                }else{
                    arr = arr.map(item=>item=false)
                }
                render();
                items.forEach(i=>{
                    console.log(i.checked)
                })
            }
            function render(){
                let flag = true;
                for(let i =0;i<items.length;i++){
                    if(arr[i]){
                        items[i].checked = true;
                    }else{
                        flag = false;
                        items[i].checked = false;
                    }
                }
                if(flag){
                    all.checked = true;
                }else{
                    all.checked = false;
                }
            }

            // 第二种方法
            var all = document.getElementById("all")
            var options = Array.from(document.querySelectorAll(".item"))
            // 补全代码
            all.onchange = () => {
                options.forEach((item) => {
                    item.checked = all.checked
                })
            }
            options.forEach((item) => {
                item.onchange = function () {
                    let isCheckAll = true
                    options.forEach((item) => {
                        if (!item.checked) {
                            isCheckAll = false
                        }
                    })
                    all.checked = isCheckAll
                }
            })
        </script>
    </body>
</html>
```

## JS30 回文字符串

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset=utf-8>
        <style type="text/css">
            pre{
                font-size: 20px;
                text-align: center;
            }
        </style>
    </head>
    <body>
        <pre>
            请补全JavaScript代码，要求以boolean的形式返回参数字符串是否为回文字符串。
        </pre>
        <hr>
        <script type="text/javascript">
            const _isPalindrome = string => {
                // 补全代码
                const length = string.length;
                for(let i = 0;i<Math.floor(length / 2);i++){
                    if(string[i]!==string[length-1-i]){
                        return false;
                    }
                }
                return true;
            }

            console.log(_isPalindrome("asdffdsa"))
        </script>
    </body>
</html>
```

