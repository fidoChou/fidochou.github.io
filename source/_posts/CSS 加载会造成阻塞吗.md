---
layout: post
title: CSS 加载会造成阻塞吗？
date: 2020-05-25 14:40:32
categories: 前端
---

[原文链接](https://github.com/Nealyang/PersonalBlog/issues/48)

# [👉 CSS 加载会造成阻塞吗](https://juejin.im/post/5b88ddca6fb9a019c7717096)

<!-- more -->

读后感：在浏览器引擎渲染的世界里，简单地将 HTML 呈现给用户的方式分为了两个过程：加载以及渲染。

DOM 树从上至下依次<strike>渲染</strike> 解析。遇到 script 标签时，默认会阻止页面解析并平行下载 JS 文件。所以大部分的文章建议你将 JS 文件放在 body 后面，这样不会影响 HTML 的解析。

属性 `defer` 以及 `async` 不会阻塞页面解析，文档解析完成之后 `defer` 和 `async` 脚本执行。

`defer` 以及 `async` 的区别在于：
`defer` 执行脚本的顺序是加载顺序，而`async`则不能保证顺序。
同时这两个属性都只在外链时生效，即含有 `src` 属性时生效。

在看完文章之后，我再次

# 提问？

既然问题是 CSS 是否会造成阻塞，那么阻塞什么内容呢？

DOM 的解析？DOM 的渲染？JS 的加载？JS的执行？

# 结论
以上我们可以分析出：

1. CSS 的加载并不会阻塞 DOM 的解析
2. CSS 的加载会阻塞 DOM 的渲染
3. CSS 的加载不会阻塞 JS 的加载，JS 加载阻塞和 script 标签的位置以及是否含有 `defer` 和 `async` 属性相关
4. CSS 的加载会阻塞「后面 JS」语句的执行，（DOMContentLoaded 内容解析完成）因为 JS 有可能需要操作前面 DOM 的样式。其他其他情况下，DOMContentLoaded 都不会等待 CSS 加载，并且 DOMContentLoaded 事件也不会等待图片、视频等其他资源加载。
