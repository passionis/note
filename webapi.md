# webapi

 浏览器提供的一条操作浏览器的功能和页面的元素

## DOM--document  object  model

### 获取页面元素

1. document.getElementById()

   ```javascript
   var d = document.getElementById("divt")
   console.dir(d);
   ```

2. document.getElementsByTagName("div")

3.  var els = document.getElementsByClassName("divt");

4.   var el = document.querySelector(".divt");

   ```javascript
   // 这两个方法有兼容问题ie9及以上可用,方法调用对象时parent node  节点
   // 选择器查找 只会返回第一个匹配到的元素
   var el = document.querySelector(".divt");
   // console.dir(el);
   
   // 该方法会返回多个匹配的数据
   var els = document.querySelectorAll(".divt");
   console.log(els);
   ```

5. document.getElementByName(”name 的属性选择器)

### 注册事件

```js
var btn = document.getElementById("btn");
var iv = document.getElementById("iv");
btn.onclick =function(){
    alert('aa')
    iv.src = '../img/微信图片_20190517153447.jpg'
}
```



### 样式的操作

`el.classname='show'`

- 取消超链接的跳转

### 节点

## BOM

