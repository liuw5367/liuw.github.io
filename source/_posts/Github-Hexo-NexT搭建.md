---
title: Github-Hexo-NexT搭建
date: 2019-01-31 18:26:29
tags:
 - 环境搭建
copyright: true
---


> 这两天突然又想折腾一下 github.io，上次建好以后，好像有三四年了吧，但文章是一次也没有发过...看到好多人的网站都是NexT主题，就给自己的也重新搭建了一下

# 安装
- [Hexo](https://hexo.io) 这套皮肤是跑在hexo上的，所以需要新建一个hexo项目，然后将next放到theme文件夹下
- [NextT](http://theme-next.iissnan.com/) 主题配置网站，可以仔细看看，很全面，基本够用了

## 工具

- 安装git 
```
 brew install git
```
- 安装node
```
 brew install node
```
-  安装hexo
```
 npm install -g hexo-cli
```

<!-- more -->

## 运行

- 创建hexo项目
```
hexo init project-name
```

- 安装必要的工具

```
// Git自动上传
npm install hexo-deployer-git --save

// 管理页面，可以在网页上编辑 http://localhost:4000/admin
npm install hexo-admin --save
```
- 下载next皮肤，在hexo项目中的theme文件夹下clone项目。（hexo项目文件夹下有个配置文件，配置项目的。皮肤文件夹下，也有个配置文件，可以对皮肤修改。不要弄混了）

```
git clone https://github.com/theme-next/hexo-theme-next.git
```

- 在hexo项目的配置文件中设置主题为 next
```
 theme: hexo-theme-next
```
- 安装依赖
```
 npm install
```

- 生成静态文件
```
hexo generate
```

- 运行
```
hexo server --debug
```

# 发布
```
hexo generate -d
```

- 需要安装 hexo-deployer-git，才能自动发布。
```
npm install hexo-deployer-git --save
```

> 可以创建两个分支，dev分支为开发代码，放网站原始文件，设置deploy的分支为master，将静态文件直接上传 。下面为hexo目录下的的git配置

```
deploy:
  type: git
  # 对应仓库的SSH地址。需要在github上配置好ssh
  repo: git@github.com.git 
  # 要上传的分支
  branch: master 
```

# 遇到的问题
- 没有hexo命令server无法运行

>  对hexo不了解，一开始我以为next是一个完整的项目，有配置文件能直接跑起来呢，想多了，只是一个theme。依赖里面也没有hexo-server这个包。把主题放到hexo项目里就好了

- leanCloud阅读统计显示初始化失败

> 主题配置文件里有个security，关掉就可以了。我也没仔细看什么什么意思。没啥要求，能用就行。后面又看到busuanzi，直接开启就能用，不仅有阅读数，还能统计站点访问量和人数...

- deploy后页面和本地不一致

> 也不清楚怎么好的，多clean，generate再上传吧

- 列表的文章显示的太长

> 主题有个配置，可以设置显示的字符长度，但是markdown在列表里就不能预览了，而且不可控。推荐使用<! -- more --> 进行分割，设置列表中文章从哪里显示阅读更多按钮

# 常用命令

```
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #部署到GitHub
hexo help  # 查看帮助
hexo version  #查看Hexo的版本

// 缩写
hexo n == hexo new
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy

hexo s -g #生成并本地预览
hexo d -g #生成并上传
```

# Discus 开启匿名评论

- Settings -> Community -> Guest Commenting -> Allow guests to comment (Enable)


# 参考文章
[https://www.jianshu.com/p/7b5702d3f072](https://www.jianshu.com/p/7b5702d3f072)

[http://shenzekun.cn/](http://shenzekun.cn/hexo%E7%9A%84next%E4%B8%BB%E9%A2%98%E4%B8%AA%E6%80%A7%E5%8C%96%E9%85%8D%E7%BD%AE%E6%95%99%E7%A8%8B.html)

[https://blog.csdn.net/marvinboy/article/details/83350437](https://blog.csdn.net/marvinboy/article/details/83350437)
