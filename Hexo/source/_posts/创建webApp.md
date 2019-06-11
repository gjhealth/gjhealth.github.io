---
title: 构建webApp
date: 2019-06-11 12:28:39
tags:
  - HTML
categories:
  - 前端
---

## UmiJS + DvaJS + Ant Mobile 创建 React WebApp

- UI 组件
  [Ant Mobile](https://mobile.ant.design/index-cn)

- 可插拔的企业级 react 应用框架
  [UmiJS](https://umijs.org/zh/)

- 数据流方案
  [DvaJS](https://dvajs.com/guide/)

### 安装 UmiJS

```
yarn global add umi # 或者 npm install -g umi
```

### 新建应用

```
mkdir react_web_app

cd react_web_app

yarn create umi
```

![](http://wx4.sinaimg.cn/large/006Fw6Kwly1g3x7hylimhj310408mwge.jpg)

![](http://wx2.sinaimg.cn/mw690/006Fw6Kwly1g3x7kquznxj310k06yt9e.jpg)

![](http://wx4.sinaimg.cn/mw690/006Fw6Kwly1g3x7jr8u9uj30zk092403.jpg)

```
npm install

npm start
```

### 添加 Antd Mobile

```
npm install antd-mobile --save

npm install babel-plugin-import
```

```
在 package.json 里添加插件

"plugins": [
[
    "import",
    {
     "libraryName": "antd-mobile",
     "style": "css"
    }
]
],
```

编辑 : Allen
