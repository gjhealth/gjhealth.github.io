---
title: Hexo 多端协同
date: 2019-02-01 13:42:37
tags: 工具
---

### 安装环境

~~~bash
git clone -b Hexo  git@github.com:gjhealth/gjhealth.github.io.git

cd gjhealth.github.io/Hexo

npm install

hexo --help
~~~

### 编写博客

~~~bash

git pull

hexo new "hello world" //创建一篇博客,markdown 在/Hexo/source/_posts 路径下

git add .

git commit -m "发布博客"

git push

hexo d //发布

//如果没有更新可以先
hexo clean 

~~~