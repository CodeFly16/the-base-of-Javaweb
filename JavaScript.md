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

  * NaN与任何数运算，结果仍然为NaN

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

### Function（非常常用的对象）

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

       

       

  

### Array（非常常用的对象）

* 含义：数组对象

* 使用方式

  1. 创建

     * var arr = new Array(元素，元素，元素····);
     * var arr = new Array(数字);// 代表数组默认长度，也可以不写，代表一个空数组
     * var arr = [ 元素，元素，元素····]；

     ```javascript
     首先写出3种创建方式，然后结合代码，演示这3种创建方式
     var arr1 = new Array(1,2,3);//
     var arr2 = new Array(4);//这种方式，只有一个数字类型时，代表长度
     var arr3 = [1,2,3，4];
     
     // 通过在页面上面的显示找出这三种创建方式的区别
     document.write(arr1+</br>);//结果为：1，2，3
     document.write(arr2+</br>);//结果为: ,,,,
     document.write(arr3+</br>);//结果为：1，2，3，4
     ```

     

  2. 方法

     * join（参数）：将数组中的元素按照指定的分隔符拼接为字符串，默认是，拼接
     * push（）：向集合的尾部添加更多元素，并返回新的长度，类比于Java中集合的add（）方法

     ```javascript
     从www.w3school.com中查找array对象的所有方法
     //演示join方法
     document.write(arr.join(--)+</br>);//结果为：1--abc--true--hehe
     //演示add方法
     arr.push(11);
     document.write(arr.join(--)+</br>);//结果为：1--abc--true--hehe--11
     
     其他的方法自行查看文档
     
     ```

     

  3. 属性

     * length

  4. 特点

     * JS中，数组元素的类型可变
     * JS中，数组的长度可变，类比于Java中的集合

     ```javascript
     结合代码演示 不同数组元素的类型
     var arr = [1,"abc",true];
     document.write(arr[0]+</br>);//1
     document.write(arr[1]+</br>);//abc
     document.write(arr[2]+</br>);//true
     document.write(arr[3]+</br>);//undefined //没有给值 默认undefined
     arr[10] = "hehe";
     document.write(arr[9]+</br>);//undefined
     document.write(arr[10]+</br>);//hehe
     
     document.write(arr.length+</br>);//11
     ```

     



### Boolean（了解）

- 基本类型包装类



### Date

- 含义：日期对象

- 使用方式：

  - 1.创建：var date = new Date（）；

  - 2.方法：

    - toLocaleString（）：返回当前date对象对应的时间本地字符串格式
    - getTime（）：获取毫秒值，返回当前时间到1970年1月1日零点的毫秒值之差
    - 其他方法浏览www.w3school.com中查询

    ```javascript
    	var date = new Date();
        document.write(date+"<br>");//Sun Apr 26 2020 09:39:55 GMT+0800 (中国标准时间)
        document.write(date.toLocaleString());//2020/4/26 上午9:39:55
        document.write(date.getTime());//1587865391238
    ```

    

### Math（非常类似于Java中的math类）

- 含义:数字对象

- 使用方法：

  - 创建：与Java中的math类一样，直接使用即可。Math.方法名（）；

  - 方法（主要内容）

    - random（）：返回0-1之间的随机数：包含0但是不包含1；
    - ceil（x）：对数进行上舍入
    - floor（x）：对数进行下舍入
    - round（x）：四舍五入

    ``` javascript
    演示：
        document.write(Math.random()+"<br>");    //0.49898024456203083
        document.write(Math.PI+"<br>");          //3.141592653589793
        document.write(Math.round(3.14)+"<br>"); //3
        document.write(Math.ceil(3.14)+"<br>");  //4
        document.write(Math.floor(3.14)+"<br>"); //3
    ```

    - 一个小练习：去1~100之间的随机数

    ```html
    思路：1.先取0~1之间的数，在乘以100，则取数为：0~99.99999 
    	 2.使用floor函数，使得小数化为整数
    	 3.在将取得的数加1，取数为1~100
    	 
    代码：
    	var num = Math.floor((Math.random()*100))+1;
    	document.write(num);
    ```

    

  - 属性

    - PI：为pi值



 ### Number

### String

```
上面两个对象与Boolean对象类似，都是原始数据类型的包装类对象
```



### RegExp

- 含义：正则表达式对象

  ```
  正则表达式的含义：定义字符串的组成规则,可用于校验字符串——引出用于表单的校验
  定义正则表达式：1.定义单个字符：[]   如[a],[ab](表示a或者b)，[a-zA-Z0-9](表示a到z A到Z 0-9) ，这样子定义非常麻烦，所以提供了特殊符号代表特殊含义的单个字符
  				如：\d:单个数字字符[0-9]
  				   \w:单个单词字符[a-zA-Z0-9_]
  		     2.量词符号：
  		     	*：表示出现0次或多次
  		     	?:表示出现0次或1次
  		     	+:表示出现1次或多次
  		     	{m,n}:表示 m<=数量<=n
  		     		m如果缺省：{，n}表示最多n次
  		     		n如果缺省：{m，}表示最少m次
  		     	更多的正则表达式 查看文档
  			 3.开始结束符号：
               	^:开始
               	$:结束
  ```

- 创建：正则表达式不仅适用于JavaScript 还适用于Java C++等语言，是一种通用的规则

  - var reg = new RegExp("正则表达式")；
  - var reg = /正则表达式/；    此时注意 不要加上双引号，否则就变成了字符串了（此种方式使用的更多）

  ```javascript
  演示：
     var reg1 = RegExp("^\\w{6,12}$"); //这里注意字符串中要用\\转义为\
     var reg2 = /^\w{6,12}$/;
     document.write(reg1+"<br>"); // 结果为：/w{6,12}/
     document.write(reg2+"<br>");// 结果为：/^\w{6,12}$/
  ```

