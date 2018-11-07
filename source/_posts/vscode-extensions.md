---
layout: post
title: VS-Code插件推荐
date: 2018-06-08 20:00
top: true
tags:
  - 笔记
---

U：“你用过最强大的编辑器是什么？”
M：“Sublime Text”
U：“你用过最好看的编辑器是什么？”
M：“Atom”
U：“你用过最方便的编辑器是什么？”
M：“Visual Studio Code”

&ensp;&ensp;&ensp;&ensp;曾经 `Atom` 的外观让我着迷，就算加载速度比较慢，我还是用了很
长一段时间。但是自从用上了 `VS-code`再也回不去 `Atom` 了，就算他看上去不是那么好看。但
是他的启动速度和插件的质量，相对来说有一定的优势的。还有一些细节上面的配置更友好。

下面就推荐一些我个人觉得不错的插件：

## Gitlens

<p align="center">
  <img src="https://raw.githubusercontent.com/eamodio/vscode-gitlens/master/images/gitlens-logo.png" alt="GitLens Logo" width="328"/>
</p>

> 主要是组织git提交记录并在你的代码中展示修改人和修改时间，很强大

![gitlens](https://raw.githubusercontent.com/eamodio/vscode-gitlens/master/images/gitlens-preview.gif)

## Vim

<p align="center">
  <img src="https://raw.githubusercontent.com/VSCodeVim/Vim/master/images/icon.png" height="128" width="128">
  <br>VS-Code Vim模拟器
</p>

> 喜欢用vim编辑器的同学必须装的，挺不错的。推荐加一个插件 `line-jumper`

## Line-jumper

&ensp;&ensp;&ensp;&ensp;vim有翻半页和一页的快捷键。有时候vim的翻半页或者翻一页太多，但是一行一行翻又太慢。所以有个能介于半页和一行之间的跳行。就使用line-jumper这个插件，可配置一次跳多少行，我是5行。

```json
// 行数设置
{
  "lineJumper.linesToJump": 5
}
```

```json
// 快捷键设置
[
  {
    "key": "ctrl+j",
    "command": "lineJumper.moveDown",
    "when": "editorTextFocus"
  },
  {
    "key": "ctrl+cmd+j",
    "command": "lineJumper.selectDown",
    "when": "editorTextFocus"
  },
  {
    "key": "ctrl+k",
    "command": "lineJumper.moveUp",
    "when": "editorTextFocus"
  },
  {
    "key": "ctrl+cmd+k",
    "command": "lineJumper.selectUp",
    "when": "editorTextFocus"
  }
]
```

![line-jumper](https://github.com/alekseychaikovsky/vscode-linejumper/raw/master/images/demo.gif)

## Beautify

<p align="center">
  <img src="https://hookyqr.gallerycdn.vsassets.io/extensions/hookyqr/beautify/1.3.0/1516928994563/Microsoft.VisualStudio.Services.Icons.Default" height="128" width="128">
  <br>代码格式化插件 Beautify
</p>

> 代码格式化插件，不用多说。

## EditorConfig for VS Code

<p align="center">
  <img src="https://editorconfig.gallerycdn.vsassets.io/extensions/editorconfig/editorconfig/0.12.4/1527781734664/Microsoft.VisualStudio.Services.Icons.Default" height="128" width="128">
  <br>编辑器设置
</p>

> 如果你打开的项目根目录存在 `editorconfig` 文件，则会用文件中的配置覆盖编辑器默认设置

```config
# editorconfig.org
root = true

[*]
indent_size = 2
indent_style = tab
end_of_line = lf
charset = utf-8
trim_trailing_whitespace = true
insert_final_newline = true

[*.md]
trim_trailing_whitespace = false
```

## Guides

<p align="center">
  <img src="https://spywhere.gallerycdn.vsassets.io/extensions/spywhere/guides/0.9.1/1511022656558/Microsoft.VisualStudio.Services.Icons.Default" height="128" width="128">
  <br>编辑器缩进导航
</p>

> 用来扩展编辑器缩进导航显示，可以自定义的样式也很多

![官方](https://github.com/spywhere/vscode-guides/raw/master/images/screenshot.png)

自定义样式  

![](http://ww1.sinaimg.cn/large/708e7d29gy1fs6i2zird5j219o0kcjx5)

```js
{
  // 暗色系主题使用的活动状态引导线颜色
  "guides.active.color.dark": "rgba(120, 60, 60, 0.75)",
  // 明色系主题使用的活动状态引导线颜色
  "guides.active.color.light": "rgba(200, 100, 100, 0.75)",
  // 是否使用活动引导线
  "guides.active.enabled": true,
  // 是否在括号行展开活动引导线
  "guides.active.expandBrackets": true,
  // 水平引动引导线，这将会渲染出多余的引导线
  "guides.active.extraIndent": false,
  // 除正常引导线，在沟槽区启用活动引导线指示器
  "guides.active.gutter": false,
  // 选中文字隐藏引导线
  "guides.active.hideOnSelection": true,
  // 活动状态引导线样式
  "guides.active.style": "solid",
  // 活动状态引导线宽度
  "guides.active.width": 1,
  // 启用此插件
  "guides.enabled": true,
  // 缩进背景颜色
  "guides.indent.backgrounds": [],
  // 选中文字隐藏引导线背景
  "guides.indent.hideBackgroundOnSelection": true,
  // 是否显示第一列引导线
  "guides.indent.showFirstIndentGuides": true,
  // 基于当前光标位置最大渲染数. 设置-1为无限制. 使用浮点数0-1之间由文档大小来确定
  "guides.limit.maximum": 500,
  // 暗色系普通引导线颜色
  "guides.normal.color.dark": "rgba(60, 60, 60, 0.75)",
  // 明色系普通引导线颜色
  "guides.normal.color.light": "rgba(220, 220, 220, 0.75)",
  // 开启普通引导线
  "guides.normal.enabled": true,
  // 选中文字隐藏普通引导线
  "guides.normal.hideOnSelection": true,
  // 普通引导线样式
  "guides.normal.style": "solid",
  // 普通引导线宽度
  "guides.normal.width": 1,
  // 覆盖vs-code默认的行为(比如：缩进引导线和尺寸线)
  "guides.overrideDefault": false,
  // 发送匿名使用统计数据给开发者
  "guides.sendUsagesAndStats": true,
  // 暗色系主题缩进引导线堆栈颜色
  "guides.stack.color.dark": "rgba(80, 80, 80, 0.75)",
  // 明色系主题缩进引导线堆栈颜色
  "guides.stack.color.light": "rgba(180, 180, 180, 0.75)",
  // 除正常引导线外显示堆栈引导线
  "guides.stack.enabled": true,
  // 选中文字隐藏堆栈引导线
  "guides.stack.hideOnSelection": true,
  // 堆栈引导线样式(solid/dashed/dotted)
  "guides.stack.style": "solid",
  // 堆栈引导线宽度
  "guides.stack.width": 1,
  // 引导线间更新间隔(单位：秒)
  "guides.updateDelay": 0.1
}
```

![indent](http://ww1.sinaimg.cn/large/708e7d29gy1fs3yfw1ojcj21860b8aby)

## Material Icon Theme

<p align="center">
  <img src="https://pkief.gallerycdn.vsassets.io/extensions/pkief/material-icon-theme/3.5.0/1527764102171/Microsoft.VisualStudio.Services.Icons.Default" height="128" width="128">
  <br>资源管理器中文件图标
</p>

> 该插件提供了大量的图标，还可以自己自定义图标。


```json
//  自定义文件夹图标
{
  "material-icon-theme.folders.associations": {
    // 文件夹名：图标名
    "store": "Redux-store"
  }
}
```

![icon](https://raw.githubusercontent.com/PKief/vscode-material-icon-theme/master/images/fileIcons.png)

## Vetur

<p align="center">
  <img src="https://octref.gallerycdn.vsassets.io/extensions/octref/vetur/0.12.5/1528324426695/Microsoft.VisualStudio.Services.Icons.Default" height="128" width="128">
  <br>Vetur 用vue开发必装插件
</p>

> 如果你是VUE的使用者，这个插件必选啊

## 推荐主题：github plus

<p align="center">
  <img src="https://thenikso.gallerycdn.vsassets.io/extensions/thenikso/github-plus-theme/1.1.3/1526373532357/Microsoft.VisualStudio.Services.Icons.Default" height="128" width="128">
  <br>Github Plus Theme
</p>

> 以前都是喜欢用暗色系的主题，久了后想换个亮一点的主题，然后找了一圈，这个主题真是超级喜欢。

![github](https://github.com/thenikso/github-plus-theme/raw/master/screenshot.jpg)

## 完事

&ensp;&ensp;&ensp;&ensp;插件暂时介绍到这，后面有好用的再做推荐。这里推一个自己开发的基于新浪微博上传图片软件（有mac和win），具体查看[这里](https://woolson.github.io/weibo-img/#/)。

<p align="center">
  <img src="https://woolson.github.io/weibo-img/static/img/etc-1.4fce764.png" width="650">
</p>

# 2018-07-31更新

## Todo Tree

<p align="center">
  <img src="https://gruntfuggly.gallerycdn.vsassets.io/extensions/gruntfuggly/todo-tree/0.0.73/1532952758588/Microsoft.VisualStudio.Services.Icons.Default" height="128" width="128">
  <br>Todo Tree
</p>

> 列出项目中所有的TODO，侧面把握项目的完成度。点击可打开对应文件和TODO所在位置。

![官方](https://raw.githubusercontent.com/Gruntfuggly/todo-tree/master/resources/screenshot.png)

## TODO Highlight

<p align="center">
  <img src="https://wayou.gallerycdn.vsassets.io/extensions/wayou/vscode-todo-highlight/1.0.4/1532254554587/Microsoft.VisualStudio.Services.Icons.Default" height="128" width="128">
  <br>TODO Highlight
</p>

> 高亮打开的页面中所有TODO，看上去更清爽。

![官方](https://github.com/wayou/vscode-todo-highlight/raw/master/assets/material-night.png)