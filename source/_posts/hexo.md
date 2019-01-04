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
## hexo备份
使用hexo＋github搭建博客，在本地可以正常编辑，但是更换电脑或者新装系统就会导致之前的源码全都丢失，无法继续维护博客，使用github的新分支备份，可以有效保护源码。
### 备份
1. 之前创建好的以.github.io结尾的项目中，新建一个分支如backup。
2. 将backup设置为默认分支
3. 将blog文件夹中的_config.yaml,themes/,source/,scaffolds/,package.json, .gitignore备份到新分支，（使用新分支上传）
4. 删除themes/next/中的.git/，否则无法将该文件夹push到git上。
5. 执行以下命令，提交blog网站的源文件
```
git add .
git commit -m ""
git push origin backup
```
6. 执行hexo d -g生成静态网页部署至github。
### 修改
在本地对博客进行修改后，需按如下操作
1. 执行以下命令，提交blog网站的源文件
```
git add .
git commit -m ""
git push origin backup
```
2. 执行hexo d -g生成静态网页部署至github。
### 恢复
换电脑或者重装系统，再次修改博客操作方法
1. 安装git、Node.js、npm
2. 克隆
```
git clone git@github.com:labulakaupppppp/labulakaupppppp.github.io.git
```
4. 在文件夹内执行
```
npm install hexo-cli -g
npm install
npm install hexo-deployer-git
```
## hexo的源文件
1. _config.yml站点的配置文件，需要拷贝；
2. themes/主题文件夹，需要拷贝；
3. source博客文章的.md文件，需要拷贝；
4. scaffolds/文章的模板，需要拷贝；
5. package.json安装包的名称，需要拷贝；
6. .gitignore限定在push时哪些文件可以忽略，需要拷贝；
7. .git/主题和站点都有，标志这是一个git项目，不需要拷贝；
8. node_modules/是安装包的目录，在执行npm install的时候会重新生成，不需要拷贝；
9. public是hexo g生成的静态网页，不需要拷贝；
10. .deploy_git同上，hexo g也会生成，不需要拷贝；
11. db.json文件，不需要拷贝。

其实不需要拷贝的文件正是.gitignore中所忽略的。
