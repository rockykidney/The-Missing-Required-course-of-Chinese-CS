**VNC****概述**

　　VNC (Virtual Network Computing)是[虚拟网络](http://baike.baidu.com/view/747782.htm)[计算机](http://baike.baidu.com/view/3314.htm)的缩写。VNC 是一款优秀的[远程控制](http://baike.baidu.com/view/51293.htm)工具软件，由著名的 [AT&T](http://baike.baidu.com/view/259956.htm) 的欧洲研究实验室开发的。VNC 是在基于 [UNIX](http://baike.baidu.com/view/8095.htm) 和 [Linux](http://baike.baidu.com/view/1634.htm)[操作系统](http://baike.baidu.com/view/880.htm)的免费的[开源软件](http://baike.baidu.com/view/444964.htm)，[远程控制](http://baike.baidu.com/view/51293.htm)能力强大，高效实用，其性能可以和 [Windows](http://baike.baidu.com/view/4821.htm) 或 [MAC](http://baike.baidu.com/view/32702.htm) 中的任何远程控制软件媲美。在 Linux 中，VNC 包括以下四个命令：vncserver，vncviewer，vncpasswd，和 vncconnect。大多数情况下只需要其中的两个命令：vncserver 和 vncviewer。目前，原来的AT&T版本已经不再使用，因为更多有重大改善的分支版本已经出现， 像是RealVNC， VNC tight 和UltraVNC。 Real VNC 是当前最活跃和强大的主流应用。

　　VNC一共有三个版本，TightVNC、RealVNC、UltraVNC，RealVNC旨在推进商业化，因此需要License；TightVNC旨在改善服务器和查看器之间的VNC压缩，但是该版本最大的缺点是不能远程复制粘贴，而RealVNC则可以（这里的复制粘贴指的是文本的复制粘贴，文件的复制粘贴各版本都不支持）；最后是UltraVNC，它则结合了其他两个版本的优势。

 **RealVNC官方网址**  :  [http://www.realvnc.com/](http://www.realvnc.com/)

 **Tight VNC官方网址**:  [http://www.tightvnc.com/](http://www.tightvnc.com/)

 **UltraVNC官方网址** ： [http://www.uvnc.com/](http://www.uvnc.com/)

**VNC****原理**

VNC系统由客户端，服务端和一个协议组成。VNC的服务端目的是分享其所运行机器的屏幕， 服务端被动的允许客户端控制它。 VNC客户端（或Viewer） 观察控制服务端，与服务端交互。 VNC 协议 Protocol (RFB)是一个简单的协议，传送服务端的原始图像到客户端（一个X,Y 位置上的正方形的点阵数据）， 客户端传送事件消息到服务端。

服务器发送小方块的帧缓存给客户端，在最简单的情况，VNC协议使用大量的带宽，因此各种各样的方法被发明出来减少通讯的开支，举例来说，有各种各样的编码方法来决定最有效率的方法来传送这些点阵方块）

协议允许客户端和服务端去协议哪种编码会被使用，最简单的编码，被大多数客户端和服务端所支持的是， 从左到右的像素扫描数据的原始编码， 当原始的满屏被发送后，只发送变化的方块区域。这种编码在幁间只有小部分屏幕变化的情况下工作的非常好（像是鼠标键在桌面移动的情况，或在光标处敲击文字），不过如果大量的像素同时变化带宽将会增加的非常高，像是拖动一个窗口或观看全屏录像。

VNC默认使用[TCP](http://zh.wikipedia.org/wiki/TCP)端口5900至5906，而JAVA的VNC客户端使用5800至5806。一个服务端可以在5500口用“监听模式”连接一个客户端，使用监听模式的一个好处是服务端不需要设置防火墙。

[UNIX](http://zh.wikipedia.org/wiki/UNIX)上的VNC称为xvnc，同时扮演两种角色，对[X窗口系统](http://zh.wikipedia.org/wiki/X_Window%E7%B3%BB%E7%B5%B1)的应用程序来说它是X server，对于VNC客户端来说它是VNC服务器程序。

## 一、tigervnc官网

[https://tigervnc.org/](https://tigervnc.org/)

## 二、安装tigervnc

注意：tigervnc 需要系统具有桌面环境，如果没有桌面环境需要先安装

apt install tigervnc-standalone-server

## 三、设置连接密码

vncpasswd

## 四、启动tigervnc

```
tigervncserver  :1 -localhost no -geometry 1920x1080
```

```
# :1 表示vnc以 5900 +1的端口号运行，及启动的端口号为：5901
# -localhost no 表示，任意地方都可以连接vnc服务  
# -geometry 1920x1080 指定运行分辨率
```

# 查看启动的vnc服务

```
root@debian:~# tigervncserver -list
TigerVNC server sessions:
X DISPLAY #     RFB PORT #      RFB UNIX PATH   PROCESS ID #    SERVER
1               5901                            751             Xtigervnc
```

# 关闭vnc进程

 关闭所有vnc进程
tigervncserver -kill

$$
# 关闭指定vnc进程 （关闭端口号为：5902的vnc进程）
$$
tigervncserver -kill ：2











## 1. 安装VNC

sudo yum install tigervnc tigervnc-server

## 2. 修改配置

sudo vim /etc/sysconfig/vncservers

修改内容如下：

![复制代码](https://assets.cnblogs.com/images/copycode.gif)

```
# THIS FILE HAS BEEN REPLACED BY /lib/systemd/system/vncserver@.service
 
# VNCSERVERS="桌面号:系统用户 桌面号:系统用户"
VNCSERVERS="1:zhang 2:root"
 
# VNCSERVERARGS[桌面号]="-geometry 分辨率 -alwaysshared[允许多个客户端同时连接] -depth [色深，值有8,16,24,32]"
VNCSERVERARGS[1]="-geometry 1024x768 -alwaysshared -depth 24"
VNCSERVERARGS[2]="-geometry 1024x768 -alwaysshared -depth 24"
```

![复制代码](https://assets.cnblogs.com/images/copycode.gif)

1. 设置密码

vncpasswd

2. 启动服务

vncserver

*防火墙开放端口

首先判断`firewalld`是否启动，输入以下命令判断

sudo firewall-cmd --state

如果启动应该输出：running

如果是：`not running`，执行下面命令

sudo systemctl start firewalld

添加端口号5901-5905

sudo firewall-cmd --permanent --zone=public --add-port=5901-5905/tcp

重新加载防火墙

sudo firewall-cmd --reload

可以使用下面命令查看端口号是否被加入

firewall-cmd --list-all-zones
# 或者(只查看活动的)
firewall-cmd --list-all

删除规则例子

firewall-cmd --permanent --zone=public --remove-port=5901-5905/tcp

3. 客户端连接

若没有客户端，可前往 [这里下载](https://download.csdn.net/download/u013992330/17091046)

![](https://img2022.cnblogs.com/blog/333516/202207/333516-20220722215617784-480217755.png)

 ![](https://img2022.cnblogs.com/blog/333516/202207/333516-20220722215624898-1188393738.png)

# 二、realvnc

## 4. 下载deb或rpm安装包

官方下载地址：[https://www.realvnc.com/en/connect/download/vnc/](https://www.realvnc.com/en/connect/download/vnc/)

CSDN下载地址：[https://download.csdn.net/download/u013992330/18503629](https://download.csdn.net/download/u013992330/18503629)

## 5. 安装

下载之后直接安装即可，例如kylin平台使用deb包进行安装：

|   |   |
|---|---|
|1|`sudo dpkg -i VNC-Server-6.7.4-Linux-x64.deb`|

## 6. 加载VNC License

由于RealVNC旨在推进商业化，因此在安装之后需要使用vnclicense加载License，命令如下：

vnclicense -add xxxx  # xxxx 是License序列号，也就是realvnc license key，自己想办法搞到。

vnclicense工具的其他用法可使用vnclicense --help查看。

![](https://img2022.cnblogs.com/blog/333516/202207/333516-20220722215806152-481518961.png)

 License加载之后，可使用vnclicense -list查看：

![](https://img2022.cnblogs.com/blog/333516/202207/333516-20220722215817931-704807151.png)

## 7. 启动VNC

realvnc有两种启动方式，一种是virtual，一种是x11，virtual跟上边的TightVNC原理差不多，x11则是直接连接的服务器的X桌面，跟你直接在服务器上操作是一样的。两种选择其中一种启动、使用即可。

a.  virtual启动：

systemctl start vncserver-virtuald.service

查看启动状态：

systemctl status vncserver-virtuald.service

b.  x11启动：

systemctl start vncserver-x11-serviced.service

查看启动状态：

systemctl status vncserver-x11-serviced.service

## 8. 连接VNC Server

连接方法跟上边的TightVNC一样，但是我在连接的时候，使用 IP:桌面号 的方式连接不上，因此查看了它监听的端口，使用端口连接成功了，端口查看命令：

netstat -tnlp |grep vnc

![](https://img2022.cnblogs.com/blog/333516/202207/333516-20220722220049472-1505855111.png)

 可以看到virtual的监听端口是5999，x11的监听端口是5900，现在使用ip:port的方式就可以连接了。

![](https://img2022.cnblogs.com/blog/333516/202207/333516-20220722220109164-1509888973.png)

————————————————  
版权声明：本文为CSDN博主「password-u」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。  
原文链接：https://blog.csdn.net/u013992330/article/details/116049635


