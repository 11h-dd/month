# Node & Ajax

# Node.js

Node——基于Chrome V8引擎构建的后端



Node支持ECMAScript 和 内置模块



### 交互模式

REPL(Read-Eval -Print-Loop)交互模式

指的是在终端窗口中，执行简单的JavaScript代码

- 在任意终端，直接入 node 命令并回车，即可进入node
- 执行你的JS代码，按回车表示执行
- 按两次“Ctrl+C”退出。



### 模块化概念

```js
把一个一个复杂的系统拆分成多个子系统，各个子系统之间互不影响，各自工作，各个子系统组合而成，形成完整的系统。

NodeJS实现了CommonJS规范
```

```js
1.module.exports = {};  // 对外暴露数据
2.require('文件')  // 注意需要文件的路径
```

test.js文件内容

```js
var a = 10;
var fn = function(cs){
  console.log(cs)
}
// 对外暴露
module.exports = {
  a:a,
  fn:fn
}
```

Hello.js

```js
// 获取模块
var {a,fn} = require('./test.js');

console.log(a) // 打印10
console.log(fn(222)) // 打印222
```



### 内置模块

node自带的模块，可以直接接收使用，详细内容通过官网文档查询使用功能。

通过 **require** 获取模块(js文件)

```js
// require
const path = require('path')

// 获取路径中的文件后缀名
let zui = path.extname('')

```



### 使用http模块搭建服务器

```js
// 加载http模块
const http = require('http')

// 2.使用http模块创建web服务器
let server = http.createServer()

// 3.监听请求request事件
server.on('request',function(req,res){ // req请求信息，res相应信息
  // 设置相应头数据
	res.setHeader('Content-Type','text/pain;charset=utf-8;')
	// 向客户端相应数据
	res.end('传智专修学院欢迎您');
})

// 4. 监听端口号
server.listen(5555,function(){
	console.log('端口5555端口已启动成功')
})

```

简写模式：

```js
// 加载http模块
const http = require('http')

// 使用http模块创建web服务器
let server = http.createServer()
```



### npm模块(第三方模块)

#### 第三方模块

- 第三方模块(其他人、组织、公司开发的模块)
- 并将这些模块发布到npm网站上
- 我们可以按照一些开源协议下载使用这些模块
- 这些模块，不是自己创建的js文件（自定义模块）、不是Node内置模块，所以叫做第三方模块

npm（node）

如何引入第三方包：

```js
// npm 初始化package.json
npm init
// 一般设置一下名字版本说明就好了

// npm 安装第三方包(例：jquery)
npm install jquery
npm i 模块名

// npm 卸载 包
npm uninstall 包名
npm un 模块名
```



### Package.json

```json
{
  "name": "dsad", // 名字
  "version": "1.0.0", // 版本
  "description": "阿巴阿吧", // 描述
  "main": "index.js", // 使用包的js脚本文件
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": { // 依赖项(项目引入的包)
    "jquery": "^3.6.0"
  }
}

```





# Ajax

#### Ajax介绍

- AJAX是 **异步的JavaScript和XML**（Asynchronous JavaScript And XML）。简单点说，*就是使用浏览器内置对象XMLHttpRequest 与服务器通信。*
- **Ajax是一种技术，通过浏览器内置对象和服务器进行数据交互的技术。**
- 它可以使用JSON，XML，HTML 和 text文本等格式发送和接收数据。
- AJAX最吸引人的就是它的“异步”特性，也就是说它可以在不重新刷新页面的情况下与服务器通信，交换数据，或更新页面。
- 你可以使用AJAX最主要的两个特性做下列事：
  - 在不重新加载页面的情况下发送请求给服务器。
  - 接受并使用从服务器发来的数据。



#### Ajax的运行原理

Ajax相当于浏览器发送请求与接收响应的代理人，以现实在不影响用户浏览页面的情况下，局部更新页面数据，从而提高用户体验。

##### 开放人员不可控：

```js
          请求
浏览器端 ————————>  服务器端
        <————————  
           相应
```

##### 开发人员可控：

```js
          创建            请求
浏览器端  ——————>  Ajax  ——————>  服务器端
        <——————        <——————  
          相应            相应
```



#### Ajax发送请求的实现步骤

1. 创建ajax对象

   ```js
   var xhr = new XMLHttpRequest();
   ```

