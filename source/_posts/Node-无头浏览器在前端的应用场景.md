---
layout: post
title: 无头浏览器在前端的应用场景
date: 2020-10-21 15:55:35
categories: Node.js
---

> 无头浏览器 from wikipedia： A headless browser is a web browser without a graphical user interface。无头实际上是指无界面地运行浏览器
我们在终端或者代码层，使用无头浏览器的技术来可以模拟用户在网页端的浏览及操作。

<!-- more -->

# 一、无头浏览器的相关应用
1. E2E 测试：无需打开UI界面，即可完成对应的测试内容。模拟表单提交，键盘输入，点击等行为
2. 网络爬虫 、SSR 服务端渲染
3. 网页截图生成海报或  PDF
4. 捕获网站时间线，帮助诊断性能问题（Lighthouse 就是使用了无头浏览器的技术的性能测量工具，他可生成各种性能数据以及网页加载时的快照，以辅助前端做一些性能优化

以上，无头浏览器的作用非常强大；今天就以 posterMan 这个比较简单但是很有代表性的服务，来讲一下在前端的具体应用。

# 二、posterMan 简介

类似于网抑云音乐，知乎的划线笔记。用户在截屏时可以生成封面海报。

<center><img src="/images/poster.jpg" width="320px" /></center>

posterMan 是一个 Node 服务。当我们提供一个 url 链接给到 posterMan 时，即可生成相应的封面截图。

## 2.1 海报生成链路

<center><img src="/images/link.png" width="640px" /></center>

## 2.2 Puppteer 相关介绍

> 译：木偶；基于 CDP（Chrome devtools-protocol） 封装的 Node 库

原理:

1. 基于 WebSocket，利用 WebSocket 实现与浏览器内核的快速数据通道；
2. CDP 分为多个域，每个域中都定义了相关的命令和事件（Commands and Events）；
3. 基于 CDP 封装一些工具对 Chrome 浏览器进行调试及分析。

## 2.3 Puppeteer VS Phantomjs

<table style="width:100%">
  <tr>
    <th></th>
    <th>puppeteer</th>
    <th>phantomjs</th>
  </tr>
  <tr>
    <td>环境依赖</td>
    <td>依赖 Node</td>
    <td>Linux: GLIBCXX_3.4.9 和 GLIBC_2.7</td>
  </tr>
  <tr>
    <td>更新进度</td>
    <td>持续更新（V1.8）</td>
    <td>停止更新（V2.1）</td>
  </tr>
  <tr>
    <td>JavaScript 标准</td>
    <td>新的ES 标准</td>
    <td>ES5</td>
  </tr>
  <tr>
    <td rowspan="3">整体优点</td>
    <td>持续更新，功能性能可期</td>
    <td>部署快捷方便，基本上达到了开箱即用</td>
  </tr>
  <tr>
    <td>使用新ES标准，对异步事件处理更简便</td>
    <td>脚本语言更适合原生开发，学习成本低</td>
  </tr>
  <tr>
    <td>支持chrome插件</td>
    <td></td>
  </tr>
  <tr>
    <td rowspan="3">整体缺点</td>
    <td>部署相对复杂，且需要翻墙</td>
    <td>已经停更</td>
  </tr>
  <tr>
    <td>Java 端调用仍需使用 CMD 和 Shell 调用，Node 端可直接使用</td>
    <td>只能通过 CMD 和 Shell 调用</td>
  </tr>
  <tr>
    <td></td>
    <td>开放的 api 较少, 且调试过程复杂</td>
  </tr>
</table>

## 2.4 Puppeteer 模拟用户操作

<center><img src="/images/op.png" width="640px" /></center>

## 2.5 链接池 Generic pool

当用户访问调用 posterMan 时，就会创建一个 Puppteer 的实例子，但是当我们的服务访问量巨大的时候，频繁的创建和销毁连接会产生非常大的系统开销。这个时候，链接池 Generic pool 就隆重登场了。

### 2.5.1 线程池-合理配置

<center><img src="/images/pool.png" width="300px" /></center>

1. 合理设置连接池数；posterMan 阈值（min：2；Max：10）;
2. 尽可能利用缓存，减少对数据库的查询；
3. 使用完一个数据库连接后，尽快释放给管理池。


# 三、纯前端实现

## 3.1 利用CanvasAPI （html2Canvas）

1. 递归取出目标模版的所有 DOM 节点，填充到一个 rederList，并附加是否为顶层元素/包含内容的容器 等信息
2. 通过 z-index postion float等css属性和元素的层级信息将 rederList 排序，计算出一个 canvas 的 renderQueue
3. 遍历 renderQueue，将 css 样式转为 setFillStyle 可识别的参数，依据 nodeType 调用相对应 canvas 方法，如文本则调用 fillText，图片 drawImage，设置背景色的 div 调用 fillRect 等
4. 将画好的canvas填充进页面

缺点：

1. 无法渲染跨域资源(支持同域)
2. 无法渲染 iframe和 Flash 内容
3. 大量的递归和计算会非常缓慢

## 3.2 SVG

1. 首先，我们要声明一个基础的svg模版，这个模版需要一些基础的描述信息，最重要的，它要有<foreignObject></foreignObject>这对标签
2. 将要渲染的 DOM 模版模版嵌入 foreignObject
3. 利用 Blob 构建 SVG 图像
4. 取出 URL

一个最为严肃的问题在于：SVG 无法加载外部资源，也就是说，在 SVG 里面，无论是还是 或者 CSS 中的背景图, 这些资源都是无法加载的。在使用 canvas 实现时，因为我们使用 Node 去绘制，所以不存在资源引用的问题。但使用 SVG  实现，相当于我们把文档交给 SVG 再来渲染，这对于我们来说是其实是无法控制的黑盒操作，是受 SVG 限制的。

<center>
	<img src="/images/diff.png" width="700px" />
</center>
