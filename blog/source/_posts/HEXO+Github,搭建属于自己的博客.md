---
title: HEXO+Github,搭建属于自己的博客
permalink: HEXO+Github,搭建属于自己的博客
comments: true
date: 2016-08-08 13:00:00
toc: true
tags:
   - hexo
description: 
---

&emsp;&emsp;HEXO+Github,搭建属于自己的博客
<!-- more -->
### HEXO+Github,搭建属于自己的博客

#### 了解 Hexo

> A fast, simple & powerful blog framework

[Hexo](https://hexo.io/) 是一个快速、简洁且高效的博客框架。Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。
[Hexo官方文档](https://hexo.io/zh-cn/docs/setup.html)

#### 安装 Git
Linux (Ubuntu, Debian):
```
sudo apt-get install git-core
``` 
Linux (Fedora, Red Hat, CentOS):
```
sudo yum install git-core
```
#### 安装 Node.js

安装 Node.js 的最佳方式是使用 nvm。

```
curl https://raw.github.com/creationix/nvm/master/install.sh | sh
```
Wget:
```
wget -qO- https://raw.github.com/creationix/nvm/master/install.sh | sh
```
安装完成后，重启终端并执行下列命令即可安装 Node.js。
```
nvm install 4
```
#### 安装 Hexo
所有必备的应用程序安装完成后，即可使用 npm 安装 Hexo。

```
npm install -g hexo-cli
```
#### 建站

安装 Hexo 完成后，请执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。

```
$ hexo init <folder>
$ cd <folder>
$ npm install
```

新建完成后，指定文件夹的目录如下：

```
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```
##### 新建一篇文章

``` hexo new [layout] <title>```
如果没有设置 layout 的话，默认使用 _config.yml 中的 default_layout 参数代替。如果标题包含空格的话，请使用引号括起来。

##### 生成静态文件

``` hexo generate```

#####启动服务器

``` hexo server```
网站会在 http://localhost:4000 下启动。在服务器启动期间，Hexo 会监视文件变动并自动更新，您无须重启服务器。

#### 部署静态网页到 GitHub
##### 注册设置 GitHub

>登录GitHub，注册自定义用户名如：xueqy
>在主页右下角创建New repository，name必须和用户名一致如：xueqy.github.io
>首次创建耐心等待10分钟左右审核，之后即可访问静态主页如：http://xueqy.github.io
##### 同步内容至 GitHub

>在Hexo目录下 git clone git@github.com:/xueqy.github.io.git
>将public文件下的所有文件拷贝到xueqy.github.io下
>git add .增加当前子目录下所有更改过的文件至index
>git commit -m 'xxx'提交到本地
>git push origin master将当前分支push到远程master分支
>最后访问主页http://xueqy.github.io观察效果
####个人域名
##### 设置 CNAME

>在Github的网站目录下创建CNAME文件
>填写自己的域名如xueqy.top，保存结束
>登录域名服务商，然后添加记录，记录类型选择CNAME，记录值xueqy.github.io.(有个点)