2. 获取服务端给与客户端的相应数据

   onload 为 **XHR2.0方法,代替onreadystatechange事件**

   responseText为XHR接收到的数据

   ```js
   // XHR2.0方法
   xhr.onload = function(){
     console.log(xhr.responseText);
   }
   
   // XHR1.0方法
   xhr.onreadystatechange = function(){
     // 获取请求响应的对象
     console.log(xhr.reponseText)
   }
   ```

3. 告诉Ajax请求地址以及请求方式

   ```js
   xhr.open('get','http://www.example.com');
   ```

4. 发送请求

   ```js
   xhr.send()
   ```

5. 获取服务端给与客户端的相应数据

   onload 为 **XHR2.0方法,代替onreadystatechange事件**

   responseText为XHR接收到的数据

   ```js
   xhr.onload = function(){
     console.log(xhr.responseText);
   }
   ```



### jQuery里的get方法

前置：引入jQ

$.get方法是jQ里封装好的Ajax方法，jQuery中$.get()函数的功能单一，专门用来发起get请求，从而将服务器上的资源请求到客户端来进行使用。

$.get()函数的语法如下：

```js
$.get(url,[data],[success],[datatype])
```

```js
$.get('url地址',function(data){ // data为接收的数据
  console.log(data)
})
```

| 参数     | 是否必填 | 类型     | 含义                                         |
| -------- | -------- | -------- | -------------------------------------------- |
| url      | 是       | string   | 请求的资源的地址，一般由后端同学提供         |
| data     | 否       | 任意     | 请求参数，由后端同学设计                     |
| succes   | 是       | function | 请求成功出发的回调函数，函数的形参为响应结果 |
| dataType | 否       | string   | 预期服务器响应数据的类型，一般不用设置       |





### jQuery中的ajax方法

$.ajax方法是jQ里封装好的Ajax方法，可以使用该方法发送get、post、head、put、delete......请求，和服务器进行数据传输。

用法: (内置只有一个参数(对象Object))

```js
$.ajax({
  type:"post",  //type属性填发送请求类型，不写默认是get
  url:"请求地址", 
  data:{属性:属性值},  // data属性填 要发送的数据
  // success为请求完成时的回调函数，参数res为接收到的数据
  success:function(res){  
    
  },
  // processData属性设置是否将发送的数据序列化(转字符串类型)
  processData: false, 
  // contentType属性设置请求头类型(也可手动设置)
  // true 为 application/x-www-form-urlencoded
  // false为 默认
	contentType: false,
})
```

processData和contentType属性一般在post请求的时候使用。





### Ajax XHR

Ajax xhr对象用于向服务端传送数据

#### XHR 创建对象

创建XMLHttpRequest对象的语法

```js
let xhr = new XMLHttpRequest();
```

#### XHR请求

XMLHttpRequest对象用于和服务器交换数据。

向服务器发送请求：

将使用XMLHttpRequest对象的open()和send()方法：

```js
// 创建XMLHttpRequest对象
let xhr = new XMLHttpRequest()
// 设置请求类型和请求地址(url)和 请求任务 异步还是同步执行
xhr.open('get','http://www.baidu.com',true)
// 设置监听onreadystatechange事件
xhr.onreadystatechange = function(){
  // 打印服务器响应的数据
  console.log(xhr.responsetText)
}
// 将请求发送到服务器
send(string)
```

#### XHR对象的readyState属性

- Ajax从创建xhr对象开始，一直到完全接收服务器返回的结果为止；我们可以把整个请求响应过程划分为5个阶段，并且**可以使用xhr.readyState 属性检测当前请求执行到了哪个阶段了**。
- readyState属性为一个数字，不同的数字表示Ajax的不同状态。
  - （xhr.readyState === 0），初始状态，表示xhr对象一定创建了
  - （xhr.readyState === 1），表示open一定调用了
  - （xhr.readyState === 2），表示send一定调用了，并且已经接收到相应头。
  - （xhr.readyState === 3），表示正在接受服务器返回的数据（可能已经接收完毕，也可能正在接收中，取决于数据量的大小）
  - 如果（xhr.readyState === 4），表示Ajax请求～相应过程完成

#### XHR对象的statue属性

status属性表示http状态码，是一个数字，代码指示特定HTTP请求是否已成功完成。

响应分为五类：

- 信息响应(100-199)
- 成功响应(200-299)
- 重定向(300-399)
- 客户端错误(400-499)
- 服务器错误(500-599)

