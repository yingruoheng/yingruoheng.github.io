---
layout:     post
title:      用vue-cli快速搭建vue脚手架+实现vue页面跳转的小demo
subtitle:    "\"不积硅步, 无以至千里。\""
date:       2019-1-29
author:     RH
header-img: img/post-bg-rwd.jpg
catalog: true
tags:
    - 技术
    - 前端
    - vue
---

> “🌈🌈🌈 ”


####	[一个简单的 vue 页面跳转示例项目地址👆](https://github.com/yingruoheng/vue-demo)

###		**vue简介**

Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue 被设计为可以自底向上逐层应用。Vue 的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue 也完全能够为复杂的单页应用提供驱动。

Vue.js特点

-	**简洁**： HTML 模板 + JSON 数据，再创建一个 Vue 实例，就这么简单。
- **数据驱动**： 自动追踪依赖的模板表达式和计算属性。
- **组件化**： 用解耦、可复用的组件来构造界面。
- **轻量**： ~24kb min+gzip，无依赖。
- **快速**： 精确有效的异步批量 DOM 更新。
- **模块友好**： 通过 NPM 或 Bower 安装，无缝融入你的工作流。


Vue 提供了一个官方的 CLI，为单页面应用 (SPA) 快速搭建繁杂的脚手架。它为现代前端工作流提供了 batteries-included 的构建设置。只需要几分钟的时间就可以运行起来并带有热重载、保存时 lint 校验，以及生产环境可用的构建版本。

###	**搭建环境**

node和npm的环境是必须的，npm和node的安装不再赘述，自行解决即可。

**npm** 全称：Node Package Manager，就是Node的包的一个管理工具，是Node.js下的主流套件管理程式。

**Node.js** 用一句话来介绍就是：Node.js 是一个让 JavaScript 运行在服务端的开发平台。

**Webpack** 是一个前端资源加载/打包工具。它将根据模块的依赖关系进行静态分析，然后将这些模块按照指定的规则生成对应的静态资源。

