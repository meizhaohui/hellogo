# hellogo
Recording the process of learning Golang
本仓库用于记录学习Golang相关知识点。

Go编程语言中文文档中介绍Go:

- Go编程语言是一个开源项目，它使程序员更具生产力。

- Go语言具有很强的表达能力，它简洁、清晰而高效。得益于其并发机制，用它编写的程序能够非常有效地利用多核与联网的计算机，其新颖的类型系统则使程序结构变得灵活而模块化。Go代码编译成机器码不仅非常迅速，还具有方便的垃圾收集机制和强大的运行时反射机制。 它是一个快速的、静态类型的编译型语言，感觉却像动态类型的解释型语言。


我们可以简单的理解Go语言解决了其他语言并发执行的痛点，像C语言一样的运行效率高，又兼容了Python语言的开发速度快的特点，``Go = C + Python``, Go语言被称为"互联网时代的C"。我们不在概念上过多的纠结，直接来开始使用Go这门编程语言。

## 特别说明

- 本文档中``Golang``简写为``Go``。
- 本文档假定您会使用Linux操作系统的基本命令，如vim、cat、ls等一些工具。
- ``Go``学习网站：官方文档 https://golang.google.cn/doc/
- ``Go``学习网站：Go编程语言中文文档 https://go-zh.org/doc/
- ``Go``学习网站：Go语言之旅 https://go-tour-zh.appspot.com/list
- ``Go``学习网站：实效Go编程 https://go-zh.org/doc/effective_go.html
- ``Go``学习网站：Go编程语言规范 https://go-zh.org/ref/spec


## 实验环境

本实验使用CentOS7.6作为实验环境。

```shell
[root@hellogitlab ~]# cat /etc/centos-release
CentOS Linux release 7.6.1810 (Core)
```

## 安装和配置GO环境

### 安装Golang

- 使用``yum install go -y``安装Golang。
```shell
[root@hellogitlab ~]# yum install go -y
Loaded plugins: fastestmirror, langpacks
Repository epel is listed more than once in the configuration
Loading mirror speeds from cached hostfile
Resolving Dependencies
--> Running transaction check
---> Package golang.x86_64 0:1.13.1-1.el7 will be updated
--> Processing Dependency: go = 1.13.1-1.el7 for package: golang-bin-1.13.1-1.el7.x86_64
---> Package golang.x86_64 0:1.13.3-1.el7 will be an update
--> Processing Dependency: golang-src = 1.13.3-1.el7 for package: golang-1.13.3-1.el7.x86_64
--> Running transaction check
---> Package golang-bin.x86_64 0:1.13.1-1.el7 will be updated
---> Package golang-bin.x86_64 0:1.13.3-1.el7 will be an update
---> Package golang-src.noarch 0:1.13.1-1.el7 will be updated
---> Package golang-src.noarch 0:1.13.3-1.el7 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

=================================================================================================================================================
 Package                             Arch                            Version                                 Repository                     Size
=================================================================================================================================================
Updating:
 golang                              x86_64                          1.13.3-1.el7                            epel                          694 k
Updating for dependencies:
 golang-bin                          x86_64                          1.13.3-1.el7                            epel                           86 M
 golang-src                          noarch                          1.13.3-1.el7                            epel                          7.1 M

Transaction Summary
=================================================================================================================================================
Upgrade  1 Package (+2 Dependent packages)

Total download size: 93 M
Downloading packages:
epel/7/x86_64/prestodelta                                                                                                 | 1.0 kB  00:00:00     
(1/3): golang-1.13.3-1.el7.x86_64.rpm                                                                                     | 694 kB  00:00:00     
(2/3): golang-src-1.13.3-1.el7.noarch.rpm                                                                                 | 7.1 MB  00:00:00     
(3/3): golang-bin-1.13.3-1.el7.x86_64.rpm                                                                                 |  86 MB  00:00:03     
-------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                             29 MB/s |  93 MB  00:00:03     
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Updating   : golang-src-1.13.3-1.el7.noarch                                                                                                1/6 
  Updating   : golang-bin-1.13.3-1.el7.x86_64                                                                                                2/6 
  Updating   : golang-1.13.3-1.el7.x86_64                                                                                                    3/6 
  Cleanup    : golang-bin-1.13.1-1.el7.x86_64                                                                                                4/6 
  Cleanup    : golang-1.13.1-1.el7.x86_64                                                                                                    5/6 
  Cleanup    : golang-src-1.13.1-1.el7.noarch                                                                                                6/6 
  Verifying  : golang-src-1.13.3-1.el7.noarch                                                                                                1/6 
  Verifying  : golang-1.13.3-1.el7.x86_64                                                                                                    2/6 
  Verifying  : golang-bin-1.13.3-1.el7.x86_64                                                                                                3/6 
  Verifying  : golang-1.13.1-1.el7.x86_64                                                                                                    4/6 
  Verifying  : golang-bin-1.13.1-1.el7.x86_64                                                                                                5/6 
  Verifying  : golang-src-1.13.1-1.el7.noarch                                                                                                6/6 

Updated:
  golang.x86_64 0:1.13.3-1.el7                                                                                                                   

Dependency Updated:
  golang-bin.x86_64 0:1.13.3-1.el7                                        golang-src.noarch 0:1.13.3-1.el7                                       

Complete!
```

