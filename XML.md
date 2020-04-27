# XML

## 概念

- Extensible Markup Language 可扩展标记语言
  - 可扩展：指的是标签都是可以自定义的。
- XML与HTML的区别
  - HTML语法松散的原因：早期浏览器之间的恶性竞争，尽管HTML语法可能有错误，但是浏览器仍可解析
  - 早期W3C组织为了解决HTML语法松散问题，发明出XML，但是XML语法更严格却没有任何提升
  - 由于不能与HTML竞争，后期以传送及携带数据信息为主
- XML的功能
  - 存储数据
    1. 配置文件
    2. 在网络中传输
- XML与HTML的区别
  - xml标签都是自定义的，html标签都是预定义的
  - xml语法严格，html语法松散
  - xml用来传送和携带数据，html用来展示数据

## 语法

### 基本语法

- xml文档的后缀名为.xml
- xml文档第一行必须定义为文档申明（注意必须是第一行）
- xml文档有且只有一个根标签
- 标签属性值必须用引号（单双都可以）引起来
- 标签必须正确结束，围堵标签必须要有结束标签
- XML标签区分大小写

### 快速入门

```xml
<?xml version="1.0" ?><!--必须在第一行-->
<users>
    <user id="1">
        <name>zhangsan</name>
        <age>23</age>
        <gender>male</gender>
    </user>
    <user id="2">
        <name>lisi</name>
        <age>25</age>
        <gender>male</gender>
    </user>
</users>
```

### 组成部分

- 文档声明

  - 格式：`<?xml version="1.0" encoding="utf-8"standalone="no" ?>`
  - 属性列表
    - version：版本号，必须要有的属性
    - encoding：编码方式，告知解析引擎当前文档使用的字符集，默认值：ISO-8859-1
    - standalone：是否独立
      - 取值为yes：不依赖其他文件
      - 取值为no：依赖其他文件

- 指令（了解）：结合css，可以展示数据。（了解即可，不必要使用这个功能）

- 标签：自定义标签名称

  - 规则
    - 名称可以含字母、数字以及其他的字符
    - 名称不能以数字或者标点符号开始
    - 名称不能以字符 “xml”（或者 XML、Xml）开始
    - 名称不能包含空格

- 属性：id值唯一

- 文本

  - CDATA区：该区域的数据会被原样展示

    ​		格式：<![CDATA[
    ​            数据
    ​            ]]>

  ```xml
  演示:
   <code>
              <![CDATA[
              数据
              ]]>
  </code>
  ```

  

## 约束

- 引言：xml文件主要由程序员开发时编写，编写完成后，框架解析相应的xml文件。但是xml文件的标签都是自   定义的，框架需要解析xml文件，就编写了一个说明文档，规定xml 文件的书写规则。程序员就得按照这个说明文档来编写xml文件，以便框架的解析。称该说明文档为约束文档

### 概念

- 规定xml文档的书写规则

- 作为框架使用者的要求
  1. 能够在xml文件中引入约束文档
  2. 能够简单的读懂约束文档

### 分类

1. DTD：一种简单的约束技术

2. Schema：一种复杂的约束技术





- DTD

  - 引入dtd文件到xml文件中
    - 内部dtd：将约束规则定义在xml文档中（不常用）
    - 外部dtd：将约束规则定义在外部dtd文件中
      - 本地dtd：`<!DOCTYPE 根标签名 SYSTEM "dtd文件的位置">`
      - 网络dtd：`<!DOCTYPE 根标签名 PUBLIC "dtd文件的名字" "dtd文件的位置URL">`

  ```dtd
  dtd文件：限制xml的书写规则
  <!ELEMENT students (student*) >      
  <!ELEMENT student (name,age,sex)>
  <!ELEMENT name (#PCDATA)>
  <!ELEMENT age (#PCDATA)>
  <!ELEMENT sex (#PCDATA)>
  <!ATTLIST student number ID #REQUIRED>
  ```

  ```xml
  xml文件：
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE students SYSTEM "student.dtd">
  <students>
      <student id="001">   <!--语法及其严格，标签顺序也必须按照dtd文件的标签顺序-->
          <name>zhangsan</name>
          <age>20</age>
          <sex>male</sex>
      </student>
      
      <student id="002">      <!--id值不能时一样的-->
          <name>lisi</name>
          <age>20</age>
          <sex>male</sex>
      </student>
  </students>
  ```

  - dtd文档的缺陷：不能限制标签的内容



