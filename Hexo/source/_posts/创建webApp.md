---
title: 构建WebApp
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
在.umirc.js 下添加插件，这样不用引入antd-mobile 的css 样式了
extraBabelPlugins: [['import', { libraryName: 'antd-mobile', style: true }]],
```

### 在 index.js 添加一个 Antd Mobile 按钮

```
import styles from './index.css';
//引入组件
import { Button, WingBlank } from 'antd-mobile';

export default function() {
return (
<div className={styles.normal}>
<div className={styles.welcome} />
<ul className={styles.list}>
<li>
To get started, edit <code>src/pages/index.js</code> and save to reload.
</li>
<li>
<a href="https://umijs.org/guide/getting-started.html">Getting Started</a>
</li>
</ul>

//添加按钮
<WingBlank>
<Button type="primary">hello world</Button>
</WingBlank>
</div>
);
}

```

![](http://wx4.sinaimg.cn/mw690/006Fw6Kwly1g3xagex0wej30jo108afv.jpg)
编辑 : Allen
