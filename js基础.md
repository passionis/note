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
   - 字符串的拼接使用+号或者String的contact（）方法
3. boolean类型
   - true      1
   - false     0
4. undefined 表示一个申明了但没有赋值的变量，变量只申明的时候默认是undefined
5. null 表示一个空 变量的值如果想为null 必须手动设置

#### 复杂数据类型

object

#### 获取变量的数据类型

`console.log(typeof 2.3)`

#### 数据类型装换

##### 1. 转换成字符串类型

1. ​	toString（）`console.log(typeof true.toString())`

   基本数据类型undefined 和null 是 没有toString（）方法，需要使用String（null）创建对象

2.  String（参数）`String(undefined) 返回 'undefined '`  `string（null)返回 ‘null’`

##### 2.转换为数值类型

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

##### 3.转换为boolean类型	

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

2. ===    !==    三个等号 判断数据类型和数值同时相同

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

### 函数

### arguments 对象

#### 作用域

##### 1.全局作用域：

​	在script或者一个独立的js的文件中 在全局作用域中定义的变量，浏览器窗口关闭了才会销毁内存

```javascript
// 全局定义变量 可以在js文件中全局引用
var str = 'aaa';
function add() {
	// 如果不用var进行申明的话  也可以全局引用   但是不推荐这种写法
	aaa = 'vvv'
	console.log(str);
 }
 add();
 console.log(aaa)
```

##### 2.局部作用域：

​	局部变量只有在定义该变量的函数中可以访问,方法执行完成内存就销毁了

##### 3.块及作用域：

​	在{}中定义的var 变量 外部获取不到数据

```javascript
{
     var num = 2;
     console.log(num);
}
     console.log('外部'+num);
```

#### 预解析

##### 1. 变量提升 

   把变量的声明提升到当前作用域的最上面 ，不包括变量赋值

##### 2. 函数提升 

   把函数的声明提升到当前作用域的最上面（函数内部的变量也会进行提升） ，不包含函数的调用

   变量和函数提升后，依次执行代码 赋值、调用

   ```javascript
var a = 25;
function add() {
   console.log(a);
   var a ="dd";
}
add();
// 该打印结果是undefined  
// 分析  根据预解析  
var a ;// 会先声明一个var a ; 
function add (){// 申明一个方法
  // 局部作用域的预解析
  var a ;
  console.log(a);
   a='dd'
}
a = 25;
add();
   ```

   变量名和函数名相同预解析的处理逻辑

   ```javascript
console.log(a);
function a() {
    console.log('aaa');
}
var a = 1;
console.log(a);

/**
 预解析分析,在预解析过程中如果变量名和方法名相同 方法名优先	
 var a ;
 function a(){
     console.log('aaaa');
 }
 console.log(a)
 a = 1;
 console.log(a);
 */

/**
执行结果
  ƒ a() {
  	console.log('aaa');
  }
  1
*/
            
   ```

   

### 对象 

#### 对象创建方式

##### 1. 字面量

```javascript
var dog={
    name :"name",
    age:24,
    eat :function(){
        console.log("匿名函数")
    }
}
//获取属性方式一
console.log(dog.age);
dog.eat();
//获取属性方式二
console.log(dog["name"])
```

##### 2. 通过new object（） 创建一个空的对象

```js
// 创建一个空对象
var o = new Object();
// 通过javascript 的动态特性 添加属性和方法
o.name = 'hahah';
console.log(o.name);
o.func =function(){
    console.log("定义一个方法")
}
o.func();
```

##### 3. 工厂方法

```javascript
 function create(name,age,sex){
    var ob = new Object();
    ob.name = name;
    ob.age = age;
    ob.eat = function(){
        console.log(name)
    }
    return ob;
}
var ob1 = create('张三',22,0);
ob1.eat();
```

##### 4. 构造方法

   ```javascript
function Body(name, age, sex) {
    this.name = name;
    this.age = age;
    this.sex = sex;
    this.eat = function () {
        console.log(this.name + this.age + this.sex);
    }
} 
var body = new Body('李四', 22, 1);
body.eat();
   ```

#### new 对象时的执行过程

