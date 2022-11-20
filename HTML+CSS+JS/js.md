### HTML中嵌入JavaScript代码

第一种：HTML的标签属性——事件句柄

```html
1、要实现的功能：
用户点击以下按钮，弹出消息框。

2、JS是一门事件驱动型的编程语言，依靠事件去驱动，然后执行对应的程序。
在JS中有很多事件，其中有一个事件叫做：鼠标单击，单词：click。并且任何
事件都会对应一个事件句柄叫做：onclick。【注意：事件和事件句柄的区别是：
事件句柄是在事件单词前添加一个on。】，而事件句柄是以HTML标签的属性存在
的。

3、onclick="js代码"，执行原理是什么？
页面打开的时候，js代码并不会执行，只是把这段JS代码注册到按钮的click事件上了。
等这个按钮发生click事件之后，注册在onclick后面的js代码会被浏览器自动调用。

4、怎么使用JS代码弹出消息框？
在JS中有一个内置的对象叫做window，全部小写，可以直接拿来使用，window代表的是浏览器对象。
window对象有一个函数叫做:alert，用法是：window.alert("消息");这样就可以弹窗了。

5、JS中的字符串可以使用双引号，也可以使用单引号。

6、JS中的一条语句结束之后可以使用分号“;”，也可以不用。

<input type="button" value="hello" onclick="window.alert('hello js')"/>
```

第二种：脚本块的方式


```HTML
<script type="text/javascript"> </script>

javascript的脚本块在一个页面当中可以出现多次。没有要求。
javascript的脚本块出现位置也没有要求，随意。

<script type="text/javascript">

/*
暴露在脚本块当中的程序，在页面打开的时候执行，
并且遵守自上而下的顺序依次逐行执行。（这个代
码的执行不需要事件）
*/
window.alert("Hello World!"); // alert函数会阻塞整个HTML页面的加载。

// JS代码的注释，这是单行注释。
/*
JS代码的多行注释。和java一样。
*/
window.alert("Hello JavaScript!");

</script>
```

第三种方式：引入外部独立的js文件

<script type="text/javascript" src="js/1.js"> 
</script>

### JS中变量

```
javascript当中的变量？
怎么声明变量？
var 变量名;
怎么给变量赋值？
变量名 = 值;
javascript是一种弱类型语言，没有编译阶段，一个变量可以随意赋值，赋什么类型的值都行。
var i = 100;
i = false;
i = "abc";
i = new Object();
i = 3.14;

重点：javascript是一种弱类型编程语言。

1、当一个变量声明的时候没有使用var关键字,那么不管这个变量是在哪里声明的,都是全局变量.

2、全局变量：
在函数体之外声明的变量属于全局变量，全局变量的生命周期是：
浏览器打开时声明，浏览器关闭时销毁，尽量少用。因为全局变量会一直在浏览器的内存当中，耗费内存空间。
能使用局部变量尽量使用局部变量。
局部变量：
在函数体当中声明的变量，包括一个函数的形参都属于局部变量，
局部变量的生命周期是：函数开始执行时局部变量的内存空间开辟，函数执行结束之后，局部变量的内存空间释放。
局部变量生命周期较短。
```

### JS中函数

```
3、JS中的变量是一种弱类型的，那么函数应该怎么定义呢？
语法格式：
第一种方式：
function 函数名(形式参数列表){
	函数体;
}
第二种方式：
函数名 = function(形式参数列表){
	函数体;
}

// 可以通过prototype这个属性来给类动态扩展属性以及函数
Product.prototype.getPname = function(){
	return this.pname;
}
```

### JS中变量类型

```
1、虽然JS中的变量在声明的时候不需要指定数据类型，但是在赋值，每一个数据还是有类型的，所以
这里也需要学习一下JS包括哪些数据类型？
JS中数据类型有：原始类型、引用类型。
原始类型：Undefined、Number、String、Boolean、Null
引用类型：Object以及Object的子类

2、ES规范(ECMAScript规范)，在ES6之后，又基于以上的6种类型之外添加了一种新的类型：Symbol

3、JS中有一个运算符叫做typeof，这个运算符可以在程序的运行阶段动态的获取变量的数据类型。
typeof运算符的语法格式：
typeof 变量名
typeof运算符的运算结果是以下6个字符串之一：注意字符串都是全部小写。
"undefined"
"number"
"string"
"boolean"
"object"
"function"

4、在JS当中比较字符串是否相等使用“==”完成。没有equals。


alert(Boolean(1)); // true
alert(Boolean(0)); // false
alert(Boolean("")); // false
alert(Boolean("abc")); // true
alert(Boolean(null)); // false
alert(Boolean(NaN)); // false
alert(Boolean(undefined)); // false
alert(Boolean(Infinity)); // true


// 小string(属于原始类型String)
var x = "king";
alert(typeof x); // "string"

// 大String(属于Object类型)
var y = new String("abc");
alert(typeof y); // "object"

// 获取字符串的长度
alert(x.length); // 4
alert(y.length); // 3

alert("http://www.baidu.com".indexOf("http")); // 0
alert("http://www.baidu.com".indexOf("https")); // -1

// 判断一个字符串中是否包含某个子字符串？
alert("http://www.baidu.com".indexOf("https") >= 0 ? "包含" : "不包含"); // 不包含

// replace (注意：只替换了第一个)
alert("name=value%name=value%name=value".replace("%","&")); // name=value&name=value%name=value

// 继续调用replace方法,就会替换第“二”个.
// 想全部替换需要使用正则表达式.
alert("name=value%name=value%name=value".replace("%","&").replace("%", "&")); // name=value&name=value&name=value

// 考点:经常问 substr和substring的区别？
// substr(startIndex, length)
alert("abcdefxyz".substr(2,4)); //cdef
// substring(startIndex, endIndex) 注意:不包含endIndex
alert("abcdefxyz".substring(2,4)); //cd
```