- Schema：可以限制标签的内容

  ```scheme
  Schema文档示例：以下标签都已经限制标签内容
  <?xml version="1.0"?>
  <xsd:schema xmlns="http://www.itcast.cn/xml"
          xmlns:xsd="http://www.w3.org/2001/XMLSchema"
          targetNamespace="http://www.itcast.cn/xml" elementFormDefault="qualified">
      <xsd:element name="students" type="studentsType"/>
      <xsd:complexType name="studentsType">
          <xsd:sequence>
              <xsd:element name="student" type="studentType" minOccurs="0" maxOccurs="unbounded"/>
          </xsd:sequence>
      </xsd:complexType>
      <xsd:complexType name="studentType">
          <xsd:sequence>
              <xsd:element name="name" type="xsd:string"/>
              <xsd:element name="age" type="ageType" />
              <xsd:element name="sex" type="sexType" />
          </xsd:sequence>
          <xsd:attribute name="number" type="numberType" use="required"/>
      </xsd:complexType>
      <xsd:simpleType name="sexType">
          <xsd:restriction base="xsd:string">
              <xsd:enumeration value="male"/><!--限制为male和female两个值-->
              <xsd:enumeration value="female"/>
          </xsd:restriction>
      </xsd:simpleType>
      <xsd:simpleType name="ageType">
          <xsd:restriction base="xsd:integer">
              <xsd:minInclusive value="0"/><!--限制为0-256-->
              <xsd:maxInclusive value="256"/>
          </xsd:restriction>
      </xsd:simpleType>
      <xsd:simpleType name="numberType">
          <xsd:restriction base="xsd:string"><!--限制为 heima_XXXX 类型  X为数字-->
              <xsd:pattern value="heima_\d{4}"/>
          </xsd:restriction>
      </xsd:simpleType>
  </xsd:schema> 
  ```

  - 引入Scheme文档
    - 填写xml文档的根元素
      - 引入xsi前缀
      - 引入xsd文件命名空间
      - 为每一个xsd约束声明一个前缀,作为标识

  ```
  演示：xml文档引入Scheme文档
  <?xml version="1.0" encoding="UTF-8" ?>
  <!-- 
  	1.填写xml文档的根元素
  	2.引入xsi前缀.  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  	3.引入xsd文件命名空间.  xsi:schemaLocation="http://www.itcast.cn/xml  student.xsd"
  	4.为每一个xsd约束声明一个前缀,作为标识  xmlns="http://www.itcast.cn/xml" 
   -->
   <students   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   			 xmlns="http://www.itcast.cn/xml" 
   		   xsi:schemaLocation="http://www.itcast.cn/xml  student.xsd"
   		    >
   	<student number="heima_0001">
   		<name>tom</name>
   		<age>18</age>
   		<sex>male</sex>
   	</student>
  		 
   </students>
  ```

  

## 解析

### 相关概念

- 含义:操作xml文档，将文档中的数据读取到内存中

- 操作xml文档

  1. 解析（读取）：将文档中的数据读取到内存中去
  2. 写入：将内存中的数据保存到xml文档中，持久化操作（不经常使用）

- 解析xml的方式

  （服务器端一般使用DOM方式）

  1. DOM：将标记语言文档一次性加载到内存，在内存中形成一个DOM树
     - 优点：操作方便，可以对文档进行CRUD的所有操作
     - 缺点：占内存
  2. SAX：逐行读取，基于事件驱动（移动端如手机设备上，使用SAX方式）
     - 优点：基本上不占用内存
     - 缺点：只能读取

- xml常见解析器

  - JAXP：SUN公司提供的解析器，支持DOM和SAX方式
  - DOM4J：一款不错的解析器
  - Jsoup（主要）：jsoup 是一款Java 的HTML解析器，可直接解析某个URL地址、HTML文本内容。它提供了一套非常省力的API，可通过DOM，CSS以及类似于jQuery的操作方法来取出和操作数据
  - PULL：Android系统内置的解析器，使用SAX方式

### Jsoup解析器

- 快速入门
  1. 导入jar包
  2. 获取Document对象
  3. 获取对应的标签Element对象
  4. 获取数据

```xml
xml文档：
<?xml version="1.0" encoding="UTF-8" ?>

<students>
    <student number="heima_0001">
        <name id="itcast">tom</name>
        <age>18</age>
        <sex>male</sex>
    </student>
    <student number="heima_0002">
        <name>jack</name>
        <age>18</age>
        <sex>female</sex>
    </student>

</students>
```