1. 在内存中创建一个空的对象
2. **让构造函数中的this指向刚刚创建的对象**
3. 执行构造函数 在构造函数中设置属性 和方法
4. 返回当前对象

#### this

1. 方法中的this ---这个方法所属的对象
2. 类的构造方法中 ---- 指向对象
3. 函数中的this  --指向window

#### 遍历对象属性 for  in 

```javascript
var obj = {
    name: "张三",
    age: 22,
    eat: function () {
        console.log(name + '------' + age)
    }
}
// for in 遍历对象中的属性和方法
for (const key in obj) {
    console.log(key + "----" + obj[key]);
}
```
[前端文档]( https://developer.mozilla.org/zh-CN/  "前端api")

### 内置对象

#### Math

#### Date

#### Array

##### 1. 数组的创建

   - `  var arr = ['a','b'];`

   - ```javascript
     var arr = new Array(3);
     arr[0] = 1;
     arr[1] = 2;
     arr[2] = 3;
     console.log(arr);
     ```

   - `   var arr = new Array(1,2);`

##### 2. 遍历数组

   ```js
   arr.forEach(function (item, index, arr) {
   	console.log('item = ' + item + '-----index = ' + index);
   })
   ```

##### 3. 栈的方式(先进后出)

   - 添加元素push () ` arr.push(1); `

   - 删除元素 `arr.pop()`

##### 4. 队列方式 (先进先出)

   - shift()；删除数组中的第一个元素 并返回

   ```javascript
var arr = new Array('a', 'b');
var fisrtel = arr.shift();//删除数组中的第一个参数
console.log(fisrtel);// --> a 
console.log(arr);// --['b']
   ```

   - unshift();向数组的第一的位置插入元素 并返回最新数组的长度

   ```javascript
   var arr = new Array('a', 'b');
   var newLength = arr.unshift(1);// 向数组的第一位置插入数据 并返回最新数组的长度
   console.log(newLength);// -->1
   console.log(arr);// --[1,'a',b']
   ```

##### 5.数组常用方法

- indexof(el,startIndex)

```javascript
var arr = new Array('a', 'b', 1, 'b');
var bindex = arr.indexOf('b',3);// 获取指定元素第一次在数组中出现的位置 如果没有找到返回-1 参数二表示从哪个位置开始查询  
console.log(bindex);// ---> 3
```

- 清空数组

```javascript
var arr = new Array(1, 2, 3);
console.log(arr);
arr = [];
console.log(arr);
```

- 删除数组指定元素

```javascript
var arr = new Array(1, 2, 3);
var delarr = arr.splice(0, 2);// splice 参数一 开始删除的起始位置  参数二：需要删除几个元素  返回删除的数组
console.log(delarr);
console.log(arr);
```

- 复制数组

```javascript
var arr = new Array(1, 2, 3);
var newarr = arr.slice(1, 2);// 复制数组 开始位置  和  结束位置   返回新的数组
console.log(newarr) // -->[2,3]
```

- 反转数组

`arr.reverse()`

- 排序

`sort（）` 默认排序顺序是在将元素转换为字符串，然后比较它们的UTF-16代码单元值序列时构建的,在定义排序时  sort方法传入一个函数  返回值正 负 0 定义了排序规则

```javascript
var arr = new Array(7,5,11,1, 2, 3);
arr.sort(function(v1,v2){
	return v1-v2;
});
console.log(arr) 
```

- 过滤filter（callback(){ return  true }）

```javascript
var arr = new Array(7, 5, 11, 1, 2, 3);
var newarr = arr.filter(function (item, index, arr) {
	return item > 5
})
console.log(newarr);
```

- join(str)  和toString（） 效果同 str是转toString时拼接字符

#### String

##### 字符串不可变

------

##### 字符串的方法：所有的方法都会返回一个新的字符串

1. charAt(index)返回指定位置的字符
2. concat（str1,str2） 拼接字符串
3. substr(start ,length) 截取字符串  start 开始位置  end 获取长度
4. indexof(str) 获取指定字符的位置 找不到返回-1
5. replace(oldstr,newstr) 替换字符串，只会找到第一个字符串 
6. split（str） 按指定字符切割字符串返回数组
7. trim() 去除空白

## js高级语法









