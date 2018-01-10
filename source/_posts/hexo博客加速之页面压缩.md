title: hexo博客加速之页面压缩
author: 有毒
tags:
  - hexo-next
  - hexo页面压缩
categories:
  - 博客
date: 2017-02-17 14:57:00
---

######  hexo博客页面大量留白原因
因为markdown转html的bug，致使生成的html留有大量的空白，十分的难看，另外就是由于性能原因，需要对js和css进行压缩。

###### 寻求改善方法
在网络的海洋里搜寻好久，终于找到了一个hexo插件`hexo-neat`。
作者在此：https://segmentfault.com/a/1190000005799759

###### 配置方法
1、下载方法：`npm install hexo-neat --save`

2、在博客的站点配置文件中添加如下配置：
```
##hexo-neat页面压缩
neat_enable: true 
neat_html:
  enable: true
  exclude: 
neat_css:
  enable: true
  exclude:
    - '*.min.css'
neat_js:
  enable: true
  mangle: true
  output:
  compress:
  exclude:
    - '*.min.js'  ```
启用hexo-neat的基础上，可以选择是否压缩HTML、CSS、Js文件，均有相应的开关选项。    
3、配置完成后生成博客就行。