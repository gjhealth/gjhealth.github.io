---
title: charles 抓包工具使用教程
date: 2019-05-10 16:00:39
tags:
  - 工具
  - 文档
categories:
  - 文档
---

#### charles 介绍

Charles 是一个 HTTP 代理/HTTP 监视器/反向代理，使开发人员能够查看其计算机和 Internet 之间的所有 HTTP 和 SSL/HTTPS 通信。这包括请求、响应和 HTTP 头（其中包含 cookie 和缓存信息）

#### 设置手机代理

第一步：首先获取电脑 ip 地址，下面介绍 3 中方法获取到本机 ip 地址

1.  在终端输入 ifconfig -a
    ![](http://wx4.sinaimg.cn/mw690/006Fw6Kwly1g2tyb86coqj30vo0fqadp.jpg)

2.  mac 电脑点击系统偏好设置->网络
    ![](http://wx2.sinaimg.cn/mw690/006Fw6Kwly1g2tyg6qjixj30zx0u0gtp.jpg)

3.  打开 Charles 点击导航栏上的 Help->Local IP Address

    ![](http://wx1.sinaimg.cn/mw690/006Fw6Kwly1g2tyl2guf1j31ds0dwne1.jpg)

    ![](http://wx1.sinaimg.cn/mw690/006Fw6Kwly1g2tykew9j3j30r80g4myp.jpg)

第二步：已 iPhone 为例，点击设置->无线网络->点击连接的 wifi->配置代理->选择手动，配置服务器和端口号，端口号默认 8888，别忘记点击存储

![](http://wx3.sinaimg.cn/mw690/006Fw6Kwly1g2tyuw6hnxj30u01sz43o.jpg)

第三部: 点击要抓包的 App，这时候 charles 工具上回弹出一个弹窗，点击 Allow 允许。

![](http://wx2.sinaimg.cn/mw690/006Fw6Kwly1g2tz8be17pj314a0aejv0.jpg)

#### 界面介绍

![](http://wx3.sinaimg.cn/large/006Fw6Kwly1g2u1mavzaaj31hx0u0tqb.jpg)

#### 修改请求参数

![](http://wx3.sinaimg.cn/large/006Fw6Kwly1g2u263sa9wj31i00u0nc6.jpg)

![](http://wx4.sinaimg.cn/large/006Fw6Kwly1g2u268k48lj31hz0u0tkm.jpg)

#### 修改返回结果

![](http://wx3.sinaimg.cn/large/006Fw6Kwly1g2u2y42vmjj31em0u04qp.jpg)

![](http://wx2.sinaimg.cn/large/006Fw6Kwly1g2u2y9iiuqj31if0u0q91.jpg)

![](http://wx2.sinaimg.cn/large/006Fw6Kwly1g2u2y9iiuqj31if0u0q91.jpg)

![](http://wx2.sinaimg.cn/large/006Fw6Kwly1g2u2yrdg2nj31i10u0alg.jpg)

![](http://wx3.sinaimg.cn/large/006Fw6Kwly1g2u2zowcgrj31io0u0nf0.jpg)

#### Map Remote 代理转发

如果服务端需要跟客户端本地调试，就可以不用修改 api 地址，直接代理转发到他的电脑地址上就可以

右键点击 Map Remote
![](http://wx3.sinaimg.cn/large/006Fw6Kwly1g2u44i020zj31at0u0hdt.jpg)

设置转发地址
![](http://wx4.sinaimg.cn/mw690/006Fw6Kwly1g2u44v4g54j30p00u60vv.jpg)

这时候重新刷新，发现已经代理成本地接口
![](http://wx1.sinaimg.cn/mw690/006Fw6Kwly1g2u4exf3uoj31ci0u0wny.jpg)

#### 取消代理转发

Tools-> Map Remote ->Remove
![](http://wx1.sinaimg.cn/large/006Fw6Kwly1g2u4lu39ezj30yu0m4459.jpg)

#### Map Local 数据本地 mock

有时候服务挂掉了，或者还没有开放完，可以通过该功能 mock 本地文件数据

![](http://wx1.sinaimg.cn/large/006Fw6Kwly1g2u4zl3126j30nk0luqhk.jpg)

![](http://wx1.sinaimg.cn/large/006Fw6Kwly1g2u4zl3126j30nk0luqhk.jpg)

#### 模拟各种网络测试

超级 App 各种网络测试，是必备的一环，用来测试弱网情况下的 loading 提示，空白页，丢包情况，异常情况等等。

导航栏 Proxy -> ThrottleSettings

![](http://wx2.sinaimg.cn/large/006Fw6Kwly1g2u5d4jx0cj30h60a2why.jpg)

![](http://wx4.sinaimg.cn/large/006Fw6Kwly1g2u5dm9dsfj314e0psqes.jpg)

#### BlackList&WhiteList

BlackList 黑名单禁止请求
WhiteList 运行请求

#### 服务器压力测试

![](http://wx3.sinaimg.cn/large/006Fw6Kwly1g2u62l6qgdj31260hw7iv.jpg)

![](http://wx2.sinaimg.cn/large/006Fw6Kwly1g2u6353htpj30ua0gojte.jpg)

#### No Caching Settings 禁止缓存

工具可防止客户端应用程序（如 Web 浏览器）缓存任何资源。因此，始终向远程网站发出请求，您始终可以看到最新版本。

适用范围

该工具可以作用于每个请求(选中 Enable No Caching 即可)，也可以仅对你配置的请求启用(启用 No Caching 的同时，请选中 Only for selected locations)。当用于选定的请求时，可以使用简单但功能强大的模式匹配将工具的效果限制为指定的主机和路径。

工作原理

No Caching 工具通过操纵控制响应缓存的 HTTP 请求头来防止缓存。从请求中删除 If-Modified-Since 和 If-None-Match 请求头，添加 Pragma：no-cache 和 Cache-control：no-cache。从响应中删除 Expires，Last-Modified 和 ETag 请求头，添加 Expires：0 和 Cache-Control：no-cache。

#### Block Cookies Settings(禁用 Cookie)

Block Cookies 工具阻止了 Cookie 的发送和接收。它可用于测试网站，就像在浏览器中禁用了 Cookie 一样。 请注意，网络爬虫（例如 Google）通常不支持 Cookie，因此该工具还可用于模拟网络爬虫网站的视图。

适用范围

该工具可以作用于每个请求(选中 Enable Block Cookies 即可)，也可以仅对你配置的请求启用(启用 Block Cookies 的同时，请选中 Only for selected locations)。当用于选定的请求时，可以使用简单但功能强大的模式匹配将工具的效果限制为指定的主机和路径。

工作原理

Block Cookies 工具通过操纵控制响应 Cookies 的 HTTP 请求头来禁用 Cookies。从请求中移除 Cookie 请求头，防止 Cookie 值从客户端应用程序（例如 Web 浏览器）发送到远程服务器。从响应中删除 Set-Cookie 请求头，防止请求设置客户端应用程序从远程服务器接收的 Cookie。

#### 如果不小心点击拒绝了或者没有出现授权弹窗怎么办 ？

点击导航栏上面的 Proxy->Access Contorl Settings->Add 添加手机 ip
![](http://wx2.sinaimg.cn/mw690/006Fw6Kwly1g2tzc8bjgej30to0l0dxj.jpg)

![](http://wx2.sinaimg.cn/mw690/006Fw6Kwly1g2tzc8bjgej30to0l0dxj.jpg)

![](http://wx3.sinaimg.cn/large/006Fw6Kwly1g2u4zgkmxvj30qw0nugp4.jpg)

![](http://wx3.sinaimg.cn/large/006Fw6Kwly1g2u4zpo146j31g70u0tnf.jpg)

#### charles 如何修改默认端口号 8888

点击导航栏上面的 Proxy->Proxy Setting

![](http://wx3.sinaimg.cn/mw690/006Fw6Kwly1g2tzm7f3lgj30x20sawi1.jpg)