### 查看Golang版本

```shell
[root@hellogitlab ~]# go version
go version go1.13.3 linux/amd64
```

### 查看``go``命令的帮助信息
```shell
[root@hellogitlab ~]# go
Go is a tool for managing Go source code.

Usage:

        go <command> [arguments]

The commands are:

        bug         start a bug report
        build       compile packages and dependencies
        clean       remove object files and cached files
        doc         show documentation for package or symbol
        env         print Go environment information
        fix         update packages to use new APIs
        fmt         gofmt (reformat) package sources
        generate    generate Go files by processing source
        get         add dependencies to current module and install them
        install     compile and install packages and dependencies
        list        list packages or modules
        mod         module maintenance
        run         compile and run Go program
        test        test packages
        tool        run specified go tool
        version     print Go version
        vet         report likely mistakes in packages

Use "go help <command>" for more information about a command.

Additional help topics:

        buildmode   build modes
        c           calling between Go and C
        cache       build and test caching
        environment environment variables
        filetype    file types
        go.mod      the go.mod file
        gopath      GOPATH environment variable
        gopath-get  legacy GOPATH go get
        goproxy     module proxy protocol
        importpath  import path syntax
        modules     modules, module versions, and more
        module-get  module-aware go get
        module-auth module authentication using go.sum
        module-private module configuration for non-public modules
        packages    package lists and patterns
        testflag    testing flags
        testfunc    testing functions

Use "go help <topic>" for more information about that topic.
```

### go安装信息检查

```shell
# 查看go处于什么位置
[root@hellogitlab ~]# whereis go
go: /usr/bin/go /usr/lib/golang/bin/go
# 查看/usr/bin/go的详细信息，可以看到最终指向了/usr/lib/golang/bin/go
[root@hellogitlab ~]# ls -lah /usr/bin/go
lrwxrwxrwx 1 root root 20 Nov 22 22:36 /usr/bin/go -> /etc/alternatives/go
[root@hellogitlab ~]# ls -lah /etc/alternatives/go
lrwxrwxrwx 1 root root 22 Nov 22 22:36 /etc/alternatives/go -> /usr/lib/golang/bin/go
[root@hellogitlab ~]# ls -lah /usr/lib/golang/bin/go
-rwxr-xr-x 1 root root 15M Nov  3 03:34 /usr/lib/golang/bin/go
# golang的安装目录
[root@hellogitlab ~]# ls -lah /usr/lib/golang/
total 44K
drwxr-xr-x   7 root root 4.0K Nov 22 22:36 .
dr-xr-xr-x. 44 root root 4.0K Nov 20 00:06 ..
drwxr-xr-x   2 root root 4.0K Nov 22 22:36 api
drwxr-xr-x   2 root root 4.0K Nov 22 22:35 bin
-rw-r--r--   1 root root 5.6K Oct 18 06:02 favicon.ico
drwxr-xr-x   3 root root 4.0K Oct 18 06:02 lib
drwxr-xr-x   8 root root 4.0K Nov  3 03:35 pkg
-rw-r--r--   1 root root   26 Oct 18 06:02 robots.txt
drwxr-xr-x  46 root root 4.0K Nov 22 22:35 src
-rw-r--r--   1 root root    8 Oct 18 06:02 VERSION
```

