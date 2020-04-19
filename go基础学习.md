# go基础学习

go与Java的区别

Java是面向对象的，所有的项目运行依赖于jvm，go是直接编译为可执行文件，不需要环境可以单独运行

Java的spring框架封装的@Transaction注解必须放在service层才能生效，有明显的层级关系

go是一种编译型语言

一般的项目结构

在gopath环境变量指向的文件夹下面有三个文件夹  bin,pkg,src，在src下面放的是各个项目，

开启可gomodule后可以在位置创建go项目

### go的命令 

```
go version
go env
go module的设置 可以让项目不再gopath下

```

go build会生成.exe文件

go install 

go的强制类型转换 float(1)

go中的默认值nil相当于Java中的null

