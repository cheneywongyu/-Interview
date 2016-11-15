# -Interview
# 面试提纲

Javascript作用链域?
全局函数无法查看局部函数的内部细节，但局部函数可以查看其上层的函数细节，直至全局细节。
当需要从局部函数查找某一属性或方法时，如果当前作用域没有找到，就会上溯到上层作用域查找，
直至全局函数，这种组织形式就是作用域链。

Ajax是什么? 如何创建一个Ajax？
ajax的全称：AsynchronousJavascript And XML。
异步传输+js+xml。
所谓异步，在这里简单地解释就是：向服务器发送请求的时候，我们不必等待结果，而是可以同时做其他的事情，等到有了结果它自己会根据设定进行后续操作，与此同时，页面是不会发生整页刷新的，提高了用户体验。
 
(1)创建XMLHttpRequest对象,也就是创建一个异步调用对象
(2)创建一个新的HTTP请求,并指定该HTTP请求的方法、URL及验证信息
(3)设置响应HTTP请求状态变化的函数
(4)发送HTTP请求
(5)获取异步调用返回的数据
(6)使用JavaScript和DOM实现局部刷新

DOM操作——怎样添加、移除、移动、复制、创建和查找节点?
 
（1）创建新节点
  createDocumentFragment()    //创建一个DOM片段
  createElement()   //创建一个具体的元素
  createTextNode()   //创建一个文本节点
（2）添加、移除、替换、插入
  appendChild()
  removeChild()
  replaceChild()
  insertBefore() //在已有的子节点前插入一个新的子节点
（3）查找
  getElementsByTagName()    //通过标签名称
  getElementsByName()    //通过元素的Name属性的值(IE容错能力较强，会得到一个数组，其中包括id等于name值的)
  getElementById()    //通过元素Id，唯一性

谈谈this对象的理解。
红宝书 ：

this 引用的是函数据以执行的环境对象， this 对象是在运行时基于函数执行环境绑定的，在全局中， this 等于 window ，当函数被作为木个对象的方法调用时， this 等于那个对象，不过，由于匿名函数的执行环境具有全局性，因此， this 对象通常指向 window ，还有就是每个函数在调用的时候都会自动获取两个特殊变量： this 和 arguments ，放在活动对象中，内部在要使用这两个变量时，只是会在本函数的活动对象中搜索，永远不会沿着作用域链访问外面的活动对象。

犀牛书 ：

this 对象没有作用域的限制，嵌套的函数不会从调用它的函数中继承 this ，如果嵌套函数作为方法调用，其 this 值指向调用它的对象，如果嵌套函数作为函数调用，其 this 值不是全局对象（非严格模式）就是 undefined （严格模式）；很多人误以为调用嵌套函数时 this 会指向调用外层函数的上下文。

eval是做什么的？
这个函数可以把一个字符串当作一个JavaScript表达式一样去执行它。

什么是window对象? 什么是document对象?
简单来说，document是window的一个对象属性。
Window 对象表示浏览器中打开的窗口。
如果文档包含框架（frame 或 iframe 标签），浏览器会为 HTML 文档创建一个 window 对象，并为每个框架创建一个额外的 window 对象。
所有的全局函数和对象都属于Window 对象的属性和方法。
document   对 Document 对象的只读引用。

null，undefined的区别？
undefined表示变量声明但未初始化时的值，
null表示准备用来保存对象，还没有真正保存对象的值。从逻辑角度看，null值表示一个空对象指针。

[“1”, “2”, “3”].map(parseInt) 答案是多少？
1,NaN,NaN
map 方法
对数组的每个元素调用定义的回调函数并返回包含结果的数组。
parseInt('1', 0);
parseInt('2', 1);
parseInt('3', 2);
因为 parseInt 需要两个参数(val,radix)，其中 radix 表示解析时用的基数。
map 传了3个(element,index,array)，对应的 radix 不合法导致解析失败。

关于事件，IE与火狐的事件机制有什么区别？ 如何阻止冒泡？
1. 我们在网页中的某个操作（有的操作对应多个事件）。例如：当我们点击一个按钮就会产生一个事件。是可以被 JavaScript 侦测到的行为
2. 事件处理机制：IE是事件冒泡、firefox同时支持两种事件模型，也就是：捕获型事件和冒泡型事件
3. ev.stopPropagation();

什么是闭包（closure），为什么要用它？
闭包就是能够读取其他函数内部变量的函数。
在理解闭包之前, 首先要清楚JS中的作用域只有2种: 全局作用域和方法作用域
闭包是可以包含自由（未绑定到特定对象）变量的代码块；这些变量不是在这个代码块内或者任何全局上下文中定义的，而是在定义代码块的环境中定义（局部变量）。“闭包” 一词来源于以下两者的结合：要执行的代码块（由于自由变量被包含在代码块中，这些自由变量以及它们引用的对象没有被释放）和为自由变量提供绑定的计算环境（作用域）
闭包是指有权访问另一个函数作用域中变量的函数，创建闭包的最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量，利用闭包可以突破作用链域，将函数内部的变量和方法传递到外部。
//
闭包特性：
(1)函数内再嵌套函数
(2)内部函数可以引用外层的参数和变量
(3)参数和变量不会被垃圾回收机制回收

