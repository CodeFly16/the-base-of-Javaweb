# JavaScript简介

## 概念

* 一门客户端脚本语言，运行在浏览器中，浏览器使用自带的JavaScript解析引擎解析
* 不需要编译，可以直接被浏览器解析执行

## 功能

* 增强用户与页面的交互过程，使页面具有动态效果，增强用户的体验

## JavaScript发展史

1. 1992年，Nombase公司，开发出第一门脚本语言，用于表单的校验，命名为：C--
2. 1995年，netScope公司，开发出一门脚本语言：LiveScript，效果不佳，后来请来SUN公司的专家，合力开发出了JavaScript，与Java没有任何关系
3. 1996年，微软公司抄袭JavaScript开发出JScript
4. 1997年，ECMA组织统一了三大脚本语言——ECMAScript，成为所有客户端语言的标准



* JavaScript=ECMAScript+BOM+DOM

# ECMAScript

## 基本语法

### 与html结合的方式

* 内部结合：JS代码可以放在任何位置，JS的运行顺序取决与代码的位置

  ```html
  <body>
  	<script>
      	alert("hello world")
      </script>
  </body>
  ```

* 外部结合：引入外部JS资源

  ```html
  <body>
  	<script src="js/a.js"></script>
  </body>
  ```

### 注释方式

* 单行注释：//
* 多行注释：/* 注释内容*/

### 数据类型

* 原始数据类型：
  1. number：数字；  整数/小数/NaN（not a number 不是数字的数字类型）
  2. String：字符串
  3. boolean： true和false
  4. null：一个对象为空的占位符
  5. undefined：未定义。 一个变量没有给定初始值，会被默认为undefined

* 引用数据类型：对象

### 变量

* 定义：一小块存储数据的内存空间

* JavaScript为弱类型语言：在开辟内存空间的时候，不会定义空间必须的存储数据类型，可存放任意类型数据

  Java为强类型语言：在开辟内存空间的时候，会定义空间必须的存储数据类型，只能存放类型数据

* 语法：

  ```javascript
  var 变量名 = 初始化值 ; 
  ```

* typeof():检查变量的类型

  ```javascript
  //定义数字类型	
  var num = 1;
  var num2 = NaN;
  document.write(num+"<br/>")
  document.write(num2+"<br/>")
  //定义字符串类型
  var str = 'abc';
  var str2 = "edf";
  //定义boolen类型
  var flag = true;
  //定义null和undefined
  var obj = null;
  typeof(obj);//这里的结果为：object
  var obj2 = undefined;
  ```

### 运算符

* 一元运算符：++   --

* 算数运算符：+ - * / %....

  * 如果运算数不是运算符所要求的类型，那么JS引擎会自动将运算数转换为所要求的类型

    * string转number：直接按照字面值转，如果不能转为数字，那么JS引擎将会把运算数转为 NaN
    * boolean转number： true转为1，false转为0

  *  NaN与任何数运算，结果仍然为NaN

    ```javascript
    var a += "123";
    typeof(a);//此时的值为 number
    ```

* 赋值运算符：=    +=    -+ ....

* 比较运算符：>     <     >=     <=   **==  ===（全等于）**

  * 比较方式
    1. 类型相同：直接比较；字符串按照字典顺序比较
    2. 类型不同：先类型转换，再比较
  * ===：在比较之前，先判断类型，如果类型不一样，放回false

  ```javascript
  document.write(3>4);//false
  document.write("abc">"acb");//false
  document.write("123"==123);//true
  document.write("123"===123);//false
  ```

  

* 逻辑运算符： && ||  ！

  * 其他类型转boolean

    1. number： 0和NaN为false，非零为true

    2. string：空字符串（”“）为false，其他都是true

    3. null和undefined：都是false

    4. 对象：所有对象都是true，typeof(null)虽然为对象类型，但是转为boolean仍为false

       ```javascript
       if(obj){//可防止空指针异常
           
       }
       ```

       

* 三元运算符：    ？：

  * 语法：表达式？值1：值2
  * 含义:判断表达式，如果为true，则取值1，如果为false，则取值2

### JS的特殊语法

* 一行若是只有一条语句，可以省略分号，但是不建议这样做

  ```javascript
  <script>
  	var a = 0
  	var b = 1
  </sciptr>
  ```

* 定义变量，可以不使用var关键字，但是有区别，并且不建议这样做

  * 使用var：定义局部变量
  * 不用var：定义全局变量

### 流程控制语句

* if ... else ...

* switch（变量){

  ​			case  常量：

  ​								语句；

  ​								break；

  ​			case  常量：

  ​								语句

  ​								break；

  ​			......				

  }  **变量可以是任意类型变量**

* while

* do...while

* for

### 小案例—九九乘法表

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport"
          content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        td {
            border: 1px solid;
        }
    </style>
</head>
<body>
<script>
    document.write("<table align='center'>");
    for (var i = 1; i < 10; i++) {
        document.write("<tr>");
        for (var j = 1; j <= i; j++) {
            document.write("<td>");
            document.write(j + "*" + i + "=" + (i * j) + "&nbsp;&nbsp;&nbsp;&nbsp;");
            document.write("</td>");
        }
        document.write("</tr>");
    }
    document.write("</table>");
</script>
</body>
</html>
```

* 结果

![avatar](/img/九九乘法表.png)

## 基本对象

### Function

* 含义：函数对象

* 使用方式

  1. 创建

     * var fun = new Function(形式参数列表，方法体)， 该方式不建议使用

     * function 方法名称（形式参数列表）{

       ​		方法体

       }

       ```javascript
       function fun1(a,b){
           alert(a+b);
       }//定义a,b时，可以不使用var
       fun1(1,2);
       ```

       

     * var 方法名称  = function（形式参数列表）{

       ​		方法体

       }

       ```javascript
       var fun2 = function(a,b){
           alert(a+b);
       }
       fun2(1,2);
       ```

  2. 属性

     * length：代表形参的个数

  3. 特点

     * 方法中定义参数时，可不用些形参的类型

     * function具有属性，所以function是对象类型，若定义相同名字的方法，则会覆盖前一个方法，而非报错

     * 在JS中，方法的调用只与方法的名称有关，与参数列表无关

       ```javascript
       var fun2 = function(a,b){
           alert(a+b);
       }
       fun2(1);//合法，此时a=1，b=undefined
       fun2(1,2,3);//合法，a=1,b=2,arguments[2]=3
       ```

       

     * 在方法声明中，存在一个隐藏的**内置对象—arguments**，封装所有的实际参数

       ```javascript
       function add(){//可以不写参数，求任意数的和
           var sum = 0;
           for (i=0;i<arguments.length;i++){
               sum+=arguments[u];
           }
           alert(sum)
       }
       ```

       

       

  

### Array

* 含义：数组对象
* 使用方式
  1. 创建
  2. 方法
  3. 属性
  4. 特点





 





