# [Clash for linux 教程](https://w1.v2ai.top/doc/#/linux/clash?id=clash-for-linux-教程)

## [创建并进入程序目录](https://w1.v2ai.top/doc/#/linux/clash?id=创建并进入程序目录)

打开linux命令行，依次执行下列命令

```
mkdir  ~/.config/
mkdir  ~/.config/mihomo/
cd     ~/.config/mihomo/
```

## [下载clash](https://w1.v2ai.top/doc/#/linux/clash?id=下载clash)

本站下载: [clash-linux.tar.gz](https://w1.v2ai.top/ssr-download/clash-linux.tar.gz)

注意，请下载到 `~/.config/mihomo/` 目录，如果下载到其它目录，请务必移动到 `~/.config/mihomo/` 目录。

解压

```markup
tar xvf clash-linux.tar.gz
```

授权可执行权限

```markup
chmod +x clash-linux
```

## [下载 clash 配置文件(更新订阅更新节点)](https://w1.v2ai.top/doc/#/linux/clash?id=下载-clash-配置文件更新订阅更新节点)

此处将显示您的V2free机场的Clash订阅链接，请注意为登录状态：

**Clash订阅链接【任选一个，哪个好用用哪个】**
 全部节点:

```
https://v1.v2ai.top/link/i0UlcjyXPoBqteFo?clash=2
```

不含高倍率节点:

```
https://v1.v2ai.top/link/i0UlcjyXPoBqteFo?clash=2&rate=false
```

全部节点:

```
https://w1.v2ai.top/link/i0UlcjyXPoBqteFo?clash=2
```

不含高倍率节点:

```
https://w1.v2ai.top/link/i0UlcjyXPoBqteFo?clash=2&rate=false
```

这个 **订阅链接** 相当于你的账号密码，跟你的账号是绑定的，你应当把它当做密码一样妥善保管。

安全提示：本站 **Clash订阅** 已默认实现国内外流量分流，一般国内网站不走代理。

用wget下载clash配置文件（**重复执行就是更新订阅更新节点**），替换默认的配置文件。**当然，你也可以用浏览器打开订阅链接，下载后拷贝或移动到~/.config/mihomo/目录替换覆盖config.yaml文件。**

**下载配置文件【任选一个，哪个好用用哪个】：**

```
wget -U "Mozilla/6.0" -O ~/.config/mihomo/config.yaml "https://v1.v2ai.top/link/i0UlcjyXPoBqteFo?clash=2"
wget -U "Mozilla/6.0" -O ~/.config/mihomo/config.yaml "https://w1.v2ai.top/link/i0UlcjyXPoBqteFo?clash=2"
```

然后，启动clash【切记：不要加 sudo】

```markup
./clash-linux
```

提示：机场节点信息可能会不定时更新，若出现大面积节点不可用现象，或者从免费用户升级为VIP用户，请手工更新订阅更新节点。 

注意：充值完成后，请到套餐购买页面用充值的余额购买套餐后才能开始使用VIP！！！购买套餐后，免费节点将不可用，请更新为VIP节点；如果您之前已经使用了免费订阅链接，购买套餐后订阅链接不变，您只需要通过更新订阅来更新节点即可；更新节点后把APP中的节点跟网站 [节点列表](https://w1.v2ai.top/user/node) 对照看看（对比节点名称，网站节点列表明确列出了免费节点和VIP付费节点），确保VIP节点已更新成功。

更新节点注意事项：如果开启系统代理，确保选择可用的节点，如果当前没有可用节点，先关闭系统代理再更新。如果 关闭系统代理 更新不了，请从用户中心或教程里重新拷贝新的订阅链接试试。

## [配置Linux 或者 浏览器使用Clash代理，以 ubunutu 为例](https://w1.v2ai.top/doc/#/linux/clash?id=配置linux-或者-浏览器使用clash代理，以-ubunutu-为例)

安全提示：本站 **Clash订阅** 已默认实现国内外流量分流，一般国内网站不走代理。

同時启用 HTTP 代理和 Socks5 代理。

clash 默认 http 和 socks5 端口都默认监听 7890

打开 设置 -> 网络 -> 网络代理

配置 HTTP 代理和 socket 代理 分别为上面的端口号(**注意：Linux命令行的程序或shell脚本不一定遵循此处代理设置，设置命令行的代理请看后文**)

![69564-fy7u3i5sqhl.png](https://w1.v2ai.top/docs/SSPanel/linux/clash_files/574938345.png)

## [Linux命令行设置代理](https://w1.v2ai.top/doc/#/linux/clash?id=linux命令行设置代理)

Linux命令行的程序或shell脚本不一定遵循上述代理设置，因此需要单独设置命令行的代理。

注意，ping 不支持代理，命令行测试外网网址请使用 curl 测试。

clash启动已占用的终端窗口无法再输入命令，请新开一个终端窗口执行下列命令。

下列命令只对当前终端窗口有效，如果希望永久性的设置代理，可以将以上命令添加到.bashrc文件中。

在Linux命令行中设置代理，可以通过设置环境变量http_proxy和https_proxy来实现：

```markup
export http_proxy="http://127.0.0.1:7890"
export https_proxy="http://127.0.0.1:7890"
```

输入 echo $http_proxy 和 echo $https_proxy 命令，然后回车查看，以确保代理已经正确设置。

如果需要取消代理，可以使用以下命令：

```markup
unset http_proxy
unset https_proxy
```

## [选择节点](https://w1.v2ai.top/doc/#/linux/clash?id=选择节点)

请使用 [Clash Web 管理](https://w1.v2ai.top/doc/#/linux/clashweb.html)

# [从官方网站下载其它版本](https://w1.v2ai.top/doc/#/linux/clash?id=从官方网站下载其它版本)

注意，本网站提供的clash下载是 linux-amd64 版本，如果你启动不了，可能是不适合你的系统，你可以从官网下载其它的版本。

https://github.com/MetaCubeX/mihomo/releases

![39509-crg2bid6yj.png](https://w1.v2ai.top/docs/SSPanel/linux/clash_files/1946477.png)

根据你的Linux版本选择相应的下载。