javascript 代码中的"use strict”;是什么意思 ? 使用它区别是什么？
1.概述

除了正常运行模式，ECMAscript 5添加了第二种运行模式："严格模式"（strict mode）。顾名思义，这种模式使得Javascript在更严格的条件下运行。

2.为什么用严格模式

- 消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为;

- 消除代码运行的一些不安全之处，保证代码运行的安全；

- 提高编译器效率，增加运行速度；

- 为未来新版本的Javascript做好铺垫。

"严格模式"体现了Javascript更合理、更安全、更严谨的发展方向，包括IE 10在内的主流浏览器，都已经支持它，许多大项目已经开始全面拥抱它。

另一方面，同样的代码，在"严格模式"中，可能会有不一样的运行结果；一些在"正常模式"下可以运行的语句，在"严格模式"下将不能运行。掌握这些内容，有助于更细致深入地理解Javascript，让你变成一个更好的程序员。

如何判断一个对象是否属于某个类？
result = object instanceof class

new操作符具体干了什么呢?
(1)创建一个空对象，并且 this 变量引用该对象，同时还继承了该函数的原型。
(2)属性和方法被加入到 this 引用的对象中。
(3)新创建的对象由 this 所引用，并且最后隐式的返回 this 。
//
var obj = {};
obj.__proto__ = Base.prototype;
Base.call(obj);

JavaScript 中，有一个函数，执行对象查找时，永远不会去查找原型，这个函数是哪个？
hasOwnProperty
//
JavaScript 中 hasOwnProperty 函数方法是返回一个布尔值，指出一个对象是否具有指定名称的属性。此方法无法检查该对象的原型链中是否具有该属性；该属性必须是对象本身的一个成员。

对JSON的了解？
JSON(JavaScript Object Notation)是一种轻量级的数据交换格式。
它是基于JavaScript的一个子集。数据格式简单，易于读写，占用带宽小。
如：
{"age":"12", "name":"back"}

[].forEach.call($$("*"),function(a){ <br />a.style.outline="1px solid #"+(~~(Math.random()*(1<<24))).toString(16) <br />})
这段代码只是首先获取了所有的页面元素，然后使用一个不同的颜色为它们添加了一个1ps的边框

js延迟加载的方式有哪些？
defer和async、动态创建DOM方式（用得最多）、按需异步载入js

如何解决跨域问题？
jsonp、iframe、window.name、window.postMessage、服务器上设置代理页面

ECMAScript 6 是JavaScript语言的下一代标准，已经在2015年6月正式发布了。它的目标，是使得JavaScript语言可以用来编写复杂的大型应用程序，成为企业级开发语言。
标准的制定者有计划，以后每年发布一次标准，使用年份作为标准的版本。因为当前版本的ES6是在2015年发布的，所以又称ECMAScript 2015。也就是说，ES6就是ES2015

异步加载 JS 的方式有哪些？
(1)defer，只支持 IE
(2)async:
(3)创建 script，插入到 DOM 中，加载完毕后 callBack

document.write 和 innerHTML 有何区别？
document.write 只能重绘整个页面
innerHTML 可以重绘页面的一部分

哪些操作会造成内存泄漏？
内存泄漏是指任何对象在您不再拥有或需要它之后任然存在。
垃圾回收器定期扫描对象，并计算引用了每个对象的其他对象的数量，如果一个对象的引用数量为0（没有其他对象引用过该对象），或对该对象的惟一引用是循环的，那么该对象的内存即可回收。
//
setTimeout 的第一个参数使用字符串而非函数的话，会引发内存泄漏。
闭包、控制台日志、循环（在两个对象彼此引用且彼此保留时，就会产生一个循环）

jQuery 中如何将数组转化为 json 字符串，然后再转化回来？
jQuery 中没有提供这个功能，所以需要先编写两个 jQuery 的扩展：
$.fn.stringifyArray = function(array) {
  return JSON.stringify(array)
}
$.fn.parseArray = function(array) {
  return JSON.parse(array)
}
//
然后调用:
$("").stringifyArray(array)

是否了解针对 jQuery 性能的优化方法？
基于Class的选择性的性能相对于Id选择器开销很大，因为需遍历所有DOM元素。
//
频繁操作的DOM，先缓存起来再操作。用Jquery的链式调用更好。
比如：var str=$("a").attr("href");
//
for (var i = size; i < arr.length; i++) {}
for 循环每一次循环都查找了数组 (arr) 的.length 属性，在开始循环的时候设置一个变量来存储这个数字，可以让循环跑得更快：
for (var i = size, length = arr.length; i < length; i++) {}

如何判断当前脚本运行在浏览器还是 node 环境中？（阿里）
通过判断 Global 对象是否为 window ，如果不为 window ，当前脚本没有运行在浏览器中

检测浏览器版本有哪些方式？
navigator.userAgent

谈谈你对 JavaScript 中的模块规范 CommonJS、AMD、CMD 的了解？
|   CommonJS   |   AMD   |   CMD   |
|--------------|---------|---------|
|    Node.js   |RequireJS|  SeaJS  |

