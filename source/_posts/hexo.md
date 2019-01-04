---
title: 一点点关于Hexo的东西
date: 2018-12-23 11:07:39
tags: IT hexo 
---
关于这篇博客的由来以及使用。
搞IT的谁还没有一个博客呢，你说是么？何必那么认真！
<!-- more-->
## 博客搭建
### Node.js
下载[node.js](https://nodejs.org/en/download/)
查看版本号如下，表示安装成功
```
C:\Users\yum717>node -v
v10.14.2
```
### git
### 创建项目
#### 项目名：后缀要一样的哦。
```
labulakaupppppp@github.io
```
#### 在合适的位置创建一个文件夹，cd执行如下命令
```
cd blog
npm install hexo -g
hexo -v //检查是否安装成功
hexo init //初始化该文件夹
npm install //安装所需组件
hexo g //首次体验
hexo s //开启服务，之后可以再http://localhost:4000上访问到自己的博客 （也可以自己更改端口号）
```
### 将hexo与github连接
#### 设置git的username与email
```
git config --global user.name "labulakaupppppp"
git config --global user.email ""
```
#### 配置ssh
将本机公钥添加到github的ssh中，并配置__config.yaml,修改repo值（在最后）
```
deploy:
  type: git
  repository: git@github.com:labulakaupppppp/labulakaupppppp.github.io.git
  branch: master

```
#### 安装扩展
生成与部署文章之前需要先安装一个扩展。
```
nmp install hexo-deployer-git --save
```
## hexo的使用
#### 写一篇新的博客
```
hexo new "My blog"
```
#### 提交代码更新
```
hexo d -g
```
#### 运行服务器
```
hexo server -p 端口号
```
#### 生成静态文件
```
hexo generate
```
#### Deploy to remote sites

```
hexo deploy
```
更多请看官网[Hexo](https://hexo.io/)，Check [documentation](https://hexo.io/docs/) for more info.

## hexo进阶
### 更改主题
可以再hexo官方的主题里面找到自己喜欢的一款[here](https://hexo.io/themes/ )
```
$ cd D:hexo/
$ git clone https://github.com/iissnan/hexo-theme-next themes/next
```
并在该站根目录下的_config.yaml文件中更改配置
```
theme: next
```
