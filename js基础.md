# js笔记

## js基础

### 变量

```js
   <script>
        // 申明变量并赋值
        var a ="1";
        // 申明多个变量
        var s1=1,s2=2;
        console.log(s1,s2);
        console.log(a);
    </script>
```

### 数据类型

#### 简单数据类型

1. Number 

   - NaN:not a number(NaN 与任何值都不相等包括他自己)
   - isNaN:is not a number 判断变量是否是数字 

2. String
   - 获取字符的长度 str.length
   - 字符串的拼接使用+号
3. boolean类型
   - true    1
   - false     0
4. undefined 表示一个申明了没有赋值的变量，变量只申明的时候默认是undefined
5. null 表示一个空 变量的值如果想为null 必须手动设置

#### 复杂数据类型

object

#### 获取变量的数据类型

`console.log(typeof 2.3)`

#### 数据类型装换

##### 转换成字符串类型

1. ​	toString（）`console.log(typeof true.toString())`

   基本数据类型undefined 和null 是 没有toString（）方法，需要使用string（null）方法

2.  String（参数）`String(undefined) 返回 'undefined '`  `string（null)返回 ‘null’`

##### 转换为数值类型

1. Number（参数） 可以把任意值转换为数值类型 如果要转的的字符串中有一个不是数值的字符 则返回NaN

    ```js
    Number(null)
    0
    Number(undefined)
    NaN
    Number(true)
    1
    Number("a")
    NaN
    ```

    

2. parseInt(参数) 前面是数字 直到非数值结束  

    ```js
    parseInt(null)
    NaN
    parseInt(undefined)
    NaN
    parseInt(false)
    NaN
    parseInt("12252a")
    12252
    parseInt("aaa1")
    NaN
    ```

3. parseFloat(变量)

    ```js
    parseFloat(1.36)
    1.36
    parseFloat(null)
    NaN
    parseFloat(undefined)
    NaN
    parseFloat(25.)
    25
    ```

##### 转换为boolean类型	

​	null  undefined '' 0 NaN 这5中类型转换时false 别的任何值都是true

```js
 Boolean(null)
false
Boolean(undefined)
false
Boolean(0)
false
Boolean(NaN)
false
Boolean('')
false
Boolean(-55)
true
```



### 操作符

#### 关系运算符

##### 比较相等

1. ==      !=  两个等号判断的是值是否相等 

2. ===    !===    三个等号 判断数据类型和数值同时相同

 ```js
var a = 10;
var b = '10'
console.log(a == b)
true
a ===b
false
a !=b
false
a !== b
true
a =10
10
b = 10
10
a !== b
false
 ```

   

### 流程控制语句

和Java一样的

### 数组

#### 数组的定义

`var arr= ['a','v']`

#### 数组的常用方法

获取数组长度   `console.log(arr2.length)`

### 函数

### 对象 

### 简单类型和复杂类型

### 内置对象

### 数组方法

### 字符串的方法

------



## js高级语法









