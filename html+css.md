# JavaWeb开发概述

## 概念

* 使用Java语言开发基于互联网的项目

## 两种软件架构

### C/S架构

* 概念：本地客户端与远程服务器端交互

* 优点：用户体验好，交互性强，技术成熟

* 缺点：开发，安装，维护，部署较麻烦

### B/S架构（详解）

* 概念：浏览器端与远程服务器交互

* 优点：开发，安装，部署，维护简单

* 缺点：对硬件要求大，用户量增大可能会带来不好的用户体验

* 资源分类

  * 静态资源（引出html，css，JavaScript）
    * 使用静态网页开发技术发布的资源
    * 特点：
      * 所有用户访问，得到相同的结果
      * 静态资源包括：文本，图片，视频，音频,html，css，JavaScript等等
      * 原理：用户请求静态资源，浏览器直接将静态资源发送给浏览器，浏览器内置的解析引擎解析资源，而后在页面进行展示
  * 动态资源（引出jsp/servlet技术）
    * 使用静态网页开发技术发布的资源
    * 特点：
      * 不同用户访问，可能得到不同的结果
      * 动态资源如：jsp/servlet，php，asp等
      * 原理：用户请求动态资源，服务器端将接收的请求转化为相应的静态资源，发送给浏览器端

  

### 静态资源概述

* HTML：搭建基础网页
* CSS：美化，布局页面
* JavaScript：控制页面，产生动态效果



# HTML

## 概念

* 超文本标记语言![avatar](/img/html概述.png)

## 快速入门

### 基本语法(语法不是特别严格)

* html文档后缀名为 .html或.htm
* 标签分类：
  * 围堵标签：有开始和结束标签。如 <div></div>
  * 自闭标签：开始和结束标签在一起。如 <br/>
* 标签之间可以嵌套
* 开始标签中可以定义属性，由键值对组成，值可以使用单引号或双引号引起来
* html标签不区分大小写，但是一般使用小写
* 示例

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    
    <font color="red">hello world</font>
    <font color='red'>hello world</font>
    
