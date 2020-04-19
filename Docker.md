# Docker

* 三要素 镜像(image)，容器(container)，仓库(repository)
  1. 镜像相当于一个模板，容器就是这个镜像的实例

```
镜像相当于java中的类，
容器是这个类的一个个实例，容器相当于一个简易版的linux环境
仓库是用来存放镜像的地方
```

### docker 命令

```
Linux命令 man ls 

docker info
docker --help

docker login
huangtengfei
h19935953813

docker run hello-world
docker images
docker search




```

### 常用命令

```
uname -a  查看服务器的系统

```



* ➜  ~ docker pull hello-world

* ```
  ➜  ~ docker images
  REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
  postgres                                latest              73119b8892f9        3 weeks ago         314MB
  mysql                                   latest              ed1ffcb5eff3        3 months ago        456MB
  mongo                                   latest              a0e2e64ac939        3 months ago        364MB
  redis                                   latest              dcf9ec9265e0        4 months ago        98.2MB
  mirrorgooglecontainers/kube-apiserver   v1.14.2             5eeff402b659        10 months ago       210MB
  hello-world                             latest              fce289e99eb9        15 months ago       1.84kB
  
  ```

* docker rmi fce289e99eb9

```
➜  ~ docker rmi fce289e99eb9
Error response from daemon: conflict: unable to delete fce289e99eb9 (must be forced) - image is being used by stopped container 84e59cd31860
```

* ```
  ➜  ~ docker rmi -f fce289e99eb9  删除镜像  latest 最新的 可以删除多个
  Untagged: hello-world:latest
  Untagged: hello-world@sha256:f9dfddf63636d84ef479d645ab5885156ae030f611a56f3a7ac7f2fdd86d7e4e
  Deleted: sha256:fce289e99eb9bca977dae136fbe2a82b6b7d4c372474c9235adc1741675f587e
  
  ```

### 容器

有镜像才能启动该镜像的容器

* 新建并启动容器 docker run -i -t --name mycentos PID
* 列出现在正在运行的容器 docker ps [options] -n, -l
* exit  停止并退出容器  Ctrl + p + q 退出不停止
* 启动容器 docker start 容器id
* docker stop 容器id
* docker kill 容器id
* docker rm -f 容器  删除容器
* docker ps 查看运行的容器
* docker exec -t pid bash   进入容器
* 

### 镜像

镜像就是一种轻量级、可执行的独立软件包，用来打包软件运行的环境和基于运行环境开发的软件，它包含运行某个软件所需的所需的所有内容。包括代码、运行时、库、环境变量和配置文件。

镜像的底层 联合文件系统（UnionFS）

* docker  run -it -p 8888:8080  tomcat   -p 主机端口，docker容器的端口

-P 随机分配端口   i 交互  t 终端    8888 docker的端口  8080 tomcat的端口



* docker commit -m=“提交的描述信息” -a=“作者” 容器ID  要创建的镜像名标签名  docker commit -a="" -m="" tomcatPID testTOMCAT1.1
* 

#### docker  容器数据卷

卷就是目录或文件，存在于一个或多个容器中，由docker挂载到容器上，但不属于联合文件系统，因此能绕过UnionFile System提供一些用于存储或共享数据的特性

卷的设计目的就是数据的持久化，完全独立于容器的生存周期，因此docker不会在容器删除时删除其挂载的卷。

特点：

1. 数据卷可在容器之间共享或重用数据
2. 卷中的更改可以直接生效
3. 数据卷中的更改不会包含在镜像的更新中
4. 数据卷的生命周期一直持续到没有容器使用它为止 

* docker run -it  -v /宿主机的绝对路径目录：/容器内的目录  镜像名 

docker run  -it  -v  /mydataVolume:/dataVolume  centos   命令运行后会产生这两个文件夹 mydataVolume dataVolume  

* docker inspect  容器PID  会将容器的描述一json串的格式输出
* touch host.text 创建文件

```
➜  ~ docker run -it -v /mydataVolume:/dataVolume  centos
[root@df49d5c5fcc2 /]#

```

* host

```
➜  ~ ls
conf                 lanmp_wdcp_ins.sh    phps.sh    zsh-syntax-highlighting
inf                  lanmp_wdcp_ins.sh.1  phps.sh.1
lanmp_laster.tar.gz  lib                  src
lanmp.sh             logs                 test
➜  ~ pwd
/root
➜  ~ cd ..
➜  / ls
b     default  home   lost+found  mydataVolume  root  srv  usr
bin   dev      lib    media       opt           run   sys  var
boot  etc      lib64  mnt         proc          sbin  tmp  www
➜  /

```

* container

```

asus@zhaohaisong MINGW64 ~/Desktop
$ ssh root@120.77.39.56
root@120.77.39.56's password:
Last login: Thu Apr  2 23:23:55 2020 from 60.186.28.242

Welcome to Alibaba Cloud Elastic Compute Service !

➜  ~ docker run -it centos
[root@4b74a22f2528 /]# ls
bin  etc   lib    lost+found  mnt  proc  run   srv  tmp  var
dev  home  lib64  media       opt  root  sbin  sys  usr
[root@4b74a22f2528 /]# ls
bin  etc   lib    lost+found  mnt  proc  run   srv  tmp  var
dev  home  lib64  media       opt  root  sbin  sys  usr
[root@4b74a22f2528 /]# pwd
/
[root@4b74a22f2528 /]#

```

