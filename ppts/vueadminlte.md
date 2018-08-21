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
模块化开发，组件复用
[/note]

[slide]
## 常用工具的使用
- bootstrap布局工具的使用。
- 字体工具
- 通过cli添加组件，不用的组件不添加，省空间，还可以在cli中添加例子
- 严格按照宫格的方式，搭积木的方式设计，搭积木的方式开发。
- 一些测试的问题
- vue——webpack项目的深入讲解
- express起的server还起到了hot reload的功能了
- mock-server

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
  var data = { products111: [{ "id": 1, "name": "Awesome Concrete Mouse", "color": "maroon", "department": "Health", "price": "265.00", "adjective": "Handmade", "material": "Steel", "product": "Chips" }] }
  return data
}
```
### 浏览器或者ajax请求即可访问这个模拟接口<br>``http://localhost:3000/products111``