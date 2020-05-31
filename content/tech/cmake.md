+++
date = 2020-05-04T15:24:06
description="创建 MakeFile 窍门"
tags = ['C','Linux']
categories = ["折腾Time"]
title = "快速编译C·MakeFile "

+++

模板为：

"程序名称":依赖的二进制对象文件，依赖的源文件
    编程命令
// 对于依赖文件的补充，它们需要什么，如下：↓

```c
hello.out:max.o min.o hello.c   
	gcc max.o min.o hello.c -o hello.out // 默认程序名称为 a.out
max.o:max.c
	gcc -c max.c
min.o:min.c gcc -c min.c
```



只需要直接 make ，无需输入长命令。