我们后续使用普通账户``meizhaohui``来进行go语言相关命令的操作。

### 配置Go的工作空间

GO代码必须在工作空间内。工作空间是一个目录，其中包含三个子目录：
- src 里面每一个子目录，就是一个包。包内是Go的源码文件
- pkg 编译后生成的，包的目标文件
- bin 生成的可执行文件


使用普通账户``meizhaohui``创建Go的工作空间目录
```shell
# 查看我是谁
[meizhaohui@hellogitlab ~]$ whoami
meizhaohui
# 查看当前文件夹中的文件
[meizhaohui@hellogitlab ~]$ ls
# 创建工作空间目录
[meizhaohui@hellogitlab ~]$ mkdir -p data/go_data
[meizhaohui@hellogitlab ~]$ ls -lsh data/
total 4.0K
4.0K drwxrwxr-x 2 meizhaohui meizhaohui 4.0K Nov 22 23:02 go_data
# 在工作空间目录下面创建子目录
[meizhaohui@hellogitlab ~]$ mkdir -p data/go_data/{src,bin,pkg}
[meizhaohui@hellogitlab ~]$ ls -lah data/go_data/
total 20K
drwxrwxr-x 5 meizhaohui meizhaohui 4.0K Nov 22 23:10 .
drwxrwxr-x 3 meizhaohui meizhaohui 4.0K Nov 22 23:02 ..
drwxrwxr-x 2 meizhaohui meizhaohui 4.0K Nov 22 23:10 bin
drwxrwxr-x 2 meizhaohui meizhaohui 4.0K Nov 22 23:10 pkg
drwxrwxr-x 2 meizhaohui meizhaohui 4.0K Nov 22 23:10 src
```

### 配置``PATH``、``GOPATH``、``GOROOT``、``GOBIN``等环境变量

在``~/.bashrc``文件中增加以下内容：

```
# Golang environment settings
export GOROOT=/usr/lib/golang # golang install path
export GOPATH=/home/meizhaohui/data/go_data # golang workspace
export GOBIN=${GOPATH}/bin # golang exe files
export PATH=${GOBIN}:${PATH}
```

保存后，``source ~/.bashrc``加载配置文件，并查看以上设置的Go语言的环境变量：
```shell
[meizhaohui@hellogitlab ~]$ source ~/.bashrc
[meizhaohui@hellogitlab ~]$ echo $GOPATH
/home/meizhaohui/data/go_data
[meizhaohui@hellogitlab ~]$ echo $GOBIN
/home/meizhaohui/data/go_data/bin
[meizhaohui@hellogitlab ~]$ echo $GOROOT
/usr/lib/golang
[meizhaohui@hellogitlab ~]$ echo $PATH
/home/meizhaohui/data/go_data/bin:/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/home/meizhaohui/.local/bin:/home/meizhaohui/bin
```

查看到以上信息，说环境变量配置成功。

### 开启Go module和代理

默认情况下，使用go get下载包时会非常慢，需要开启Go module和代理，加快我们包的安装速度。

