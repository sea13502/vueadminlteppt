title: 基于vue的adminlte脚手架
speaker: 张海
url: https://github.com/ksky521/nodeppt
transition: slide3
files: /js/demo.js,/css/demo.css,/js/zoom.js
theme: moon
usemathjax: yes

[slide]

# adminlte
## 一套丰富的后台ui及交互的组件基于jquery和bootstrap的

[slide]

# 使用vue
## 模块化开发，丰富的生态，社区强大。

[slide]

# vue与adminlte结合
# 基于adminlte基础的样式和交互，打造属于我们自己的组件库。

[slide]

# 如何让大家喜欢去用乐意用。这里我们回到vue，vue强大的地方就在于文档和vue-cli这个脚手架。有疑问或者忘记一些用法，文档很容易就能查到。生成项目用cli工具也相当方便。借鉴vue我们也建立了我们的文档网站和cli工具。初期可能功能比较单一，满足的需求不太大，希望大家加入进来。丰富完善他，离合公司所有前端的技术，把这个项目做好，为更多的项目服务。

[slide]
# 基于vue的adminlte脚手架
## 如何快速开发并提高效率

[slide]
* 为何采用vue
{:&.rollIn}
* 积木式开发
[note]
模块化开发，组件复用，搭积木式开发。

## 常用工具的使用
- bootstrap布局工具的使用，布局规范按照bootstrap走。
- 字体工具
- 通过cli添加组件，不用的组件不添加，省空间，还可以在cli中添加例子
- 严格按照宫格的方式，搭积木的方式设计，搭积木的方式开发。
- 一些测试的问题
- vue——webpack项目的深入讲解
- express起的server还起到了hot reload的功能了
- mock-server
- eslint的一些规则，一个介绍性的网站gitbook或者使用vuepress，还有脚手架工具的开发，yo看看
- 一些组件 VASmallBox.vue 
[/note]

[slide]
## 概要
- 开发环境的启动和构建生产环境
{:&.rollIn}
- mock-server的配置
- 前端的自动化测试
- 代码规范
- 搭积木
 - 栅格布局
 - 常用组件
 - ajax请求组件。
 - vuex的使用。
[note]
开发环境的启动和构建生产环境  端口配置的一些问题
ajax请求的固定模式
何时用vuex呢
[/note]

[slide]
## 从package.json里面命令开始
```javascript
"scripts": {
    "mock": "./node_modules/.bin/json-server ./mock-server/index.js",
    "dev-server": "node build/dev-server.js",
    "dev": "npm-run-all --parallel mock dev-server",
    "build": "node build/build.js",
    "unit": "cross-env BABEL_ENV=test karma start test/unit/karma.conf.js --single-run",
    "e2e": "node test/e2e/runner.js",
    "test": "npm run unit && npm run e2e",
    "lint": "eslint --ext .js,.vue src test/unit/specs test/e2e/specs"
  },
```
[slide]
## 命令
### 启动开发环境和构建生产环境的命令
```
"dev-server": "node build/dev-server.js",
"dev": "npm-run-all --parallel mock dev-server",
"build": "node build/build.js"
```
### 原理与重点
- 区分生产与开发环境的方式
<div class="columns-2">
    <pre><code class="javascript">
//如何使用 比如在vue
//项目的src\main.js文件中
console.log(process.env);
// 然后会输出 
//{NODE_ENV:"development"}
    </code></pre>
    <pre><code class="javascript">
//我只截取webpack配置的一个片段，
//来说下原理
plugins: [
    new webpack.DefinePlugin({
      'process.env': config.dev.env
    }),
]
    </code></pre>
</div>
[note]
为何要区分生产与开发环境呢，为了简化发布流程。
重点是应用了webpack的一个内置的功能。
主要应用场景是在开发环境和正式环境是调用不同的接口的。
[/note]

[slide]
## mock 
mock 数据模拟服务，在不依赖后台接口的时候模拟数据进行开发<br>
```
"./node_modules/.bin/json-server ./mock-server/index.js"
```
{:&.rollIn}
### mock数据的配置文件
```javascript
module.exports = function () {
  var data = { products111: [{ "id": 1, 
  "name": "Awesome Concrete Mouse", "color": "maroon", "department": "Health", "price": "265.00", 
  "adjective": "Handmade", "material": "Steel", "product": "Chips" }] }
  return data
}
```
### 浏览器或者ajax请求即可访问这个模拟接口<br>``http://localhost:3000/products111``
- 接口可以在data数据中配置，详情请查看json-server的文档
