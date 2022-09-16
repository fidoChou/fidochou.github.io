---
layout: post
title: Babel
date: 2020-12-18 16:35:19
categories: 前端
---

最好的学习当然是从看官方文档，如果英文不行那就来份[中文文档](https://www.babeljs.cn/)的 🤦‍♀️

从官方文档来看，总共五个方面：指南、概览、用法、预设以及工具。

# 指南

<!-- more -->

1. 是什么：Babel 的作用是将「先进」的 ES 语法进行降级，编译成较低版本的浏览器能够识别的语法。

#  插件 & 预设

插件的作用就是 translate，预设的作用是启用一组插件

## 短名称
1. 插件 babel-plugin- 可忽略
	eg: babel-plugin-lodash 等同于 lodash

	可适用冠名 @org/

2. 预设 babel-preset- 可忽略
	eg: babel-preset-myPreset 等同于 myPreset

	可适用冠名 @org/

##. 顺序
2. 插件顺序：从左往右

```js
{
  "plugins": ["transform-decorators-legacy", "transform-class-properties"]
}
```

3. 预设顺序：从右往左

```json
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```

## AttachMent

### Polyfills 可按需引入

[loose 参数](https://betgar.github.io/2019/07/30/babel6-loose-mode/)

即松散模式：转换为简单的 ES5 实现。
而严格模式：转换时尽可能遵循、接近 ES6 语义。

可全局配置添加预设，也可给每个 plugin 设置参数