- 方法

  - test（）： 验证指定的字符串是否符合正则定义的规范

  ```javascript
  演示:
      var user = "zhangsan";
      var password = "asdfghjklqwerty"
      var flag1 = reg1.test(user);
      var flag2 = reg2.test(password);
      document.write(flag1);//user字符串有8个字符 ，所以结果为true
      document.write(flag2);//user字符串有个字符 ，所以结果为false
  ```

  

### Global(全局对象)

- 全局对象的特点:不需要对象就可以直接调用，方法名（） ,  所以很多人并不知道这个对象名字

- 方法:

  - decodeURI()：解码某个编码的 URI

    encodeURI()：把字符串编码为 URI

  - decodeURIComponent()：解码一个编码的 URI 组件。

    encodeURIComponent()：把字符串编码为 URI 组件。

  - parseInt():将字符串转化为数字

    逐一判断每一个字符是否为数字，直到不是数字为止，将前面的所有字符转化为number类型

  - isNaN():判断一个值是否为NaN

    ​		注意：NaN==任何东西（包括NaN），此值 都是false，于是产生了isNaN函数

  - eval():计算 JavaScript 字符串，并把它作为脚本代码来执行。

  ```
  何为URL解码：浏览器访问做数据传输的时候，通过一些传输协议，如http协议，这些协议是不支持中文数据的，如果要		   将中文数据发送到服务端，此时需要将中文数据转码。
  		   如 长江大学 = %E9%95%BF%E6%B1%9F%E5%A4%A7%E5%AD%A6
  decodeURI()，encodeURI()和decodeURIComponent()，encodeURIComponent()的区别：
  		  在与后者可以编码更多的字符
  ```

  ```javascript
  演示:
     var str = "长江大学";
     var encode = encodeURI(str);
     document.write(encode); //结果  %E9%95%BF%E6%B1%9F%E5%A4%A7%E5%AD%A6
     var decode = decodeURI("%E9%95%BF%E6%B1%9F%E5%A4%A7%E5%AD%A6");
     document.write(decode); // 结果 长江大学
     
     
     var str = "234abc123";
     var num = parseInt(str);
     document.write(num+1);//此时结果为235
     
     var a = NaN;
     document.write(a == NaN);//false
     document.write(isNaN(a));//true
     
    var str1 = "alert(123)";
    document.write(str1);//结果在页面显示:alert(123)
    eval(str1);//结果在页面弹出提示框：123
  ```





# DOM（先简单学习）

```
首先简单学习DOM，满足做案例的要求之后，在深入的学习BOM和DOM
```



## 简单介绍

- 功能：控制html文档的内容
- 相关代码：获取页面标签(元素)对象—Element
  - document.getElementById("id值")      —通过元素的ID获取元素对象
- 作用：操作Element对象
  - 修改属性值：只能修改Element中存在的属性
  - 修改标签体内容：
    - 属性：innerHTML

```html
演示
<body>
	<h1 id = "title">床前明月光</h1>
	
<script>
	var title = document.getElementById("title");
    alert("换内容");
    title.innerHTML = "疑是地上霜";  // 效果：点击了弹出框之后，床前明月光变为疑是地上霜
</script>

</body>
```



## 事件简单学习

- 功能：某些组件被执行了某些操作后，触发某些代码后执行操作
- 绑定事件（两种方式）
  - 直接在html标签上，指定事件的属性，属性值就是js代码（这种方式耦合度太大）
    - 事件：onclick — 单击事件
  - 通过js获取元素对象，指定事件属性，设置一个函数（降低耦合度，利于分工协作）

```html
演示：
<body>
<img src="img/1.png" onclick="fun()">

<img src="img/2.png" id="img">
<script>
    //方式一
    function fun() {
        alert("点击事件");
    }
    
    //方式二
    function fun2() {
        alert("点击事件2");
    }
    var img2 = document.getElementById("img");
    img2.onclick = fun2;//这里注意不要等于fun2(),否则打开页面会直接跳出 点击事件2 的提示，并且点击事件                         //失效
</script>

</body>
```



## 小案例-电灯开关

```
思路：
  1.首先获取图片对象
  2.绑定单击事件
  3.每次点击切换图片
  	1.此时需要判断灯的状态来判断需要切换的图片
  	2.使用flag来标记
```

```html
演示：
<body>

<img src="img/off.gif" alt="" id="light">

<script>
    var light = document.getElementById("light");
    var flag = false;//代表灯是关着的
    light.onclick = function () {
        if (flag) {//判断灯的状态，flag 为true 点击图片切换为关灯状态
            light.src = "img/off.gif"
            flag = false;
        } else {//判断灯的状态，flag 为false 点击图片切换为开灯状态
            light.src = "img/on.gif"
            flag = true;
        }
    }
</script>

</body>
```





# BOM

## 概念

- Browser Object Model 浏览器对象模型

- 将浏览器的各个组成部分封装成对象

## 组成部分

