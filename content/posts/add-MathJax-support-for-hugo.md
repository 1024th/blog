+++
title = "为 Hugo 添加 MathJax 支持（重新编译 Hugo）"
date = 2021-04-01T00:29:23+08:00
description = "使用 goldmark-mathjax 彻底解决数学公式渲染问题"
draft = false
tags = [ "hugo", "MathJax" ]
categories = [ "编程" ]
+++

> 参考：https://www.cnblogs.com/jiahu-Blog/p/14350046.html

## 源码编译 Hugo （添加 MathJax 支持）

Hugo 默认使用 GoldMark 解析 Markdown 文件，因为 GoldMark 不支持复杂的 Markdown 数学表达式，比如 `$\mathbf{v}*_{1}=\left[\begin{array}{r}-1* *\\**1\end{array}\right]$`

按照官方的说法，markdown 使用下划线给字符添加黑体与斜体，而 lex 使用 下划线表示下标，二者冲突了

Goldmark 有插件可以解决这个问题，但不知为何 0.8 版没有使用 [goldmark-mathjax](https://github.com/litao91/goldmark-mathjax) 这个插件，所以为了完美支持 markdown 数学表达式，需添加这个插件并编译，执行过程如下：

1.  修改 go proxy，使用国内的镜像更快：`go env -w GOPROXY=https://goproxy.cn,direct`
    1.  使用这条命令需要 go 版本大于等于 1.13
2.  `git clone https://github.com/gohugoio/hugo.git`
3.  修改 `markup/goldmark/convert.go` 文件
    1.  添加依赖，在 import 里添加：`mathjax "github.com/litao91/goldmark-mathjax"`
    2.  注册插件，在调用 `goldmark.New` 之前添加：`extensions = append(extensions, mathjax.MathJax)`
4.  编译：`go build -o hugo main.go`
5.  拷贝可执行文件到 PATH 路径下即可