![](http://www.runoob.com/wp-content/uploads/2017/01/what-is-webpack.png)
从图中我们可以看出，Webpack 可以将多种静态资源 js、css、less 转换成一个静态文件，减少了页面的请求。

**Vue.js 目录结构**
![](https://ws4.sinaimg.cn/large/006tNc79ly1fzns96oihuj30bm0biq31.jpg)

**目录解析**

| 目录/文件 | 说明 |
| :------| :------ |
| build | 项目构建(webpack)相关代码	|
| config | 配置目录，包括端口号等。我们初学可以使用默认的。|
| node_modules | npm 加载的项目依赖模块 |
| src | 这里是我们要开发的目录，基本上要做的事情都在这个目录里。里面包含了几个目录及文件：assets: 放置一些图片，如logo等。components: 目录里面放了一个组件文件，可以不用。App.vue: 项目入口文件，我们也可以直接将组件写这里，而不使用 components 目录。main.js: 项目的核心文件。|
| static | 静态资源目录，如图片、字体等。 |
| test | 初始测试目录，可删除	|
| .xxxx文件 | 这些是一些配置文件，包括语法配置，git配置等。 |
| index.html | 首页入口文件，你可以添加一些 meta 信息或统计代码啥的。|
| package.json | 项目配置文件。 |
| README.md | 	项目的说明文档，markdown 格式|

####	1.全局安装 **webpack**

请先确认自己已经安装npm和node.js,使用npm全局安装 **webpack**，打开命令行工具输入：``npm install webpack -g``,安装完成后输入``webpack -v``，如果出现相应版本号，则安装成功

webpack 4.X 开始，需要安装 webpack-cli 依赖 ,所以使用这条命令 ``npm install webpack webpack-cli -g``

####	2.全局安装 **vue-cli**

在命令行输入``npm install -g vue-cli``，安装完成后输入``vue-V``，如果出现相应版本号，则安装成功

####	3.使用**vue-cli**来构建项目

首先新建一个文件夹作为项目存放地，cd进入其目录，输入以下命令创建项目``vue init webpack vue-demo``，模版下载成功后会有一些交互的项需要填写

```
? Project name vue-demo # 项目名称，直接回车，按照括号中默认名字（注意这里的名字不能有大写字母，如果有会报错Sorry, name can no longer contain capital letters），阮一峰老师博客为什么文件名要小写 ，可以参考一下。
? Project description A Vue.js project # 项目描述,随便写
? Author # 作者名称
? Vue build standalone # 我选择的运行加编译时
	Runtime + Compiler: recommended for most users
? Install vue-router? Yes # 是否需要 vue-router，路由肯定要的
? Use ESLint to lint your code? Yes # 是否使用 ESLint 作为代码规范.
? Pick an ESLint preset Standard # 一样的ESlint 相关
? Set up unit tests Yes # 是否安装单元测试
? Pick a test runner 按需选择 # 测试模块
? Setup e2e tests with Nightwatch? 安装选择 # e2e 测试
? Should we run `npm install` for you after the project has been created? (recommended) npm # 包管理器，我选的NPM
```
安装成功后，cd进入项目目录，执行命令``npm install``进行初始化，安装我们的项目依赖包，也就是安装**package.json**里的包。

####	4.运行项目
命令行执行``npm run dev``

打开浏览器访问 **http://localhost:8080** 就能看到欢迎页面，若页面加载不出来可能是本地8080端口被占用，需要修改一下配置文件``config``里的``index.js``的post即可
![](https://ws1.sinaimg.cn/large/006tNc79ly1fznrpdlgz4j30rq0myt9t.jpg)

####	5.**vue-cli** 的 **webpack** 配置

从 **package.json** 可以看到 开发 和 生产 环境的入口。
![](https://ws1.sinaimg.cn/large/006tNc79ly1fzns3oygfbj30y207iq35.jpg)

-	**dev** 是开发环境的启动命令
- 	**build** 是生产打包环境的命令
-  **lint** 是ESLint的检查命令 在 --ext 前加一个 --fix 可以自动修复不符合规范的代码

打包上线：运行 ``npm run build`` 命令，就可以进行打包工作了，打包完成后，会生成 dist 目录，项目上线时，把dist 目录下的文件放到服务器就可以了

在谷歌商店搜索调试工具 ``vue-tool`` 安装到浏览器，调试项目很好用

---

###		vue项目实现页面跳转

假设现在有两个页面 **HelloWorld** 和 **Registered** ，路由配置在 **src/router/index.js** 中

```
import Vue from 'vue'
import Router from 'vue-router'
import HelloWorld from '@/components/HelloWorld'
import Registered from '@/components/Registered'

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'HelloWorld',
      component: HelloWorld
    },
    {
      path: '/Registered',
      name: 'Registered',
      component: Registered
    }
  ]
})
```

页面 **HelloWorld**

```
<template>
  <div class="hello">
    <h1>密码登录</h1>
    <input placeholder="请输入用户名" type="text" name="userName"/>
    <br><br>
    <input placeholder="请输入密码" type="text" name="passWord"/>
    <br><br>
    <input type="submit" value="登录" />
    <button @click="go">点我跳转</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      msg1: 'hello my app'
    }
  },

  methods:{
  	go(){
  		this.$router.push('/Registered')
  	}
  }
}
</script>
```

页面 **Registered**

```
<template>
  <div class="hello">
    <h1>我是Registered</h1>
    <button @click="back">点我返回</button>
  </div>
</template>

<script>
export default {
  name: 'Registered',
  data () {
    return {
    }
  },

  methods:{
  	back(){
  		this.$router.push('/')
  	}
  }
}
</script>
```
在HelloWorld中点击按钮跳转到Registered，在Registered中点击按钮也可以返回到HelloWorld，实现的效果如下图:

**HelloWorld** 页面
![](https://ws2.sinaimg.cn/large/006tNc79ly1fznsssxdy8j30me0gsq2x.jpg)
**Registered** 页面
![](https://ws3.sinaimg.cn/large/006tNc79ly1fznst9d8dpj30no0bya9z.jpg)

###	项目地址
####	[戳这里 👆](https://github.com/yingruoheng/vue-demo)