</body>
</html>
```

### 学习网站

***https://www.runoob.com/***

****

****

****

## 基本标签

#### 文件标签

* `<html></html>`
* `<head></head>`
* `<title></title>`
* `<body></body>`
* `<!DOCTYPE html>`

#### 文本标签

* `<h1></h1>~<h6></h6>`:标题标签，字体大小由1-6逐渐递减
* `<p></p>`：段落标签
* `<br/>`：换行标签
* `<hr/>`：一条直线
  * 包含许多属性:color,width,size,align等等
* `<b></b>`：加粗
* `<i></i>`：斜体
* `<font></font>`(以淘汰):
  * 属性:color,size,face等等
* `<center></center>`：居中标签

#### 图片标签

* `<img >`:图片标签
  * 属性：**src**，align，alt，width，height
  * src
    * 相对路径（通常使用）
      * ./  代表当前目录
      * ../  代表上一级目录
    * 绝对路径:图片的全路径

#### 列表标签

* 有序列表

  ```html
  <ol>
      <li></li>
      <li></li>
  </ol>
  ```

  

* 无序列表

  ```html
  <ul>
      <li></li>
      <li></li>
  </ul>
  ```

  

#### 链接标签

* `<a></a>`:超链接
  * 属性
    * href：添加url地址或者其他静态页面，点击跳转到该地址
    * target:指定打开的方式 
      * _blank(在新页面跳转该地址),
      *  _self(在该页面跳转该地址)

#### 块标签

* 常常与css样式结合起来

* `<span></span>`:不换行
* `<div></div>`：换行

#### 语义化标签

* `<header></header>`:头标签
* `<footer></footer>`：尾标签
* 一般增加可读性，没有任何样式

#### 表格标签

* `<table></table>:定义表格`

  * 属性

    * width:表宽度

    * border：边框，

    * cellpadding:定义内容和单元格的距离

    * cellspacing:定义单元格的距离

    * bgcolor:表格背景色

    * align:表格对齐方式

      

* `<tr></tr>`：定义行

* `<td></td>`:定义单元格

  * 属性
    * colspan:合并列
    * rowspan:合并行

* `<th></th>`:定义表头单元格，使内容在表格中居中加粗

  * 属性
    * colspan:合并列
    * rowspan:合并行

* `<caption></caption>`:表格标题

* `<thead></thead>`:类似于语义化标签，增加可读性

* `<tbody></tbody>`:。。。

* `<tfoot></tfoot>`:。。。

#### **表单标签（重要）**

* 用于采集用户输入数据，以便与服务器进行交互



* 表单标签

  * `<form></form>`:用于定义表单，定义一个采集用户数据的范围

    * 属性：

      * action：指定提交数据的URL

      * method：指定提交表单的方式（七种）

        1. get（常用）：若要提交表单中数据，必须指定输入表单项的name属性

        2. post（常用）：同上

        * 二者的区别
          * get
            * 请求参数会在地址栏中显示；
            * 请求参数的长度有限制
          * post
            * 请求参数不会再地址栏中显示，会封装在请求体中，更安全
            * 请求参数没有长度限制 



* 表单项标签
  * `<input>`:可通过type属性值，改变input样式
    * type属性：
      * text：文本输入框，默认
        1. placeholder：指定输入框的提示信息
      * password：密码框
      * radio：单选框
        1. 多个name相同的单选框组合起来
        2. 给每个单选框一个value值，才具有实际意义
        3. checked属性值可以指定默认值
      * checkbox：复选框 
      * file：文件选择框，提交文件到服务器端
      * hidden：隐藏域，用于携带隐藏的数据，提交到服务器端
      * submit：提交按钮，可以提交表单
      * button：普通提交按钮，结合JavaScript使用
      * image：通过src属性，使用图片进行提交表单
      * color：取色器，提交颜色代码
      * date：选择时间，包括年月日
      * datetime-local：选择时间，包括年月日时分
      * email：邮箱输入
      * number：只能输入数字
  * `<select></select>`:下拉列表，添加name属性才有意义
    * `<option></option>`：定义列表项
  * `<textarea></textarea>`：文本域，一个可以输入更多信息的文本框
    * cols：指定列数
    * rows：默认行数





# CSS（不做太高要求）



## 概述



## ![avatar](/img/css概述.png)



## 优点

* 功能更加强大，具有更多的样式
* 将内容展示和样式控制分离，降低耦合度，提高开发效率



## CSS与HTML结合方式

### 内联样式（不常使用）

* 使用style属性指定css代码

* 直接在html中插入

  ```html
  <div style="color: red;">
      Hello World!
  </div>
  ```



### 内部样式（较常用）

* 在`<head></head>`标签中定义style标签

* 但是这种方式的css样式只能作用与特定作用域中

  ```html
  <!-- 代表所有div标签中的字体颜色为红色 -->
  <head>
      <style>
          div{
              color: red;
          }
      </style>
  </head>
  ```

### 外部样式(常用)

* 将css样式抽取到css资源文件
* 使用`<link>`标签引入外部资源文件

```css
div{
    color:red;
}
```

```html
<head>
    <link rel="stylesheet" href="css/a.css">
    
    <!--另一种写法,不常用-->
    <style>
    	@import: "css/a.css";
    </style>
</head>
```



## CSS基本语法

### 格式

```css
选择器{   //筛选出具有相同特征的元素
    属性名1：属性值1;   //注意需要加上分号
    属性名2：属性值2;
    ...
}
```



### 选择器

* 基本选择器

  * id选择器

  * 元素选择器

  * 类选择器

    ```html
    <head>
        <style>
            <!-- id选择器-->
            #div1{
                color:red;
            }
            <!-- 元素选择器-->
            div{
                color:red;
            }
            <!-- 类选择器-->
            .cls1{
                color:red;
            }
            <!--
            	优先级：
            		id选择器>类选择器>元素选择器
            -->
        </style>
    </head>
    <body>
        
        <p id='div1'>Hello World</p>
        <div>Hello World</div>
        <p class='cls1'>Hello World</p>
        
    </body>
    ```

    

* 扩展选择器

  https://www.w3school.com.cn/cssref/css_selectors.asp

  1. 选择所有元素：
     * 语法：*{}
  2. 并集选择器：
     * 语法： 选择器1，选择器2 {}
  3. 子选择器：
     * 语法：选择器1	选择器2{}
  4. 父选择器：
     * 语法：选择器1>选择器2{}
  5. 属性选择器：
     * 语法：元素名称[属性名=”属性值“]{}
  6. 伪选择器：
     * 语法：元素：状态{}





### 属性

1. 字体，文本
   * font-size ：字体大小
   * color：字体颜色
   * text-align：对其方式
   * line-height：行高
2. 背景
   * background：背景的相关属性
3. 边框
   * border：边框的相关属性
4. 尺寸
   * width：宽度
   * height：高度
5. 盒子模型
   * margin：外边距
   * padding：内边距
     * 默认情况下内边距会影响整个盒子的大小
     * box-sizing： border-box； 设置盒子属性，固定盒子的大小
   * float：浮动
     * left：像左浮动
     * right：向右浮动