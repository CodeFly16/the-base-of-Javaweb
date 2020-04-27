# BootStrap（会用就行）

## 引言

- 由于web开发者对css样式的要求不高，所以很难写出一个好看的页面，此时引入bootstrap，里面拥有着很多的小组件以及页面模板，可以直接拿来使用，使页面更加的好看。

## 概述

- 概念：一个前端开发框架，基于HTML，CSS，JavaScript，开发简洁灵活，快捷
  - 框架：指的是一个半成品软件，开发人员可以在框架的基础上，进行开发，简化开发编码
- 优点：
  - 定义了很多的css样式和js插件，可直接使用这些样式和插件得到丰富的页面效果
  - 响应式布局：指的是同一套页面，可以兼容不同分辨率（重要优点)

## 快速入门

- 进入官网下载相应css和JavaScript的包

  - css文件与.min.css文件的区别在于，.min.css文件的所有回车和tab清除了，所有代码显示在一行中
  - .min.css文件的运行速度更快

- 在项目中引入bootstrap

  - 直接引入本地下载的css和JavaScript文件

  ```html
  演示：
  <!DOCTYPE html>
  <html lang="zh-CN">
  ```
<head>
      <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
      <title>Bootstrap 101 Template</title>

      <!-- Bootstrap -->
      <link href="css/bootstrap.min.css" rel="stylesheet">
      
      <!--&lt;!&ndash; HTML5 shim 和 Respond.js 是为了让 IE8 支持 HTML5 元素和媒体查询（media queries）功能 &ndash;&gt;-->
      <!--&lt;!&ndash; 警告：通过 file:// 协议（就是直接将 html 页面拖拽到浏览器中）访问页面时 Respond.js 不起作用 &ndash;&gt;-->
      <!--&lt;!&ndash;[if lt IE 9]>-->
      <!--<script src="https://cdn.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>-->
      <!--<script src="https://cdn.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>-->
      <!--<![endif]&ndash;&gt;-->
  </head>
  <body>
  <h1>你好，世界！</h1>

  <!-- jQuery (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
  <script src="js/jquery-1.11.3.min.js"></script><!-- 后期内容-->
  <!-- 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
  <script src="js/bootstrap.min.js"></script>
  </body>
  </html>
  ```
  
  - 引入远程服务器的css和JavaScript文件`<link>和<script>`标签引入
  
  ```html
  演示：
  <!DOCTYPE html>
  <html lang="zh-CN">
  <head>
      <meta charset="utf-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <!-- 上述3个meta标签*必须*放在最前面，任何其他内容都*必须*跟随其后！ -->
      <title>Bootstrap 101 Template</title>
  
      <!-- Bootstrap -->
      <link href="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/css/bootstrap.min.css" rel="stylesheet">
  
      <!-- HTML5 shim 和 Respond.js 是为了让 IE8 支持 HTML5 元素和媒体查询（media queries）功能 -->
      <!-- 警告：通过 file:// 协议（就是直接将 html 页面拖拽到浏览器中）访问页面时 Respond.js 不起作用 -->
      <!--[if lt IE 9]>
        <script src="https://cdn.jsdelivr.net/npm/html5shiv@3.7.3/dist/html5shiv.min.js"></script>
        <script src="https://cdn.jsdelivr.net/npm/respond.js@1.4.2/dest/respond.min.js"></script>
      <![endif]-->
    </head>
    <body>
      <h1>你好，世界！</h1>
  
      <!-- jQuery (Bootstrap 的所有 JavaScript 插件都依赖 jQuery，所以必须放在前边) -->
      <script src="https://cdn.jsdelivr.net/npm/jquery@1.12.4/dist/jquery.min.js"></script>
      <!-- 加载 Bootstrap 的所有 JavaScript 插件。你也可以根据需要只加载单个插件。 -->
      <script src="https://cdn.jsdelivr.net/npm/bootstrap@3.3.7/dist/js/bootstrap.min.js"></script>
    </body>
  </html>
  ```

  

## 响应式布局(栅格系统 重要)

- 概念：同一套页面可以兼容不同分辨率的设备，如电脑上面的页面，在手机上面依旧适用

- 实现：依赖于栅格系统

- 步骤

  - 定义容器：相当于table
    - 容器分类
      1. container：每种设备并非100%宽度，两边会有留白
      2. container.fluid：每种设备都是100%宽度
  - 定义行：相当于tr    样式：row
  - 定义元素：指定元素在不同设备上，所占的格子数目   样式：col-设备代号-格子数目

  ![栅格系统](/img/栅格系统.png)

  ```
  演示：
  <!DOCTYPE html>
  <html lang="zh-CN">
  <head>
      <meta charset="utf-8">
      <meta http-equiv="X-UA-Compatible" content="IE=edge">
      <meta name="viewport" content="width=device-width, initial-scale=1">
      <title>Bootstrap 101 Template</title>
  
      <link href="css/bootstrap.min.css" rel="stylesheet">
      <script src="js/jquery-1.11.3.min.js"></script>
      <script src="js/bootstrap.min.js"></script>
  </head>
  <body>
      <div class="container-fluid">
          <div class="row">
          //这里表示在pc端一行有12个格子，当浏览器窗口逐渐缩小到平板差不多大小时，一行可以有12/2个格子
              <div class="col-lg-1 col-sm-2 col-xs-3 table-bordered">栅格</div>
              <div class="col-lg-1 col-sm-2 col-xs-3 table-bordered">栅格</div>
              <div class="col-lg-1 col-sm-2 col-xs-3 table-bordered">栅格</div>
              <div class="col-lg-1 col-sm-2 col-xs-3 table-bordered">栅格</div>
              <div class="col-lg-1 col-sm-2 col-xs-3 table-bordered">栅格</div>
              <div class="col-lg-1 col-sm-2 col-xs-3 table-bordered">栅格</div>
              <div class="col-lg-1 col-sm-2 col-xs-3 table-bordered">栅格</div>
              <div class="col-lg-1 col-sm-2 col-xs-3 table-bordered">栅格</div>
              <div class="col-lg-1 col-sm-2 col-xs-3 table-bordered">栅格</div>
              <div class="col-lg-1 col-sm-2 col-xs-3 table-bordered">栅格</div>
              <div class="col-lg-1 col-sm-2 col-xs-3 table-bordered">栅格</div>
              <div class="col-lg-1 col-sm-2 col-xs-3 table-bordered">栅格</div>
          </div>
      </div>
  </body>
  </html>
  ```

  - 注意事项
    - 一行中如果格子数目超过12，则超出部分会自动换行
    - 栅格类的属性可以向上兼容，例如如果只给col-xs-3的属性，那么在pc端和pad端也会显示4个格子
    - 但是不会向下兼容，最终效果是，下面属性的格子会占满一整行

## CSS样式和JS插件（要求会查找文档，并依据自己的需求修改即可）

### 全局CSS样式

- 按钮 class="btn btn-xxxxxxx"

  ```
  演示:
  <!--透明按钮-->
  <button type="button" class="btn btn-default">（默认样式）Default</button>
  <!--蓝色按钮-->
  <button type="button" class="btn btn-primary">（首选项）Primary</button>
  <!--绿色按钮-->
  <button type="button" class="btn btn-success">（成功）Success</button>
  <!--浅蓝色按钮-->
  <button type="button" class="btn btn-info">（一般信息）Info</button>
  <!--橙色按钮-->
  <button type="button" class="btn btn-warning">（警告）Warning</button>
  <!--红色按钮-->
  <button type="button" class="btn btn-danger">（危险）Danger</button>
  <!--蓝色链接-->
  <button type="button" class="btn btn-link">（链接）Link</button>
  ```

  ![按钮](/img/按钮样式.png)

- 图片

  - 实现图片的响应式:class="img-responsive"
  - 设置图片圆角，方角，相框等等

  ```
  演示
  <img src="img/1.png" class="img-responsive img-circle">//圆角
  <img src="img/1.png" class="img-responsive img-thumbnail">//方角
  <img src="img/1.png" class="img-responsive img-rounded">//相框
  ```

  

- 表格

  ```
  演示:
  <table class="table table-bordered table-hover">//添加表格边框，鼠标悬停变色
      <tr>
          <td>1</td>
          <td>2</td>
          <td>3</td>
      </tr>
      <tr>
          <td>4</td>
          <td>5</td>
          <td>6</td>
      </tr>
  </table>
  ```

- 表单

  - 给表单项添加class=“form-XXXXX”

  ```
  演示：
  <form class="form-inline">
    <div class="form-group">
      <label for="exampleInputName2">Name</label>
      <input type="text" class="form-control" id="exampleInputName2" placeholder="Jane Doe">
    </div>
    <div class="form-group">
      <label for="exampleInputEmail2">Email</label>
      <input type="email" class="form-control" id="exampleInputEmail2" placeholder="jane.doe@example.com">
    </div>
    <button type="submit" class="btn btn-default">Send invitation</button>
  </form>
  ```

  ![表单样式](/img/表单样式.png)

### 组件(能够修改即可)

- 导航条

  - 可以通过浏览器审查元素，找出需要修改的地方，并自定义
  - 反转导航条：class=“navbar navbar-inverse”   导航条颜色反转，黑色变成白色，白色变成黑色

- 分页条

  - 用于数据库，对数据库中数据进行分页显示

  ```
  演示:
  <nav aria-label="Page navigation">
    <ul class="pagination">
      <li>
        <a href="#" aria-label="Previous">
          <span aria-hidden="true">&laquo;</span>
        </a>
      </li>
      <li><a href="#">1</a></li>
      <li><a href="#">2</a></li>
      <li><a href="#">3</a></li>
      <li><a href="#">4</a></li>
      <li><a href="#">5</a></li>
      <li>
        <a href="#" aria-label="Next">
          <span aria-hidden="true">&raquo;</span>
        </a>
      </li>
    </ul>
  </nav>
  ```

### 插件

- 轮播图(Carousel 旋转木马)

  ```
  演示
  <div id="carousel-example-generic" class="carousel slide" data-ride="carousel">
    <!-- Indicators -->
    <ol class="carousel-indicators">
      <li data-target="#carousel-example-generic" data-slide-to="0" class="active"></li>
      <li data-target="#carousel-example-generic" data-slide-to="1"></li>
      <li data-target="#carousel-example-generic" data-slide-to="2"></li>
    </ol>
  
    <!-- Wrapper for slides -->
    <div class="carousel-inner" role="listbox">
      <div class="item active">
        <img src="..." alt="...">
        <div class="carousel-caption">
          ...
        </div>
      </div>
      <div class="item">
        <img src="..." alt="...">
        <div class="carousel-caption">
          ...
        </div>
      </div>
      ...
    </div>
  
    <!-- Controls -->
    <a class="left carousel-control" href="#carousel-example-generic" role="button" data-slide="prev">
      <span class="glyphicon glyphicon-chevron-left" aria-hidden="true"></span>
      <span class="sr-only">Previous</span>
    </a>
    <a class="right carousel-control" href="#carousel-example-generic" role="button" data-slide="next">
      <span class="glyphicon glyphicon-chevron-right" aria-hidden="true"></span>
      <span class="sr-only">Next</span>
    </a>
  </div>
  ```

  ![轮播图](/img/轮播图.png)



## 小案例—黑马旅游网

- 分析

  页面主要分为3个部分

  - 页眉部分：无留白  class="container-fluid"
    - 顶部商标图片：搜索栏等等 根据CSS样式自己调试
    - 导航栏：直接从bootstrap中提取，以栅格系统为主，根据自己要求修改
    - 轮播图：直接从bootstrap中提取，在根据自己要求修改
  - 主题部分：有留白  class="container"
    - 多个栅格系统合并
  - 页脚部分：无留白  class="container-fluid"



