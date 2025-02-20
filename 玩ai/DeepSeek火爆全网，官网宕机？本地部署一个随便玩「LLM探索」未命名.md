
## 前言[#](https://www.cnblogs.com/deali/p/18695132#%E5%89%8D%E8%A8%80)

最近 DeepSeek 狠狠刷了一波屏，国产大模型真的越来越厉害了👍，官方的服务器已经爆满了，以至于频繁出现反应迟缓甚至宕机的情况，和两年多之前 ChatGPT 的遭遇颇为相似。

我已经好久没有本地部署模型了（现在各厂商的模型都便宜量大），这次正好来试试 DeepSeek 开源模型的效果。

### 关于AI大模型的扩展阅读[#](https://www.cnblogs.com/deali/p/18695132#%E5%85%B3%E4%BA%8Eai%E5%A4%A7%E6%A8%A1%E5%9E%8B%E7%9A%84%E6%89%A9%E5%B1%95%E9%98%85%E8%AF%BB)

- [LLM探索：环境搭建与模型本地部署](https://www.cnblogs.com/deali/p/llm-1.html)
- [LLM探索：GPT类模型的几个常用参数 Top-k, Top-p, Temperature](https://www.cnblogs.com/deali/p/llm-2.html)
- [快来玩AI画图！StableDiffusion模型搭建与使用入门~](https://www.cnblogs.com/deali/p/17275651.html)
- [使用Django-Channels实现websocket通信+大模型对话](https://www.cnblogs.com/deali/p/18359353)
- [项目完成小结：使用Blazor和gRPC开发大模型客户端](https://www.cnblogs.com/deali/p/17553214.html)

## 安装 ollama[#](https://www.cnblogs.com/deali/p/18695132#%E5%AE%89%E8%A3%85-ollama)

[https://ollama.com/download/linux](https://ollama.com/download/linux)

我是在 Linux 服务器上安装的，一行命令就可以。如果是 Windows 的话，可能是下载安装包就行。

```bash
curl -fsSL https://ollama.com/install.sh | sh
```

我安装的时候似乎遇到网络问题

改成先下载

```bash
wget https://ollama.com/install.sh
```

然后手动执行安装，就可以了

```bash
sh ./install.sh
```

## 配置 ollama 监听地址[#](https://www.cnblogs.com/deali/p/18695132#%E9%85%8D%E7%BD%AE-ollama-%E7%9B%91%E5%90%AC%E5%9C%B0%E5%9D%80)

ollama 安装后默认监听 127.0.0.1, 为了方便使用，要么修改监听地址，要么用 SSH 转发，这里我选择了修改地址

```bash
sudo systemctl edit ollama
```

它会自动在 `/etc/systemd/system/ollama.service.d/override.conf` 中存储你添加或修改的配置。

在里面添加配置

```ini
[Service]
Environment="OLLAMA_HOST=0.0.0.0:11434"
```

即可覆盖主服务文件里对 `OLLAMA_HOST` 的设置，其他环境变量（如 `PATH` 等）则仍保留主服务文件里的值。

### 验证[#](https://www.cnblogs.com/deali/p/18695132#%E9%AA%8C%E8%AF%81)

先重启以下

```bash
sudo systemctl daemon-reload
sudo systemctl restart ollama
```

然后执行以下命令验证

```bash
sudo systemctl show ollama | grep Environment
```

你会看到系统最终为该服务设置的所有环境变量。其中如果存在同名变量，就会以最后写入（即 override 配置）的值为准。

## 搜索模型[#](https://www.cnblogs.com/deali/p/18695132#%E6%90%9C%E7%B4%A2%E6%A8%A1%E5%9E%8B)

[https://ollama.com/search?q](https://ollama.com/search?q) = deepseek

目前最火的 DeepSeek-R1 排在显眼位置

这里根据显存选择合适的模型，我选了 14b 的模型

右侧有安装命令，点击按钮复制

## 安装[#](https://www.cnblogs.com/deali/p/18695132#%E5%AE%89%E8%A3%85)

接着执行命令

```bash
ollama run deepseek-r1:14b
```

开始下载，14b 的模型大小是 9GB

## 使用[#](https://www.cnblogs.com/deali/p/18695132#%E4%BD%BF%E7%94%A8)

在命令行可以直接使用

[![](https://img2024.cnblogs.com/blog/866942/202501/866942-20250130130835448-574157211.png)](https://img2024.cnblogs.com/blog/866942/202501/866942-20250130130835448-574157211.png)

## 安装 Open WebUI[#](https://www.cnblogs.com/deali/p/18695132#%E5%AE%89%E8%A3%85-open-webui)

[https://github.com/open-webui/open-webui](https://github.com/open-webui/open-webui)

### pip 安装[#](https://www.cnblogs.com/deali/p/18695132#pip-%E5%AE%89%E8%A3%85)

```bash
conda create -n open-webui python=3.11
```

切换环境

```bash
conda activate open-webui
```

安装

```bash
pip install open-webui
```

启动

```bash
open-webui serve
```

### docker[#](https://www.cnblogs.com/deali/p/18695132#docker)

官方只提供了 docker 命令

```bash
docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main
```

我改成了 docker-compose 配置

```yaml
services:
  open-webui:
    image: ghcr.io/open-webui/open-webui:main
    container_name: open-webui
    restart: always
    ports:
      - "3000:8080"
    extra_hosts:
      - "host.docker.internal:host-gateway"
    volumes:
      - "./open-webui:/app/backend/data"

```

## SSH 转发[#](https://www.cnblogs.com/deali/p/18695132#ssh-%E8%BD%AC%E5%8F%91)

在本机执行以下命令，将服务器的端口转发到本机

```bash
ssh -L 3000:localhost:3000 用户名@服务器地址 -p 端口
```

这样就可以在本机的浏览器打开 `http://localhost:3000` 访问到 webui 了

## 使用 webui[#](https://www.cnblogs.com/deali/p/18695132#%E4%BD%BF%E7%94%A8-webui)

很简单，第一次打开会需要创建管理员账号

进入之后界面与 ChatGPT 有点相似

[![](https://img2024.cnblogs.com/blog/866942/202501/866942-20250130130813308-507392736.png)](https://img2024.cnblogs.com/blog/866942/202501/866942-20250130130813308-507392736.png)

和 DeepSeek 模型对话，这个14b的模型就感觉效果已经不错了，如果完整版模型就更好，真的未来可期啊！

[![](https://img2024.cnblogs.com/blog/866942/202501/866942-20250130130821042-2060900524.png)](https://img2024.cnblogs.com/blog/866942/202501/866942-20250130130821042-2060900524.png)

## 后记[#](https://www.cnblogs.com/deali/p/18695132#%E5%90%8E%E8%AE%B0)

据说 DeepSeek 的代码能力很强，可惜现在官网的 API 服务进不去。

下一篇文章我来试试拿本地部署的 DeepSeek 来写代码，看看效果如何。

## 参考资料[#](https://www.cnblogs.com/deali/p/18695132#%E5%8F%82%E8%80%83%E8%B5%84%E6%96%99)

- [DeepSeek-R1本地部署，再也不怕宕机，还有语音功能！](https://mp.weixin.qq.com/s/JUe73lGnnXv-13B8oME_Rg)
- [DeepSeek 3大用法！再见ChatGPT/cursor](https://www.bilibili.com/video/BV18qcweJE7X)

作者：DealiAxy

出处：[https://www.cnblogs.com/deali/p/18695132](https://www.cnblogs.com/deali/p/18695132)

版权：本作品采用「[署名-非商业性使用-相同方式共享 4.0 国际](https://creativecommons.org/licenses/by-nc-sa/4.0/)」许可协议进行许可。

微信公众号：「程序设计实验室」  
新版StarBlog已经上线，地址：[http://blog.deali.cn](http://blog.deali.cn/)

微信公众号：「程序设计实验室」 专注于互联网热门新技术探索与团队敏捷开发实践，包括架构设计、机器学习与数据分析算法、移动端开发、Linux、Web前后端开发等，欢迎一起探讨技术，分享学习实践经验。