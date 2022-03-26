# JavaScript基础-JSON

## 一、什么是JSON，有什么用？

> JavaScript Object Notation，简称JSON，数据交换格式。
>
> 主要作用：进行数据交换。（目前非常流行）

1. JSON是一种标准的轻量级的数据交换格式。
2. 特点是体积小，易解析
3. 在实际的开发中，有两种数据交换格式，使用最多，一个是JSON，另一个是XML。
4. XML体积大，解析麻烦，但其优点是：语法严谨，通常银行相关的系统进行数据交换会使用XML

**语法格式：**

```javascript
<script type="text/javascript">
    var jsonObj1 = {
        "属性名" : "属性值",
        "属性名" : "属性值",
        "属性名" : "属性值",
        "属性名" : "属性值",
        ...
    };
    // JSON的属性值可以是任意类型，可以是一个JSON对象,可以是数组
    var jsonObj2 = {
        "属性名" : "属性值",
        "属性名" : "属性值",
        "属性名" : "属性值" : ["元素1", "元素2", "元素3", ...],
        "属性名" : "属性值" : {"属性名" : "属性值", "属性名" : "属性值", "属性名" : "属性值", ...},
        ...
    };
</script>
```



## 二、创建一个JSON对象

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JSON001</title>
</head>
<body>
    <script type="text/javascript">
        // 创建一个JSON对象
        var studentObj = {
            "sno" : "110",
            "sname" : "张三",
            "sex" : "男"
        };
    </script>
</body>
</html>
```



### 2.1如何访问JSNO对象的属性

```javascript
// 访问JSON对象的属性
alert(studentObj.sno + "," + studentObj.sname + "," + studentObj.sex);
alert(studentObj["sno"] + "," + studentObj["sname"] + "," + studentObj["sex"]);
```

> 之前没有JSON的时候，需要定义类，创建对象，访问对象的属性。
>
> **JSON对象的特点是没有类型，所以JSON对象又称为无类型对象，轻量级。轻巧，体积小，易解析。**



### 2.2如何创建JSON对象数组

```javascript
// 创建JSON对象数组
var students = [
    {"sno" : "110", "sname" : "张三", "sex" : "男"}, 
    {"sno" : "120", "sname" : "李四", "sex" : "男"}, 
    {"sno" : "130", "sname" : "王五", "sex" : "男"}
];
```

如何遍历？

```javascript
// 遍历
for (var i = 0; i < students.length; i++){
    var stuObj = students[i];
    alert(stuObj.sno + "," + stuObj.sname + "," + stuObj.sex);
}
```



### 2.3设计一个JSON对象，可以描述整个班级中每一个学生的信息以及总人数信息

```html

```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JSON001</title>
</head>
<body>
    <script type="text/javascript">
        var classObj = {
            "students" : student = [
                {"name" : "张三", "birth" : "1980-10-11"} , 
                {"name" : "李四", "birth" : "1984-10-11"}, 
                {"name" : "王五", "birth" : "1985-10-11"}
            ],
            "num" : 3
        };
    </script>
</body>
</html>
```



## 三、eval函数

eval函数的作用是将字符串当作一段js代码，解释并执行。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JSON001</title>
</head>
<body>
    <script type="text/javascript">
        window.eval("var i = 100;"); // 将字符串当作JS代码解释并执行，相当于var i = 100;
        alert("i = " + i); // i = 100
    </script>
</body>
</html>
```

### 3.1eval函数的作用

java连接数据库，查询数据之后，将数据在java程序中拼接成JSON格式的字符串，将JSON格式的字符串响应到浏览器。

也就是说，java响应到浏览器上的仅仅是JSON格式的字符串，还不是一个JSON对象。

可以使用eval函数将JSON格式的字符串转换成JSON对象。

```javascript
var fromJava = "{\"name\" : \"zhangsan\", \"password\" : \"123\"}";
// 这是java程序给发过来的json格式的字符串
// 将此字符串转换成JSON对象
window.eval("var jsonObj = " + fromJava);
// 然后可以访问
alert(jsonObj.name + "," + jsonObj.password);
```



## 四、面试题

### 4.1在JS当中，[ ]和{ }有什么区别？

> [ ] 是数组。
>
> { } 是JSON。