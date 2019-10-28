# [jquery](https://jquery.com/)

jquery的顶级对象 jQuery 或者$

[中文文档](http://jquery.cuishifeng.cn/index.html)

## [选择器](https://api.jquery.com/category/selectors/)

### 常用选择器（id 、类、标签、标签+类、多条件）

1. id选择器

   ```javascript
           // 页面加载的回调
           $(function(){
               // 标签选择器 + 点击事件
               $("#btn").click(function(){
                   console.log("aaa");
                   jQuery("#box").css("background-color","yellow")
               })
   ```

   

2. 标签选择器

   ```javascript
           // 页面加载的回调
           $(function () {
               $("#btn").click(function(){
                   // 标签选择器
                   $("p").text("aaaaa");
               })
           })
   ```

   

3. 类选择器   

   ```javascript
           // 页面加载的回调
           $(function () {
               $("#btn").click(function(){
                   // 类选择器
                   $(".cls").css("background-color","red");
               })
           })
   ```

4. 标签+类选择器

   ```html
       <style>
           .cls {
               background-color: aquamarine
           }
       </style>
   
       <script>
           // 页面加载的回调
           $(function () {
               $("#btn").click(function () {
                   // 标签类选择器
                 $("li.cls").css("background-color","red")
               })
           })
       </script>
   </head>
   
   <body>
       <input type="button" value="切换" id="btn">
       <ol>
           <li class="cls">123</li>
           <li>456</li>
           <li>789</li>
           <li class="cls">666</li>
           <li>212</li>
       </ol>
   </body>
   
   ```

5. 多条件选择器

   ```html
       <style>
           .cls {
               background-color: aquamarine
           }
       </style>
   
       <script>
           // 页面加载的回调
           $(function () {
               $("#btn").click(function () {
                   // 多条件选择器 需要啥写啥
                 $("#sp,.cls,h1").css("background-color","green")
               })
           })
       </script>
   </head>
   
   <body>
       <input type="button" value="切换" id="btn">
       <ol >
           <li class="cls" >123</li>
           <li>456</li>
           <li>789</li>
           <li class="cls">666</li>
           <li>212</li>
       </ol>
       <span id="sp">span</span>
       <h1>dpp</h1>
   
   </body>
   ```

### 层次选择器

#### 1. 后代选择器(Descendant Selector (“ancestor descendant”))

```html
    <style>
        .cls {
            background-color: aquamarine
        }
    </style>

    <script>
        $(function () {
            $("#btn").click(function () {
                $(".cls ul").css({ "backgroundColor": "red" })
            })
        })
    </script>
</head>

<body>
    <input type="button" value="切换" id="btn">
    <div id="box">

        <ul class="cls">
            <li>123</li>
            <li>item2
                <ul>
                    <li>222</li>
                    <li>333</li>
                    <li>444</li>
                </ul>
            </li>
            <li>456</li>
        </ul>
        <div>
            <ul>
                <li>asd</li>
                <li>ggg</li>
            </ul>
        </div>
    </div>
</body>
```



#### 2. 子代选择器(Child Selector (“parent > child”))

```html
    <style>
        .cls {
            background-color: aquamarine
        }
    </style>

    <script>
        $(function () {
            $("#btn").click(function () {
                $("ul.cls>li").css("border", "3px double red");
            })
        })
    </script>
</head>

<body>
    <input type="button" value="切换" id="btn">
    <ul class="cls">
        <li>123</li>
        <li>item2
            <ul>
                <li>222</li>
                <li>333</li>
                <li>444</li>
            </ul>
        </li>
        <li>456</li>
    </ul>
</body>
```

### 奇数偶数选择器(:even 偶数  、:odd 奇数)

```html
    <script>
        $(function () {
            $("#btn").click(function () {
                // 偶数选择器
                // $("ul>li:even").css("backgroundColor","red")
                // 奇数选择器
                $("li:odd").css("backgroundColor","red")

            })
        })
    </script>
</head>

<body>
    <input type="button" value="切换" id="btn">
   <ul>
       <li>1</li>
       <li>2</li>
       <li>3</li>
       <li>4</li>
       <li>5</li>
   </ul>
</body>
```

### 索引选择器

```javascript
$(function () {
    $("#btn").click(function () {
        // :eq() 等于
        // $("li:eq(4)").css("backgroundColor","red")
        // :gt() 大于
        // $("li:gt(2)").css("backgroundColor","red")
        // :lt()小于
        $("li:lt(2)").css("backgroundColor","red")
    })
})

```

## 样式修改

### 1.  类样式修改

```javascript
// addClass 添加一个class 或者多个 用空格 隔开 并且不用.类名
$("div").addClass("cls cls2");
// 删除添加的样式
$("div").removeClass("cls2");
// 判断是否使用class
if($("div").hasClass("cls"))
// toggleClass如果有class就删除 没有就添加class 
$("div").toggleClass("cls2")
```

### 2.css样式修改

`   var pcss = $("p").css("color");`获取第一个p标签的css 中指定的样式

`var pcss = $("p").css({"color":"blue","border":"1px solid black"});`为所有的p标签设置自样式

## 常用方法

#### html()

获取指点选择器的HTML的字符串

1. `  var content = $("div").html();`返回的是第一个匹配标签 的类容是个字符串
2. 设置标签中的内容`$("#box").html("<p>你好</p>")`

#### text()

获取或者设置标签的文本内容

1. `  var textcontent =$("div").text();`获取标签的标签文本
2.  var textcontent =$("div").text("aaaa");设置div标签的所有文本为aaa

#### val()

 返回任意元素的值了。包括select。如果多选，将返回一个数组，其包含所选的值。 

```javascript
   <script>
        $(function () {
            $('.input-group-btn').click(function () {
                // var text = $("#input").val();
                // 设置标签的内容
                var text = $("#input").val('aaaa');
                console.log(text)
            })
        })
    </script>
</head>

<body>
    <span class="input-group-btn">
        <button type="button" class="btn btn-default">Go!</button>
    </span>
    <input type="text" name="" id="input" class="form-control" value="" required="required" pattern="" title="">
</body>
```

#### siblings（）

 用于筛选同辈元素的表达式 

`    var els = $("#input").siblings("p");`找到input标签的兄弟标签中的P b标签

#### next()

 取得一个包含匹配的元素集合中每一个元素紧邻的后面同辈元素的元素集合 

#### nextAll()

 查找当前元素之后所有的同辈元素。 

#### prev()

 取得一个包含匹配的元素集合中每一个元素紧邻的前一个同辈元素的元素集合 

#### prevAll()

 查找当前元素之前所有的同辈元素 

## 动画

#### hide()  or show()

```javascript
    <script>
        $(function () {
            $(".input-group-btn")
                .click(function () {
                    //hide() show() 方法  显示和隐藏动画 
                    // 参数一：执行时间 可以是数值类型也可以是string类型 slow normal fast 三种 ，参数二  动画执行结束的监听
                    $("#input").hide(2000,function(){
                        alert("完成")
                    })
                })
        })
    </script>
```

#### slideUp() 滑入、slideDown()滑出 、slideToggle()滑入切换

#### fadeIn()淡入、 fadeOut()淡出、fadeToggle()淡入淡出切换

#### fadeTo()改变透明度\

```javascript
 //透明度变化的时间长度    参数二：透明度
 $(".main").fadeTo(1000, 0.3);
```

#### animal()动画方法

#### stop()