title: Google搜索之高级使用篇
author: 有毒
tags:
  - google
  - hacking
categories:
  - hacking
date: 2017-02-06 16:06:00
---
###### 基础篇：
> * intitle：搜索网页标题中包含有特定字符的网页。例如`intitle: 后台`，这样网页标题中带有‘后台’的网页都会被搜索出来。
> * inurl：搜索包含有特定字符的URL。例如`inurl:admin`，可以用来查找网站后台。
> * intext: 搜索网页正文内容中的指定字符，例如`intext:操作系统`。可以搜索含有‘操作系统’的页面
> * Filetype: 搜索指定类型的文件。例如`操作系统　filetype:pdf`，就可以找到关于操作系统的pdf文档。
> * Site：找到与指定网站有联系的URL。例如`Site：baidu.com`。所有和这个网站有联系的URL都会被显示。
> * movie: 当我们用movie提交查询的时候，Google会返回跟查询关键词相关的电影信息。(当前只支持英文Google)
> * info: 查询网站的一些信息。例如`info:bbs.byr.cn`，它只会返回一个结果，是一个选择列表，列表的选项是这个网站的某一方面的信息。info=cache+related+link+site+intext+intitle。
> * 双引号: 代表完全匹配，使关键词不分开，顺序都不能变。
> * 减号: 减号与前一个关键词之间一定要有一个空格，与后一个关键词之间一定不能有空格。搜索结果为，匹配前一个关键词但不匹配后一个关键词的结果。例如`seo -搜索引擎`。
> * AND: 逻辑与，这个命令我们其实一直都在用，只是没有意识到。一般用空格代替，还可以用“+”代替。例如`霹雳布袋+败亡之剑`，返回的结果同时包含两者。
> * weather: 查询某一地区或城市的天气。不过我们这一地区或城市必须是Google能识别的，例`weather:beijing`，Google将会给我们返回北京的天气。
> * 星号（\*）: 通配符，可以匹配任意字符串。例如`搜索*擎`，则返回的结果中不仅有“搜索引擎”，还有“搜索巨擎”之类的。
> * allinurl: 结果的url中包含多个关键词。例如`allinurl:byr jobs`，等于inurl:byr inurl:jobs。allinurl也是排他性指令
> * define: 查询关键词的词义，起的是字典的作用。Google会返回包含查询关键词定义的网页，例`define:computer`，支持汉字哦！



###### 进阶篇：

> * 查找后台地址：site:域名
inurl:login|admin|manage|member|admin_login|login_admin|system|login|user|main|cms
> * 查找文本内容：site:域名 intext:管理|后台|登陆|用户名|密码|验证码|系统|帐号|admin|login|sys|managetem|password|username
> * 查找可注入点：site:域名 inurl:aspx|jsp|php|asp
> * 查找上传漏洞：site:域名 inurl:file|load|editor|Files
> * 查看脚本类型：site:域名 filetype:asp/aspx/php/jsp
> * 迂回策略：inurl:cms/data/templates/images/index/
> * 网络设备关键词：intext:WEB Management Interface for H3C SecPath Series
> * 存在的数据库：site:域名 filetype:mdb|asp|#