为了今后中国的Go语言开发者能更好地进行开发，七牛云推出了非营利性项目 goproxy.cn，其目标是为中国和世界上其他地方的 Gopher 们提供一个免费的、可靠的、持续在线的且经过 CDN 加速的模块代理。

参考：
- 干货满满的 Go Modules 和 goproxy.cn https://github.com/EDDYCJY/blog/blob/master/talk/goproxy-cn.md
- Go module和goproxy 设置 https://luhua.cc/2019/08/23/Go-module-%E5%92%8C-goproxy-%E8%AE%BE%E7%BD%AE/

在``~/.bashrc``文件中增加以下内容：

```shell
export GO111MODULE=on
export GOPROXY=https://goproxy.cn
```

保存后，``source ~/.bashrc``加载配置文件，并查看以上设置的Go语言的环境变量：

```shell
[meizhaohui@hellogitlab ~]$ echo $GO111MODULE
on
[meizhaohui@hellogitlab ~]$ echo $GOPROXY 
https://goproxy.cn

# 测试安装包
[meizhaohui@hellogitlab ~]$ go get -v github.com/stamblerre/gocode
```


## 第一个Go程序，你好世界

### 编写Go代码文件
以最经典的``Hello world``程序为例，编写第一个Go代码文件。

我们切换到``$GOPATH/src``目录中，创建第一个Go代码文件。
```shell
[meizhaohui@hellogitlab ~]$ cd $GOPATH/src
[meizhaohui@hellogitlab src]$ pwd
/home/meizhaohui/data/go_data/src
# 使用vim编写hello.go文件，保存后查看内容如下
[meizhaohui@hellogitlab src]$ cat hello.go
package main

import "fmt"

func main() {
    fmt.Println("Hello,World")
}
```

### 编译Go程序``go build``

- 使用``go build filename.go``编译go程序，如``go build hello.go``编译生成可执行文件``hello``。
```shell
[meizhaohui@hellogitlab src]$ go build hello.go 
[meizhaohui@hellogitlab src]$ ls
hello  hello.go
# 运行可执行文件hello
[meizhaohui@hellogitlab src]$ ./hello
Hello,World
```

### 编译并直接运行Go程序``go run``

- 使用``go run filename.go``编译并直接运行go程序，如``go build hello.go``编译时不生成可执行文件，直接显示运行结果。

```shell
[meizhaohui@hellogitlab src]$ trash-put hello
[meizhaohui@hellogitlab src]$ ls
hello.go
[meizhaohui@hellogitlab src]$ go run hello.go
Hello,World
[meizhaohui@hellogitlab src]$ ls
hello.go
```

### 编译并安装``go install``
- 对go源码文件``go install``,会进行编译+链接+生成可执行文件, 会在``$GOBIN``目录下生成可执行文件。

```shell
# 编译并安装
[meizhaohui@hellogitlab src]$ go install hello.go
# 查看当前目录下是否生成可执行文件
[meizhaohui@hellogitlab src]$ ls 
hello.go
# 查看bin目录下是否生成可执行文件
[meizhaohui@hellogitlab src]$ ls $GOBIN
hello
# 查看hello可执行文件的位置
[meizhaohui@hellogitlab src]$ whereis hello
hello: /home/meizhaohui/data/go_data/bin/hello
# 在任何目录执行hello，会打印出世界你好
[meizhaohui@hellogitlab src]$ hello
Hello,World
[meizhaohui@hellogitlab src]$ cd
[meizhaohui@hellogitlab ~]$ hello
Hello,World
```

## GO语言之旅

### 基础

#### 注释

- Go语言支持C风格的块注释``/* */``和C++风格的行注释``//``。 行注释更为常用，而块注释则主要用作包的注释，当然也可在禁用一大段代码时使用。

我们在``hello.go``中增加一下注释。

查看源文件内容：

