### 1.为什么要用Docker
&emsp;&emsp;在进行软件开发的时候，软件运行环境以及软件的依赖，配置起来非常麻烦，因此就产生了这么一种想法，自己调试好的东西能不能把运行环境以及软件包依赖一起打包到一个东西里面，方便开发者进行部署。
### 2. Docker是什么
&emsp;&emsp;Docker是一个应用打包，分发，部署的工具，可以理解为一个轻量虚拟机，只虚拟软件运行所需要的环境。Docker里面有`镜像(Image)`,`容器(Container)`,`仓库(Repository)`三个概念。
- 镜像：就相当于是一个 root 文件系统。比如官方镜像 ubuntu:16.04 就包含了完整的一套 Ubuntu16.04 最小系统的 root 文件系统。可以把他理解为类
- 容器：镜像和容器的关系，就像是面向对象程序设计中的类和实例一样，镜像是静态的定义，`容器是镜像运行时的实体`。容器可以被创建、启动、停止、删除、暂停等。
- 仓库：仓库可看成一个代码控制中心，用来保存镜像。
### 3.Docker安装和使用
#### 3.1 Ubuntu安装Docker
&emsp;&emsp;在安装之前，你可能需要先安装以下`curl`
```shell
sudo apt-get install curl
```
直接采用`curl`命令进行安装，
```shell
curl -fsSL https://get.docker.com | bash -s docker --mirror Aliyun
```
#### 3.2 Docker常用命令
```shell
docker pull hello-world #拉取名为hello-world的镜像，默认版本为latest
docker run -it ubuntu robot \bin\bash #在ubuntu镜像中新建一个名字为robot容器，并在容器里面运行\bin\bash命令，-it表示交互模式。
docker start <container_name> #启动容器
docker restart <container_name> #重启容器
docker rm <container_name>  #移除容器
docker rmi <image_name> #移除镜像
docker images #列出本地镜像
docker ps #展示正在运行的容器
docker ps -a #展示所有的容器，包含未运行的容器
docker exec -u <usr_name> -it <container_name> /bin/bash #用usr_name进入到容器中并执行命令
docker rename <container_name> <new_container_name>  #对容器重新命名
docker run -it -v /home/workspace:/home/workspace <image_name> /bin/bash #把主机文件目录/home/workspace挂载到docker容器的/home/workspace目录下
docker commit <container_id> <image_name> #把容器保存成镜像
docker save <image_name> > <path/name>.tar #把镜像打包成tar文件
docker load < <path/name>.tar #根据tar文件生成新的镜像
```
#### 3.3Docker打包镜像
![images](https://img-blog.csdnimg.cn/34692c0613ff4bc39ec76d2c3f84b609.png)
&emsp;&emsp;比如要打包`foxy-x86`镜像，直接把镜像保存成`tar`文件。
```shell
docker save matrixhub.geekplus.cc/matrix/ros:foxy-x86 > /home/heyongqi/foxy.tar
```
&emsp;&emsp;把`tar`文件拷贝到新的机器上，执行命令
```shell
docker load < /home/heyongqi/foxy.tar
```
&emsp;&emsp;之后启动容器就完成了，如果要打包容器到其他电脑上，需要先把容器打包成镜像，后面操作与上面一样
```shell
docker commit <container_id> <image_name>
```