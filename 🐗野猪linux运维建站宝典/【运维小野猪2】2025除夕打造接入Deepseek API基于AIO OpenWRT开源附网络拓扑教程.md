# 运维小野猪】2025除夕打造接入Deepseek API基于AIO OpenWRT开源附网络拓扑教程

原创 胡忘年 胡忘年 _2025年01月30日 00:05_ _浙江_

博客创作不易 欢迎加入仓库共创

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKUevV61oicUZiaia5Bs5I9d8IP0PD1X8lY04Tfdic9kY8g49l9XyyA7UTaw/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)硬媒Tom‘s Hardware今早（大年初一） 最新热议：

“DeepSeek甚至绕过了CUDA，使用更底层的编程语言做优化。”

因此，以折腾心态，为测评这位AI黑马，本著决定设计部署一份可运行大模型的家庭版AIO。

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqK9toxiaibQg275DP8kpNmDwc4Gm5Y7U3KbbgtXFzGd2MFljv6Mu3IkvFg/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKxkHf5de41kIkua8iaomvlQFgPibjPlkpTWg85jXDiarEZFibqib3ZQ8GJHg/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

==本教程几乎零代码放心食用==

由于本著家庭开通了电信公网ipv4

无需额外的内网穿透

故网络拓扑设计图如下 大家以实际情况为准

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKV6YLk1PdMtWmJxM3ufpKib5mP8AjebPtY7ABxoAGHs07AtRn6YUS0iaw/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

基于Debian PVE不多介绍了

目前拓展能力无线的家庭AIO首选底层操作系统

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKziawCDV3HGFjCVBicE1C3BkJKbCsqdtYFy7nt4M6ezAmXA4HfBcRJ1Tg/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKyCDyePYNG07iauSDAMMs6IWNTOnZ7PGsCdo0yc8qE44IVfcCNQwTYDA/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

# 下载OpenWRT镜像至local存储

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKaKZ6QibTD7884P6pjUFIunfNmoRnpib3APpVJYAZ4KEDbThX3gDYnf9A/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKvD3EOlLzGF7k6wUCvMFuaLazcEfIyWnoSPERiablkTNVTYmaUfX0Jeg/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKvD3EOlLzGF7k6wUCvMFuaLazcEfIyWnoSPERiablkTNVTYmaUfX0Jeg/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

# 新建并配置虚拟机VM

注意不要错选为LXC容器

创建 1 个 OpenWrt 的虚拟机，不需要 CD 光盘，删掉自带的硬盘，

添加 2 个网络设备，CPU 权重设置高一点，毕竟是软路由，得保证路由的运行稳定优先级，整体配置如下：

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqK3C6u0H2Umw6THmQMDOicRnqGpdtDLRFECjxhHQ8ibTQulgkibR9Rhdg5g/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKn1LVBlhtLDyR3HhcvhToIheJystG8lnlshkfiaf8v2mTibEnbaGibYlPw/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKKAbV0tugW0rrrc23CkFFfJgrg8akHXbd2M0TgW9eUC8Eyc3xtGExhQ/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKNia9FgicCSIgatib3ibicrM9oo8qiaZedID9AbknpaAM6C1M2w0ibpIaPJREQ/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

其中网络部分的关系如下：

|硬件|网桥|说明||
|---|---|---|---|
|net0|vmbr0|PVE7默认自带-作为 OpenWrt 的  WAN 口||
|net1|vmbr1|作为 OpenWrt 的 LAN 口||

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKCuPOT8oxDUAkwz0vONNrJsQ6hBuCic6TyBb5PJkwqc2kcTQhsUGibdqQ/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### 导入磁盘镜像