MVC
模型（Model）：数据保存
视图（View）：用户界面
控制器（Controller）：业务逻辑
(1)View 传送指令到 Controller
(2)Controller 完成业务逻辑后，要求 Model 改变状态
(3)Model 将新的数据发送到 View ，用户得到反馈
所有通信都是单向的。

页面编码和被请求的资源编码如果不一致如何处理？
charset="utf-8"

模块化开发怎么做？
理解模块化开发模式：浏览器端requirejs，seajs；服务器端nodejs；ES6模块化；fis、webpack等前端整体模块化解决方案；grunt、gulp等前端工作流的使用


50、列举常用的js框架以及分别适用的领域
jquery：简化了js的一些操作，并且提供了一些非常好用的API
jquery ui、jquery-easyui：在jqeury的基础上提供了一些常用的组件 日期，下拉框，表格这些组件
require.js、sea.js（阿里的玉帛）+》模块化开发使用的
jquery mobile：是jquery自己出的支持移动端网页开发，不过非常笨重，但是功能非常强大
zepto：精简版的jquery，常用于手机web前端开发 提供了一些手机页面实用功能,touch
 
ext.js：跟jquery差不多，但是不开源，也没有jquery轻量
angular、knockoutjs、avalon(去哪儿前端总监，作者：司徒正美)：MV*框架，适合用于单页应用开发(SPA)

59、程序中捕获异常的方法？
window.error=function(){};   try{}catch(){}finally{}

70、AMD（Modules/Asynchronous-Definition）、CMD（Common Module Definition）规范区别？
理解这两种规范的差异，主要通过requirejs与seajs的对比，理解模块的定义与引用方式
的差异以及这两种规范的设计原则
 
1、对于依赖的模块，AMD 是提前执行，CMD 是延迟执行。不过 RequireJS 从 2.0 开始，也改成可以延迟执行（根据写法不同，处理方式不同）。CMD 推崇 as lazy as possible.
2、CMD 推崇依赖就近，AMD 推崇依赖前置。
3. AMD 的 API 默认是一个当多个用，CMD 的 API 严格区分，推崇职责单一。比如 AMD 里，require 分全局 require 和局部 require，都叫 require。CMD 里，没有全局 require，而是根据模块系统的完备性，提供 seajs.use 来实现模块系统的加载启动。CMD 里，每个 API 都简单纯粹。

71、requireJS的核心原理是什么？（如何动态加载的？如何避免多次加载的？如何 缓存的？）
核心是js的加载模块，通过正则匹配模块以及模块的依赖关系，保证文件加载的先后顺序，根据文件的路径对加载过的文件做了缓存

76、简述一下你对web性能优化的方案？
1、尽量减少 HTTP 请求
2、使用浏览器缓存
3、使用压缩组件
4、图片、JS的预载入
5、将脚本放在底部
6、将样式文件放在页面顶部
7、使用外部的JS和CSS
8、精简代码

IE下,可以使用获取常规属性的方法来获取自定义属性,
   也可以使用getAttribute()获取自定义属性;
   Firefox下,只能使用getAttribute()获取自定义属性。
   解决方法:统一通过getAttribute()获取自定义属性。

*  IE下,even对象有x,y属性,但是没有pageX,pageY属性;
   Firefox下,event对象有pageX,pageY属性,但是没有x,y属性。

*  解决方法：（条件注释）缺点是在IE浏览器下可能会增加额外的HTTP请求数。

*  Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示,
   可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决。

介绍js有哪些内置对象？
Object 是 JavaScript 中所有对象的父对象

数据封装类对象：Object、Array、Boolean、Number 和 String
其他对象：Function、Arguments、Math、Date、RegExp、Error

谈谈This对象的理解。
this总是指向函数的直接调用者（而非间接调用者）；
如果有new关键字，this指向new出来的那个对象；
在事件中，this指向触发这个事件的对象，特殊的是，IE中的attachEvent中的this总是指向全局对象Window；

模块化开发怎么做？
立即执行函数,不暴露私有成员

