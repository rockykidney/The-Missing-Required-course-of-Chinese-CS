# 如何在Linux系统上安装图形化界面

更新时间：2024-12-19 15:05:02

[产品详情](https://www.aliyun.com/product/ecs)

[我的收藏](https://help.aliyun.com/my_favorites.html)

在需要直观操作界面、进行图形设计或多媒体处理、执行日常办公任务或对命令行不熟悉时，使用图形化用户界面（GUI）能够极大地提升操作体验和工作效率。基于性能及通用性等因素考虑，阿里云云服务器ECS实例提供的公共Linux系统镜像**默认不安装**图形化桌面组件（GNOME/KDE Plasma/MATE Desktop/Ubuntu Desktop）。本文介绍为常见Linux系统实例图形化界面的操作步骤和常见问题。

## GUI基本介绍和组成

### **什么是Linux GUI**

GUI全称为Graphical User Interface，中文全称为**图形用户界面**。在 Linux 操作系统中，图形用户界面（GUI） 是一种允许用户通过图形元素（如窗口、图标、按钮、菜单等）与系统进行交互的界面，类似Windows操作界面。与传统的命令行界面（CLI）相比，GUI 更加直观和用户友好，适合大多数用户进行日常操作。

### **主要组件**

- 显示服务器（Display Server）

  显示服务器负责管理图形显示和输入设备。常见的显示服务器有 Xorg（X11 的一个实现）和 Wayland。X11 协议的实现是 Linux  图形环境的基础，负责管理显示、输入设备（如键盘、鼠标）以及窗口的绘制。Wayland是一种较新的显示协议，旨在取代  X11，提供更高的效率、更好的安全性及更流畅的图形体验。许多现代桌面环境已经开始支持 Wayland。

- 窗口管理器（Window Manager）

  窗口管理器负责窗口的外观和行为，如窗口的移动、大小调整、最小化等。窗口管理器可以是独立的，也可以集成在桌面环境中。

- 桌面环境（Desktop Environment）

  桌面环境是一个集合，包含了窗口管理器、图标、工具栏、系统设置等组件，提供一致的用户体验。常见的桌面环境有 GNOME、KDE Plasma、XFCE、LXDE 等。

- 应用程序框架和工具包

  包含各类应用程序和系统组件，如文本编辑器、浏览器、文件管理器、多媒体播放器等，这些组件共同构成了完整的图形用户体验。

### **常见桌面环境**

- GNOME

  GNOME 是一个现代化、简洁且注重用户体验的桌面环境。它采用了 GTK 工具包，拥有自己的应用程序集，如 Nautilus 文件管理器和 GNOME Terminal。GNOME 注重一致性和易用性，适合初学者和希望简洁界面的用户。更多信息，请参见[GNOME](https://www.gnome.org/)。

- KDE Plasma

  KDE Plasma 是一个功能丰富、可高度自定义的桌面环境，基于 Qt 工具包。它提供了丰富的应用程序生态，如 Dolphin 文件管理器和 Konsole 终端。KDE 适合需要高度定制和丰富功能的高级用户。更多信息，请参见[The KDE Plasma desktop](https://fedoraproject.org/atomic-desktops/kinoite/)。

- XFCE

  XFCE 是一个轻量级、资源占用低的桌面环境，适合旧硬件或需要高性能的系统。它提供基本的桌面功能，支持 GTK 工具包，兼顾性能和用户体验。更多信息，请参见[Xfce Desktop](https://www.xfce.org/)。

- LXDE/LXQt

  LXDE 和 LXQt 是更加轻量级的桌面环境，专为低资源系统设计。LXDE 基于 GTK，而 LXQt 则基于 Qt，提供快速、简洁的用户界面。更多信息，请参见[LXQt](https://lxqt-project.org/)。

- MATE Desktop

  基于GNOME 2，传统桌面布局，稳定且轻量。适合喜欢经典桌面体验的用户。应用包括Ubuntu MATE、Linux Mint MATE版等。更多信息，请参见[MATE Desktop](https://mate-desktop.org/)。

## 安装前注意事项

- Alibaba Cloud Linux操作系统的ECS实例**不支持**安装图形化界面。
- 请在安装之前，为ECS实例创建快照，做好数据备份，请参见[创建快照](https://help.aliyun.com/zh/ecs/user-guide/create-a-snapshot-of-a-disk)。
- 图形化界面依赖组件较多，大批量安装组件会降低服务器的性能，若安装不当，则会导致操作系统无法正常启动，请谨慎操作。
- 安装图形化界面后，仅影响VNC登录后默认界面为图形化界面，**通过Workbench远程连接**和**通过会话管理远程连接**登录界面不受影响。

**重要** 

- 本文以CentOS 7、CentOS 8、Ubuntu 14、Ubuntu 18/20/22操作系统为例，其它发行版的配置可能有所差异，具体情况请参阅相应发行版的官方文档。
- CentOS 6与CentOS 8操作系统版本结束了生命周期（EOL），按照社区规则，CentOS 6/8的源地址内容已移除。当您在CentOS  6/8系统内继续使用默认配置的源地址时会发生报错。建议您先切换CentOS 6/8的源地址，然后再进行操作。具体操作，请参见[CentOS 6 EOL如何切换源？](https://help.aliyun.com/zh/ecs/user-guide/change-the-centos-6-source-address)和[CentOS 8 EOL如何切换源？](https://help.aliyun.com/zh/ecs/user-guide/change-centos-8-repository-addresses)。

## **CentOS 7安装GUI**

以CentOS 7操作系统为例介绍安装图形化桌面MATE的方法，其它发行版的配置可能有所差异，具体情况请参阅相应发行版的官方文档。

1. 通过VNC远程连接Linux实例。具体操作，请参见[使用VNC登录实例](https://help.aliyun.com/zh/ecs/user-guide/log-on-to-an-instance-by-using-vnc)。

2. 执行以下命令，更新系统的软件包。 

   ​        

   ​                        

   ```shell
   sudo yum -y upgrade
   ```

3. 依次执行以下命令，安装MATE桌面环境。 

   ​        

   ​                        

   ```shell
   sudo yum groups install "X Window System"
   sudo yum groups install "MATE Desktop"
   ```

4. 执行以下命令，设置默认使用图形化桌面环境启动实例。 您可以执行`systemctl set-default multi-user.target`，即可取消图形化界面登录。

   ​        

   ​                        

   ```shell
   sudo systemctl set-default graphical.target
   ```

5. 执行以下命令，重启ECS实例。

   ​        

   ​                        

   ```shell
   sudo reboot
   ```

6. 等待系统重启完成，出现图形化界面，确认安装成功。

   **说明** 

   您无需设置VNC的登录密码，只需要输入实例的用户名和密码即可安全地访问ECS实例。

   ![image](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/1731812371/p874533.png)

**取消图形化界面**



## **CentOS 8安装GUI**

以CentOS 8操作系统为例介绍安装图形化桌面GUI的方法，其它发行版的配置可能有所差异，具体情况请参阅相应发行版的官方文档。

1. 通过VNC远程连接Linux实例。具体操作，请参见[使用VNC登录实例](https://help.aliyun.com/zh/ecs/user-guide/log-on-to-an-instance-by-using-vnc)。

2. 执行以下命令，更新系统的软件包。 

   ​        

   ​                        

   ```shell
   sudo yum -y upgrade
   ```

3. 执行以下命令，安装图形桌面的软件包。 

   ​        

   ​                        

   ```shell
   sudo yum groupinstall "Server with GUI" -y 
   ```

4. 执行以下命令，设置图形模式为默认模式启动。 您可以执行`systemctl set-default multi-user.target`，即可取消图形化界面登录。

   ​        

   ​                        

   ```shell
   sudo systemctl set-default graphical.target
   ```

5. 执行以下命令，重启实例即可。 

   ​        

   ​                        

   ```shell
   sudo reboot
   ```

6. 等待系统重启完成，出现图形化界面，确认安装成功。

   **说明** 

   您无需设置VNC的登录密码，只需要输入实例的用户名和密码即可安全地访问ECS实例。

   ![image](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/1731812371/p874477.png)

**取消图形化界面**



## **Ubuntu 14安装GUI**

以Ubuntu 14操作系统为例介绍安装图形化桌面GNOME的方法，其它发行版的配置可能有所差异，具体情况请参阅相应发行版的官方文档。

1. 通过VNC远程连接Linux实例。具体操作，请参见[使用VNC登录实例](https://help.aliyun.com/zh/ecs/user-guide/log-on-to-an-instance-by-using-vnc)。

2. 执行以下命令，更新软件源。 

   ​        

   ​                        

   ```shell
   sudo apt-get update
   ```

3. 依次执行以下命令，安装GNOME桌面环境。 

   ​        

   ​                        

   ```shell
   sudo apt-get install x-window-system-core
   sudo apt-get install gnome-core
   ```

4. 执行以下命令，启动图形化桌面。 

   ​        

   ​                        

   ```shell
   sudo startx
   ```

5. 运行以下命令，重启ECS实例。

   ​        

   ​                        

   ```shell
   sudo reboot
   ```

6. 等待系统重启完成，出现图形化界面，确认安装成功。

   **说明** 

   您无需设置VNC的登录密码，只需要输入实例的用户名和密码即可安全地访问ECS实例。

    ![image](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/1731812371/p874561.png)

**取消图形化界面**



## Ubuntu 18/20/22/24安装GUI

以Ubuntu 18操作系统为例介绍安装图形化桌面Ubuntu Desktop的方法，其他发行版的配置可能有所差异，具体情况请参阅相应发行版的官方文档。

1. 通过VNC远程连接Linux实例。具体操作，请参见[使用VNC登录实例](https://help.aliyun.com/zh/ecs/user-guide/log-on-to-an-instance-by-using-vnc)。

2. 运行以下命令，更新软件源。

   ​        

   ​                        

   ```shell
   sudo apt-get update
   ```

3. 运行以下命令，安装图形化桌面。

   ​        

   ​                        

   ```shell
   sudo apt-get install ubuntu-desktop
   ```

   如果安装出现unmet dependencies报错，请参见[常见问题](https://help.aliyun.com/zh/ecs/use-cases/installing-a-graphical-desktop-environment-for-a-linux-instance#section-h9d-6ps-66l)中的解决方案解决以后，再启动图形化桌面。

4. 运行以下命令，设置默认启动为图形化桌面。您可以执行`systemctl set-default multi-user.target`，即可取消图形化界面登录。

   ​        

   ​                        

   ```shell
   sudo systemctl set-default graphical.target
   ```

5. 运行以下命令，重启ECS实例。

   ​        

   ​                        

   ```shell
   sudo reboot
   ```

6. 等待系统重启完成，出现图形化界面，确认安装成功。

   **说明** 

   您无需设置VNC的登录密码，只需要输入实例的用户名和密码即可安全地访问ECS实例。

   等待出现如下欢迎界面时，表示Ubuntu 18图形化桌面安装完成。![欢迎界面](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/9846066661/p507541.png)

7. 按照界面默认配置，一直单击**Next**。

   直至出现如下界面时，表示Ubuntu 18图形化桌面完成，您就可以开始使用Ubuntu 18图形化桌面。![桌面配置完成](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/1946066661/p507546.png)

   **取消图形化界面**

   

## Anolis 8安装GUI

龙蜥Anolis 8 基于 RHEL/CentOS 8，因此可以使用 `dnf` 包管理器来安装桌面环境。要在 Anolis 8 上安装图形化界面（例如 GNOME 桌面环境），请按照以下步骤操作：

1. 通过VNC远程连接Linux实例。具体操作，请参见[使用VNC登录实例](https://help.aliyun.com/zh/ecs/user-guide/log-on-to-an-instance-by-using-vnc)。

2. 更新系统软件包。

   ​        

   ​                        

   ```shell
   sudo dnf update -y
   ```

3. 安装图形化桌面环境。

   ​        

   ​                        

   ```shell
   sudo dnf groupinstall "Server with GUI" -y
   ```

   也可以选择其他桌面环境，例如 KDE Plasma：

   ​        

   ​                        

   ```shell
   sudo dnf groupinstall "KDE Plasma Workspaces" -y
   ```

   若要查看可用的桌面环境组，可以运行：

   ​        

   ​                        

   ```shell
   sudo dnf group list
   ```

4. 设置系统默认启动到图形化界面。

   安装完成后，需要将系统的默认启动目标设置为图形化界面：

   ​        

   ​                        

   ```shell
   sudo systemctl set-default graphical.target
   ```

5. 启动图形化界面。

   选择立即切换到图形化界面，而无需重启整个系统：

   ​        

   ​                        

   ```shell
   sudo systemctl isolate graphical.target
   ```

   如果需要通过重启来进入图形化界面，可以执行：

   ​        

   ​                        

   ```shell
   sudo reboot
   ```

6. （可选）安装额外的图形化工具。

   安装完成后，可能需要一些额外的图形化工具或驱动程序，以确保图形界面运行顺畅。例如，安装图形驱动程序：

   ​        

   ​                        

   ```shell
   sudo dnf install xorg-x11-drv-* -y
   ```

7. 等待系统重启完成，出现图形化界面，确认安装成功。

   **说明** 

   您无需设置VNC的登录密码，只需要输入实例的用户名和密码即可安全地访问ECS实例。

   ![image](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/1731812371/p874841.png)

- 确保图形化服务已启用并正在运行：

  ​        

  ​                        

  ```shell
  sudo systemctl status gdm
  sudo systemctl start gdm
  ```

- 检查当前的运行级别，确保返回的是 `graphical.target`。

  ​        

  ​                        

  ```shell
  sudo systemctl get-default
  ```

- 日志检查：

  如果遇到问题，可以查看相关日志获取更多信息：

  ​        

  ​                        

  ```shell
  sudo journalctl -xe
  ```

完成以上步骤后，Anolis 8 就会启动到图形化界面。



**取消图形化界面**



## **常见问题**

### **CentOS系统在安装图形化桌面后无法使用键盘和鼠标**

**问题现象** 

安装桌面环境后，通过ECS管理控制台的VNC连接ECS实例时，发现无法使用鼠标和键盘。

**问题原因** 

键盘和鼠标驱动异常所导致。

**解决方法** 

请参考以下步骤，将驱动类型修改为**evdev**。 

- 执行以下命令，安装evdev程序。 

  ​        

  ​                        

  ```shell
  yum install xorg-x11-drv-evdev
  ```

- 执行以下命令，创建`/etc/X11/xorg.conf`配置文件。 

  ​        

  ​                        

  ```shell
  Xorg -configure
  ```

- 执行以下命令， 备份配置文件。 

  ​        

  ​                        

  ```shell
  cp xorg.conf.new /etc/X11/xorg.conf
  ```

- 编辑`/etc/X11/xorg.conf`配置文件，将鼠标和键盘驱动类型修改为**evdev**。 

  ​        

  ​                        

  ```shell
  Identifier "Keyboard0"
  Driver "evdev"       [[修改为]] evdev
  Option "Device" "/dev/input/event3"
  EndSection
  Section "InputDevice"
  Identifier "Mouse0"
  Driver "evdev"       [[修改为]] evdev
  Option "Device" "/dev/input/event5"
  Option "Mode" "Absolute"
  EndSection
  ```

  - 修改前的配置文件类似如下。 

    ![img](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/3538439661/p519177.png)

  - 修改后的配置文件类似如下。

    ![img](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/3538439661/p519178.png)

1. 重启ECS实例，确认正常使用鼠标和键盘。

### **CentOS系统未开机启动messagebus和haldaemon服务导致无法使用GNOME桌面**

**问题现象** 

安装GNOME桌面环境并重启ECS实例后，输入账号和密码后，无法登录ECS实例，并提示以下错误。 

​        

​                        

```shell
"You are currently trying to run as the root super user. The super user is a specialized account that is not designed to run a normal user session. Various programs will not function properly, and actions performed under this account can cause unrecoverable damage to the operating system."
```

**问题原因** 

messagebus和haldaemon服务没有自动启动所致，为了提高系统性能和稳定性，默认情况下，Linux官网公共镜像未自动启动messagebus和haldaemon服务。

**解决方法**

1. 通过历史快照回滚操作系统，详情请参见[使用快照回滚云盘](https://help.aliyun.com/zh/ecs/user-guide/roll-back-a-disk-by-using-a-snapshot)。

2. 请安装GUI步骤，重新安装图形化桌面。

3. 执行以下命令，使messagebus和haldaemon服务开机自动启动。 

   ​        

   ​                        

   ```shell
   chkconfig --level 35 messagebus on
   chkconfig --level 35 haldaemon on
   ```

   **说明** 

   建议您将启动级别修改为“Level 3”，然后通过`startx`命令启动桌面环境，测试桌面环境的可用性。当出现问题时，您还可以切换到终端模式进行问题排查和处理。最后，在确保桌面环境启动无误后，再将启动级别修改为“Level 5”。

### Ubuntu安装图形化界面提示unmet dependencies

**问题现象**

安装Ubuntu 18图形化桌面过程中可能出现如下所示的报错。![安装报错](https://help-static-aliyun-doc.aliyuncs.com/assets/img/zh-CN/2946066661/p507487.png)

**问题原因**

该报错是由于安装ubuntu-desktop所需要的软件包列表中，依赖较低版本的update-manager-core、libparted2和python3-update-manager软件包，您需要删除较高版本的软件包，系统会根据软件包依赖树重新安装软件包。

**解决方案**

1. 运行以下命令，卸载较高版本的软件包。

   ​        

   ​                        

   ```shell
   apt-get remove update-manager-core libparted2 python3-update-manager
   ```

2. 运行以下命令，重新安装图形化桌面。

   ​        

   ​                        

   ```shell
   apt-get update
   apt-get install ubuntu-desktop
   ```

### **Invalid configuration value: failovermethod=priority**

执行 `yum groupinstall "Server with GUI" -y` 命令时遇到错误`Invalid configuration value: failovermethod=priority`。

**问题现象**

​        

​                        

```shell
Invalid configuration value: failovermethod=priority in /etc/yum.repos.d/CentOS-epel.repo; Configuration: OptionBinding with id "failovermethod" does not exist
CentOS Linux 8 - AppStream
```

**问题原因**

由于 EPEL（Extra Packages for Enterprise Linux）仓库配置文件 `/etc/yum.repos.d/CentOS-epel.repo` 中包含了一个无效的配置选项 `failovermethod=priority`。在 CentOS 8 中，`yum` 实际上是基于 `dnf` 的，而 `dnf` 不再支持 `failovermethod` 这个配置选项。因此，当 `dnf` 解析该仓库配置文件时，会报出上述错误。

**解决方法**

您可以通过修改 EPEL 仓库的配置文件，移除或注释掉 `failovermethod=priority` 这一行来解决问题。步骤如下。

1. 编辑 EPEL 仓库配置文件

   使用您喜欢的文本编辑器（如 vim/nano）打开 `/etc/yum.repos.d/CentOS-epel.repo` 文件。例如：

   ​        

   ​                        

   ```bash
   sudo vi /etc/yum.repos.d/CentOS-epel.repo
   ```

2. 查找并移除 `failovermethod=priority`

   在打开的文件中，找到包含 `failovermethod=priority` 的行。然后，可以选择以下两种方法之一：

   - 注释掉该行：在行首添加 `#`，使其变为注释。

     ​        

     ​                        

     ```ini
     # failovermethod=priority
     ```

   - 删除该行：直接删除包含`failovermethod=priority`的整行。

3. 保存并退出编辑器

   - 如果使用`vim`，按`Esc`，然后输入`:wq`并按回车键保存并退出。
   - 如果使用`nano`，按`Ctrl + O`保存，按`Ctrl + X`退出。

4. 清理 YUM/DNF 缓存

   执行以下命令以清理缓存，确保新的配置生效：

   ​        

   ​                        

   ```bash
   sudo yum clean all
   sudo yum makecache
   ```

   或者使用 `dnf` 命令：

   ​        

   ​                        

   ```bash
   sudo dnf clean all
   sudo dnf makecache
   ```

5. 再次尝试安装 GUI

   ​        

   ​                        

   ```bash
   sudo yum groupinstall "Server with GUI" -y
   ```

### **如何解决卡顿问题**

安装图形化界面后系统运行缓慢，可能是由于所选桌面环境资源消耗较大或系统配置较低。

Xrdp可以调用本地Windows自带的远程桌面mstsc程序，稳定性更好。尤其是在网络条件良好的情况下，Xrdp可以在远程使用时提供更流畅的体验。安装Xrdp的参考命令如下：

​        

​                        

```
sudo apt install xrdp -y
sudo adduser xrdp ssl-cert
sudo ufw allow 3389/tcp
sudo systemctl status xrdp
sudo systemctl enable xrdp
```

如果Linux系统本身资源不足或桌面环境过于沉重，建议使用更轻量级的桌面环境来提升性能。

## **相关文档**

如何在轻量应用服务器上搭建图形化界面，并使用VNC Viewer工具进行测试访问。请参见如下相关文档：

- [通过VNC搭建Ubuntu 16.04图形界面](https://help.aliyun.com/zh/simple-application-server/use-cases/use-vnc-to-build-guis-on-ubuntu-16-04)
- [通过VNC搭建Ubuntu 18.04和20.04图形界面](https://help.aliyun.com/zh/simple-application-server/use-cases/use-vnc-to-build-guis-on-ubuntu-18-04-and-20-04)