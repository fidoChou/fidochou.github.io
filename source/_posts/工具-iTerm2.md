---
layout: iterm
title: iTerm2
date: 2020-05-11
categories: 工具
---
iTerm2 是我常用的终端工具，每次换电脑安装的第一个软件就是它。青睐于 iTerm 的原因很简单：

<!-- more -->

1. 支持分屏模式
2. 可配置插件
3. 颜值 online

I love this black cat background！

<img src="/images/iterm.png"  width="500px"/>

# Shell 冷知识

前端开发往往不关心 *nix 内核。Shell 仅仅只是一个「壳」而已。我们借助 Shell 和内核打交道。Mac 自带终端的 Shell 是 bash。常见的 Shell 有 sh、bash、zsh、csh

通过

```
cat /etc/shells
```

可以查看安装
<img src="/images/cat.png"  width="300px"/>

# zsh
## 手动安装
```sh
git clone git://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
chsh -s /bin/zsh
```

换回bash

```sh
chsh -s /bin/bash
```

## 自动安装
```sh
wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | sh
```

# 配置

## 必备插件
[ohmyzsh](https://github.com/ohmyzsh/ohmyzsh)
itermpreference.png

内置了 git 的插件管理 还有一些漂亮的主题，这里不在赘述

## 快捷键

对于日常开发我常用分屏模式，已经能够满足对于多个窗口的诉求

command + D
command + shift + D

### 默认打开工作区


在 preference 的设置里面，我勾选了 Reuse previous session‘s directory。

<img src="/images/itermpreference.png"  width="300px"/>

这样每次打开都是从上一个工作区切出来的目录，这对于一个项目需要启动多个端口来说非常友好。

### open Buff

其实这算事 iTerm 的一个 Buff，我给 ~/.zshrc 配置了 open 命令的别名：

<img src="/images/itermalias.png"  width="300px"/>

这使得我可以使用终端快速打开文件。据我所知 atom 自带了 atom 命令来实现这个效果，但是我更倾向于自己 DIY，而不是依赖 IDE。这也是我选择 sublime 的原因。

```sh
	subl {path}
```

### 颜值 Buff

做为一只颜狗，我给 iTerm2 配置了背景图，并且设置了默认的行列数，以减少手动放大 iTerm2。

<img src="/images/itermbg.png"  width="300px"/>
