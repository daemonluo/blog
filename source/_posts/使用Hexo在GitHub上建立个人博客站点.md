---
title: 使用Hexo在GitHub上建立个人博客站点
categories:
    - 写作
tags:
    - hexo
description: 最近使用hexo在github上搭建了个人博客站点，整个过程虽然不是十分复杂，但还是花费了一些时间。作为第一篇博客，正好回顾一下hexo建立博客站点的整个过程
---

### 在Github上创建博客项目
在github上创建一个博客项目，项目名称必须为`{username}.github.io`。其中的`{username}`就是注册github时的用户名。
当博客文章推送到这个项目时，访问`{username}.github.io`，就可以看到自己的博客了。

### 在本地创建博客项目
1. 安装`hexo`
`hexo`是一个nodejs包，所以安装`hexo`之前必须安装nodejs。nodejs的安装可以参考nodejs的[官方网站](https://nodejs.org/zh-cn/)
下面是`hexo`的安装步骤
```bash
$ npm install -g hexo # 安装hexo
$ npm install -g hexo-cli # 安装hexo命令行工具
```
2. 创建一个目录作为博客文件夹
```bash
$ mkdir blog
```
3. 使用`hexo`初始化这个目录
```bash
$ hexo init blog
```
4. 进入该目录，安装一些必要的组件
```bash
$ npm install hexo-renderer-jade --save
$ npm install hexo-renderer-sass --save
$ npm install hexo-deployer-git --save
```
5. 选择主题
在github上选择一款自己喜欢的主题，拉取到本地的themes目录， 然后修改`_config.yml`文件，修改themes的值为该主题。
6. 运行`hexo g && hexo s`，验证博客是否正常。
在浏览器里打开[http://127.0.0.1:4000](http://127.0.0.1:4000)，如果能够看到hello world的博客，就是说明一切正常，接下来就可以自己去写博客了。

### 部署至github
打开`_config.yml`文件，编辑deploy选项，如下所示：
```yml
deploy:
    type: git
    repository: <repository_url>
    branch: master
```
然后运行`hexo deploy`，就可以将该博客部署至github了。


关于Hexo的具体使用可以参考 {% post_link hexo一些常见的使用方法 Hexo一些常见的使用方法 %} 。
