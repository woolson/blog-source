---
title: wepy框架使用问题记录
date: 2018-11-12 14:32:01
categories:
  - 笔记
tags:
  - 前端
---

`wepy`是目前相对来说比较好用的一个小程序开发框架。由于`wepy`框架还不够完善，开发过程中各种坑需要踩，这里记录笔记、遇到的问题和解决的方式。

{% centerquote %}**文中提到的方式可能不是最好的，可以在评论中给出您的方法**{% endcenterquote %}

<!-- more -->

# 1. 背景图片background-image

<span class="label danger">问题描述</span>

官方 `.wxss` 文件中 `background-image` 属性只支持使用**网络图片链接**和**base64图片编码**，**不支持**使用本地图片路径！

<span class="label success">解决方法</span>

1. 在 `.wxml` 文件中使用内联样式
  ```html
  <template>
    <view style="background-image: url(./background.png)"></view>
  </template>
  ```
2. 把图片转成base64编码，缺点是转换后会很长。[图片转base64工具](http://tool.chinaz.com/tools/imgtobase)

# 2. 不支持在wx:for中使用函数

<span class="label danger">问题描述</span>

不支持在`wx:for`格式化数据（不可用过滤器）

```html
<template>
<view>
  <view wx:for="{{list}}">
    <text>{{formatDate(item.createTime)}}</text>
  </view>
</view>
</template>
```

```js
<script>
import wepy from 'wepy'
import { date } from '@/plugins/utils'

export default class HomePage extends wepy.page {
  data = {
    list: [
      { createTime: 1542004971512 },
      { createTime: 1542004971211 }
    ]
  }

  methods = {
    formatDate (createTime) {
      return date(createTime).format('YYYY-MM-DD HH:mm:SS')
    }
  }
}
</script>
```

<span class="label success">解决方法</span>

1. 在使用数据之前就把数据给格式化好
2. 使用`wxs`模式`vuejs`中的过滤器
3. 比较复杂的格式化可以考虑使用组件来解决

# 3. 设置backgroundColor无效

<span class="label danger">问题描述</span>

修改`app.wpy`文件中的`window.backgroundColor` 或页面 `config.backgroundColor` 颜色不起效果

<span class="label success">解决方法</span>

其实这个 `backgroundColor` 是设置下拉加载的时候，窗口下移露出 `loading` 的背景色而不是整个页面的背景色