ECMAScript6 怎么写class，为什么会出现class这种东西?
class Point {
 constructor(x, y) {
   this.x = x;
   this.y = y;
  }
var point = new Point(2, 3);
Class不存在变量提升
面向对象,模块化,语言发展

.call() 和 .apply() 的作用和区别？
1、call，apply都属于Function.prototype的一个方法，它是JavaScript引擎内在实现的，因为属于Function.prototype，所以每个Function对象实例(就是每个方法)都有call，apply属性。既然作为方法的属性，那它们的使用就当然是针对方法的了，这两个方法是容易混淆的，因为它们的作用一样，只是使用方式不同。
2、语法：foo.call(this, arg1,arg2,arg3) == foo.apply(this, arguments) == this.foo(arg1, arg2, arg3);
3、相同点：两个方法产生的作用是完全一样的。
4、不同点：方法传递的参数不同。

数组和对象有哪些原生方法，列举一下？
concat()
join()
pop()
push()
reverse()
shift()
slice()
sort()
splice()
toString()
unshift()

JQuery的源码看过吗？能不能简单概况一下它的实现原理？
jQuery的外衣：通用的模块的写法，使用闭包来隔离变量，制造块作用域，防止污染全局变量。

jQuery.fn的init方法返回的this指的是什么对象？为什么要返回this？
jQuery()实际上就是jQuery.fn.init()
jQuery.fn和jQuery.prototype一样，实际上就是一个jQuery对象的一个原型的定义
这两段代码的作用实际上就是要让用户使用jQuery()或者$.jQuery()的时候,就完成对jQuery对象的初始化，不需要在动态的去调用init方法

jQuery 的属性拷贝(extend)的实现原理是什么，如何实现深拷贝？
extend实际上是挂载在jQuery和jQuery.fn上的两个不同方法
jQuery.extend()接收多个对象作为参数，如果只有一个参数，则把这个对象的属性方法附加到jQuery上，如果含有多个参数，则把后面的对象的属性和方法附加到第一个对象上
有最简单的 JSON.parse() 方法，也有常用的递归拷贝方法，和ES5中的 Object.create() 方法。
var newObject = jQuery.extend(true, {}, oldObject);

jquery.extend 与 jquery.fn.extend的区别？
1.jquery.extend(object); 为扩展jQuery类本身.为类添加新的方法。 
jquery.fn.extend(object);给jQuery对象添加方法。

$.extend({ 
　　add:function(a,b){return a+b;} 
}); 
 
//$.add(3,4);
//return 7 
jQuery添加一个为 add的“静态方法”，之后便可以在引入 jQuery　的地方，使用这个方法了.
2.jQuery.fn.extend(object); 对jQuery.prototype进得扩展，就是为jQuery类添加“成员函数”。jQuery类的实例可以使用这个“成员函数”。

$.fn.extend({ 
  alertClick:function(){ 
    $(this).click(function(){ 
      alert($(this).val()); 
    }); 
  } 
}); 
 
//页面上为：
<input id="input1" type="text"/>    
 
//使用
$("#input1").alertClick();  

jQuery 的队列是如何实现的？队列可以用在哪些地方？
封装了push() shift()等  
ajax 动画

JQuery一个对象可以同时绑定多个事件，这是如何实现的？
其实$ele元素的eventName事件有一个处理函数数组 监听一次就往里面放一个handle， 数组是先进后出型的也就是栈， 然后触发事件的时候一次执行

是否知道自定义事件。jQuery里的fire函数是什么意思，什么时候用？
trigger
jQuery 自定义事件是PubSub 模式的忤逆产物，因为这里由可选择的DOM 元素而不是脚本中的对象来触发事件。事件化模型更像是一种直观表达状态相关事件的方式，而jQuery 的自定义事件允许直接通过DOM 来表达DOM 相关的事件，不必再把DOM 变化的状态复制到应用程序的其他地方
使用 callbacks.fire() 用任何已传递的参数调用列表中的回调:

jQuery 是通过哪个方法和 Sizzle 选择器结合的？（jQuery.fn.find()进入Sizzle）

针对 jQuery性能的优化方法？
1. 使用最新版本的jQuery
2. 用对选择器
3. 理解子元素和父元素的关系
4. 不要过度使用jQuery
5. 做好缓存
6. 使用链式写法
7. 事件的委托处理（Event Delegation）
8. 少改动DOM结构
9. 正确处理循环
10. 尽量少生成jQuery对象

jquery是对原生javascript的封装，框架。
jquery ui 是jquery的一个扩展，也可以理解为插件。jquery ui 是基于jquery写的一系列UI方面的框架。
jquery ui 可以说是官方插件。

1. Zepto 对象 不能自定义事件

jQueryUI如何自定义组件?
$.widget()方法开始定义你的组件，它只接收三个参数：第一个是组件名称，第二个是可选的基类组件（默认的基类是$.Widget），第三个是组件的原型。组件名称必须包含命名空间，要注意的是，官方组件的命名空间是以‘ui’开头的，比如:‘ui.tabs’。

ES6有哪些新特性？
参考答案：类的支持，模块化，箭头操作符，let/const块作用域，字符串模板，解构，参数默认值/不定参数/拓展参数,for-of遍历,generato 
r器, Map/Set, Promise

说到AJAX就会不可避免的面临两个问题，第一个是AJAX以何种格式来交换数据？第二个是跨域的需求如何解决？这两个问题目前都有不同的解决方案，比如数据可以用自定义字符串或者用XML来描述，跨域可以通过服务器端代理来解决。

但到目前为止最被推崇或者说首选的方案还是用JSON来传数据，靠JSONP来跨域。

JSON的优点：

1、基于纯文本，跨平台传递极其简单；

2、Javascript原生支持，后台语言几乎全部支持；

3、轻量级数据格式，占用字符数量极少，特别适合互联网传递；

4、可读性较强，虽然比不上XML那么一目了然，但在合理的依次缩进之后还是很容易识别的；

5、容易编写和解析，当然前提是你要知道数据结构；

1、一个众所周知的问题，Ajax直接请求普通文件存在跨域无权限访问的问题，甭管你是静态页面、动态网页、web服务、WCF，只要是跨域请求，一律不准；

2、不过我们又发现，Web页面上调用js文件时则不受是否跨域的影响（不仅如此，我们还发现凡是拥有"src"这个属性的标签都拥有跨域的能力，比如<script>、<img>、<iframe>）；

3、于是可以判断，当前阶段如果想通过纯web端（ActiveX控件、服务端代理、属于未来的HTML5之Websocket等方式不算）跨域访问数据就只有一种可能，那就是在远程服务器上设法把数据装进js格式的文件里，供客户端调用和进一步处理；

4、恰巧我们已经知道有一种叫做JSON的纯字符数据格式可以简洁的描述复杂数据，更妙的是JSON还被js原生支持，所以在客户端几乎可以随心所欲的处理这种格式的数据；

5、这样子解决方案就呼之欲出了，web客户端通过与调用脚本一模一样的方式，来调用跨域服务器上动态生成的js格式文件（一般以JSON为后缀），显而易见，服务器之所以要动态生成JSON文件，目的就在于把客户端需要的数据装入进去。

6、客户端在对JSON文件调用成功之后，也就获得了自己所需的数据，剩下的就是按照自己需求进行处理和展现了，这种获取远程数据的方式看起来非常像AJAX，但其实并不一样。

7、为了便于客户端使用数据，逐渐形成了一种非正式传输协议，人们把它称作JSONP，该协议的一个要点就是允许用户传递一个callback参数给服务端，然后服务端返回数据时会将这个callback参数作为函数名来包裹住JSON数据，这样客户端就可以随意定制自己的函数来自动处理返回数据了。
1、ajax和jsonp这两种技术在调用方式上“看起来”很像，目的也一样，都是请求一个url，然后把服务器返回的数据进行处理，因此jquery和ext等框架都把jsonp作为ajax的一种形式进行了封装；

2、但ajax和jsonp其实本质上是不同的东西。ajax的核心是通过XmlHttpRequest获取非本页内容，而jsonp的核心则是动态添加<script>标签来调用服务器提供的js脚本。

3、所以说，其实ajax与jsonp的区别不在于是否跨域，ajax通过服务端代理一样可以实现跨域，jsonp本身也不排斥同域的数据的获取。

4、还有就是，jsonp是一种方式或者说非强制性协议，如同ajax一样，它也不一定非要用json格式来传递数据，如果你愿意，字符串都行，只不过这样不利于用jsonp提供公开服务。

总而言之，jsonp不是ajax的一个特例，哪怕jquery等巨头把jsonp封装进了ajax，也不能改变着一点！

参考答案: 闭包这个术语，无论中文翻译还是英文解释都太２Ｂ了，我必须骂人，因为它什么其实都不是．非要讲它是什么的话，两个字函数，更多字嵌套函数的父子自我引用关系．所有函数都是闭包．通俗的说，闭包就是作用域范围，因为js是函数作用域，所以函数就是闭包．全局函数的作用域范围就是全局，所以无须讨论．更多的应用其实是在内嵌函数，这就会涉及到内嵌作用域，或者叫作用域链．说到内嵌，其实就是父子引用关系(父函数包含子函数，子函数因为函数作用域又引用父函数，这它妈不是死结吗？所以叫闭包），这就会带来另外一个问题，什么时候引用结束？如果不结束，就会一直占用内存，引起内存泄漏．好吧，不用的时候就引用设为空，死结就解开了．

defineProperty, hasOwnProperty, isEnumerable都是做什么用的？
参考答案：Object.defineProperty(obj, prop, descriptor)用来给对象定义属性,有value,writable,configurable,enumerable,set/get等.hasOwnProerty用于检查某一属性是不是存在于对象本身，继承来的父亲的属性不算．isEnumerable用来检测某一属性是否可遍历，也就是能不能用for..in循环来取到.

js常用设计模式的实现思路，单例，工厂，代理，装饰，观察者模式等
单例:任意对象
工厂:同样形式参数返回不同实例
代理:新建类调用老类的接口,包一下
观察者:事件模式,按钮onclick
列举数组相关的常用方法
参考答案: push/pop, shift/unshift, split/join, slice/splice/concat, sort/reverse, map/reduce, forEach, filter

列举字符串相关的常用方法
参考答案: indexOf/lastIndexOf/charAt, split/match/test, slice/substring/substr, toLowerCase/toUpperCase

为什么要用node?
参考答案: 总结起来node有以下几个特点:简单强大，轻量可扩展．简单体现在node使用的是javascript,json来进行编码，人人都会；强大体现在非阻塞IO,可以适应分块传输数据，较慢的网络环境，尤其擅长高并发访问；轻量体现在node本身既是代码，又是服务器，前后端使用统一语言;可扩展体现在可以轻松应对多实例，多服务器架构，同时有海量的第三方应用组件．

node的构架是什么样子的?
参考答案: 主要分为三层，应用app » V8及node内置架构 » 操作系统. V8是node运行的环境，可以理解为node虚拟机．node内置架构又可分为三层: 核心模块(javascript实现) » c++绑定 » libuv + CAes + http.

node有哪些核心模块?
参考答案: EventEmitter, Stream, FS, Net和全局对象

node全局对象

node有哪些全局对象?
参考答案: process, console, Buffer和exports

process有哪些常用方法?
参考答案: process.stdin, process.stdout, process.stderr, process.on, process.env, process.argv, process.arch, process.platform, process.exit

console有哪些常用方法?
参考答案: console.log/console.info, console.error/console.warning, console.time/console.timeEnd, console.trace, console.table

node有哪些定时功能?
参考答案: setTimeout/clearTimeout, setInterval/clearInterval, setImmediate/clearImmediate, process.nextTick

node中的事件循环是什么样子的? 
总体上执行顺序是：process.nextTick » setImmidate » setTimeout/SetInterval 
看官网吧： 
https://github.com/nodejs/node/blob/master/doc/topics/event-loop-timers-and-nexttick.md
node中的Buffer如何应用?
参考答案: Buffer是用来处理二进制数据的，比如图片，mp3,数据库文件等.Buffer支持各种编码解码，二进制字符串互转．

EventEmitter

什么是EventEmitter?
参考答案: EventEmitter是node中一个实现观察者模式的类，主要功能是监听和发射消息，用于处理多模块交互问题.

如何实现一个EventEmitter?
参考答案: 主要分三步：定义一个子类，调用构造函数，继承EventEmitter

node的网络模块架构是什么样子的?
参考答案: node全面支持各种网络服务器和客户端，包括tcp, http/https, tcp, udp, dns, tls/ssl等.

node是怎样支持https,tls的?
参考答案: 主要实现以下几个步骤即可: 1) openssl生成公钥私钥 2) 服务器或客户端使用https替代http 3) 服务器或客户端加载公钥私钥证书