### JS中常用事件

```
JS中的事件：

blur失去焦点	
focus获得焦点

click鼠标单击
dblclick鼠标双击

keydown键盘按下
keyup键盘弹起

mousedown鼠标按下
mouseover鼠标经过
mousemove鼠标移动
mouseout鼠标离开
mouseup鼠标弹起

reset表单重置
submit表单提交

change下拉列表选中项改变，或文本框内容改变
select文本被选定
load页面加载完毕（整个HTML页面中所有的元素全部加载完毕之后发生。）

任何一个事件都会对应一个事件句柄，事件句柄是在事件前添加on。
onXXX这个事件句柄出现在一个标签的属性位置上。（事件句柄以属性的形式存在。）


捕获回车
usernameElt.onkeydown = function(event){
  if(event.keyCode === 13){
	  alert("正在进行验证....");
  }
}
void函数
<a href="javascript:void(0)" onclick="window.alert('test code')">
```

### JS代码中设置节点属性

```
window.onload = function(){
			   //var btnElt = window.document.getElementById("btn");
			   var btnElt = document.getElementById("btn");
			   alert(btnElt); // object HTMLInputElement
}
```

### DOM

```
1、JavaScript包括三大块：
ECMAScript：JS的核心语法（ES规范 / ECMA-262标准）
DOM：Document Object Model（文档对象模型：对网页当中的节点进行增删改的过程。）HTML文档被当做一棵DOM树来看待。
var domObj = document.getElementById("id");
BOM：Browser Object Model（浏览器对象模型）
关闭浏览器窗口、打开一个新的浏览器窗口、后退、前进、浏览器地址栏上的地址等，都是BOM编程。

2、DOM和BOM的区别和联系？
BOM的顶级对象是：window
DOM的顶级对象是：document
实际上BOM是包括DOM的！
```

![BOM和DOM的关系](G:/BaiduNetdiskDownload/02-JavaWeb/HTML+CSS+JavaScript/document/BOM和DOM的关系.jpg)

正则表达式

```
4、常见的正则表达式符号？
. 匹配除换行符以外的任意字符 
\w 匹配字母或数字或下划线或汉字 
\s 匹配任意的空白符 
\d 匹配数字 
\b 匹配单词的开始或结束 
^ 匹配字符串的开始 
$ 匹配字符串的结束

* 重复零次或更多次 
+ 重复一次或更多次 
? 重复零次或一次 
{n} 重复n次 
{n,} 重复n次或更多次 
{n,m} 重复n到m次

\W 匹配任意不是字母，数字，下划线，汉字的字符 
\S 匹配任意不是空白符的字符 
\D 匹配任意非数字的字符 
\B 匹配不是单词开头或结束的位置 
[^x] 匹配除了x以外的任意字符 
[^aeiou] 匹配除了aeiou这几个字母以外的任意字符 

正则表达式当中的小括号()优先级较高。
[1-9] 表示1到9的任意1个数字（次数是1次。）
[A-Za-z0-9] 表示A-Za-z0-9中的任意1个字符
[A-Za-z0-9-] 表示A-Z、a-z、0-9、- ，以上所有字符中的任意1个字符。

| 表示或者
```

**表单验证**

```
1.获取的是Elt和Span,比较判断使用Elt.value和Span.innerText
如果比较密码是否相等
不是userpwdElt==userpwd2Elt，而是userpwdElt.value = userpwd2Elt.value
不是usernameErrorSpan=="",usernameErrorSpan.innerText == ""
2.绑定事件用onfocus,  emailElt.onfocus
id和对象尽量别重名

```

**复选框的全选和取消全选**

```
获取复选框Elt
var aihaos = document.getElementsByName("aihao");
```

