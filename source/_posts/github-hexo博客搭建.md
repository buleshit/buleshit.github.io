title: github+hexo博客搭建
author: 有毒
tags:
  - hexo
  - github
  - next主题
categories:
  - 博客
date: 2017-01-18 22:48:00
---
写这篇博文并不是为了记录操作步骤，因为步骤确实很繁琐，并且偏向个人爱好的配置居多，无法面面俱到。本篇博文主要记录自己搭建过程中遇到的坑，然后给小白提供下方向和经验。

###### 一、git和nodejs等组件的下载与安装

1、git下载安装,下载对应平台的git安装包，cmd中测试git --version ，如果不识别命令，请将git安装目录添加至系统环境变量。

**下载地址**：https://git-scm.com/downloads

2、node.js下载安装，安装完成后，cmd中输入node -v,如果不能打印当前node版本号即不识别node命令，则请将node的安装目录添加到系统环境变量。

**下载地址**：https://nodejs.org/en/

3、安装hexo,在cmd中输入 npm install hexo （npm是node的包管理工具，如果此处无法识别npm命令，请检查node的环境变量配置或命令行进入到node的安装目录执行次命令。
安装报错，如下：
<!--more-->
npm warn deprecated swig@1.4.2 This package is no longer maintained.(此处应该张图，还没找到合适方式强入)。

百度得知，是因为下载源不可用，找了个镜像源，地址如下：
http://npm.taobao.org/
具体使用说明，上述网址内有描述，我们这里就用：
    npm install -g hexo --registry=https://registry.npm.taobao.org
安装完成。

###### 二、本地博客创建与测试

1、新建个存放博客文章的目录文件夹，在cmd中进入该目录，输入hexo init ,完成初始化（下载相关配置和依赖）

 又报了和上面一样的问题而终止了、、、。百度搜索了一通没找到对应原因，只好硬着头皮继续了。
输入npm install，结果报错。然后跳过输入hexo server 启动服务，显示本地服务启动成功！！！
（实在不知道前面的报错是什么鬼，有人知道的话，希望能告知下，不吝感激）。

2、打开浏览器，输入地址(http://localhost:4000/)回车之后就打开我们的博客了。到这步，我们的博客基本已经完成了，但是还能在本地使用。  

###### 三、上传到github

1、先注册github，创建新的仓库，命名为your_user_name.github.io。
2、建立本地仓库与github仓库的联系。进入本地博客目录，打开站点配置文件_config.yml文件，修改对应位置为：
<pre>
  deploy: 
    type: git
    repository: https://github.com/buleshit/buleshit.github.io.git
    branch: master
    message: update
</pre>

这里有两个重要的参数：（其他两个参数可以参照着写） 
1）type：Hexo之前的版本好像是填github，但是Hexo3.0之后，必须填git，我的Hexo是最新的3.2.2，填写git。 
2）repository这个参数，很重要，它就是用来链接我们在github上创建的创库。看网上有的人使用SSH，但是SSH配置起来相对有些复杂，我这里用的是HTTPS方式，网上借鉴的方法。

3、接下来就是将博客发布到远端：

    npm install hexo-deployer-git --save
    hexo clean
    hexo g
    hexo d

此时，应该会弹出输入用户名和密码的对话框，正确输入github的账户和密码。完成后会打印Deploy done:git，打开浏览器输入（https://your_user_name.github.io） ,回车后打开你的个人博客站点。

4、后面还可以自己购买域名，设置DNS，来优化我们的博客，让其显得高大上些，这里不做赘述。
因为重点是博文质量，其他花哨的东西后面再弄不急。

###### 四、主题及其他优化

关于主题的设置也不想多说了，因为都是自定义的东西，根据自己喜好来。我用的是next的主题，大家可以浏览下。写这篇博客的原因是记录中间遇到的问题，不能面面俱到，相信把关键词给大家，大家按需学习配置就行。关键词如下：
主题配置：设置RSS、添加标签的tags页面、添加分类页面、添加404页面、代码高亮、侧边栏、友情链接、菜单栏等等。
其他三方：多说评论、百度统计、站内搜索、阅读量统计等等。
部分参考链接：
**主题官网**：
https://hexo.io/themes/
**next主题的配置和优化**：
http://blog.csdn.net/willxue123/article/details/50994852
**添加阅读量统计**：
http://www.joryhe.com/2016-05-29-how_to_create_leancloud_read_Counter.html
**添加友情链接**：
http://blog.csdn.net/itmyhome1990/article/details/43489361
http://www.jianshu.com/p/3884e5cb63e5
**访问速度优化**：
http://www.cnblogs.com/jarson-7426/p/5660424.html
http://www.joryhe.com/2016-06-05-hexo_site_seo_speed_more_optimization.html