实现一个简单的http服务器?
参考答案: 经典又很没毛意义的一个题目．思路是加载http模块，创建服务器，监听端口.
为什么需要child-process?
参考答案: node是异步非阻塞的，这对高并发非常有效．可是我们还有其它一些常用需求，比如和操作系统shell命令交互，调用可执行文件，创建子进程进行阻塞式访问或高CPU计算等，child-process就是为满足这些需求而生的．child-process顾名思义，就是把node阻塞的工作交给子进程去做．

exec,execFile,spawn和fork都是做什么用的?
参考答案: exec可以用操作系统原生的方式执行各种命令，如管道 cat ab.txt | grep hello; execFile是执行一个文件; spawn是流式和操作系统进行交互; fork是两个node程序(javascript)之间时行交互.

实现一个简单的命令行交互程序?
参考答案: 那就用spawn吧.

node中的异步和同步怎么理解
参考答案: node是单线程的，异步是通过一次次的循环事件队列来实现的．同步则是说阻塞式的IO,这在高并发环境会是一个很大的性能问题，所以同步一般只在基础框架的启动时使用，用来加载配置文件，初始化程序什么的．

有哪些方法可以进行异步流程的控制?
参考答案: 1) 多层嵌套回调 2)　为每一个回调写单独的函数，函数里边再回调 3) 用第三方框架比方async, q, promise等

