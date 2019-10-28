# [jquery](https://jquery.com/)

jquery的顶级对象 jQuery 或者$

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