常用状态码

- 200  OK  -  请求成功
- 400 Bad Request  -  语义有误，当前请求无法被服务器理解，或参数有误。
- 401 Unauthorized  -  当前请求需要用户验证。
- 404 Not Found  -  请求失败，请求所希望的到的资源未被在服务器上发现。
- 500 Internal Server Error  - 服务器遇到了不知道如何处理的情况。

使用status状态码，判断在请求发送中是否完成的状态，在将数据使用

```js
// 2.注册 xhr.onreadystatechange 事件，当Ajax请求完成后，会触发该事件。在该函数中，接收响应结果。
xhr.onreadystatechange = function(){
  // 当 xhr.readyState 变化到 4 的时候 （请求响应过程结束了）
  // 当 xhr.status === 200 的时候 （请求是成功的）
  if(xhr.readyState === 4 && xhr.status === 200){
    // 使用 xhr.responseText 接收响应结果
    var res = xhr.responseText;
  }
}
```



### Ajax中post和get请求的区别

- post请求数据传输通过send方法传输，类型是字符串，属性值形式：'name=张三'
- post请求一般用于发送数据
- post请求需要设置请求头setHeader('Content-Type','text/pain;charset=utf-8;')
- get请求数据传输是将数据写在url地址后,以"?"后接"属性=属性值"并用"&"拼接的形式传送
- get请求一般用于数据获取

post请求方式：

```js
xhr.open('POST',url地址)
xhr.send(传送的数据[string])
```

get请求方式：

```js
xhr.open('GET',`url地址?属性=属性值&属性=属性值&属性=属性值......`)
```



#### XHR2新增事件和方法

##### timeout属性 和 ontimeout事件

timeout属性可以设置xhr对象请求超时为多少（单位：毫秒）

配合ontimeout事件可以设置请求超时时运行的代码。

```js
// 设置XHR对象请求时常为300毫秒是超时
xhr.timeout = 300
// 设置XHR对象请求超时的时候触发的事件
xhr.ontimeout = function(){
  console.log('请求超时')
}
```

##### onload事件

onload事件，在请求成功完成时触发（即readyState为4时触发）

可以用onload事件，代替之前的onreadystatechange事件。

```js
xhr.onload = function(){
  // 成功响应后，获取相应结果。
  console.log(JSON.parse(this.responseText))
}
```

##### onerror事件

请求失败时触发的事件

```js
xhr.onerror = function(){
  // 请求失败后触发
  console.log('请求失败了')
}
xhr.open('GET','http://xxxxxxxxxx.com') // 不存在的地址
```

##### onprogress事件

onprogress事件，在请求完成之前周期性调用的函数。redyState为3时触发

```js
xhr.onprogress = function(event){
  console.log(event.loaded) // 已传输的数据量
  console.log(event.total) // 总共的数据量
}
```

##### event的两个属性

event.loaded属性为已传输的数据量

event.total属性为总共传输的数据量

##### onloadstart事件

开始传送数据时被调用

```js
xhr.onloadstart = function(){
  console.log('即将开始下载数据')
}
```

##### onloadend事件

请求结束时被调用

```js
xhr.onloadend = function(){
  console.log('请求已经结束')
}
```







### FormData表单数据对象

FormData()是一个构造函数，也是个对象，用于收集form表单的数据，配合ajax使用，向服务器提交数据。使用时，**只能使用post请求**，且使用formdata传数据不用设置请求头。

```html
<form id="">
  <-->账户名和密码</-->
  <input type="text" name="uname" value="小明">
  <input type="text" name="upwd" value="xiaoming">
</form>

<script>
// 先创建一个XML对象
let xhr = new XMLHttpRequest()
  
let formdata = new FormData(form表单DOM对象)

xhr.open('post','url地址')
// 使用formdata传数据不用设置请求头
// 调用send方法时将formdata数据传入
xhr.sned(formdata)

</script>
```

##### FormData实例对象的API方法：

