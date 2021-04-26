## 请简述AJAX都是哪些优点缺点

```js
// 优点 : 
// 1. 提高了性能和速度
// 2. 交互性能好
// 异步调用
// 缺点:
// 1. 增加了设计和开发时间
// 2. 可能会出现网络延迟问题
```

## json字符串与对象相互交换

```js
JS对象转json字符串
JSON.stringify()
JSON字符串转js对象 
JSON.parse()
```

## 请简述GEt和POST两种请求方式的区别

```js
1. get安全性低 post安全性高
2. get请求只能是url编码 post支持多种编码
3. get把参数放到url中 post通过请求体传送
4. get是从服务器上获取数据的 post是向服务器传递数据的
```

## 请简述readyState属性是干嘛的,都有几个状态

```js
//readyState属性用来存放XMLHttpRequest的状态 监听从0-4发生不同变化
//readyState == 0 请求未初始化(此时还未调用open)
//readyState == 1 服务器已建立 已经发送请求开始监听
//readyState == 2 请求已接收, 已经收到服务器返回的内容
//readyState == 3 请求处理中, 解析服务器响应内容
//readyState == 4 请求已完成 且响应就绪
```

## 请简述从输入URL到浏览器显示页面发生了什么?

```js
DNS解析,将域名解析为IP地址
浏览器与服务器建立TCP连接(三次握手)
浏览器向服务器发起HTTP请求
服务器接收并相应,返回回应的HTML文件
浏览器接收从服务器端返回的数据,并进行页面渲染
```

## 请写出jquery中$.ajax中的参数有哪些？分别代表什么意思

```js
type:'请求类型是get还是post',
url:'地址'
data:{属性:属性值} // 需要填写要发送的数据
success:function(res) {} // success里面是一个函数函数的res是接收到的数据
```



## 请简述http常用的状态码有哪些？分别表示什么意思

```js
200(成功) 服务器已经成功处理了请求通常
500(服务器内部错误)服务器遇到错误无法完成请求
501(尚未实施) 服务器不具备完成请求的功能
503(服务器不可用) 服务器目前无法使用 通常这只是暂时状态
```

## 原生js ajax请求有几个步骤？分别是什么

```js
创建XMLHHttpRequest对象
设置请求的类型和请求地址以技术否异步处理
设置发送数据值服务器是的内容编码类型
发送请求
接收服务器响应数据
```

## 请简述XMLHttpRequest对象的常用方法和属性

```js
open方法:设置请求方式和请求地址
send方法:开始发送请求
onload:请求结束时触发该事件
onerror:设置浏览器错误事件
timeout属性:设置请求超时时间
```

## 请简述art-template使用渲染页面的流程?

```js
引入art-template.js文件
设置script标签 type类型为text/html的html模板并且设置id值
template()方法 参数一位上面script标签的id值参数二是需要渲染的数据
设置板块内需要填充的数据
template()返回的值送到页面需要的地方
```

