---
title:  高济 JSBridge 开发文档
date: 2019-04-01 14:15:30
tags: 
- 文档
categories: 
- 文档
author: Allen
---

#####  复制文本到剪切板


name：
~~~
pasteboardJSBridge
~~~

params:
~~~
{'pasteboardText' : 'text content'}
~~~


#####  打开一个新WebView窗口

name：
~~~
openNewWindowJSBridge
~~~

params:
~~~
{'url' : 'https://xxxx'}
~~~

#####  调用goback

name：
~~~
gobackJSBridge
~~~

params:
~~~
nil
~~~

#####   Native 返回上一页

name：
~~~
controllerPopJSBridge
~~~

params:
~~~
nil
~~~

#####  自定义标题

name：
~~~
controllerPopJSBridge
~~~

params:
~~~
{'titleString':'title'}
~~~

#####   退出登录

name：
~~~
loginoutJSBridge
~~~

params:
~~~
nil
~~~

#####   设置导航栏右边按钮

name：
~~~
navRightButtonTitle
~~~

params:
~~~
{"navRightButtonTitle":"保存"}
~~~

#####   设置导航栏右边按钮隐藏

name：
~~~
rightButtonHidenClick
~~~

params:
~~~
nil
~~~

#####   设置导航栏导航中间按钮

name：
~~~
navCenterButtonJSBridge
~~~

params:
~~~
{"navCenterButtonTitle":"花儿大药房"}
~~~

#####   设置导航栏导航中间按钮隐藏

name：
~~~
navCenterButtonHidenJSBridge
~~~

params:
~~~
nil
~~~

#####   跳转Native业务模块

name：
~~~
H5PushNativeRoute
~~~

params:
~~~
//找native同事提供路由
{"NativeRoute":"gjhealth://cstore/member/memberQRCodeCard"}
~~~

#####   选择地址

name：
~~~
selectAddressJSBridge
~~~

params:
~~~
nil
~~~

callback:
~~~
{
    "logitudeString" : 116.46 
    "latitudeString" : 39.92 
    "addressString" : 北京 
}
~~~

#####   选择组织

name：
~~~
selectOrgBridge
~~~

params:
~~~
{"selectOrgType":"2"}
~~~

callback:
~~~
{   "orgId" : xxx,
    "orgName" : xxx,
    "orgType" : xxx,
    "storeId" : xxx,
    "userId" : xxx,
    "storeName" : xxx,
}
~~~

#####   扫一扫

name：
~~~
QRCodeJSBridge
~~~

params:
~~~
{
    "title":"请扫描二维码/条形码",
    "light":true,
    "codeType":0 //0 条形码 ,1 二维码
}
~~~

callback:
~~~
{ @"QRCodeValueString" : codeString}
~~~

#####   调用图表预览

name：
~~~
previewImageJSBridge
~~~

params:
~~~
{
 "previewImageSelectIndex":"0"
 "previewImagesArray":["url1","url2",]
}
~~~

#####   保存图片到相册

name：
~~~
saveImageJSBridge
~~~

params:
~~~
imageBase64
~~~

#####   分享图片

name：
~~~
shareImageJSBridge
~~~

params:
~~~
imageBase64
~~~

#####   获取相册图片

name：
~~~
getImagesJSBridge
~~~

params:
~~~
{"imageCount":"4"}
~~~

callback:
~~~
[imageBase64,imageBase64,imageBase64,imageBase64]
~~~

#####   分享

name：
~~~
shareJSBridge
~~~

params:
~~~
{
    "title":"iOS 分享组件",
    "description":"高济医疗官网",
    "webpageUrl":"http://www.gaojihealth.com",
    "thumbImageURL":"https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3706507586,466188827&fm=26&gp=0.jpg"
}
~~~