| 方法                  | 用途                  |
| --------------------- | --------------------- |
| append('key','value') | 向对象中追加数据      |
| set('key',value')     | 修改对象中的数据      |
| delete('key')         | 从对象中删除数据      |
| get('key')            | 获取指定key的一项数据 |
| getAll('key')         | 获取指定key的全部数据 |
| forEach()             | 遍历对象中的数据      |

示例：

```js
let formdata = new FormData(form)
formdata.append('sex','男')
```



#### fetch的使用





#### Axios.js

Axios是一个机遇promise的HTTP库，可以用在浏览器和node.js中

使用axios的前置: (引入axios.js文件)

`<script src="https://unpkg.com/axios/dist/axios.min.js"></script>`

##### 通过axios发送ajax请求

1.get请求

```js
// 参数1为url地址,可直接在后面跟传送的数据,以?号开头&拼接
axios.get('http://www.baidu.com?q=CDN')
// .then方法将在请求结束后执行，函数里边的参数为接收到的数据
  .then(function (response) {
    console.log(response);
  })
// .catch方法会在请求错误时执行,函数里边的参数为错误信息
  .catch(function (error) {
    console.log(error);
  });

// 另一种方式

// 参数1为url地址,参数2为传送的数据
axios.get('http://www.baidu.com',
          {q:"CDN"})
// .then方法将在请求结束后执行，里边的response参数为接收到的数据
  .then(function (response) {
    console.log(response);
  })
// .catch方法会在请求错误时执行,里边的error参数为错误信息
  .catch(function (error) {
    console.log(error);
  });

```

2.post请求

同上(.get换成.post即可)

3.综合写法

```js
axios({
  method:'post', //method为发送请求的方式
  url:'http://www.baidu.com',
  data:{   // data为要传输的数据
  q:'英雄联盟'
}
}).then(function(res){ 
  console.log(res)
})
// .then方法将在请求结束后执行，里边的参数为接收到的数据
```



### Art-template高性能JavaScript模版引擎

#### art-template介绍

art-template 是一个简约、超快的模板引擎。

它采用作用域预声明的技术来优化模板渲染速度，从而获得接近 JavaScript 极限的运行性能，并且同时支持 NodeJS 和浏览器。

#### 模版语法

art-template 同时支持两种模板语法。标准语法可以让模板更容易读写；原始语法具有强大的逻辑处理能力。

##### 标准语法

```js
{{if user}}
  <h2>{{user.name}}</h2>
{{/if}}
```

##### 原始语法

```js
<% if (user) { %>
  <h2><%= user.name %></h2>
<% } %>
```

##### 模版语法

html模版写在script标签里，type类型要设置成"text/html"

模版里的"each"是循环遍历(要使用双大括号括起来)

模版里的"$value"是遍历数组里的每一项

模版里的"$index"是数组每一项对应的下标

*相当于forEach*

```html
<script type="text/html" id='tpl'>
			{{each list}}
			<h1>{{$value}} {{$index}}</h1>
			{{/each}}
</script>
```

##### template()传入的第二个参数类型:

1. 如果传入数据是数组，each后不写东西，直接可以遍历数组。

2. 如果传入的是对象，each后不写东西，$value为对象里所有属性值，$index为对象里所有的属性名，属性和属性名一一对应。

3. 如果传入的是"字符串"，那就厉害了，each后不写东西，$value是字符串每一个字符，$index是字符串每个字符的下标。

##### 核心方法

```js
// 基于模版名渲染模版
template('script模版id',data)
// template()

```

例：

```html
<!-- 效果 -->
<div>
  <ol>
    <li>0 - 小明</li>
    <li>1 - 小红</li>
    <li>2 - 小蓝</li>
    <li>3 - 小绿</li>
  </ol>
<div>

<!-- 模版 -->
<script type="text/html" id="con">
  <ol>
  {{each}}
   <li>{{$index}} -- {{$value}}</li>
  {{/each}}
  </ol>
</script>
<!-- 代码 -->
<script>
// 数据
let arr = ['小明','小红','小蓝','小绿']
// 存储art-template渲染的字符串
let html = template('con',arr) // 参数1为模版id,参数2为传入的数据
// 将art-template渲染的字符串放到要放的DOM元素里
document.querySelector('div').innerHTML = html
</script>

```











---

## JSON



### JSON的相关内容



#### JSON的介绍

JSON的本质是字符串，作为一种通用的格式，在传输数据时，当做数据的载体。

JSON字符串中，允许出现的类型有：null，number，string，boolean，array，object。

**注释、函数、undefined等其他所有类型都不能出现在JSON字符串中**

所有字符串必须使用  **"双引号"**  括起来



#### JSON字符串和JS数据转换

- JS  ---->  JSON  (序列化)

  ```js
  let jsonStr = JSON.stringify(JS数据)
  // JS数据一般为对象(Object)
  ```

  这个过程称之为JS对象序列化

- JSON  ---->  JS对象  (反序列化)

  ```js
  let json = "{"uname":"小明","age":"21"}"
  console.log(JSON.pares(json))
  // 控制台打印 {uname:'小明',age:21}
  ```

  这个过程称之为  反序列化





## Git

Git——分布式版本控制系统

git是一个开源的分布式版本控制系统，可以有效、高速地处理很小到非常大的项目版本管理

**有三个区域：1.工作区，2.暂存区，3.仓库。**

### Git的安装配置

使用git必要的操作

1. 从网上下载安装git

2. 打开终端，在终端中输入 ` git config --global user.name "用户名" ` 回车执行，用户名需要在github或gitee等版本分布系统网站注册获得。
3. 完成第二步，接着在终端输入 ` git config --global user.email "邮箱" ` 回车执行。

完成这三步就基本配置好了git

### 版本管理系统

大白话：可以管理项目版本的一个系统，可以给项目每个版本阶段存档

#### 集中式版本管理

集中式版本管理软件的特点是，代码的版本集中到一个服务器上。问题是，如果没有网络或者服务器崩溃，将无法进行版本管理。

#### 分布式版本管理

本地计算机可以当项目版本库用

分布式版本管理软件的特点是，代码的版本分布到每个计算机上。99%的操作都是在自己的计算机上完成。

#### git的使用

##### 首先需要初始化一个本地仓库

1. 打开终端，利用cd命令进入到项目文件夹。

   ```cmd
   cd (项目所在目录)  // Enter(回车)
   ```

2. 输入命令 `git init` 执行，完成仓库的初始化。

##### GIt终端命令表

| 命令                               | 作用                               |
| ---------------------------------- | ---------------------------------- |
| git init                           | git仓库初始化                      |
| git add ./                         | 提交本次项目至暂存区               |
| git commit -m "本次版本更新的说明" | 将暂存区添加的项目提交至仓库       |
| git commit <file> -m "提交日志"    | 提交指定文件到仓库，形成一个新版本 |
| git log                            | 查看git记录了几次                  |
| git reset --hard 版本号            | 回滚/更新至对应版本号的项目        |
| git log --oneline                  | 单行查看简略版日志                 |
| git log -n                         | 查看最近n次提交                    |
| git log --reflog                   | 查看所有版本的日志                 |
| git log --reflog --oneline         | 配合使用                           |
| git status                         | 查看工作区文件更改                 |
| git checkout <file>                | 撤销指定的文件修改(工作区内)       |
| git checkout ./                    | 撤销所有文件的修改(工作区内)       |
| git reset <flie>                   | 撤销指定的文件                     |
| git reset ./                       | 撤销全部文件                       |
| git commit -a -m "提交日志"        | 直接将工作区改动提交至仓库         |
| git reflog                         | 查看所有提交/回滚日志及版本        |

git提交本地项目版本至远程仓库命令

| 命令                                    | 用途                                              |
| --------------------------------------- | ------------------------------------------------- |
| git remote -v                           | 查看推送地址别名                                  |
| git remote add 地址别名 http/ssh地址    | 添加提交地址，及地址别名                          |
| git remote remove 地址别名 http/shh地址 | 删除提交地址，及地址别名                          |
| git push -u 地址别名                    | 提交最新版本代码至远程仓库(第一次需要-u 地址别名) |
| git push 地址别名(选填,一般不填)        | 提交最新版本代码至远程仓库                        |
| git pull 地址别名(选填,一般不填)        | 从远程服务器拉取代码                              |

#### git项目分支

git项目分支可以将项目代码克隆一份出来进行开发，主支路和分路互不影响，可同时开发，主分支一般用于稳定版本的发布和推送，分支版本一般用于开发新功能和测试使用，分支项目测试完成，确定没有问题的时候才会合并起来到主分支，分支项目可以进行删除修改合并，主分支不可删除。

git本地分支管理命令

| 命令                  | 用途                 |
| --------------------- | -------------------- |
| git checkout 分支名称 | 进入分支             |
| git branch            | 查看本地项目分支     |
| git branch 分支名称   | 创建分支             |
| git merge 分支名称    | 合并分支到master分支 |
|                       |                      |