```go
[meizhaohui@hellogitlab src]$ cat hello.go
/*
File    : hello.go
Author  : Zhaohui Mei<mzh.whut@gmail.com>
Date    : 2019-11-23
Sammary : display hello world
*/
package main

import "fmt" // 导入包fmt

// 主函数,在main包中，主函数必须以main命名
func main() {
        // 打印输出"Hello,World"
        fmt.Println("Hello,World")
}
```

再次运行程序：

```shell
[meizhaohui@hellogitlab src]$ go run hello.go
Hello,World
```

#### 包、变量、函数

##### 包

- 每个Go程序都是由一个包组成的。
- Go程序从``main``包开始执行的。
- 使用``package name``来定义名称为``name``的包。
- 每个Go程序必须包含一个名称为``main``的包，即必须有一个``package main``这样的包。如果程序未定义``main``包，运行程序时则会提示``go run: cannot run non-main package``异常。
- 必须在Go源文件中非注释的第一行指明这个文件属于哪个包。
- 包名不一定要和源文件名保持一致。如源文件``swagger.go``中定义的包``package swag``就是这种情况。
- 在``package main``主包中必须定义一个主函数``func main()``，否则运行程序时则会提示``function main is undeclared in the main package``异常，即主包中未声明主函数。
- 文件夹包与包名没有直接关系，并非需要一致。
- 同一个文件夹下的文件只能有一个包名，否则编译报错。

###### 引入包

- Go程序通过``import``语句引入包并在代码中使用。
- ``import``语句告诉编译器这个程序使用哪些包。
- ``import``语句可以像Python一样的，一次导入一个包，像hello.go中``import "fmt"``导入fmt包。
- ``import``语句也可以一性引入多个包，也称批量导入或打包导入语句。**推荐使用批量导入语句**。

下面示例中，使用了批量导入语句：
示例：
```go
[meizhaohui@hellogitlab src]$ cat packages.go 
/*
 *      Filename: packages.go
 *        Author: Zhaohui Mei<mzh.whut@gmail.com>
 *   Description:
 *   Create Time: 2019-11-24 17:27:21
 * Last Modified: 2019-11-24 17:28:34
 */
package main

import (
        "fmt"
        "math/rand"
)

func main() {
        fmt.Println("The rand Number: ", rand.Intn(10))
}
```

此示例中，定义了main包，并批量导入了两个包，一个"fmt"包，一个"math/rand"包。

运行程序：
```shell
[meizhaohui@hellogitlab src]$ go run packages.go
The rand Number:  1
```


###### 名字导出

- 在导入一个包后，就可以使用其导出的名称来调用它。
- Go语言是大小写敏感的。
- 在Go语言中，以大写字母开头的名字就会被``导出``( exported )。类似面向对象里面的属性public。
- 在Go语言中，以小写字母开头的名字**不会被**``导出``( exported )。类似面向对象里面的属性private。对包外不可见。


我们将上面的packages.go程序修改一下：
```go
[meizhaohui@hellogitlab src]$ cat packages.go 
/*
 *      Filename: packages.go
 *        Author: Zhaohui Mei<mzh.whut@gmail.com>
 *   Description:
 *   Create Time: 2019-11-24 17:27:21
 * Last Modified: 2019-11-24 17:54:50
 */
package main

import (
        "fmt"
        "math"
        "math/rand"
)

func main() {
        fmt.Println("The rand Number: ", rand.Intn(10))
        fmt.Println("The PI: ", math.pi)
}
```

尝试运行程序：
```shell
[meizhaohui@hellogitlab src]$ go run packages.go 
# command-line-arguments
./packages.go:18:26: cannot refer to unexported name math.pi
./packages.go:18:26: undefined: math.pi
```

可以看到执行错误，无法获取到``math.pi``这个变量。

将``math.pi``改成``math.PI``后再运行：

```shell
[meizhaohui@hellogitlab src]$ go run packages.go 
The rand Number:  1
The PI:  3.141592653589793
```

可以正常获取到``pi``的值为``3.141592653589793``。


```shell


```