怎样绑定node程序到80端口?
参考答案: 多种方式 1) sudo 2) apache/nginx代理 3) 用操作系统的firewall iptables进行端口重定向

有哪些方法可以让node程序遇到错误后自动重启?
参考答案: 1) runit 2) forever 3) nohup npm start &

怎样充分利用多个CPU?
参考答案: 一个CPU运行一个node实例

怎样调节node执行单元的内存大小?
参考答案: 用–max-old-space-size 和 –max-new-space-size 来设置 v8 使用内存的上限

程序总是崩溃，怎样找出问题在哪里?
参考答案: 1) node –prof 查看哪些函数调用次数多 2) memwatch和heapdump获得内存快照进行对比，查找内存溢出

有哪些常用方法可以防止程序崩溃?
参考答案: 1) try-catch-finally 2) EventEmitter/Stream error事件处理 3) domain统一控制 4) jshint静态检查 5) jasmine/mocha进行单元测试

怎样调试node程序?
参考答案: node –debug app.js 和node-inspector

async都有哪些常用方法，分别是怎么用?
参考答案: async是一个js类库，它的目的是解决js中异常流程难以控制的问题．async不仅适用在node.js里，浏览器中也可以使用． 
1) async.parallel并行执行完多个函数后，调用结束函数

    async.parallel([
        function(){ ... },
        function(){ ... }
    ], callback);
1234
2) async.series串行执行完多个函数后，调用结束函数

    async.series([
        function(){ ... },
        function(){ ... }
    ]);
1234
3) async.waterfall依次执行多个函数，后一个函数以前面函数的结果作为输入参数

    async.waterfall([
        function(callback) {
            callback(null, 'one', 'two');
        },
        function(arg1, arg2, callback) {
          // arg1 now equals 'one' and arg2 now equals 'two'
            callback(null, 'three');
        },
        function(arg1, callback) {
            // arg1 now equals 'three'
            callback(null, 'done');
        }
    ], function (err, result) {
        // result now equals 'done'
    });
123456789101112131415
4) async.map异步执行多个数组，返回结果数组

    async.map(['file1','file2','file3'], fs.stat, function(err, results){
        // results is now an array of stats for each file
    });
123
5) async.filter异步过滤多个数组，返回结果数组

    async.filter(['file1','file2','file3'], fs.exists, function(results){
        // results now equals an array of the existing files
    });
123
express项目的目录大致是什么样子的
参考答案: app.js, package.json, bin/www, public, routes, views.

