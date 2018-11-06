---
layout: post
title: React-router 2.X 中使用browserHistory
date: 2016-07-21 19:30
tags:
  - 前端
---

之前开发一直都有使用react-router。使用的hashHistory（看上去有点丑，不简洁）。因为项目都不是SPA的，所以没遇到什么坑。但是现在呢，公司一个SPA项目需要后端Redirect URL，hashHistory就不方便了。于是准备使用browserHistory。先看了下官方的[Historise](https://github.com/ReactTraining/react-router/blob/master/docs/guides/Histories.md)。还是蛮简单明了的。

__实现的原理就是后端服务器除了API其他的路由访问都返回index.html，路由匹配交给前端啦__


我们先从前端切入吧，前端配置比较简单。

# 先把前端的```hashHistory```改成```browserHistory```

```javascript
import { Router, Route, browserHistory } from "react-router"

const RootRounter = <Router history={ browserHistory }>
    <Route path="/" component={ App }></Route>
</Router>
```

这个时候如果你用webpack-dev-server的话，需要在开启测试服务的命令后面加上```--history-api-fallback```不然的话页面会```404```

# 在Nodejs后端服务中配置

直接亮配置吧

```javascript
app.get("*", (req, res) => {
    res.sendFile(path.resolve(__dirname, "./index.html"))
})
```

> 这个配置需要放在其他路由或者后端API的后面，不然的话会造成前端访问API无法正确拿到数据  
可以在前端路由中加入通配符匹配不存在的路径显示404页面，增加体验

# 在Tomcat后端服务中配置

其实说实话我不懂Tomcat，原因是公司项目中使用的是Tomcat。公司同事很配合得和我一起配置弄好了。

> 其实也是在后端的路由中也是类似Nodejs的处理，后端JAVA使用的是JFinal框架。处理呢就是在匹配不到路由的时候render Tomcat中指定的项目根目录的index.html

在配置JAVA之前我Google了一下别人的配置，很多人使用了官方介绍的方法。

先在nginx中加入一下配置

```shell
server {
    ...
    location / {
    try_files $uri /index.html;
    }
}
```

在项目根目录中新加```.ftaccess```文件，加入内容为

```shell
RewriteBase /
RewriteRule ^index\.html$ - [L]
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.html [L]
```

但是呢貌似没啥作用，最后修改的还是```render("./index.html")```解决问题的

# 如果配置确认无误后，访问你的项目即可看到清爽的URL咯。
