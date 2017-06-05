---
layout: post
title:  "解决svg中的image元素在safari中不能显示的问题"
date:   2017-06-05
categories: Safari svg
tags: Safari svg
author: oops
---

* content
{:toc}

因业务需要，在svg中使用image标签，通过href属性引入图片url，发现Safari浏览器(版本10.1.1)无法正常显示这个url所指向的图片，代码片段如下：
```
<image x="300" y="600" width="20" height="20" href="imageUrl"></image>
```
href是SVG 2的标准属性，而我引用的svg图片使用的是SVG 1.1规范，为更大程度地保障浏览器兼容，需要用较旧的xlink:href属性代替，尽管SVG 2规范中已经移除了xlink:href。
```
<image x="300" y="600" width="20" height="20" xlink:href="imageUrl"></image>
```
## 参考资料
* [StackOverflow - Svg image element not displaying in Safari
](https://stackoverflow.com/questions/27245673/svg-image-element-not-displaying-in-safari){:target="_blank"}
* [W3C WIKI - SVG Links](https://www.w3.org/wiki/SVG_Links){:target="_blank"}
* [MDN - SVG Attribute xlink:href](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/xlink:href){:target="_blank"}
* [MDN - SVG Attribute href](https://developer.mozilla.org/en-US/docs/Web/SVG/Attribute/href){:target="_blank"}