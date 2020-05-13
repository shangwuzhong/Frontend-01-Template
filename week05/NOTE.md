- js Context => Realm
- 宏任务
- 微任务
- 函数调用（Execution Context）
- 语句/声明
- 表达式
- 直接量/变量/this
- execution context
  - code evaluation state
  - Function
  - Script or Module
  - Generator
- ECMAScript Code Execution Context
  - code evolution state
  - Function
  - Script or Module
  - Realm
  - LexicalEnvironment
  - VariableEnvironment
- LexicalEnvironment
  - this
  - new.target
  - super
  - 变量
- VariableEnvironment
  - 主要用作处理var
  - eval
  - with
- Environment Records
  - Declarative Environment Records
    - Function
    - module
  - Global Environment Records
  - Object Environment Records

Function- Glosure

```
var y = 2;
function foo2() {
  console.log(y)
}
export foo2
```

// 箭头函数会在Environment Record 中产生this

Realm 的定义

Before it is evaluated, all ECMAScript code must be associated with a realm. Conceptually, a realm consists of a set of intrinsic objects, an ECMAScript global environment, all of the ECMAScript code that is loaded within the scope of that global environment, and other associated state and resources.

```
Object.getPrototypeOf({}) === Object.prototype
```

函数表达式和对象之间量均会创建对象

使用 . 做隐式转换也会创建对象

这些对象也有原型，如果没有Realm，就不知道他们的原型

```
var iframe = document.createElement("iframe")
document.body.appendChild(iframe)
iframe.contentWindow.eval("this.o ={}")
var o = iframe.contentWindow.o
var b = {}
Object.getPrototypeOf(o) === Object.prototype // false
Object.getPrototypeOf(b) === Object.prototype // true
```

## 浏览器工作原理

### 总结与http协议

- 浏览器

```
  HTTP		parse	csscomputing	   layout				render
url =》HTML   =》 DOM =》 DOM with CSS   =》 DOM with position =》 Bitmap

输入url 敲了回车以后 浏览器首先请求了HTTP 回来了 HTML代码，  然后进行parse(解析) 成 DOM树，然后css规则应用上去(csscomputing) 让DOM树带有CSS，然后排版(layout)，DOM树所有元素确定位置 DOM树就带有了位置，在进行渲染，就可以得到内存中的图片(Bitmap)，然后将图片显示到浏览器上
```

## ISO-OSI七层网络模型

应用 表示 HTTP require('http') 会话

------

传输 ——》 TCP require('net') 网络 ——》 Internet
数据链路 ——》 4G/5G/WIFI
物理层 ——》 4G/5G/WIFI

## TCP与IP的一些基础知识

- 流 - 包
  端口 - IP地址 require('net') - libnet/libpcap

### HTTP

- Request
- Response

TCP 服务端 浏览器端都有权发送信息也有权不回复 HTTP 服务端不能主动发送信息