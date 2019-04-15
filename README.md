# StudentInfo
基于SSM的学生信息管理系统(选课)

**项目简介：**
由SpringMVC+MyBatis为主要框架，mysql8.0配置主从复制实现读写分离，主机丛机分别为腾讯云的服务器，而项目部署在阿里云上。前端主要由bootstrap完成，背景用particles.js插件。数据库交互查询用到pagehelper分页。在添加修改相关功能时通过ajax来验证其主键是否存在可用。代码层次清晰，输入框约束较高，已配置登录拦截。

<!-- more -->
#### 一、应用技术 ####

* 工具：eclipse、navicat
* 环境：JDK1.8、tomcat9.0、mysql8.0
* 前端：JavaScript、jQuery、bootstrap4、particles.js
* 后端：maven、SpringMVC、MyBatis、ajax、mysql读写分离、mybatis分页
#### 二、功能 ####	
这是在上个springmvc选课系统的基础上进行修改完善的，目前功能基本相同，修复诸多bug，上个系统中有详细介绍：[B/S基于springMVC的网上选课系统](https://fuzui.net/2018/12/08/onlineSC-springmvc/)
主要功能模块图：
![](https://fuzui.oss-cn-shenzhen.aliyuncs.com/img/20190414000551.png)

**新增：**
* 增加分页查询
* 输入框约束
	学号、身份证、课程编号、教师编号只能输入数字，并且有最大输入限制，其中学号固定12位，若小于12位将会有提示。姓名只能输入中文。几乎所有输入框不能输入空格等约束
* 下拉框联动
	添加、修改课程采用二级联动，即所属系别——所属专业；
	添加、修改学生采用三级联动，即系别——专业——班级。（三级联动代码有些复杂，因为JavaScript学的不好=-=）。
* ajax+springmvc验证
	用于验证学号、课程编号、教师编号是否存在并给出提示信息等。
	其中课程安排时间地点排重功能正在开发中····
* 登录拦截
	在handler层配置拦截器，对各角色进行登录拦截，即未登录用户不能直接通过相应url访问。
	***更多功能持续更新中······***
	
#### 三、主页面截图 ####	
![](https://fuzui.oss-cn-shenzhen.aliyuncs.com/img/20190415162534.png)
![enter description here](https://fuzui.oss-cn-shenzhen.aliyuncs.com/img/1555316814587.png)
![](https://fuzui.oss-cn-shenzhen.aliyuncs.com/img/20190415162832.png)
更多请查看演示：[studentInfo.fuzui.net](studentInfo.fuzui.net)

#### 四、编写日志 ####	
**第一步计划：**
将原来的springmvc选课系统修改为ssm框架并初步新增功能。
时间：2019.4.6——2019.4.14
>2019年
>>4月6日
>>* 创建maven项目StudentInfo，编写pom.xml，配置好ssm环境；
>>* 创建七大pojo类，编写pojo文档。
>>
>>4月7日
>>* 配置mysql主从，在两台腾讯云服务器上；
>>* 导入原有mysql读写java文件；
>>* 测试成功读写分离。
>>
>>4月8日
>>* 编写学生（Student）相关操作service和mapper层（DAO），并测试成功；
>>
>>4月9日
>>*  编写教师相关（Teacher）相关操作service和mapper层（DAO），并测试成功；
>>* 编写管理员相关（Admin）相关操作service和mapper层（DAO），并测试成功；
>>
>>4月10日
>> * 编写课程类、课程安排类、选课类、退选类、相关操作service和mapper层（DAO），并测试成功；
>> * 编写管理员handler层的登录功能，并调试成功。
>> 
>> 4月11日
>> * 编写学生、教师、课程、课程安排、选课的handler层（原servlet层移植修改）；
>> * 编写前端页面，测试成功（原前端页面移植修改）（该前端页面风格设计最初由一位大佬在原srpingmvc选课系统基础上修改而成）（页面风格几乎完全改变，利用bootstrap、particles.js背景插件）。
>> 
>> 4月12日
>> * 添加登录拦截功能
>> * 为所有查询功能添加分页（mybatis的pagehelper分页），前端利用bootstrap。
>> * 前端分页风格使用bootstrap风格。
>> 
>> 4月13日
>> * **修复**已知bug：{管理员操作查询学生、教师、课程时，进去需点查询全部才能出来（小bug），对学生、课程、教师进行增删改后，需重新点查询才能出来刷新出新的数据！（较严重）。学生：对未安排课程选课时会发生异常，目前只能选已有教师安排的课程（较严重），确认选课时教师简介刷不出来（小bug），退选无法显示刷新（较严重）}
>> * 添加ajax验证（在增加、修改时提示是否可用等）
>> * 为所有输入框添加约束
>> * 在登录页添加轮播图
>> 
>> 4月14日
>> * 完成系统部署、发布。

**第二步计划：**
新增排课查重、选课限制、学分统计、教师系别
时间：2019.4.15——至今


#### 五、更新记录 ####

* 2019.4.14：发布第一个版本





<br><br>
-------------------

<center><font face="华文行楷" size=6 color="blue">
当你的才华还撑不起你的野心的时候，<br>你就应该静下心来学习。
</center>

-----------------------