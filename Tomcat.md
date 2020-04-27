# Web相关概念（回顾）

- 软件架构
  - C/S架构：客户端/服务器端
  - B/S架构：浏览器/服务器端
- 资源分类
  - 静态资源：所有用户访问页面得到相同的结果，可直接被浏览器解析
  - 动态资源：不同用户访问页面可能得到不同结果，服务器端将其转变为静态资源，在返回浏览器解析
- 网络通信三要素
  - IP：电子设备在网络中的唯一标识
  - 端口：应用程序在计算机中的唯一标识，端口范围:0~65536
  - 传输协议：规定了数据传输的规则
    - 基础协议
      - tcp:安全协议，三次握手确认后传输，速度较慢
      - udp：不安全协议。速度较快





# web服务器软件

- 服务器：安装了服务器软件的计算机
- 服务器软件：接收用户的请求，处理请求，做出响应
- web服务器软件：接收用户请求，处理请求，做出响应
  - 在web服务器软件中，可以部署web项目，让用户通过浏览器来访问这些项目
  - 动态资源主要在web服务器中运行，所以web服务器也称web容器
- 常见的java相关的web服务器软件
  - webLogic：Oracle公司的服务器，大型javaEE服务器，支持所有的JavaEE规范，收费
  - webSphere：IBM公司的服务器，大型javaEE服务器，支持所有的JavaEE规范，收费
  - JBOSS：JBOSS公司的服务器，大型javaEE服务器，支持所有的JavaEE规范，收费
  - Tomcat：Apache基金组织，中小型javaEE服务器，仅支持少了JavaEE规范，免费开源

# Tomcat

## 基本使用

### 下载

https://tomcat.apache.org/download-10.cgi

### 安装

- 解压下载的压缩包即可

- 注意：安装目录建议不要使用中文或者空格

### 卸载

- 直接删除目录即可

### Tomcat目录结构

![tomcat目录结构](/img/tomcat目录结构.png)
- backup：备份文件的目录
- bin目录：存放可执行文件
- conf：存放配置文件
- lib：存放依赖的jar包
- logs：存放日志文件
- temp：存放临时文件
- webapps（重要）：存放web项目
- work：存放运行时的数据

### 启动tomcat

- bin目录下的：双击startup.bar(windows系统)，startup.sh(Linux系统)即开启服务器
- 浏览器访问：127.0.0.1:8080或者(localhost:8080) 如果出现tomcat官网，即服务器开启成功
- 同一局域网内：别人可以访问   “你的ip地址”:8080 

- 启动tomcat可能遇到的问题

  - 黑窗口一闪而过

    - 原因：没有正确JAVA_HOME环境变量
    - 解决方法：正确配置JAVA_HOME环境变量即可

  - 启动报错

    - 原因：存在2个start_up窗口，端口已经被第一次占用

    - 解决方法

      1. 找到占用端口号，并找到对应进程，直接中止

         - cmd---->输入：netstat -ano---->寻找8080端口的PID编号---->任务管理器中止对应PID进程

      2. 修改自身的端口号

         - config目录下，找到server.xml文件，编辑
         - 修改port端口

         ```xml
         <Connector connectionTimeout="20000" port="8080" protocol="HTTP/1.1" redirectPort="8443"/>
         ```

         

         - 一般会将tomcat的默认端口号修改为80，80端口号是http协议的默认端口号

           - 好处：在访问时，就不需要输入端口号

           

           

### 关闭tomcat

- 强制关闭
  - 直接点击启动窗口的“X”号
  - 不推荐，可能会导致文档未保存
- 正常关闭
  - 点击bin目录下的shutdown.bat(麻烦，不推荐)
  - 在服务器端口里，按Ctrl+C 正常对出



### 配置

- 部署项目的方式

  - 直接将项目放到webapps目录下面即可

    - 访问方式：localhost:8080/项目文件夹/项目名称
    - 简化部署：将项目打成war包放在webapps中，会自动生成项目，删除war文件，会自动删除生成的项目

  - 可以配置config/server.xml文件

    - 在<Host>标签体中配置<Context docBase= "项目路径" path="虚拟目录"/>
    - 缺点：可能损害server.xml配置文件，让服务器崩溃

  - 在config/Catalina/localhost创建一个xml文件

    ​	在文件中编写<Context docBase= "项目路径"/>

    - 其虚拟目录就是所创建的xml文件的名称

- 项目形式说明

  - 静态项目：只能存放静态资源

  - 动态资源：不仅仅可以存放静态资源，还可以存放动态资源

  - 目录结构的区别

    - Java动态项目的目录结构

      -- 项目的根目录

      ​	-- WEB-INF目录

      ​		-- web.xml:web项目的核心配置文件

      ​		-- classes目录：放置字节码文件的目录

      ​		-- lib目录：放置依赖的jar包

## 集成tomcat到Idea

- 将Tomcat集成到Idea中，并且创建JavaEE的项目，部署项目

- 步骤

  - run-->Edit Configurations...-->Defaults-->Tomcat Server-->Local

    ![tomcat集成idea](/img/tomcat集成idea.png)

  - 点击configure.. 添加安装的tomcat目录

  - 创建JavaEE项目

  ![idea中的tomcat](/img/idea中的tomcat.png)

