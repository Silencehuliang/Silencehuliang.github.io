# Python学习之路-接口测试:工具使用


## Jmeter

### 概念

Jmeter：是Apche公司使用Java平台开发的一款测试工具。

### 作用

- 接口测试  
- 性能测试  
- 压力测试  
- Web自动化测试  
- 数据库测试  
- JAVA程序测试

### 优点：

- 开源、免费
- 支持多协议
- 小巧
- 功能强大

### 缺点

- 不支持IP欺骗
- 使用JMeter无法验证JS程序，也无法验证页面UI，所以要须要和Selenium配合来完成Web2.0应用的测试

## Jmeter工具安装

### 下载

#### 官网下载地址

http://jmeter.apache.org/download_jmeter.cgi

注意：下载后，解压文件到任意目录，避免在一个有空格的路径安装Jmeter，这将导致远程测试出现问题。

### 启动JMeter的两种方式

进入bin目录

- 双击 ApacheJMeter.jar文件;

- 双击 Jmeter.bat文件;

- 两种打开方式的区别

- 发送桌面快捷方式

### 常用目录文件介绍

#### Bin目录

存放可执行文件和配置文件

- Jmeter.bat：windows系统中JMeter的启动文件
- ApacheJMeter.jar Java环境下的JMeter启动文件
- Jmeter.log：日志文件
- Jmeter.sh：linux系统中JMeter的启动文件
- Jmeter.properties：系统配置文件
- Jmeter-server.bat：windows分布式测试要用到的服务器配置
- Jmeter-serve：linux分布式测试要用到的服务器配置

#### docs目录

docs：是JMeter的java Doc，可打开api\index.html页面来查看;

#### printable_docs目录

printable_docs的usermanual子目录下的内容是JMeter的用户手册文档，其中usermanual下**component_reference.html**是最常用到的核心元件帮助文档。

### 工具功能界面布局

#### 界面布局

JMeter的主界面布局分为标题栏、菜单栏、工具栏、树形标签栏和内容栏

标题栏：主要显示计划信息及JMeter版本。
菜单栏：全部的功能的都包含在菜单栏中。
工具栏：工具栏中的按钮在菜单栏都可以找到，工具栏就相当于菜单栏常用功能的快捷按钮
树形标签栏：树形标签栏通常用来显示测试用例（计划）相关的标签。
内容栏：配合树形标签栏显示，树形标签中点击哪个标签，内容栏中就显示相应的内容和操作。

#### 使用JMeter进行接口测试

##### 遗留的问题：


-  需求对我们学院查询执行100次，如何去做？
-  50个请求同时请求如何操作？  


##### 使用JMeter的解决方案


- 添加【**测试计划**】
- 基于添加的测试计划添加【**线程组**】，循环次数设置为100次
- 在【取样器】中基于线程组添加**HTTP请求**  
- 在【监听器】基于线程组添加【察看结果树】  
- 在监听器基于线程组添加【聚合报告】 

#### Test Plan

##### 作用：


- 本次测试所需要的【组件】都是基于测试计划添加；
-  本次测试所有组件的设置与执行都基于测试计划；

组件：完成指定功能代码段的封装；

#### 选项

- **独立运行每个线程组：**

  
  进程：是每个正在运行的应用程序。
  线程：按照进程的指令去执行指定的代码。
  线程组（多线程）：多个线程的组合。
  线程组（多线程）的执行顺序是并行的。 
  
  勾选：让本次测试计划中所有线程组保持从上到下顺序执行
  
- **Add directory or jar to classpath：**

  ```
  加载第三方jar包；比如：测试数据库时使用，加载数据库驱动jar包。
  ```

#### Threads(User)线程组

##### thread group(线程组)

###### 作用

添加测试中使用的大多数组件

###### 线程属性

- 线程数：虚拟用户数
- Ramp-Up Period(in serconds)：启动虚拟全部用户数所需要的时间
- 循环次数 ：指定次数或勾线永远
- 调度器：勾选后，调度器配置才能使用；

###### 调度器配置

- 持续时间（秒）：设置脚本压测持续时间
- 启动延迟（秒）：启动延迟时间

#### 组件详解

##### HTTP请求

###### 作用


- 模拟前端或第三方软件向服务器发送请求;
- 设置请求时的方法和参数数据;

###### 参数详解


- 名称：本属性用于标识一个取样器，建议使用一个有意义的名称。
- 服务器名称或IP ：HTTP请求发送的目标服务器名称或IP地址。
- 端口号：目标服务器的端口号，默认值为80 。
- 协议：向目标服务器发送HTTP请求时的协议,可以是http或者是https ,默认值为http 。
- 方法：发送HTTP请求的方法，可用方法包括GET、POST、PUT、DELETE。
- Content encoding ：内容的编码方式，默认值为iso8859；一般设置【UTF-8】
- 路径：目标URL路径（不包括服务器地址和端口）
- 同请求一起发送参数:请求时需要传递参数

###### Body Data选项作用：

- 新增或更新时需要传递JSON报文；
  
- 新增和更新时传入报文也需要设置Content-Type:application/json，告诉服务器我传的数据格式为JSON格式；设置地点：配置元件-->HTTP信息头管理器

##### 察看结果树

###### 作用：


- 查看请求服务器时的请求信息;
- 查看服务器响应数据;
- 记录信息到指定文件;

###### 说明：
- 文件名：存放服务器响应后的状态信息； 如：e:\查询所有response.txt
- 取样结果：服务器响应的信息头信息；比如：响应代码，响应数据大小
- 请求：查看向服务器请求时的信息；比如：请求地址、方法、数据等
- 响应数据：查看服务器响应的数据；比如：获取资源时，返回的JSON数据

###### 察看结果树总结：
- 查看请求
- 查看响应
- 存储请求状态信息

## 元件

### 概念
相同类似功能组件的集合称之为元件   
   1. 逻辑控制器  
   2. 配置元件  
   3. 定时器  
   4. 前置处理器  
   5. Sampler  
   6. 后置处理器  
   7. 断言  
   8. 监听器


### 元件结论

只学重要的、常用的

### 各元件中需要掌握元件

#### 配置元件（config Element）


- CSV Data Set Config
- HTTP请求默认值
- HTTP信息头管理器      


#### 前置处理器（Per Processors）
用户参数 

#### 定时器（Timer）
Synchronizing Timer 


#### 取样器（sample）


- HTTP请求
- JDBC Request 
- Debug Sampler


#### 后置处理器（Post Processors）

- 正则表达式提取器 
- XPath Extractor

####断言（Assertions）
响应断言 


#### 监听器（Listener）


- 察看结果树
- 聚合报告 
- 断言结果 


#### 逻辑控制器


- 如果（If）控制器 
- ForEach控制器   
- 循环控制器   
- Include Controller
- 模块控制器


#### 总结：


正常来说，应该开始按照顺序一个组件一个组件的进行讲解。
问题：每个组件都不能独立执行。都需要多个组件进行配合，才能够解决实际问题。
解决方案：按照JMeter主要解决的问题点来讲解组件。
	
