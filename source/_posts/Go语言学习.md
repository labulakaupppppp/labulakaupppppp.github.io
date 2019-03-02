---
title: Go语言学习
date: 2019-03-02 10:58:52
tags: GO code
---
GO语言学习，从0开始！
<!-- more-->
## GO安装
#### 下载地址
[GO官网](https://golang.org/dl/)
Windows/macOS/Linux三个版本按需下载。要是链接打不来，ShadowSocks了解一下。

## Hello World
先用记事本试一下：
```
package main

import "fmt"

func main(){
	fmt.Println("Hello world!")
}
```
在test.go所在目录下执行
```
go run test.go
```
你的世界你看见！