- [Window](https://www.w3school.com.cn/jsref/dom_obj_window.asp)：窗口对象
- [Navigator](https://www.w3school.com.cn/jsref/dom_obj_navigator.asp)：浏览器对象   -不做讲解，基本使用不到
- [Screen](https://www.w3school.com.cn/jsref/dom_obj_screen.asp)：屏幕对象    -不做讲解，基本使用不到
- [History](https://www.w3school.com.cn/jsref/dom_obj_history.asp)：历史记录对象
- [Location](https://www.w3school.com.cn/jsref/dom_obj_location.asp)：地址栏对象

## 对象

### Window对象

- 含义：窗口对象

  ``` 
  直接从Window对象的特点讲起，便于Window对象的学习,
  接着讲Window对象的方法，由于Window对象的方法很多，所以将这些方法归类，在来讲
  ```

- 使用方式

  1. 创建

  2. 方法

     - 与弹出窗口有关的方法：

       - [alert()](https://www.w3school.com.cn/jsref/met_win_alert.asp)：显示带有一段消息和一个确认按钮的警告框 

       - [confirm()](https://www.w3school.com.cn/jsref/met_win_confirm.asp)：显示带有一段消息以及确认按钮和取消按钮的对话框。

         - 用户点击确定按钮，方法返回true
         - 用户点击取消按钮，方法返回false
         - 由此通过点击的按钮，就可以判断用户的行为，可防止用户的误操作

       - [prompt()](https://www.w3school.com.cn/jsref/met_win_prompt.asp)： 显示可提示用户输入的对话框。

         - 返回值：获取用户输入的值

         ```html
         演示：
         <body>
         <script>
             var flag = confirm("确定吗")
             document.write(flag); //点击确定，结果为true
         </script>
         </body>
         ```

         

     - 与打开和关闭有关的方法：

       - [close()](https://www.w3school.com.cn/jsref/met_win_close.asp): 关闭浏览器窗口。

         - 哪一个窗口调用该函数，那么该窗口就会关闭

       - [open()](https://www.w3school.com.cn/jsref/met_win_open.asp): 打开一个新的浏览器窗口或查找一个已命名的窗口。

         - open()方法中可以添加url地址，此时可以打开到该url地址

         ```html
         演示
         <body>
         <input id="openBtn" type="button" value="打开窗口">
         <input id="closeBtn" type="button" value="关闭窗口">
         <script>
             var openBtn = document.getElementById("openBtn");
             var closeBtn = document.getElementById("closeBtn");
             var newWindow;
             openBtn.onclick = function(){
                 newWindow=open("https://www.baidu.com");//点击按钮，可以跳转到百度
             }
             closeBtn.onclick = function(){
                 newWindow.close("https://www.baidu.com");//点击按钮，可以关闭新出来的窗口
             }//注意这里如果直接使用close()的话  会关闭当前窗口，谁调用close()，就关闭谁的窗口
         </script>
         </body>
         ```

     - 与定时器有关的方法

       - [setTimeout()](https://www.w3school.com.cn/jsref/met_win_settimeout.asp)：在指定的毫秒数后调用函数或计算表达式。

         - 参数
           1. 第一个参数是js代码或者方法
           2. 第二个参数是毫秒数
         - 返回值：返回一个标识，用于取消定时器的参数

       - [clearTimeout()](https://www.w3school.com.cn/jsref/met_win_cleartimeout.asp)：取消由 clearTimeout() 设置的 timeout。

       - [setInterval()](https://www.w3school.com.cn/jsref/met_win_setinterval.asp)：按照指定的周期（以毫秒计）来调用函数或计算表达式。

         - 参数
           1. 第一个参数是js代码或者方法
           2. 第二个参数是毫秒数
         - 返回值：返回一个标识，用于取消定时器的参数

         - 相比于setTimeout()，这种方法可以循环执行

       - [clearInterval()](https://www.w3school.com.cn/jsref/met_win_clearinterval.asp)：取消由 setInterval() 设置的 timeout。

         ```html
         演示：
         <script>
             function fun() {
                 document.write("123"+"<br/>");
             }
             var id1 = setTimeout(fun, 2000);//效果：2s后，在页面中显示一次123
             var id2 = setInterval(fun,2000)//效果：每过2s，就在页面中显示一次123
             //clearTimeout(id1); //可取消定时器
             //clearInterval(id2);
         </script>
         ```

         

  3. 属性

     - 可以获取其他BOM对象：history，location，Navigation，Screen
     - 可以获取DOM对象：document
     - 由此可见，平时编写JS代码是使用的DOM对象都是从window对象中调用的，只不过平时省略window关键字

  4. 特点

     - Window对象可以直接使用， Window.方法名();
     - Window引用可以省略， 方法名（）;

  

#### 小案例—轮播图

- 这一个小案例主要运用了BOM定时器的功能，实现自动轮播的效果

- 要求：在页面上依次展示3张图片，经过2s后自动切换到下一张图片
- 思路：
  - 首先展示图片到页面上
  - 定义一个方法，修改src属性，目的是切换图片
  - 定义一个定时器，目的是在一定时间内自动切换图片
- 难点:控制图片src属性的正确切换

```html
演示:
<body>

<img src="img/banner_1.jpg" alt="" width="100%" id="img">

//注意 要将js代码放在最下面
<script>
    var num = 1;
    function fun() {
        num++;
        if (num>3){//这一段控制图片的切换
            num = 1;
        }
        var img = document.getElementById("img");
        img.src = "img/banner_"+num+".jpg";
    }
    setInterval(fun,2000);//注意要使用周期定时器
</script>

</body>

```

### Location对象

- 含义：地址栏对象
- 使用方式：
  1. 创建：window.location()或者直接调用location()
  2. 方法（三种）
     - reload（）：重新加载当前文档，相当于刷新功能
     - assign（）： 加载新的文档。
     - replace（）： 用新的文档替换当前文档。
  3. 属性
     - href：设置或返回完整的 URL

#### 小案例—自动跳转首页

- 主要使用定时器和location对象
- 要求：5s之后跳转到别的页面，需要在页面上显示倒计时的效果，时间一到，就自动跳转
- 思路
  1. 首先制作页面效果：html+css样式
  2. 实现秒数的倒计时：使用定时器
  3. 当时间为0时，跳转

```html
演示
<head>
 	<style>
        p {
          text-align: center;
        }
        p span{
            color: red;
        }
    </style>
</head>
<body>

<p>
    <span id="time">5</span>秒后跳转....
</p>
<script>

    var second=5;//设置跳转的时间
    function showTime() {
        second --;
        if (second<=0){//设置跳转
            location.href="https://www.baidu.com";
        }
        var time = document.getElementById("time");
        time.innerHTML= second ;
    }
    setInterval(showTime,1000);//设置定时器

</script>

</body>
```



### History对象

- 含义：历史记录对象
- 该处历史记录的含义：History 对象包含用户（在浏览器窗口中）访问过的 URL。仅仅指的是在该窗口中访问的url地址，并非时浏览器中总的历史记录
- 使用方式
  1. 创建：window.history()或者直接调用history()
  2. 方法
     - back（）：加载 history 列表中的前一个 URL。
     - forward（）：加载 history 列表中的下一个 URL。
     - go（参数）:加载 history 列表中的某个具体页面。
       - 参数为正数：前进几个历史记录
       - 参数为负数：后退几个历史记录
  3. 属性
     - length：返回当前窗口历史列表中的URL数量

# DOM

## 概念

- Document Object Model 文档对象模型
- 将标记语言文档的各个组成部分，封装成对象。可以使用这些对象，对标记语言文档进行CRUD的动态操作
- DOM定义了访问HTML和XML文档的标准
- DOM是W3C的标准 
- **DOM 将 HTML 文档表达为树结构。**

![DOM树](/img/DOM树.png)

## 组成部分

- 分为三种不同部分
  - 核心 DOM - 针对任何结构化文档的标准模型
  - XML DOM - 针对 XML 文档的标准模型
  - HTML DOM - 针对 HTML 文档的标准模型

  ```
  XML DOM和HTML DOM都是对核心DOM的扩展和封装
  先了解核心DOM，在学习HTML DOM
  ```

- 核心DOM
  - Document：文档对象（重点掌握）
  - ELement：元素对象（重点掌握）
  - Attribute：属性对象
  - Text：文本对象
  - Comment：注释对象
  - Node：节点对象，其他5个对象的父对象（了解）



## 核心DOM

- Document对象

  1. 创建方式：HTML DOM模型中可以通过window.document或者直接调用document

  2. 方法（XML DOM对核心DOM方法修改较少，此处以XML DOM为例）

     - 获取Element对象：
       - getElementById():根据id属性获取元素对象
       - getElementsByTagName():根据元素名称获取元素对象。返回值是一个数组
       - getElementByClassName():根据class属性值获取元素对象，返回值是一个数组
       - getElementByName():根据class属性值获取元素对象，返回值是一个数组

     ```html
     演示：
     <body>
     
     <div id="div1">div1</div>
     <div id="div2">div2</div>
     <div id="div3">div3</div>
     <div class="cls1">div4</div>
     <div class="cls1">div4</div>
     <input type="text" name="username">
     
     <script>
         var divs = document.getElementsByTagName("div");
         var div_cls = document.getElementsByClassName("cls1");
         var ele_username = document.getElementsByName("username");
         alert(divs.length);//结果为5
         alert(div_cls.length);//结果为2
         alert(ele_username.length);//结果为1
     </script>
     
     </body>
     ```

     - 创建其他DOM对象
       - createAttribute(name)
       - createComment()
       - createElement()
       - createTextNode()

     ```html
     演示：
     <script>
        var table = document.createElement("table");
        alert(table);//结果为[object HTMLTableElement]
     </script>
     
     ```

  3. 属性

- Element对象

  1. 创建方式：通过document来获取和创建

  2. 方法：
     - removeAttribute():删除属性
     - setAttribute():设置属性

  ```html
  演示：
  
  <body>
  
  <a href="">点击</a>
  <input type="button" id="btn_set" value="添加">//点击按钮添加a标签的url地址
  <input type="button" id="btn_remove" value="清除">//点击按钮清楚a标签的url地址
  <script>
      var btn_set = document.getElementById("btn_set");
      btn_set.onclick = function () {
          var element_a = document.getElementsByTagName("a")[0];
          element_a.setAttribute("href", "https://www.baidu.com");
      };
      var btn_remove = document.getElementById("btn_remove");
      btn_remove.onclick = function () {
          var element_a = document.getElementsByTagName("a")[0];
          element_a.removeAttribute("href");
      };
  
  </script>
  
  </body>
  ```

  

- Node对象

  1. 特点：所有DOM对象都可以被认为是一个节点

  2. 方法
     - CRUD dom树的方法：
       - appendChild()：向节点的子节点列表的结尾添加新的子节点（常用）
       - removeChile()：删除（并返回）当前节点的指定子节点（常用）
       - replaceChild()：用新节点替换一个子节点。
  3. 属性
     - parentNode：返回当前节点的父节点

  ```html
  演示：
  <head>
  	 <style>
          div{
              border: solid red 1px;
          }
          #div1{
              width: 200px;
              height: 200px;
          }
          #div2{
              width: 100px;
              height: 100px;
          }
          #div3{
              width: 100px;
              height: 100px;
          }
      </style>
  </head>
  <body>
  
  <div id="div1">
      <div id="div2">div2</div>
      div1
  </div>
  <!--
      如果这个地方不加上JavaScript:void(0),则点击超链接的时候
      虽然会删除掉子节点，但是页面会迅速的重新刷新一遍，回到
      子节点未删除的页面。void是组织返回值的运算符
  -->
  <a href="JavaScript:void(0)" id="del">删除子节点</a>
  <a href="JavaScript:void(0)" id="add">添加子节点</a>
  
  <script>
  
      var element_del = document.getElementById("del");
      element_del.onclick=function () {
          var div1 = document.getElementById("div1");
          var div2 = document.getElementById("div2");
          //div1删除子节点
          div1.removeChild(div2);
      }
  
      var element_add = document.getElementById("add");
      element_add.onclick=function () {
          var div1 = document.getElementById("div1");
          //创建节点
          var div3 = document.createElement("div");
          div3.setAttribute("id","div3");
          //div1添加子节点
          div1.appendChild(div3);
      }
  
  </script>
  
  </body>
   
  ```





## HTML DOM (使用时更加的方便，简洁)

- innerHTML对象

  - 功能：设置和获取标签体

    ```html
    演示:
    
    <body>
    <div id="div1">
        div
    </div>
    <script>
        var div = document.getElementById("div1");
        var text = div.innerHTML;//获取标签体
        div.innerHTML += "<input type='text'>"; //将页面中追加输入框
        alert(text);//结果弹出提示框，内容为div
    //  div.innerHTML = "<input type='text'>"; //将页面中div替换为输入框
    </script>
    </body>
    ```

    

- 属性（属性非常多，遇到了各种问题时，查看文档）

- 控制元素样式（两种方式）

  - 使用元素style属性设置

  ```html
  演示:
  
  <body>
  
  <div id="div1">
      div
  </div>
  
  <script>
      var div = document.getElementById("div1");
      div.onclick = function () {  //该方法实现点击页面的div 就可以出现一个红色边框
          div.style.border="1px solid red";
          div.style.width = "200px";
          div.style.fontSize="50px"; //这里的font-size样式 需要将-替换成驼峰命名法
      }
  </script>
  </body>
  ```

  - 通过className属性来设置，相当于改变元素的class属性

  ```html
  演示：
  <head>
  	.d1{
              border: solid 1px red;
              width: 100px;
              height: 100px;
          }
      </style>
  </head>
  
  <body>
  
  <div id="div2">
      div
  </div>
  
  <script>
      var div = document.getElementById("div2");
      div.onclick = function () {
          div.className="d1";//相当于给div标签添加 class="d1"
      }
  </script>
  </body>
  ```





## DOM小案例—动态表格

- 样式

  ​	![动态表格](/img/动态表格.png)





- 要求

  1. 点击删除按钮，则会删除整列
  2. 点击添加按钮，会在下方增加添加的内容

- 思路

  - 添加按钮：(两种方式，一种复杂，另外一种简单)

    ```
    1. 给添加按钮绑定单击事件
    2. 获取文本框的内容
    3. 创建td，设置td的文本为文本框的内容。
    4. 创建tr
    5. 将td添加到tr中
    6. 获取table，将tr添加到table中
    ```

  - 删除按钮

    ```
    1.确定点击的超链接
        <a href="javascript:void(0);" onclick="delTr(this);" >删除</a>
    2.删除
        removeChild():通过父节点删除子节点
    ```



```html
素材：

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>动态表格</title>
    <style>
        table{
            border: 1px solid;
            margin: auto;
            width: 500px;
        }

        td,th{
            text-align: center;
            border: 1px solid;
        }
        div{
            text-align: center;
            margin: 50px;
        }
    </style>
</head>
<body>
<div>
    <input type="text" id="id" placeholder="请输入编号">
    <input type="text" id="name"  placeholder="请输入姓名">
    <input type="text" id="gender"  placeholder="请输入性别">
    <input type="button" value="添加" id="btn_add">

</div>
<table>
    <caption>学生信息表</caption>
    <tr>
        <th>编号</th>
        <th>姓名</th>
        <th>性别</th>
        <th>操作</th>
    </tr>
    <tr>
        <td>1</td>
        <td>令狐冲</td>
        <td>男</td>
        <td><a href="" >删除</a></td>
    </tr>
    <tr>
        <td>2</td>
        <td>任我行</td>
        <td>男</td>
        <td><a href="" >删除</a></td>
    </tr>
    <tr>
        <td>3</td>
        <td>岳不群</td>
        <td>?</td>
        <td><a href="">删除</a></td>
    </tr>
</table>

</body>
</html>
```

```html
案例演示：

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>动态表格</title>
    <style>
        table{
            border: 1px solid;
            margin: auto;
            width: 500px;
        }
        td,th{
            text-align: center;
            border: 1px solid;
        }
        div{
            text-align: center;
            margin: 50px;
        }
    </style>
</head>
<body>
<div>
    <input type="text" id="id" placeholder="请输入编号">
    <input type="text" id="name"  placeholder="请输入姓名">
    <input type="text" id="gender"  placeholder="请输入性别">
    <input type="button" value="添加" id="btn_add">

</div>
<table>
    <caption>学生信息表</caption>
    <tr>
        <th>编号</th>
        <th>姓名</th>
        <th>性别</th>
        <th>操作</th>
    </tr>
    <tr>
        <td>1</td>
        <td>令狐冲</td>
        <td>男</td>                       // this表示当前超链接
        <td><a href="javascript:void(0);" onclick="delTr(this);">删除</a></td>
    </tr>
    <tr>
        <td>2</td>
        <td>任我行</td>
        <td>男</td>
        <td><a href="javascript:void(0);" onclick="delTr(this);">删除</a></td>
    </tr>
    <tr>
        <td>3</td>
        <td>岳不群</td>
        <td>?</td>
        <td><a href="javascript:void(0);" onclick="delTr(this);" >删除</a></td>
    </tr>
</table>
<script>
   /*
   		//获取按钮（方式一）
   		
   		document.getElementById("btn_add").onclick = function(){
        //获取文本框的内容
        var id = document.getElementById("id").value;
        var name = document.getElementById("name").value;
        var gender = document.getElementById("gender").value;
        //创建td，赋值td的标签体
        var td_id = document.createElement("td");
        var text_id = document.createTextNode(id);
        td_id.appendChild(text_id);
        
        var td_name = document.createElement("td");
        var text_name = document.createTextNode(name);
        td_name.appendChild(text_name);
        
        var td_gender = document.createElement("td");
        var text_gender = document.createTextNode(gender);
        td_gender.appendChild(text_gender);

        var td_a = document.createElement("td");
        var ele_a = document.createElement("a");
        ele_a.setAttribute("href","javascript:void(0);");
        ele_a.setAttribute("onclick","delTr(this);");
        var text_a = document.createTextNode("删除");
        ele_a.appendChild(text_a);
        td_a.appendChild(ele_a);
        //创建tr
        var tr = document.createElement("tr");
        //添加td到tr中
        tr.appendChild(td_id);
        tr.appendChild(td_name);
        tr.appendChild(td_gender);
        tr.appendChild(td_a);
        //获取table
        var table = document.getElementsByTagName("table")[0];
        table.appendChild(tr);
    }
 */


   //使用innerHTML添加（方式二）
    document.getElementById("btn_add").onclick = function() {
        //获取文本框的内容
        var id = document.getElementById("id").value;
        var name = document.getElementById("name").value;
        var gender = document.getElementById("gender").value;
        //获取table
        var table = document.getElementsByTagName("table")[0];
        //追加一行
        table.innerHTML += "<tr>\n" +
               " <td>"+id+"</td>\n" +
             " <td>"+name+"</td>\n" +
           " <td>"+gender+"</td>\n" +
        " <td><a href=\"javascript:void(0);\" onclick=\"delTr(this);\" >删除</a></td>\n"    						+"</tr>";
    }

    //删除方法
    function delTr(obj){
        var table = obj.parentNode.parentNode.parentNode;
        var tr = obj.parentNode.parentNode;

        table.removeChild(tr);
    }


</script>

</body>
</html>
```

# 事件监听机制（很重要）

## 概念

- 某些组件被执行了某些操作后，触发某些代码的执行（不仅仅在JavaScript中应用，在所有高级语言中均有应用）
  - 事件：指的是某些操作，如点击，双击，键盘事件等等
  - 事件源：指的是组件，如按钮，文本输入框等等
  - 监听器：代码
  - 注册监听：将事件，事件源，监听器绑定起来。事件源上发生某些事件时，则触发某个监听器代码
  - 以上操作除事件种类外，基本上在DOM和BOM的学习中均有触及。这一节，以事件为主



## 常见事件

- 点击事件

  - onclick：单击事件
  - ondblclick：双击事件

- 焦点事件

  - onblur：元素失去焦点
    - 一般用于表单校验：例如注册账号时，当输入框失去焦点时，立刻校验账号是否存在
  - onfacus：元素获得焦点

  ```
  演示：
  <body>
  	<input type="text" id="demo">
  	
  	<script>
  		document.getElementById("demo").onblur = function(){
  			alert("失去焦点");//点击文本框后，在点击文本框外的区域，会弹出该提示框
  		}
  	</script>
  </body>
  ```

  

- 加载事件

  - onload：一张页面或一幅图完成加载
    - 一般给``<body>, <frame>, <frameset>, <iframe>, <img>, <link>, <script>``添加该事件
    - 可以给window对象添加事件

  ```html
  演示：
  <body>
  	//当页面加载完成后加载此事件
  	<script>
  		window.unload = function(){
  		//这里的script代码放在了文本上面，如果没unload事件，那么下面的失去焦点事件就会失效
  		//因为文本框还没加载出来，就已经运行了焦点事件
              document.getElementById("demo").onblur = function(){
                  alert("失去焦点");
              }
  		}
  	</script>
  	
  	<input type="text" id="demo">
  </body>
  ```

  

- 鼠标事件

  - onmousedown: 鼠标按键被按下
    - 定义方法时，可以定义一个形参，接收event对象
    - event对象的button属性可以获取那个鼠标按键点击了
  - onmouseup:鼠标按键被松开
  - onmousemove:鼠标被移动
  - onmouseout:鼠标从某元素移开
  - onmouseover:鼠标移到某元素之上

  ```html
  演示：
  <body>
  	<input type="text" id="demo">
  	
  	<script>
  		document.getElementById("demo").onmousedown = function(event){
                 alert(event.button);//左键点击弹出0，滚轮点击弹出1，右键点击弹出2
          }
           
  	</script>
  </body>
  ```

  

- 键盘事件

  - onkeydown：某个键盘按键被按下
  - onkeyup：某个键盘按键被松开
  - onkeypress：某个键盘按键被按下并松开

  ```html
  演示：
  <body>
  	<input type="text" id="demo">
  	
  	<script>
  		document.getElementById("demo").onkeydown = function(event){
                 alert(event.keycode);//在输入框中输入a，立刻弹出65
          }
           
  	</script>
  </body>
  ```

  

- 选择和改变事件

  - onchange：域的内容被改变（很多时候作用与下拉列表）
  - onselect：文本被选中

  ```html
  演示：
  <body>
  
  	<input type="text" id="demo">
  	<select id="city">
      <option>--请选择--</option>
      <option>北京</option>
      <option>上海</option>
      <option>西安</option>
  	</select>
  	
  	<script>
  		document.getElementById("demo").onchange = function(event){
                 alert("改变了");//改变文本框中的值，失去焦点，立刻弹出提示框
          }
          
          //用与省市级联动功能
          document.getElementById("city").onchange = function(event){
                 alert("改变了");//修改下拉列表，立刻弹出提示框
          }
  	</script>
  </body>
  ```

  

- 表单事件

  - onsubmit（重要）：确认按钮被点击
    - 可以通过表单校验的方式，阻止表单的提交
  - onreset：表单被重置

  ```html
  演示：
  
  <body>								//必须要有return，否则不能得到返回值
      <form action="#" id="form" onclick="return checkForm()">
          <select id="city">
              <option>--请选择--</option>
              <option>北京</option>
              <option>上海</option>
              <option>西安</option>
          </select>
          <input type="submit" value="提交">
      </form>
  	<script>
  	
  		 //校验表单
          document.getElementById("form").onsubmit = function{
              var flag = fales;
              //只有return boolean值，才能确定表单是否提交
              return flag
          }
          
          //另一种方式
          function checkForm(){
           	return false;
          }
           
  	</script>
  </body>
  ```

  



## 案例1—表格全选

- 效果

  ![表格全选](/img/表格全选.png)

- 要求

  - 点击全选，上面所有选择框打勾
  - 点击全不选，上面所有选择框不打勾
  - 点击反选，则上面打勾的选择框不打勾，不打勾的选择框打勾

- 思路

  - 全选
    1. 获取所有的checkbox
    2. 遍历checkbox，设置每一个checkbox的状态为选中  checked=true
  - 全部选
    1. 获取所有的checkbox
    2. 遍历checkbox，设置每一个checkbox的状态为不选中 checked=false
  - 反选
    1. 获取所有的checkbox
    2. 遍历checkbox，设置每一个checkbox的状态为其反状态，使用 ！运算符

  

```html
演示：
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表格全选</title>
    <style>
        table{
            border: 1px solid;
            width: 500px;
            margin-left: 30%;
        }

        td,th{
            text-align: center;
            border: 1px solid;
        }
        div{
            margin-top: 10px;
            margin-left: 30%;
        }

        .out{
            background-color: white;
        }
        .over{
            background-color: pink;
        }
    </style>

  <script>
      
      //1.在页面加载完后绑定事件
      window.onload = function(){
          //2.给全选按钮绑定单击事件
          document.getElementById("selectAll").onclick = function(){
                //全选
                //1.获取所有的checkbox
                var cbs = document.getElementsByName("cb");
                //2.遍历
                  for (var i = 0; i < cbs.length; i++) {
                      //3.设置每一个cb的状态为选中  checked
                      cbs[i].checked = true;
                  }
          }

          document.getElementById("unSelectAll").onclick = function(){
              //全不选
              //1.获取所有的checkbox
              var cbs = document.getElementsByName("cb");
              //2.遍历
              for (var i = 0; i < cbs.length; i++) {
                  //3.设置每一个cb的状态为未选中  checked
                  cbs[i].checked = false;
              }
          }

          document.getElementById("selectRev").onclick = function(){
              //反选
              //1.获取所有的checkbox
              var cbs = document.getElementsByName("cb");
              //2.遍历
              for (var i = 0; i < cbs.length; i++) {
                  //3.设置每一个cb的状态为相反
                  cbs[i].checked = !cbs[i].checked;
              }
          }

          document.getElementById("firstCb").onclick = function(){
              //第一个cb点击
              //1.获取所有的checkbox
              var cbs = document.getElementsByName("cb");
              //获取第一个cb

              //2.遍历
              for (var i = 0; i < cbs.length; i++) {
                  //3.设置每一个cb的状态和第一个cb的状态一样
                  cbs[i].checked =  this.checked;
              }
          }

          //给所有tr绑定鼠标移到元素之上和移出元素事件
          var trs = document.getElementsByTagName("tr");
          //2.遍历
          for (var i = 0; i < trs.length; i++) {
              //移到元素之上
              trs[i].onmouseover = function(){
                    this.className = "over";
              }

              //移出元素
              trs[i].onmouseout = function(){
                     this.className = "out";
              }

          }

      }
  </script>

</head>
<body>

<table>
    <caption>学生信息表</caption>
    <tr>
        <th><input type="checkbox" name="cb" id="firstCb"></th>
        <th>编号</th>
        <th>姓名</th>
        <th>性别</th>
        <th>操作</th>
    </tr>

    <tr>
        <td><input type="checkbox"  name="cb" ></td>
        <td>1</td>
        <td>令狐冲</td>
        <td>男</td>
        <td><a href="javascript:void(0);">删除</a></td>
    </tr>

    <tr>
        <td><input type="checkbox"  name="cb" ></td>
        <td>2</td>
        <td>任我行</td>
        <td>男</td>
        <td><a href="javascript:void(0);">删除</a></td>
    </tr>

    <tr>
        <td><input type="checkbox"  name="cb" ></td>
        <td>3</td>
        <td>岳不群</td>
        <td>?</td>
        <td><a href="javascript:void(0);">删除</a></td>
    </tr>

</table>
<div>
    <input type="button" id="selectAll" value="全选">
    <input type="button" id="unSelectAll" value="全不选">
    <input type="button" id="selectRev" value="反选">
</div>
</body>
</html>
```

## 案例2—表单校验

- 效果

  ![表单校验](/img/表单校验.png)

- 要求

  - 输入用户名和密码时，如果用户名或者密码格式不对，则提示用户名或者密码格式有误

- 思路

  - 给表单绑定onsubmit事件。监听器中判断每一个方法校验的结果。
        如果都为true，则监听器方法返回true
        如果有一个为false，则监听器方法返回false
  - 定义一些方法分别校验各个表单项
    - 需要结合正则表达式进行判断
  - 给各个表单项绑定onblur事件

  ```html
  演示：
  <!DOCTYPE html>
  <html lang="en">
  <head>
      <meta charset="UTF-8">
      <title>注册页面</title>
  <style>
      *{
          margin: 0px;
          padding: 0px;
          box-sizing: border-box;
      }
      body{
          background: url("img/register_bg.png") no-repeat center;
          padding-top: 25px;
      }
      .rg_layout{
          width: 900px;
          height: 500px;
          border: 8px solid #EEEEEE;
          background-color: white;
          /*让div水平居中*/
          margin: auto;
      }
      .rg_left{
          /*border: 1px solid red;*/
          float: left;
          margin: 15px;
      }
      .rg_left > p:first-child{
          color:#FFD026;
          font-size: 20px;
      }
      .rg_left > p:last-child{
          color:#A6A6A6;
          font-size: 20px;
  
      }
      .rg_center{
          float: left;
         /* border: 1px solid red;*/
  
      }
      .rg_right{
          /*border: 1px solid red;*/
          float: right;
          margin: 15px;
      }
      .rg_right > p:first-child{
          font-size: 15px;
  
      }
      .rg_right p a {
          color:pink;
      }
  
      .td_left{
          width: 100px;
          text-align: right;
          height: 45px;
      }
      .td_right{
          padding-left: 50px ;
      }
      #username,#password,#email,#name,#tel,#birthday,#checkcode{
          width: 251px;
          height: 32px;
          border: 1px solid #A6A6A6 ;
          /*设置边框圆角*/
          border-radius: 5px;
          padding-left: 10px;
      }
      #checkcode{
          width: 110px;
      }
      #img_check{
          height: 32px;
          vertical-align: middle;
      }
      #btn_sub{
          width: 150px;
          height: 40px;
          background-color: #FFD026;
          border: 1px solid #FFD026 ;
      }
      .error{
          color:red;
      }
      #td_sub{
          padding-left: 150px;
      }
  
  </style>
  <script>
      window.onload = function(){
          //1.给表单绑定onsubmit事件
          document.getElementById("form").onsubmit = function(){
              //调用用户校验方法   chekUsername();
              //调用密码校验方法   chekPassword();
              return checkUsername() && checkPassword();
          }
          //给用户名和密码框分别绑定离焦事件
          document.getElementById("username").onblur = checkUsername;
          document.getElementById("password").onblur = checkPassword;
      }
      //校验用户名
      function checkUsername(){
          //1.获取用户名的值
          var username = document.getElementById("username").value;
          //2.定义正则表达式
          var reg_username = /^\w{6,12}$/;
          //3.判断值是否符合正则的规则
          var flag = reg_username.test(username);
          //4.提示信息
          var s_username = document.getElementById("s_username");
  
          if(flag){
              //提示绿色对勾
              s_username.innerHTML = "<img width='35' height='25' src='img/gou.png'/>";
          }else{
              //提示红色用户名有误
              s_username.innerHTML = "用户名格式有误";
          }
          return flag;
      }
  
      //校验密码
      function checkPassword(){
          //1.获取用户名的值
          var password = document.getElementById("password").value;
          //2.定义正则表达式
          var reg_password = /^\w{6,12}$/;
          //3.判断值是否符合正则的规则
          var flag = reg_password.test(password);
          //4.提示信息
          var s_password = document.getElementById("s_password");
  
          if(flag){
              //提示绿色对勾
              s_password.innerHTML = "<img width='35' height='25' src='img/gou.png'/>";
          }else{
              //提示红色用户名有误
              s_password.innerHTML = "密码格式有误";
          }
          return flag;
      }
  </script>
  </head>
  <body>
  
  <div class="rg_layout">
      <div class="rg_left">
          <p>新用户注册</p>
          <p>USER REGISTER</p>
  
      </div>
  
      <div class="rg_center">
          <div class="rg_form">
              <!--定义表单 form-->
              <form action="#" id="form" method="get">
                  <table>
                      <tr>
                          <td class="td_left"><label for="username">用户名</label></td>
                          <td class="td_right">
                              <input type="text" name="username" id="username" placeholder="请输入用户名">
                              <span id="s_username" class="error"></span>
                          </td>
                      </tr>
  
                      <tr>
                          <td class="td_left"><label for="password">密码</label></td>
                          <td class="td_right">
                              <input type="password" name="password" id="password" placeholder="请输入密码">
                              <span id="s_password" class="error"></span>
                          </td>
                      </tr>
  
                      <tr>
                          <td class="td_left"><label for="email">Email</label></td>
                          <td class="td_right"><input type="email" name="email" id="email" placeholder="请输入邮箱"></td>
                      </tr>
  
                      <tr>
                          <td class="td_left"><label for="name">姓名</label></td>
                          <td class="td_right"><input type="text" name="name" id="name" placeholder="请输入姓名"></td>
                      </tr>
  
                      <tr>
                          <td class="td_left"><label for="tel">手机号</label></td>
                          <td class="td_right"><input type="text" name="tel" id="tel" placeholder="请输入手机号"></td>
                      </tr>
  
                      <tr>
                          <td class="td_left"><label>性别</label></td>
                          <td class="td_right">
                              <input type="radio" name="gender" value="male" checked> 男
                              <input type="radio" name="gender" value="female"> 女
                          </td>
                      </tr>
  
                      <tr>
                          <td class="td_left"><label for="birthday">出生日期</label></td>
                          <td class="td_right"><input type="date" name="birthday" id="birthday" placeholder="请输入出生日期"></td>
                      </tr>
  
                      <tr>
                          <td class="td_left"><label for="checkcode" >验证码</label></td>
                          <td class="td_right"><input type="text" name="checkcode" id="checkcode" placeholder="请输入验证码">
                              <img id="img_check" src="img/verify_code.jpg">
                          </td>
                      </tr>
  
  
                      <tr>
                          <td colspan="2" id="td_sub"><input type="submit" id="btn_sub" value="注册"></td>
                      </tr>
                  </table>
  
              </form>
  
  
          </div>
  
      </div>
  
      <div class="rg_right">
          <p>已有账号?<a href="#">立即登录</a></p>
      </div>
  </div>
  </body>
  </html>
  ```
  
  