我们之前上传的镜像存放在：**/var/lib/vz/template/iso/** 目录下，使用下面命令把镜像转成虚拟磁盘并导入到 ID 为 102 的 VM 中：

`qm importdisk 102 /var/lib/vz/template/iso/openwrt-24.10.0-rc6-x86-64-generic-ext4-combined.img local-lvm   `

转换提示成功：

其中[102]和.img文件转为你下载的对应版本

转化为虚拟硬盘!![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKMEa2fWrPcubyhomfCRicRmAc4zByIBiaIZsicNVpiaaemuBO0ftwRZ8p0A/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

显示成功!![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKSQkS0GSAcoO4uKiapbeohghoTcYKOxEPVxkicibc36pNib3r1OhzhjxfeA/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

导入成功后在虚拟机的「硬件」选项卡就能看到一个 **未使用的磁盘0**，选中它点击编辑，弹出配置窗口，设备类型选「Sata」，最后点击添加：

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKib9XVGSo5S6JFdXRqDqDUFVBxOS3kXNib4ht1ODlrjsZia9IZGVzJhtxA/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

删除多余的CD驱动器

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqK3Gf3MJDvgcFbdkV4JAVS4ZyQfQJOe7gYaxlsqklQ9USG2f5HeqW41g/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

更换引导顺序 打勾sata0

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKph7gibovCdtbgZIF2zfJ2Jgic42KkDcssPmfwjGOpOu4ics073yWEjQsw/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

启动虚拟机初始化

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKoLreXibEYqSiatiakNicvgbujAEibMUC5AYtGRNFvTItfQV6T143xPLTmoQ/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

成功进入阴导状态

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqK4Fpp4R0C4udyG4B9azhL3G86Bp0PWV6ib52dL8NeuvL1qb9OdbcmRxg/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

在shell中敲回车进入

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKMDZk9XZpPTVhJibYzDpMboibvkicmzBuKeLibMUJlXUicuGr8TUUb9P7Jrw/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

## 梳理网络情况

开启 OpenWrt 后默认输出完日志并不会自动进入到 shell 控制台，**手动回车**即可进行 shell 交互，首先看下当前的 IP 情况：!

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKSXbLKI4ALtg8XYf06GExmia5dwcqMzDicn3sLHOgChIiaEYGCGq30TDcA/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

此时发现拓扑逻辑有误 发现 OpenWrt 默认是将 eth0 作为 LAN 口，eth1 作为 WAN 口，这个恰恰和我们的拓扑图相反了，所以我们需要纠正一下网络配置。编辑纠正 根据我们之前的网络架构设计，将 ipaddr 改为：**10.10.1.1**，然后将 eth0 和 eth1 的定位调换一下，即 eth0 作为 WAN 口，eth1 作为 LAN 口，：

注：可怜的openWRT没有Nano 只能用Vim来编辑 因此若不会vim的可自行参考

LAN配置纠正前：

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKtaXLf3jvcUB7iabEUU02V4iao7CiahQCuv3ibmMxB3eIgts2tyyCwfhMqg/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

LAN配置纠正后：

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKSSnDqS133BYJ33xRO0sv4ibH9KjwKjYMeiafkzcB9jkW2WwzW19cNX7A/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

WAN配置纠正前：：

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKuNHTSVuicx6ZEicKWtrl2lLOHYNb0TySz6unuJ2I3kWRIT4brG3JibCCQ/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

WAN配置纠正后

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKvEqF6RLDOXGIqYDHb22ibgcCZDW1SCJXRYV6rpicjSsVo9uZlpAo7vsg/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

再看一遍是否误填

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKDCaNq3BUgtUYlicfHt8WRjrzUE8zvsbric7jPXZHhuZ8IEPUXydvxSMw/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

再编辑防火墙策略组  将REJRCT改成ACCEPT

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKBicMOz2XvJrvObELC531ZBiaSfia6QRsO575bbUGbia6os88eHvmf3ia0uQ/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqK8anQgPVrKehUM2ogeoWlZVrjE7MXGWPornxaySuOY737knaTWKwPlQ/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

改完之后重启网络即可生效配置：

Bash

`/etc/init.d/network restart   `

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKzXYQASYD0Y9Hu9Ptf15QRFo6d86ZxAvr6k2xqPicylsP9icWf9HO1cSA/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

`输入ifconfig也可查询网络接口状态   `

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKSc4htepf0iaJDmicqdGibwQ3lOEyveVicgbbnBXljgAJ1jiawDzqria7lLpw/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

发现更新成功

# web客户端设置

恭喜你 到这一步 输入ip地址进入登陆界面

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKg2HgzibkER1a3zJIxnC8A8Oms3GHNPXoiaUW74a48KDhxHo21mJ7hIDQ/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

改一下默认密码

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKuCTic7KKUzictctYChTxwYCR9JDwNzBaWYaxzPNF9cm3HlwWicSa5dbug/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

开始探索吧！安装中文插件

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqK3Dtiav1ZdFn4T2Y5ZbwoO55KqTpJEUGyGJibfYQSfjPCpicqSYUDuXp5A/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

# 使用Docker搭建Node环境接入DeepSeekAPI

![[{68B9B811-1012-4A37-92C0-7F46C39DF032}.png]]

### 配置NODE .JS环境

参考宝塔的node环境

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKibEng15ndYH1hbRvuW1K3g842Zm5TIwwqrMBx9AIDHY3FlTeMhYrukA/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

### 配置方法

`server   {       listen 3338;       server_name xxxxxxx#示例;       index index.html index.htm default.htm default.html;       [[root]] /www/wwwroot/server-master;       [[CERT-APPLY-CHECK--START]]       # 用于SSL证书申请时的文件验证相关配置        include /www/server/panel/vhost/nginx/well-known/collgeservermaster.conf;       [[CERT-APPLY-CHECK--END]]             [[SSL-START]] SSL相关配置       [[error_page]] 404/404.html;              [[SSL-END]]          [[ERROR-PAGE-START]]  错误页相关配置       [[error_page]] 404 /404.html;       [[error_page]] 502 /502.html;       [[ERROR-PAGE-END]]             [[REWRITE-START]] 伪静态相关配置       include /www/server/panel/vhost/rewrite/node_collgeservermaster.conf;       [[REWRITE-END]]          [[禁止访问的文件或目录]]       location ~ ^/(\.user.ini|\.htaccess|\.git|\.svn|\.project|LICENSE|README.md|package.json|package-lock.json|\.env) {           return 404;       }          [[一键申请SSL证书验证目录相关设置]]       location /.well-known/ {           root  /www/wwwroot/server-master;       }          [[禁止在证书验证目录放入敏感文件]]       if ( $uri ~ "^/\.well-known/.*\.(php|jsp|py|js|css|lua|ts|go|zip|tar\.gz|rar|7z|sql|bak)$" ) {           return 403;       }             # HTTP反向代理相关配置开始 >>>       location ~ /purge(/.*) {           proxy_cache_purge cache_one $host$request_uri$is_args$args;       }          location / {           proxy_pass http://127.0.0.1:3337;           proxy_set_header Host $host:$server_port;           proxy_set_header X-Real-IP $remote_addr;           proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;           proxy_set_header REMOTE-HOST $remote_addr;           add_header X-Cache $upstream_cache_status;           proxy_set_header X-Host $host:$server_port;           proxy_set_header X-Scheme $scheme;           proxy_connect_timeout 30s;           proxy_read_timeout 86400s;           proxy_send_timeout 30s;           proxy_http_version 1.1;           proxy_set_header Upgrade $http_upgrade;           proxy_set_header Connection "upgrade";       }       # HTTP反向代理相关配置结束 <<<          access_log  /www/wwwlogs/collgeservermaster.log;       error_log  /www/wwwlogs/collgeservermaster.error.log;   }   `

`#依赖   torch==2.4.1#老三样   triton==3.0.0#微软的一款机器学习框架   transformers==4.46.3#老三样   safetensors==0.4.5#一种新型序列化格式，旨在简化和精简大型复杂张量的存储和加载。它主要用于深度学习领域，特别是在处理大型模型时，能够提供更高的效率和安全性。   `

简单聊天模型推理 实战：

`from transformers import AutoTokenizer, AutoModelForCausalLM   import torch   tokenizer = AutoTokenizer.from_pretrained("deepseek-ai/deepseek-coder-6.7b-instruct", trust_remote_code=True)   model = AutoModelForCausalLM.from_pretrained("deepseek-ai/deepseek-coder-6.7b-instruct", trust_remote_code=True, torch_dtype=torch.bfloat16).cuda()   messages=[       { 'role': 'user', 'content': "write a quick sort algorithm in python."}   ]   inputs = tokenizer.apply_chat_template(messages, add_generation_prompt=True, return_tensors="pt").to(model.device)   # tokenizer.eos_token_id 是 <|EOT|> token的id   outputs = model.generate(inputs, max_new_tokens=512, do_sample=False, top_k=50, top_p=0.95, num_return_sequences=1, eos_token_id=tokenizer.eos_token_id)   print(tokenizer.decode(outputs[0][len(inputs[0]):], skip_special_tokens=True))   `

输出。。。。卡爆了😢

可惜最近太火 服务器拥堵 截至2025-1-28 本篇教程得鸽一会儿

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKjgxwwe2h0WWJYpoFY1rOg5klTFMQ1iathNWER7xX4sibPXzvLbxAHIfA/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

下期预告（暂停更运维搞机 开始进军ML DL AIOT等实用技术及科研进展)：

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqK9SR7VScTS4rKrnQ16cyY30qTc10micnUBL9j3A46q8E8UwAhhW4WatQ/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

![图片](https://mmbiz.qpic.cn/sz_mmbiz_png/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKmpmh2rw0cMf2uYzU2V42eJnspTGFNI3iaACu9aG7M64NtcIUXyNhtSQ/640?wx_fmt=png&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)

本文参考

https://github.com/deepseek-ai/DeepSeek-V3

https://github.com/sqlsec/PVE

博客创作不易 欢迎充电 欢迎加入仓库共创  

![图片](https://mmbiz.qpic.cn/sz_mmbiz_jpg/vYXYKiaQll1ibS4RTbgRhZZTgPm9d5xiaqKTBCRFBMtzM7FrpzK1jbGRKHZC27fZzX9LyqFEDf0RiaTZZMjZaBIVqw/640?wx_fmt=jpeg&from=appmsg&tp=webp&wxfrom=5&wx_lazy=1&wx_co=1)