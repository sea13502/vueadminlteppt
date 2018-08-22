title: 基于vue的adminlte脚手架
speaker: 张海
url: https://github.com/ksky521/nodeppt
transition: slide3
files: /js/demo.js,/css/demo.css,/js/zoom.js
theme: moon
usemathjax: yes

[slide]
# 基于vue的adminlte脚手架
## 如何快速开发并提高效率

[slide]
# 为何采用vue
[note]
模块化开发，组件复用，搭积木式开发。
[/note]

[slide]
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

[slide]
## vuecli生成的项目的开发流程
- 开发与生产
[note]
开发与生产的参数配置，比如接口的调用，开发的时候需要调用测试接口，而正式环境需要调用正式接口，这个就需要代码来判断。
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
重点是应用了webpack的一个内置的功能
[/note]