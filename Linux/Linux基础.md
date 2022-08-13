### 1.Ubuntu系统安装
&ensp;&ensp;对于Ubuntu系统安装一般分为两种：1.安装虚拟机，在虚拟机里面安装Ubuntu系统；（虚拟机可以采用VMware软件，安装比较简单，但是用起来会比较卡顿）2.采用U盘安装双系统。（运行速度较快，但是安装比较麻烦，安装失败的话电脑系统受影响）
1.虚拟机VMware安装Ubuntu系统（安装比较简单，随便百度一下就可以。）
2.双系统安装Ubuntu系统
&emsp;&ensp;主要参考文章
1.[Ubuntu 18.04](https://blog.csdn.net/weixin_39831242/article/details/110110796?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_baidulandingword~default-1-110110796-blog-108490098.pc_relevant_downloadblacklistv1&spm=1001.2101.3001.4242.2&utm_relevant_index=4)
2.[Windows和Ubuntu双系统安装](https://baijiahao.baidu.com/s?id=1704949448370974960&wfr=spider&for=pc) 在给Ubuntu系统分区的时候可以参考，分为`/boot`,`交换空间`,`/`三个区，第一个区存放系统，第二个区数据交换，第三个区存放别的东西。
###  2.Linux命令
```shell
pwd #打印当前目录
ps #进程状态
ls #列出当前路径的信息
clear #清屏命令
history #查看命令历史
dir #列出当路径的信息
mkdir [目录名] #创建目录
rmdir [目录名] #删除目录
rm [文件名] #删除文件(只能删除空的文件)
rm -r [文件名] #删除文件夹和里面的文件
rm -rf /home/he/* #把he文件夹下的所有东西全部删除
touch [文件名] #创建文件
mv [文件名] [路径名] #移动文件
cp [文件名] [路径名] #复制文件
g++ [文件名] -o [编译之后的名字] C++程序编译 ex: g++ test.cpp -o test
./[文件名字] C++程序运行 ex:./test
python [文件名] python程序运行 ex:python test.py
df -lh #查看硬盘信息
ifconfig #查看ip地址
sudo apt-get update #读取软件仓库的软件列表，把链接保存到本地
sudo apt-get upgrade #把已经安装的软件包升级
sudo apt-get clean #把安装包删除
sudo apt-get install -y [package_name]  #-y是不需要ubuntu提示你，直接安装
apt-cahe search [packagename] #搜索软件包
apt-cache depends [packagename] #查看安装包的依赖，反向依赖为rdepends
locale #查看语言环境，中英文设置
cat [filename] #查看文件内容
vim [filename] #对文件进行编辑，按i进入编辑，编辑模式Esc退出，q不编辑退出，q!编辑不保存退出，wq编辑保存退出
su - # 切换为root用户
su [usrname] # 切换为普通用户
cmake #编译，根据CMakeLists.txt生成makefiles文件
make -j2 #采用双核去编译 make也可单独使用
make install #对编译的文件进行安装
cp a.txt b.txt #把a的内容复制给b
sudo passwd root #更改root密码，第一次进root的时候使用
df -lh #查看硬盘信息
du -h --max-depth=1 #查看该文件夹下文件大小，最多该文件夹下一级目录
tail -f [log_name] #实时显示log文件内容
systemctl start [service_name] #systemctl是系统管理命令,启动一个service
systemctl stop [service_name] #停止service
systemctl restart [service_name] #重新启动service
dpkg -l #查看已经安装的软件
scp [local_file] remote_username@remote_ip:remote_folder #用于Linux之间复制文件
sudo find / -name [file_name] #查找文件的地址，‘/’表示所有文件夹下查找，'.'表示该目录下查找"*.a"查找所有静态库。
sudo vim ~/.bashrc #打开ubuntu的环境变量设置








```
### 3.Linux源设置
&emsp;&emsp;在linux中，源全称“软件源”，是Linux系统免费的应用程序安装仓库，很多的应用软件都会这收录到这个仓库里面。`apt-get update`作用是访问源列表里的每个网址，并读取软件列表，然后保存在本地电脑。源列表在`/etc/apt/sources.list`中，因此想要下载软件，需要对源进行合理的设置。
其中，`sources.list`中建议设置为

```shell
# deb cdrom:[Ubuntu 20.04.3 LTS _Focal Fossa_ - Release amd64 (20210819)]/ focal main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirrors.aliyun.com/ubuntu/ focal main restricted
# deb-src http://cn.archive.ubuntu.com/ubuntu/ focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirrors.aliyun.com/ubuntu/ focal-updates main restricted
# deb-src http://cn.archive.ubuntu.com/ubuntu/ focal-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirrors.aliyun.com/ubuntu/ focal universe
# deb-src http://cn.archive.ubuntu.com/ubuntu/ focal universe
deb http://mirrors.aliyun.com/ubuntu/ focal-updates universe
# deb-src http://cn.archive.ubuntu.com/ubuntu/ focal-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirrors.aliyun.com/ubuntu/ focal multiverse
# deb-src http://cn.archive.ubuntu.com/ubuntu/ focal multiverse
deb http://mirrors.aliyun.com/ubuntu/ focal-updates multiverse
# deb-src http://cn.archive.ubuntu.com/ubuntu/ focal-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirrors.aliyun.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://cn.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu focal partner
# deb-src http://archive.canonical.com/ubuntu focal partner

deb http://mirrors.aliyun.com/ubuntu/ focal-security main restricted
# deb-src http://security.ubuntu.com/ubuntu focal-security main restricted
deb http://mirrors.aliyun.com/ubuntu/ focal-security universe
# deb-src http://security.ubuntu.com/ubuntu focal-security universe
deb http://mirrors.aliyun.com/ubuntu/ focal-security multiverse
# deb-src http://security.ubuntu.com/ubuntu focal-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
```
&emsp;&emsp;在`Ubuntu桌面版`中`Software & Updates`里面的设置可以如下:
![在这里插入图片描述](https://img-blog.csdnimg.cn/5ba5c5f852eb4221850cf13cf583f397.png#pic_center)![在这里插入图片描述](https://img-blog.csdnimg.cn/5e2262a238904b098c9eb22a69e408bb.png#pic_center)



### 4.Linux插件
#### 4.1 便于窗口管理的插件`terminator`，安装方法比较简单，在终端输入命令行
```shell
sudo apt-get install terminator
```
最终的效果为
![终端管理](https://img-blog.csdnimg.cn/425275b5a10940349246440a77f87efe.png)
#### 4.2 VScode的安装
&emsp;&emsp;在VScode的[官网](https://code.visualstudio.com/)下载`deb`类型的文件到本地，到本地之后可以直接选择`Ubuntu Software`进行安装，或者采用命令行进行安装，后面的是安装包的名字。
```shell
sudo dpkg -i code_1.62.2-1636665017_amd64.deb
```
#### 4.3 其他软件的安装
```shell
sudo apt-get install python #python的安装
sudo apt-get install gcc #C++的安装
sudo apt-get install git #git的安装
```
