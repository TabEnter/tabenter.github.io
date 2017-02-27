---
layout: post
title:  "macOS Sierra上使用gem install出现Operation not permitted问题的解决方案"
date:   2017-02-24
categories: RubyGems
tags: RubyGems macOS
author: oops
---

* content
{:toc}

昨天开始尝试借助jekyll和Github Pages搭建本博客，为实现本地预览，需安装jekyll。因本地已有ruby和gems环境，遂直接在终端运行
```
sudo gem install jekyll
```
出现错误提示
```
Operation not permitted - /usr/bin/safe_yaml
```
似乎是管理用户权限不够，无法向/usr/bin/目录写入文件所致。

在网络上搜索相关问题，大多数解答都围绕OS X的Rootless设定：即从OS X 10.11起，OS X的Rootless默认enable，部分系统路径即使是root用户也无法执行读写操作，需进入恢复模式将Rootless关闭。然而我先前在使用OS X 10.11时执行sudo gem install从未出现此类错误，对这个解决方案持怀疑态度。经历一番周折，我在[Stack Overflow](http://stackoverflow.com/questions/32891965/error-while-executing-gem-errnoeperm-operation-not-permitted){:target="_blank"}上找到了更加简单且无副作用的解决方案：

手动指定路径
```
sudo gem install -n /usr/local/bin jekyll
```
顺利完成jekyll的安装，且/usr/local/bin路径只需指定一次，随后我安装jekyll-paginate，执行
```
sudo gem install jekyll-paginate
```
不再出现`Operation not permitted`错误。

## memo
国内的淘宝RubyGems镜像已不再维护，迁移到[Ruby China](https://gems.ruby-china.org/){:target="_blank"}，我也是通过这个新镜像安装jekyll和jekyll-paginate的。