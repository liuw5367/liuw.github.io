title: Hexo-Next主题搭建
tags:
  - 环境配置
categories: []
date: 2019-01-30 20:31:00
copyright: true
---
# 安装

[Next](http://theme-next.iissnan.com/) 主题配置网站，很全面

## 工具

- 安装git 
> brew install git
- 安装node
> brew install node
-  安装hexo
> npm install -g hexo-cli

<!-- more -->

## 运行

- 创建hexo项目
> hexo init

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
> theme: hexo-theme-next

- 依赖库
> npm install

- 生成静态文件
> hexo generate

- 运行
> hexo server --debug

# 发布
> hexo generate -d

- 安装 hexo-deployer-git
> npm install hexo-deployer-git --save

> 可以创建两个分支，dev分支为开发代码，放网站原始文件，设置deploy的分支为master，将静态文件直接上传 。下面为hexo目录下的的git配置


```
deploy:
  type: git
  # 对应仓库的SSH地址
  repo: git@github.com.git 
  # 要上传的分支
  branch: master 
```



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

// 文章中可以用 <!-- more --> 来设置列表预览分割
```

# Discus 开启匿名评论

- Settings -> Community -> Guest Commenting -> Allow guests to comment (Enable)


# 参考文章
[https://www.jianshu.com/p/7b5702d3f072](https://www.jianshu.com/p/7b5702d3f072)