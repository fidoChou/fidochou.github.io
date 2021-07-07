---
layout: post
title: iFrame
date: 2019-01-30 20:12:44
categories: 前端相关
---

#  确定
  * iframe会阻塞主页面的Onload事件；
  * 搜索引擎的检索程序无法解读这种页面，不利于SEO;

  * iframe和主页面共享连接池，而浏览器对相同域的连接有限制，所以会影响页面的并行加载。

  使用iframe之前需要考虑这两个缺点。如果需要使用iframe，最好是通过 javascript
  动态给iframe添加src属性值，这样可以绕开以上两个问题。