express常用函数
参考答案: express.Router路由组件,app.get路由定向，app.configure配置，app.set设定参数,app.use使用中间件

express中如何获取路由的参数
参考答案: /users/:name使用req.params.name来获取; req.body.username则是获得表单传入参数username; express路由支持常用通配符 ?, +, *, and ()

 vertical-align:middle;// 垂直居中对齐

 display:inline|inline-block 块级元素转行级元素

行级元素浮动之后，display为block。flex（弹性盒子）

示例3：伪类对象::after+zoom:1(推荐使用)
2.使用overflow属性
3.使用display属性

上面代码可以合并一行代码
[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
//str=hello  
  function reverseString(str) {   
      return str.split('').reverse().join('');;  
  }  

2）使用for循环
[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
function reverseString(str) {     
var newStr="";  
for(var i=str.length-1;i>=0;i--){  
newStr+=str[i];  
}  
return newStr;  
}  
            使用逆序遍历字符串，从后面将字符串累加起来。
3）使用递归
[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
function reverseString(str) {  
 if (str === "") {  
 return "";  
 } else {  
 return reverseString(str.substr(1)) + str.charAt(0);  
 }  
}  
reverseString("hello"); // => olleh  

第一种方法 使用splice方法
语法介绍
[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
splice(start, deleteCount, value, ...)  
start 
开始插入和(或)删除的数组元素的下标。
deleteCount 
从start开始，包括start所指的元素在内要删除的元素个数。这个参数是可选的，如果没有指定它，splice()将删除从start开始到原数组结尾的所有元素。
value, ... 
要插入数组的零个或多个值，从start所指的下标处开始插入。
var str = [0, 1, 3, 4, 6, 7];//原始字符串  
var insWord = 5;//待插入字符串  
var index = 4;//待插入位置  
//待插入位置的元素全部向后移动一位  
for(var i=str.length-1;i>=index;i--){  
 str[i+1]=str[i];  
}  
str[index]=insWord;//移动完后，将待插入的位置赋值为待插入的值  
console.log(str);//[0, 1, 3, 4, 5, 6, 7]  

事件用于监听浏览器的操作行为，浏览器触发动作时被捕捉到而调用相应的函数。

事件执行三个阶段

① 事件捕获阶段 
② 处于目标阶段
③ 事件冒泡阶段
捕获型事件是自上而下，而冒泡型事件是自下而上的，而我们程序员通常要做的就是第二阶段，完成事件的动作。而第一、三阶段由系统封装自动调用完成。
event.stopPropagation()

bind：把事件绑定到每一个匹配的元素上，主要特点

1.兼容性比较好

2.绑定事件到所有选出来的元素上

3.不会绑定事件到动态添加的那些元素上

4.当元素很多时，会出现效率问题，特别是嵌套层次比较深的元素。
delegate：将事件绑定到指定的父元素上，和live类似但比较能活。主要特点：

1.可以用在动态添加的元素上

2.绑定的父元素可以采用就近原则，减少查询的次数，比live的性能好

3.在live和delegate两者推荐使用delegate

On：是jQuery1.7中新增的，前面的三种方法都是依赖on方法来实现的。，主要特点：

1.事件的添加和卸载都要是通过on来实现的，提供一种统一的事件处理方法。

2.增加了使用的难度，对于不熟悉on的使用的，很有可能就勿用，导致性能下降。

JSON(JavaScript Object Notation) 是一种轻量级的数据交换格式。它是基于JavaScript的一个子集。数据格式简单, 易于读写, 占用带宽小。是前后台数据交互最常见的一种数据格式。

JSON语法

1.数据在键值对中，如： key:value 使用冒号分隔。

2.数据由逗号分隔

3.花括号保存对象

4.方括号保存数组

闭包是就是函数中的函数，里面的函数可以访问外面函数的变量，外面的变量的是这个内部函数的一部分。

1.使用闭包可以访问函数中的变量。

2.可以使变量长期保存在内存中，生命周期比较长。
闭包不能滥用，否则会导致内存泄露，影响网页的性能。闭包使用完了后，要立即使用资源，将引用变量指向null。

1.创建Ajax核心对象XMLHttpRequest

[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
var xmlhttp;  
if (window.XMLHttpRequest)  
  {// 兼容 IE7+, Firefox, Chrome, Opera, Safari  
  xmlhttp=new XMLHttpRequest();  
  }  
else  
  {// 兼容 IE6, IE5  
  xmlhttp=newActiveXObject("Microsoft.XMLHTTP");  
  }  

2.向服务器发送请求
[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
xmlhttp.open(method,url,async);  
send(string)  

注意：open 的参数要牢记，很多面试官爱问这样的细节
method：请求的类型；GET 或 POST
url：文件在服务器上的位置
async：true（异步）或 false（同步）
send(string)方法post请求时才使用字符串参数，否则不用带参数。



注意：post请求一定要设置请求头的格式内容

[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
xmlhttp.open("POST","ajax_test.html",true);  
xmlhttp.setRequestHeader("Content-type","application/x-www-form-urlencoded");  
xmlhttp.send("fname=Henry&lname=Ford");  
3.服务器响应处理

responseText    获得字符串形式的响应数据。
responseXML   获得XML 形式的响应数据。

       3.1 同步处理

[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
xmlhttp.open("GET","ajax_info.txt",false);  
xmlhttp.send();  
document.getElementById("myDiv").innerHTML=xmlhttp.responseText;  
直接在send()后面处理返回来的数据。

3.2 异步处理

异步处理相对比较麻烦，要在请求状态改变事件中处理。

[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
xmlhttp.onreadystatechange=function()  
  {  
  if (xmlhttp.readyState==4 &&xmlhttp.status==200)  
    {  
   document.getElementById("myDiv").innerHTML=xmlhttp.responseText;  
    }  
  }  

一共有5中请求状态，从0 到 4 发生变化。

0: 请求未初始化

1: 服务器连接已建立

2: 请求已接收

3: 请求处理中

4: 请求已完成，且响应已就绪



xmlhttp.status：响应状态码。这个也是面试比较爱问的，这个必须知道4个以上，比较常见的有：

200: "OK"

403   （禁止） 服务器拒绝请求。

404   （未找到） 服务器找不到请求的网页。

408  （请求超时） 服务器等候请求时发生超时。

500   （服务器内部错误）  服务器遇到错误，无法完成请求。

xmlhttp.open("POST","ajax_test.html",true);  
xmlhttp.setRequestHeader("Content-type","application/x-www-form-urlencoded");  
xmlhttp.send("fname=Henry&lname=Ford");

this.alert() <=> window.alert()<=> alert(); 

var Go=function(){  
     this.address="深圳";  
}  
var Show=function(){  
     console.log(this.address);//输出 深圳  
}  
var go=new Go();  
Show.call(go);//改变Show方法的this指向go对象  

var age=20;  
function show(age){  
   this.age=age;  
}  

目前，通行的JavaScript模块规范共有两种：CommonJS和AMD。

js延迟加载的方式有哪些？
1.defer 属性
2.async 属性
3.动态创建DOM方式
4.使用jQuery的getScript()方法

[javascript] view plain copy
$.getScript("outer.js",function(){//回调函数，成功获取文件后执行的函数  
      console.log("脚本加载完成")  
});  
从源码可以看出，这个方法最后还是调用了jQuery.ajax()来请求了js文件的。

new的具体操作
1、创建一个空对象

[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
varobj=new Object();  
2、设置原型链

[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
obj.__proto__= Func.prototype;  
3、让Func中的this指向obj，并执行Func的函数体。

[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
var result =Func.call(obj);  
4、判断Func的返回值类型：

如果是值类型，返回obj。如果是引用类型，就返回这个引用类型的对象。

[javascript] view plain copy 在CODE上查看代码片派生到我的代码片
if (typeof(result) == "object"){  
  func=result;  
}  
else{  
    func=obj;;  
}  

SVG比较优势编辑
首先简要解释一下矢量图像格式和位图图像格式的区别。矢量图像用点和线来描述物体，所以文件会比较小，同时也能提供高清晰的画面，适合于直接打印或输出。而位图图像的存储单位是图像上每一点的像素值，因此一般的图像文件都很大，会占用大量的网络带宽。SVG是一种矢量图形格式，GIF、JPEG是光栅文件格式。有了两者的概念后，SVG较GIF、JPEG的优势显而易见。
1．任意放缩。
用户可以任意缩放图像显示，而不会破坏图像的清晰度、细节等。
2．文本独立。
SVG图像中的文字独立于图像，文字保留可编辑和可搜寻的状态。也不会再有字体的限制，用户系统即使没有安装某一字体，也会看到和他们制作时完全相同的画面。
3．较小文件。
总体来讲，SVG文件比那些GIF和JPEG格式的文件要小很多，因而下载也很快。
4．超强显示效果
SVG图像在屏幕上总是边缘清晰，它的清晰度适合任何屏幕分辨率和打印分辨率。
5．超级颜色控制。
SVG图像提供一个1 600万种颜色的调色板，支持ICC颜色描述文件标准、RGB、线X填充、渐变和蒙版。
6．交互X和智能化。SVG面临的主要问题一个是如何和已经占有重要市场份额的矢量图形格式Flash竞争的问题，另一个问题就是SVG的本地运行环境下的厂家支持程度。
开发编辑
SVG是一个XML文件，用于XML编程的两种模型DOM和SAX也适用于它。因为SVG是被设计用于互联网，所以通过Javascript和DOM访问它就是最重要的应用模式。通过Javascript和DOM可以动态地修改HTML，同样也可以在浏览器中动态地创建、修改和删除图片。

1.CSS3的选择器

1）E:last-child 匹配父元素的最后一个子元素E。
2）E:nth-child(n)匹配父元素的第n个子元素E。 
3）E:nth-last-child(n) CSS3 匹配父元素的倒数第n个子元素E。

2. @Font-face 特性

Font-face 可以用来加载字体样式，而且它还能够加载服务器端的字体文件，让客户端显示客户端所没有安装的字体。
3. 圆角
5.阴影（Shadow） 
6.CSS3 的渐变效果 
7.css弹性盒子模型
8. CSS3制作特效

location.assign("https://www.baidu.com");
window.location="https://www.baidu.com";

navigator.geolocation 定位
