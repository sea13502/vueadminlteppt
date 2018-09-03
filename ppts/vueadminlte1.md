title: 基于vue的后台前端框架规范adminlte的技术分享
speaker: 张海
url: https://github.com/ksky521/nodeppt
transition: slide3
files: /js/demo.js,/css/demo.css,/js/zoom.js
theme: moon
usemathjax: yes

[slide]

# 基于vue的后台前端框架规范adminlte的技术分享

[slide]

## AdminLTE <a href="http://adminlte.la998.com/" target="_blank">传送门</a>
- 基于jquery和bootstrap的一套丰富的后台ui及交互的组件
{:&.rollIn}
- 优秀的后台交互方式

[slide]

## VUE
- 使用VUE
{:&.rollIn}
- 文档友好  <a href="https://cn.vuejs.org/v2/guide/" target="_blank">传送门</a>
- 模块化开发
- vue丰富的生态
[note]
vue-cli和丰富的组件，及实践。遇到问题能很快的找到解决方案。
[/note]

[slide]

## vue与adminlte结合
- adminlte基础的样式交互和基础组件
{:&.rollIn}
- 我们的业务特点
- ![我们的业务](/img/spcialselect.png "我们的业务")
[note]
筛选组件
[/note]
- 用vue打造属于我们自己的组件库

[slide]
## tcsl-cli
- 像vue-cli一样的快速生成项目
{:&.rollIn}
- 致力于提高程序员的开发体验，愉悦编码
- 通过命令增加功能和组件
[note]
这也是我们这套存在意义之一，同时提高开发速度和体验。
比如增加按需加载，增加路由，增加vuex，增加ajax组件
增加一些如何使用的实例文件，当然这些文件都加入到了gitignore中，不会影响提交
一些文档可以放到node的包里面，直接给出绝对路径到浏览器打开看
[/note]
- 通过命令增加实例程序

[slide]

## 前端项目

- 我们熟悉的vue-cli的项目
{:&.rollIn}
- 只不过他的样式是来自adminlte的

[slide]

## 项目功能

- mock数据及配置
{:&.rollIn}
- 集成bootstrap栅格布局
- 集成一些基础的字体图标
- 常用ajax组件及实例，比如跨域的配置
- 前端的自动化测试
- 代码规范eslint
- 代码开发和发布生产的配置
- 常用的adminlte的bootstrap组件，比如modal，button
- vuex的配置，及实例

[slide]

## 开源项目，集合大家的智慧 

[slide]

## 像vue文档一样友好的文档
- 项目地址 <a href="https://git.wuuxiang.com/zhanghai/tcslclidoc" target="_blank">传送门</a>
{:&.rollIn}
- 临时文档地址，未来可以放在我们自己的服务器 <a href="https://sea13502.github.io/tcslcli" target="_blank">传送门</a>
- 协作完成文档，及组件的开发
- 年底根据贡献，积分
- 将需求维护上去，需求认领

[note]
bootstrap栅格布局，可以实现响应式布局，格局浏览器的宽度实现不同的展示。
今天我们不主要讲代码，只讲这套系统，能给我们什么，能给我们的开发提供什么便利。
上面这些主要是我在开发中遇到的，我也希望大家把在开发中遇到的一些问题或者经验提出来，丰富我们这套系统。
参与进来参与开发，一个人的力量有限。
[/note]