```java
演示:
public class JsoupDemo1 {

    public static void main(String[] args) throws IOException {
        //获取Document对象，根据xml文档获取
        //1.获取xml文档的path
        String path = JsoupDemo1.class.getClassLoader().getResource("student.xml").getPath();
        //2.解析xml文档，加载进入内存，获取DOM树——Document
        Document document = Jsoup.parse(new File(path), "utf-8");
        //3.获取元素对象Element  (Element继承ArrayList数组)
        Elements elements = document.getElementsByTag("name");

        //获取name标签的数目
        System.out.println(elements.size());
        //获取第一个name标签的内容
        System.out.println(elements.get(1).text());
    }
}
```

- Jsoup常见对象以及各自常用方法

  - Jsoup：工具类，可以解析xml或html文档，返回Document

    - parse：解析html或者xml文档，返回Document
      - parse(File in,String charsetName):解析xml或html对象（常用）
      - parse(String html):解析xml或者html字符串（不常用）
      - parse(URL url,int timeoutMillis)：通过网络路径获取xml或html文档对象（解析html文件常用，可以做一些爬虫的小程序，获取各个网站的数据）

    ```java
    演示：
        public class JsoupDemo2 {
    
        public static void main(String[] args) throws IOException {
            //1.获取xml文档的path
            String path = JsoupDemo1.class.getClassLoader().getResource("student.xml").getPath();
            //2.解析xml文档，加载进入内存，获取DOM树——Document
            URL url = new URL("httpSs://www.baidu.com");
            Document document = Jsoup.parse(url, 10000);//10000表示最大响应时间
            System.out.println(document);//控制台会打印www.baidu.com页面的html代码
        }
    }
    ```

    

  - Document：文档对象，代表内存中的DOM树

    - 获取Elements对象
      - getElementById(String id):根据id获取元素对象
      - getElementByTag(String tagName):根据标签名称获取元素对象集合
      - getElementByAttribute(String key):根据属性名称获取元素对象集合
      - getElementByAttributeValue(String key,String value):根据对应属性名和属性值获取元素对象集合

    ```java
    演示：
       public class JsoupDemo3 {
    
        public static void main(String[] args) throws IOException {
            //获取Document对象，根据xml文档获取
            //1.获取xml文档的path
            String path = JsoupDemo1.class.getClassLoader().getResource("student.xml").getPath();
            //2.解析xml文档，加载进入内存，获取DOM树——Document
            Document document = Jsoup.parse(new File(path), "utf-8");
            //3.获取元素对象
            /*
              3.1获取所有name标签对象
              输出结果：<name id="itcast">
                         tom
                        </name>
                        <name>
                         jack
                        </name>
             */
            Elements elements1 = document.getElementsByTag("name");
            System.out.println(elements1);
            System.out.println("--------------------------");
            /*
              3.2获取属性名为id的对象
              输出结果：<name id="itcast">
                         tom
                        </name>
             */
            Elements elements2 = document.getElementsByAttribute("id");
            System.out.println(elements2);
            System.out.println("--------------------------");
             /*
              3.2获取number属性值为heima_0001的元素对象
              输出结果：<student number="heima_0001">
                         <name id="itcast">
                          tom
                         </name>
                         <age>
                          18
                         </age>
                         <sex>
                          male
                         </sex>
                        </student>
             */
            Elements elements3 = document.getElementsByAttributeValue("number","heima_0001");
            System.out.println(elements3);
        }
    }
    ```

  - Elements:元素中Element对象的集合。可以当作ArrayList<Element>来使用

  - Element：元素对象

    - 获取子元素对象
      - getElementById(String id):根据id获取元素对象
      - getElementByTag(String tagName):根据标签名称获取元素对象集合
      - getElementByAttribute(String key):根据属性名称获取元素对象集合
      - getElementByAttributeValue(String key,String value):根据对应属性名和属性值获取元素对象集合
    - 获取属性值
      - String attr(String key):根据属性名称获取属性值(该类继承父类Node中的attr方法，在这里属性名称不区分大小写)
    - 获取文本内容
      - String text():获取纯文本内容
      - String html():获取标签体中的所有内容（包括标签体中的字符串内容）

    ```java
    演示：
        public class JsoupDemo4 {
    
        public static void main(String[] args) throws IOException {
            //1.获取xml文档的path
            String path = JsoupDemo1.class.getClassLoader().getResource("student.xml").getPath();
            //2.解析xml文档，加载进入内存，获取DOM树——Document
            Document document = Jsoup.parse(new File(path), "utf-8");
            //通过Document对象获取子标签对象
            Element element_student = document.getElementsByTag("student").get(0);
            /*
                获取第一个student标签对象的name标签
                结果：  <name id="itcast">
                         tom
                        </name>
             */
            Elements ele_name = element_student.getElementsByTag("name");
            System.out.println(ele_name);
    
            /*
                获取第一个student标签对象的number属性值
                结果：heima_0001
             */
            String number = element_student.attr("NUMBer");
            System.out.println(number);
    
            /*
                获取文本内容
                结果：  tom
                        -----------------
                        tom
    
                 如果这里的name标签内容变成：<name id="itcast">
                                                <xing>张</xing>
                                                <ming>三</ming>
                                            </name>
                 那么结果变成： 张 三
                                -----------------
                                <xing>
                                 张
                                </xing>
                                <ming>
                                 三
                                </ming>
    
             */
            String text = ele_name.text();
            String html = ele_name.html();
            System.out.println(text);
            System.out.println("-----------------");
            System.out.println(html);
    
        }
    }
    ```

    

  - Node：节点对象（了解，有印象即可）

    - 是Document和Element的父类

