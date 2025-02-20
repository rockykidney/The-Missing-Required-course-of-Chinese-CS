
- SSH（Secure Shell）：一种加密的网络协议，用于远程登录和执行命令。
- Telnet：一种基于文本的[远程管理协议](https://zhida.zhihu.com/search?content_id=572546091&content_type=Answer&match_order=1&q=%E8%BF%9C%E7%A8%8B%E7%AE%A1%E7%90%86%E5%8D%8F%E8%AE%AE&zhida_source=entity)- ，用于远程登录和执行命令。
- RDP（Remote Desktop Protocol）：一种[远程桌面协议](https://zhida.zhihu.com/search?content_id=572546091&content_type=Answer&match_order=1&q=%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2%E5%8D%8F%E8%AE%AE&zhida_source=entity)

- ，用于远程控制Windows操作系统。
- VNC（Virtual Network Computing）：一种远程桌面协议，用于远程控制Linux和Windows操作系统。
- FTP（File Transfer Protocol）：一种文件传输协议，用于在本地计算机和远程服务器之间传输文件。
- SCP（Secure Copy）：一种加密的文件传输协议，用于在本地计算机和远程服务器之间传输文件。
- SFTP（Secure File Transfer Protocol）：一种加密的文件传输协议，用于在本地计算机和远程服务器之间传输文件。
- SNMP（Simple Network Management Protocol）：一种网络管理协议，用于监控和管理网络设备。

## SSH

SSH（Secure Shell）是一种网络协议，用于在不安全的网络中以安全的方式进行远程登录和其他网络服务。它可以加密数据传输、验证远程主机的身份、防止[中间人攻击](https://zhida.zhihu.com/search?content_id=572546091&content_type=Answer&match_order=1&q=%E4%B8%AD%E9%97%B4%E4%BA%BA%E6%94%BB%E5%87%BB&zhida_source=entity)

等，使得用户在远程登录和数据传输时能够更加安全可靠。SSH协议被广泛用于Linux和其他类Unix操作系统中进行远程登录和远程管理。

![](https://pic1.zhimg.com/80/v2-7a8ee744834489813f2900efce803c41_720w.webp?source=2c26e567)

常见的SSH工具：

1. OpenSSH：是一个用于Linux和Unix操作系统的SSH实现，提供了加密的远程登录和其他网络服务。OpenSSH也为Windows提供了一个客户端。
2. PuTTY：是一个Windows上常用的SSH客户端，支持SSH、Telnet、rlogin和串口连接，提供了图形界面和命令行界面。
3. SecureCRT：是一个商业级SSH客户端，支持SSH、Telnet、rlogin和串口连接，具有多语言、多会话、自动登录、自动重连等特性。
4. Termius：是一个跨平台的SSH客户端，支持多种操作系统和设备，具有图形界面和命令行界面，提供了多种安全认证方式和便捷的文件传输功能。
5. MobaXterm：是一个Windows上的SSH客户端，支持SSH、Telnet、RDP、VNC等协议，具有分屏、多标签页、X11转发等特性。

  

## Telnet

Telnet是一种用于远程登录到计算机网络上的协议。它允许用户在本地计算机上使用命令行界面来连接到远程计算机，并通过输入命令来控制远程计算机。Telnet协议最初是在20世纪60年代开发出来的，现在已经被SSH协议所取代，因为SSH协议提供了更高的安全性。

![](https://picx.zhimg.com/80/v2-43c5b9545ef84bc4b00a0908e49cff78_720w.webp?source=2c26e567)

常见的Telnet工具：

6. PuTTY：跨平台的Telnet和SSH客户端，支持Windows、Linux、Mac OS等操作系统。
7. SecureCRT：一款强大的终端仿真软件，支持Telnet、SSH、SFTP等协议。
8. iTerm2：仅适用于Mac OS的命令行工具，支持Telnet、SSH等协议。
9. Tera Term：一个开源的[终端仿真程序](https://zhida.zhihu.com/search?content_id=572546091&content_type=Answer&match_order=1&q=%E7%BB%88%E7%AB%AF%E4%BB%BF%E7%9C%9F%E7%A8%8B%E5%BA%8F&zhida_source=entity)

10. ，支持Telnet、SSH等协议，仅适用于Windows系统。
11. mRemoteNG：一个开源的远程连接管理器，支持多种协议，包括Telnet。
12. Xshell：一个Windows下的SSH/Telnet客户端，支持多语言界面，具有高级调试功能。

此外还有AbsoluteTelnet、Solar-PuTTY、Telnet Client、KiTTY、MobaXterm等工具。

## RDP

RDP（远程桌面协议）是一种微软开发的协议，用于在远程计算机之间共享桌面、应用程序和其他资源。通过RDP，用户可以从另一个计算机上访问并控制远程计算机，就像坐在远程计算机前一样。这使得远程工作、技术支持和协作变得更加便捷和高效。

![](https://picx.zhimg.com/80/v2-91085f8b86ce1b648090c7ffa9c4c4e8_720w.webp?source=2c26e567)

常见的 RDP 工具：

13. Windows 自带的[远程桌面连接](https://zhida.zhihu.com/search?content_id=572546091&content_type=Answer&match_order=1&q=%E8%BF%9C%E7%A8%8B%E6%A1%8C%E9%9D%A2%E8%BF%9E%E6%8E%A5&zhida_source=entity)

14. （Remote Desktop Connection）。
15. TeamViewer。
16. AnyDesk。
17. VNC（Virtual Network Computing）。
18. Chrome 远程桌面（Chrome Remote Desktop）。
19. LogMeIn。
20. Splashtop。
21. Remote Utilities

这些工具均可用于远程连接至另一台电脑进行控制和管理。

## VNC

VNC是Virtual Network Computing（虚拟网络计算）的缩写，它是一种用于远程桌面控制的开放源码软件。通过VNC，用户可以在本地计算机上控制远程计算机的桌面，并且可以实现文件共享、剪贴板共享、打印机共享等功能。VNC支持多种操作系统和平台，包括Linux、Windows、Mac OS X等，而且它的安全性也得到不断改进和加强。

![](https://pica.zhimg.com/80/v2-1791a59afcee1537373e58211dff59e8_720w.webp?source=2c26e567)

常见的VNC工具：

22. RealVNC：一款跨平台的VNC工具，支持Windows、Mac OS X、Linux等系统。
23. TightVNC：一款免费的VNC工具，支持Windows和Linux系统。
24. UltraVNC：一款功能强大的VNC工具，支持Windows系统。
25. TigerVNC：一款基于RealVNC开发的VNC工具，支持Windows、Linux、Mac OS X等系统。
26. TurboVNC：一款高性能的VNC工具，支持Windows和Linux系统。
27. Remmina：一款支持RDP、SSH、VNC等协议的远程桌面客户端，支持多个操作系统。
28. Vinagre：一款基于GTK+的远程桌面客户端，支持VNC、SSH等协议，适用于Linux系统。

## FTP

FTP是File Transfer Protocol（文件传输协议）的缩写。它是用于在计算机之间传输文件的[标准网络协议](https://zhida.zhihu.com/search?content_id=572546091&content_type=Answer&match_order=1&q=%E6%A0%87%E5%87%86%E7%BD%91%E7%BB%9C%E5%8D%8F%E8%AE%AE&zhida_source=entity)

。使用FTP，用户可以将文件从一个计算机传输到另一个计算机，也可以下载远程计算机上的文件。FTP通常用于网站管理、软件发布和文件共享等任务。

![](https://pic1.zhimg.com/80/v2-709b56039dca803c4b59322e975f9c9e_720w.webp?source=2c26e567)

常见的FTP工具有：FileZilla、WinSCP、Cyberduck、Transmit、CuteFTP、Fetch、Core FTP、 WS_FTP Pro、 SmartFTP、 FlashFXP等。

## SCP

SCP是Secure Copy Protocol的缩写，是一种网络协议，用于在计算机之间进行安全的文件传输。SCP使用SSH（Secure Shell）加密协议来保护数据传输的安全性和完整性。它被广泛用于Linux系统中，通常用于将文件从一个Linux服务器复制到另一个Linux服务器。

常见的SCP工具有：

29. WinSCP：用于Windows系统的SCP客户端软件，支持FTP、SFTP、WebDAV等协议。
30. PuTTY：SSH和SCP客户端工具，支持多种加密方法。
31. Cyberduck：跨平台的FTP、SFTP、WebDAV、Amazon S3等协议的客户端软件。
32. FileZilla：免费开源的FTP、SFTP客户端软件，支持Windows、Linux和MacOS。
33. [scp命令](https://zhida.zhihu.com/search?content_id=572546091&content_type=Answer&match_order=1&q=scp%E5%91%BD%E4%BB%A4&zhida_source=entity)

34. ：在Linux和Unix系统中自带的SCP命令行工具，可以通过终端使用。

![](https://picx.zhimg.com/80/v2-af781c38b13cc70020bbed666612d3dd_720w.webp?source=2c26e567)

[发布于 2023-04-14 14:11](https://www.zhihu.com/question/590668335/answer/2983532004)・IP 属地广东

还没有人送礼物，鼓励一下作者吧

#### 更多回答

[![惰惰猴](https://picx.zhimg.com/v2-a75d5e8ef977b3b390acfd524d71a42d_l.jpg?source=1def8aca)](https://www.zhihu.com/people/patrickhe)

[惰惰猴](https://www.zhihu.com/people/patrickhe)

[​![知乎知识会员](https://picx.zhimg.com/v2-57fe7feb4813331d5eca02ef731e12c9.jpg?source=88ceefae)](https://www.zhihu.com/kvip/purchase)

油腻网络工程师、DevNet人才、老年电脑爱好者、军迷

谢邀[@Nick](https://www.zhihu.com/people/nick-php)

​

目录

收起

一、CLI 模式

1、Telnet

2、SSH（Secure Shell）

二、GUI 模式

1、VNC（Virtual Network Computing）

2、RDP（Remote Desktop Protocol）

三、总结

## 一、CLI 模式

### 1、Telnet

Telnet 是一种早期的远程管理协议，用于在本地计算机和远程计算机之间建立连接。然而，由于 Telnet 不加密通信内容，安全性较差，在实际应用中较少使用。

### 2、SSH（Secure Shell）

SSH 是一种加密的远程管理协议，用于在本地计算机和远程计算机之间建立安全的连接，以进行远程管理操作。SSH 提供了许多安全功能，像加密、身份验证和密钥管理等。许多GNU/Linux发行版大多使用OpenSSH，其组件包含 SSH、SCP、SFTP .

## 二、GUI 模式

### 1、VNC（Virtual Network Computing）

VNC 是一种远程桌面协议，类似于 RDP，可让用户在本地计算机上通过网络连接到远程计算机，以远程控制远程计算机。VNC 的优点是可用性广泛，支持多种操作系统。

### 2、RDP（Remote Desktop Protocol）

RDP 是一种远程桌面协议，可让用户在本地计算机上通过网络连接到远程计算机，以远程控制远程计算机。RDP 可以用于远程管理、技术支持和远程协作等应用场景。

## 三、总结

通常，CLI 界面，SSH 最为常见。而 VNC 和 RDP 则被广泛用于 类Unix（GNU/Linux） 操作系统的远程桌面控制。











## 四、


# 在 Ubuntu 上搭建 RDP（Remote Desktop Protocol）服务器可以通过以下步骤实现：
### 安装 X Window System

X Window System 是 Linux 系统中图形化界面的基础，若 Ubuntu 系统尚未安装，可通过以下命令安装：

```plaintext
sudo apt update
sudo apt install xorg
```

### 安装 RDP 服务器软件

常见的 RDP 服务器软件有 xrdp 和 rdesktop 等，以 xrdp 为例，使用以下命令安装：

```plaintext
sudo apt install xrdp
```

### 配置 xrdp

35. 安装完成后，可能需要对 xrdp 进行一些配置，配置文件通常位于`/etc/xrdp/`目录下。
36. 主要配置文件是`xrdp.ini`，可以根据需要进行修改。例如，如果要更改允许访问的用户组等，可以在文件中找到相应的配置项进行调整。

### 启动 xrdp 服务

安装和配置完成后，使用以下命令启动 xrdp 服务：

sudo systemctl start xrdp

可以使用以下命令检查服务是否启动成功：

```plaintext
sudo systemctl status xrdp
```

若服务正常运行，会显示相关的运行信息。

### 设置防火墙

如果 Ubuntu 系统启用了防火墙，需要允许 RDP 连接通过防火墙。可以使用以下命令允许 RDP 的默认端口 3389 通过防火墙：

收起

```plaintext
sudo ufw allow 3389/tcp
```

### 客户端连接

在远程客户端设备上，使用 RDP 客户端软件，如 Windows 系统自带的 “远程桌面连接”，输入 Ubuntu 服务器的 IP 地址，点击 “连接”，然后输入 Ubuntu 系统的用户名和密码，即可连接到 Ubuntu 的远程桌面。



分享

