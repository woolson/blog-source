---
layout: post
title: 减少nvm对shell启动速度的影响
date: 2018-07-02 20:00
categories:
  - 原创
tags:
- 笔记
---

> 从事前端开发或者 `nodejs` 开发，难免遇到 `nodejs` 多版本切换。如果使用官方的 `pkg` 安装的话，切换版本比较麻烦。目前有两个比较热门的版本切换工具: `n` 和 `nvm`。

<!-- more -->

# 问题

使用 `nvm` 后，发现一个问题，每次创建一个新窗口的时候，发现shell启动的比较慢。查看[github](https://github.com/creationix/nvm/issues/539)的 `issue` 后作者解释就是创建的时候受 `nvm.sh` 的影响，在脚本中 `nvm use default` 版本这一步比较耗费时间。

# 解决

所以作者建议对启动速度比较在意的人，在 `"$NVM_DIR/nvm.sh"` 后面加上 `--no-use`设置以禁止启动的时候 `nvm use default` 减少启动的速度。但是这样造成在用node之前需要先`nvm use ` 这样执行一下。查看了 `nvm` [github](https://github.com/creationix/nvm/issues/539) 有个大神建议修改配置如下：

```shell
# nvm
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" --no-use # This loads nvm

alias node='unalias node ; unalias npm ; nvm use default ; node $@'
alias npm='unalias node ; unalias npm ; nvm use default ; npm $@'
```

启动时`--no-use` 在你使用 `node` 命令的时候在去做 `nvm use default` 操作。666