- 快捷查询方式

  - selector：选择器

    - 使用的方法:select(String cssQuery)
    - 具体的cssQuery的编写方法可查询文档

    ```java
    演示：
        public class JsoupDemo5 {
        public static void main(String[] args) throws IOException {
            //1.获取xml文档的path
            String path = JsoupDemo1.class.getClassLoader().getResource("student.xml").getPath();
            //2.解析xml文档，加载进入内存，获取DOM树——Document
            Document document = Jsoup.parse(new File(path), "utf-8");
           /*
                查询name标签
                结果：  <name id="itcast">
                         tom
                        </name>
                        <name>
                         jack
                        </name>
            */
            Elements elements1 = document.select("name");
            System.out.println(elements1);
    
            System.out.println("-----------------------");
            /*
                查询id为itcast的标签
                结果：  <name id="itcast">
                         tom
                        </name>
            */
            Elements elements2 = document.select("#itcast");
            System.out.println(elements2);
            System.out.println("-----------------------");
            /*
                获取student标签里number属性值为heima_0001的age子标签
                结果：  <age>
                         18
                        </age>
            */
            Elements elements3 = document.select("student[number='heima_0001'] > age");
            System.out.println(elements3);
        }
    }
    ```

    

  - XPath

    - 概念：XPath即为XML路径语言（XML Path Language），它是一种用来确定XML文档中某部分位置的计算机语言  

    - 使用

      - 需要额外导入jar包JsoupXpath-0.3.2.jar

      - 根据document对象，创建JXDocument对象

      - 结合XPath语法查询(语法查询文档学习）

        https://www.w3school.com.cn/xpath/xpath_syntax.asp

    ```java
    演示:
    public class JsoupDemo6 {
    
        public static void main(String[] args) throws IOException, XpathSyntaxErrorException {
            //1.获取xml文档的path
            String path = JsoupDemo1.class.getClassLoader().getResource("student.xml").getPath();
            //2.解析xml文档，加载进入内存，获取DOM树——Document
            Document document = Jsoup.parse(new File(path), "utf-8");
            //根据document对象，创建JXDocument对象
            JXDocument jxDocument = new JXDocument(document);
            //结合XPath语法查询
            /*
                查询所有student标签
                结果：   <student number="heima_0001">
                         <name id="itcast">
                          tom
                         </name>
                         <age>
                          18
                         </age>
                         <sex>
                          male
                         </sex>
                        </student>
                        <student number="heima_0002">
                         <name>
                          jack
                         </name>
                         <age>
                          18
                         </age>
                         <sex>
                          female
                         </sex>
                        </student>
             */
            List<JXNode> jxNodes = jxDocument.selN("//student");
            for (JXNode jxNode  : jxNodes ) {
                System.out.println(jxNode);
            }
            System.out.println("-----------------------------");
            /*
                查询所有student标签下带有id属性为itcast的name标签
                结果:   <name id="itcast">
                         tom
                        </name>
             */
            List<JXNode> jxNodes1 = jxDocument.selN("//student/name[@id='itcast']");
            for (JXNode jxNode  : jxNodes1 ) {
                System.out.println(jxNode);
            }
        }
    }
    ```

    

