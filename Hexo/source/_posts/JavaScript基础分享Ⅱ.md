---
title: 进击的前端开发（JavaScript基础篇二）
date: 2019-04-01 13:28:39
tags: 
- HTML
- JavaScript
categories: 
- 前端
---
## 进击的前端开发（JavaScript基础篇二）

### Ⅲ. 函数
### Ⅳ. 标准对象
- Date
- RegExp
- JSON

### Ⅴ. 面向对象编程
- 创建对象
- 原型继承
- class继承

### Ⅵ.浏览器
由于JavaScript的出现就是为了能在浏览器中运行，所以，浏览器自然是JavaScript开发者必须要关注的。

目前主流的浏览器分这么几种：

IE 6~11：国内用得最多的IE浏览器，历来对W3C标准支持差。从IE10开始支持ES6标准；

Chrome：Google出品的基于Webkit内核浏览器，内置了非常强悍的JavaScript引擎——V8。由于Chrome一经安装就时刻保持自升级，所以不用管它的版本，最新版早就支持ES6了；

Safari：Apple的Mac系统自带的基于Webkit内核的浏览器，从OS X 10.7 Lion自带的6.1版本开始支持ES6，目前最新的OS X 10.11 El Capitan自带的Safari版本是9.x，早已支持ES6；

Firefox：Mozilla自己研制的Gecko内核和JavaScript引擎OdinMonkey。早期的Firefox按版本发布，后来终于聪明地学习Chrome的做法进行自升级，时刻保持最新；

移动设备上目前iOS和Android两大阵营分别主要使用Apple的Safari和Google的Chrome，由于两者都是Webkit核心，结果HTML5首先在手机上全面普及（桌面绝对是Microsoft拖了后腿），对JavaScript的标准支持也很好，最新版本均支持ES6。

其他浏览器如Opera等由于市场份额太小就被自动忽略了。

另外还要注意识别各种国产浏览器，如某某安全浏览器，某某旋风浏览器，它们只是做了一个壳，其核心调用的是IE，也有号称同时支持IE和Webkit的“双核”浏览器。

不同的浏览器对JavaScript支持的差异主要是，有些API的接口不一样，比如AJAX，File接口。对于ES6标准，不同的浏览器对各个特性支持也不一样。

在编写JavaScript的时候，就要充分考虑到浏览器的差异，尽量让同一份JavaScript代码能运行在不同的浏览器中。

- 浏览器对象
   - window
   
      window对象不但充当全局作用域，而且表示浏览器窗口。

      window对象有innerWidth和innerHeight属性，可以获取浏览器窗口的内部宽度和高度。内部宽高是指除去菜单栏、工具栏、边框等占位元素后，用于显示网页的净宽高。
      
      对应的，还有一个outerWidth和outerHeight属性，可以获取浏览器窗口的整个宽高。
   
   - navigator

      navigator对象表示浏览器的信息，最常用的属性包括：

      navigator.appName：浏览器名称；
      navigator.appVersion：浏览器版本；
      navigator.language：浏览器设置的语言；
      navigator.platform：操作系统类型；
      navigator.userAgent：浏览器设定的User-Agent字符串。
      
      ```
      console.log('appName = ' + navigator.appName);
      console.log('appVersion = ' + navigator.appVersion);
      console.log('language = ' + navigator.language);
      console.log('platform = ' + navigator.platform);
      console.log('userAgent = ' + navigator.userAgent);
      ```
 
   - screen

      screen对象表示屏幕的信息，常用的属性有：

      screen.width：屏幕宽度，以像素为单位；
      
      screen.height：屏幕高度，以像素为单位；
      
      screen.colorDepth：返回颜色位数，如8、16、24。

   - location

      location对象表示当前页面的URL信息。例如，一个完整的URL：
      `http://www.example.com:8080/path/index.html?a=1&b=2#TOP`
      可以用location.href获取。要获得URL各个部分的值，可以这么写：
      
      ```
      location.protocol; // 'http'
      location.host; // 'www.example.com'
      location.port; // '8080'
      location.pathname; // '/path/index.html'
      location.search; // '?a=1&b=2'
      location.hash; // 'TOP'
      ```
      要加载一个新页面，可以调用location.assign()。如果要重新加载当前页面，调用location.reload()方法非常方便。
      
      ```
      if (confirm('重新加载当前页' + location.href + '?')) {
    location.reload();
} else {
    location.assign('/'); // 设置一个新的URL地址
}
```
      document对象表示当前页面。由于HTML在浏览器中以DOM形式表示为树形结构，document对象就是整个DOM树的根节点。

      document的title属性是从HTML文档中的<title>xxx</title>读取的，但是可以动态改变：
      `document.title = '努力学习JavaScript!';//运行后观察浏览器窗口标题变化`
      
      要查找DOM树的某个节点，需要从document对象开始查找。最常用的查找是根据ID和Tag Name。
      我们先准备HTML数据：
      
      ```
      <dl id="drink-menu" style="border:solid 1px #ccc;padding:6px;">
    <dt>摩卡</dt>
    <dd>热摩卡咖啡</dd>
    <dt>酸奶</dt>
    <dd>北京老酸奶</dd>
    <dt>果汁</dt>
    <dd>鲜榨苹果汁</dd>
</dl>
      ```
      用document对象提供的getElementById()和getElementsByTagName()可以按ID获得一个DOM节点和按Tag名称获得一组DOM节点：
      
      ```
      var menu = document.getElementById('drink-menu');
      var drinks = document.getElementsByTagName('dt');
      var i, s, menu, drinks;

		menu = document.getElementById('drink-menu');
		menu.tagName; // 'DL'
		
		drinks = document.getElementsByTagName('dt');
		s = '提供的饮料有:';
		for (i=0; i<drinks.length; i++) {
		    s = s + drinks[i].innerHTML + ',';
		}
		console.log(s);

      ```

      

      
   - document
   - history
- 操作DOM
   - 更新DOM
   - 插入DOM
   - 删除DOM
- 操作表单
- 操作文件
- AJAX
- Promise
- Canvas

### Ⅶ jQuery

### Ⅷ 错误处理

### Ⅸ underscore

### Ⅹ Node.js

### ⅩⅠ React
