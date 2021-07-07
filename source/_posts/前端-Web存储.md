---
layout:
title: Web 的存储
date: 2019-01-29 12:46:47
tags: 混合开发
categories: 前端相关
---

# 客户端Cookie
## 优点
1. 通过良好的编程，控制保存在cookie中的session对象的大小。
2. 通过加密和安全传输技术（SSL），减少cookie被破解的可能性。
3. 只在cookie中存放不敏感数据，即使被盗也不会有重大损失。
4. 控制cookie的生命期，使之不会永远有效。偷盗者很可能拿到一个过期的cookie。

## 确定
 1. `Cookie`数量和长度的限制。每个domain最多只能有20条cookie，每个cookie长度不能超过4KB，否则会被截掉。
2. 安全性问题：如果cookie被人拦截 ,他只要原样转发cookie就可以达到目的了。邮箱
3. 隐私问题：隐私浏览模式，浏览器关闭之后，期间所有的 cookie 都消失。
4. 

#  服务器端 Session
与盗取用户名、密码登陆用户帐户的方式有所不同，Session劫持是一种通过窃取用户的SessionID，使用该SessionID登录目标账户的攻击方法。此时攻击者实际上是使用了目标账户的有效Session。如果SessionID是保存在Cookie中的，则这种攻击可以成为Cookie劫持。

#  Webstorage
不与服务器又交互

localStorage

sessionStorage


