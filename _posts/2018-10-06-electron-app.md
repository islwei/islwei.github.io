---
layout: post
title: "搭建electron app，并打包"
categories: Project
tags: electron app electron-package
author: Elijah
---

* content
{:toc}

最近搭建了Github Blog，但是Jekyll写Blog比较困难，博客中每篇帖子是个需要固定格式的MarkDown文件，上传到Github后Jekyll框架才能转换成自己的格式，
所以计划使用electron搭建个APP去生成MD文件，如果可以的话直接上传到Github仓库，项目正在构建中…
博主也是第一次接触Electron，都是参考的其他博客中的方法，然后整理实践的.
话不多说，开始第一个App搭建！





## 搭建app

- 参考:[https://electronjs.org/](https://electronjs.org/)
- 依赖:Nodejs

#克隆示例项目的仓库
```md
$ git clone https://github.com/electron/electron-quick-start
```

#进入这个仓库
```md
$ cd electron-quick-start
```

#安装依赖并运行
```md
$ npm install && npm start
```

其实这时你的app已经可以运行了
![tool](https://i.loli.net/2018/10/06/5bb89172860e9.png 'tool')

只不过，只是一个框架而已，还没有实现业务逻辑，诸位看官自己实现啦~


## 打包
博主用的是[electron-packager](https://github.com/electron-userland/electron-packager)

安装electron-packager
```md
$ npm install --save-dev electron-packager 
```

好多博客都是在工程目录的app目录下执行打包命令，不过electron-quick-start示例并没有app目录，
main.js index.html都是在根目录里，我们可以直接在根目录执行打包命令
为了以后的程序扩展，我们新建了app目录，并copy根目录的main.js index.html package.json文件到./app目录下
以下命令是在..\blog-editor\app下执行

打包命令
```md
$ electron-packager <location of project> <name of project> <platform> <architecture> <electron version> <optional options>
```
命令说明：
* `location of project`：项目所在路径 
* `name of project`：打包的项目名字 
* `platform`：确定了你要构建哪个平台的应用（Windows、Mac 还是 Linux） 
* `architecture`：决定了使用 x86 还是 x64 还是两个架构都用 
* `electron version`：electron 的版本 
* `optional options`：可选选项

所以我们最终的打包命令就是
```md
$ electron-packager . BlogEditor --platform=win32 --arch=x64 --icon=../img/favicon.ico --out=../BuildOut --asar --app-version=0.0.1
```
包就会打在根目录里

![config](https://i.loli.net/2018/10/06/5bb893d9d7059.png 'config')

不过这种打包命令的参数太多，有点反人类，所以我们可以像上面图片中蓝色框中配置一下，然后简单命令就可以实现相同效果
新的打包命令就是
```md
$ npm run-script packager
```

至此，搭建app和打包流程也就结束了

## 总结

其实整个过程还是很简单的，正所谓会而不难，不过想真正了解底层实现逻辑或者说能够整体把握具体流程，还需要我们以后进一步学习.
学海无涯啊
之后在实现BlogEditor业务逻辑时，我会继续更新一些有价值的干货 :)

