---
title: 《Hexo 多端协同文档》
date: 2019-02-01 13:42:37
tags: 
- 工具 
- 文档
categories: 
- 文档
author: Allen
---



### 安装环境

```bash

cat ~/.ssh/id_rsa.pub //copy公钥添加到github 上

git clone -b Hexo  git@github.com:gjhealth/gjhealth.github.io.git

cd gjhealth.github.io/Hexo

npm install

hexo --help
```

### 编写博客

```bash

git pull

hexo new "hello world" //创建一篇博客,markdown 在/Hexo/source/_posts 路径下

hexo s //本地预览

git add .

git commit -m "发布博客"

git push

hexo d -g //发布

//如果没有更新可以先celan 再hexo d 。浏览器会有缓存，可以清除下缓存在看下是否更新。
hexo clean
```

 编辑 : Allen
