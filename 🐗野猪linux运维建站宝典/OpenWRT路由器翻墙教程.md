# [OpenWRT路由器翻墙教程](https://w1.v2ai.top/doc/#/Router/OpenWRT?id=openwrt%e8%b7%af%e7%94%b1%e5%99%a8%e7%bf%bb%e5%a2%99%e6%95%99%e7%a8%8b)

[支持OpenWRT的硬件设备列表](https://openwrt.org/zh/toh/start)

## [特别提醒:防止你的路由器变成公共代理](https://w1.v2ai.top/doc/#/Router/OpenWRT?id=%e7%89%b9%e5%88%ab%e6%8f%90%e9%86%92%e9%98%b2%e6%ad%a2%e4%bd%a0%e7%9a%84%e8%b7%af%e7%94%b1%e5%99%a8%e5%8f%98%e6%88%90%e5%85%ac%e5%85%b1%e4%bb%a3%e7%90%86)

openwrt的防火墙设置，wlan口的入站和转发应该都禁止. 如果使用OpenClash, 也在 全局设置-基本设置里 设置为 仅允许内网.

OpenWRT 可以使用 [OpenClash 插件](https://github.com/vernesong/OpenClash)， 请点链接查看教程。

如果使用OpenClash 插件，务必勾选`仅允许内网`【如下图】，否则很可能被别人偷跑流量。 ![](https://w1.v2ai.top/docs/SSPanel/Router/openclash-lan-only.jpg)

或者使用shadowsocksR-plus插件，下面是shadowsocksR-plus插件的简单教程。

**前情：已在openwrt中安装了shadowsocksR-plus插件，现在具体设置**

## [一，拷贝获取订阅链接](https://w1.v2ai.top/doc/#/Router/OpenWRT?id=%e4%b8%80%ef%bc%8c%e6%8b%b7%e8%b4%9d%e8%8e%b7%e5%8f%96%e8%ae%a2%e9%98%85%e9%93%be%e6%8e%a5)

如果您还没有登录，请先 （[**注册登录**](https://w1.v2ai.top/auth/register)）

注册登录完毕，接着充值后按需求选择套餐，至此第一步完成。

此处将显示您的V2free机场订阅链接，请注意为登录状态：

**v2ray订阅链接-仅vmess-不含高倍率节点【任选一个，哪个好用用哪个】**

```
https://v1.v2ai.top/link/i0UlcjyXPoBqteFo?sub=3.1
```

```
https://w1.v2ai.top/link/i0UlcjyXPoBqteFo?sub=3.1
```

**ss订阅链接【任选一个，哪个好用用哪个】**

```
https://v1.v2ai.top/link/i0UlcjyXPoBqteFo?sub=2
```

```
https://w1.v2ai.top/link/i0UlcjyXPoBqteFo?sub=2
```

这个 **订阅链接** 非常重要，你应当把它当做密码一样妥善保管。

复制上面的订阅链接。

## [二，在shadowsocksR-plus插件中设置相应参数](https://w1.v2ai.top/doc/#/Router/OpenWRT?id=%e4%ba%8c%ef%bc%8c%e5%9c%a8shadowsocksr-plus%e6%8f%92%e4%bb%b6%e4%b8%ad%e8%ae%be%e7%bd%ae%e7%9b%b8%e5%ba%94%e5%8f%82%e6%95%b0)

1.登录进路由器，点击服务器节点页面。

![](https://w1.v2ai.top/docs/SSPanel/Router/OpenWRT2.jpg)

2.在订阅URL栏目粘贴进之前复制的订阅链接。（如图所示），并点击 **“保存 & 应用”**。大约几分钟后刷新页面就可以看到节点列表了（**需联网操作**）。

![](https://w1.v2ai.top/docs/SSPanel/Router/OpenWRT3.jpg)

3.出现节点列表后，返回 “**客户端**” 页面选择任意一个**可用**节点 并 “保存&应用”。

![](https://w1.v2ai.top/docs/SSPanel/Router/OpenWRT4.jpg)

当页面出现绿色的 “ShadowsocksR Plus+ 运行中”字样即表示设置成功。

在运行模式那里，选择 绕过中国大陆IP模式或者GFW列表模式，按需设置即可。

至此就可以实现路由端科学上网设置。

## [单个节点导入](https://w1.v2ai.top/doc/#/Router/OpenWRT?id=%e5%8d%95%e4%b8%aa%e8%8a%82%e7%82%b9%e5%af%bc%e5%85%a5)

如果订阅链接无法导入节点，可以使用此方法先导入单个节点，翻墙成功后再使用订阅链接导入。

![](https://w1.v2ai.top/docs/SSPanel/Router/OpenWRT5.jpg)  
vmess:// 或 ss:// 节点URL，请从[节点列表](https://w1.v2ai.top/user/node)拷贝，【不支持Trojan】  
![](https://w1.v2ai.top/docs/SSPanel/Router/OpenWRT6.jpg)