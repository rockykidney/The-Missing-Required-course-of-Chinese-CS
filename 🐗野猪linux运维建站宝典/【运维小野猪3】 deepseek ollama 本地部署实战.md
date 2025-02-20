![
## 安装 ollama[#](https://www.cnblogs.com/deali/p/18695132#%E5%AE%89%E8%A3%85-ollama)

[https://ollama.com/download/linux](https://ollama.com/download/linux)

我是在 Linux 服务器上安装的，一行命令就可以。如果是 Windows 的话安装包就行。

改成先下载拉去

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

[![](https://img2024.cnblogs.com/blog/866942/202501/866942-20250130130821042-2060900524.png)

## 安装[#](https://www.cnblogs.com/deali/p/18695132#%E5%AE%89%E8%A3%85)

接着执行命令

```bash
ollama run deepseek-r1:14b
```

开始下载，14b 的模型大小是 9GB

## 使用[#](https://www.cnblogs.com/deali/p/18695132#%E4%BD%BF%E7%94%A8)

在命令行可以直接使用

[![](https://img2024.cnblogs.com/blog/866942/202501/866942-20250130130835448-574157211.png)](https://img2024.cnblogs.com/blog/866942/202501/866942-20250130130835448-574157211.png)

人工智能聊世界

**DeepSeek 本地部署全攻略：保姆级教程**

大家好我是艾西，很久没有发文写一些技术相关或是知识普及的文章了，随着2024的结束，迎来全新的2025deepseek在春节期间爆火。我也想蹭着热度还在通过自己个人了解还有网络上一些现有的信息资源给大家说下自己本地怎么部署deepseek。

（注：因平台规范问题本文中所有www，http，https，com等全部用xxxx替代）

本文将详细介绍如何在本地部署 DeepSeek 模型，并以图文的形式把操作步骤展示出来，确保即使是初学者也能轻松上手。我们将从环境准备、安装依赖、模型下载到运行模型的每一步进行详细讲解。

![](https://i0.hdslb.com/bfs/new_dyn/a174de5f33a166bb0b1d3ba8c42010062142503379.png@1192w.webp)

**一、本地部署的适用场景**

本地部署适合以下情况：

**电脑配置较高，有独立显卡**：本地部署需要较强的硬件支持，尤其是GPU需求。

**有私密数据需要处理，担心泄密**：本地部署可以避免数据上传到云端，确保数据安全。

**需要与本地工作交流结合**：处理高频任务或复杂任务时，本地部署可以提供更高的灵活性和效率。

**日常使用量大，调用 API 需要收费**：本地部署可以节省 API 调用的费用。

**想要在开源模型基础上做个性化定制**：本地部署允许你对模型进行二次开发和定制。

**总结**：**有钱有技术 + 怕泄密** → 本地部署  **没钱没技术 + 图省事** → 直接使用网页/APP

· 

**二、本地部署的基本步骤**

**1. 环境准备：确保你的系统满足以下要求**

**操作系统**：Linux（推荐 Ubuntu 20.04 或更高版本）或 Windows。

**Python**：3.8 或更高版本。

**GPU**：支持 CUDA 的 NVIDIA GPU（推荐16GB 显存以上）。

**CUDA**：11.2 或更高版本。

**CUDNN**：8.1 或更高版本。

Linux择按照我编辑的跟着操作就行，Windows根据自己的电脑类型，选择不同版本。

苹果电脑选最左边（蓝色框），Windows系统选最右边（红色框），之后点击下载（绿色框）。

![](https://i0.hdslb.com/bfs/new_dyn/cd7cac70b1b5beffc9c398c9d2aa140b2142503379.png@1192w.webp)

**2. 安装依赖**

首先，安装必要的依赖项：

sudo apt-get update

sudo apt-get install -y python3-pip python3-dev python3-venv git

**3. 创建虚拟环境**

为了避免依赖冲突，建议在虚拟环境中操作：

python3 -m venv deepseek-env

source deepseek-env/bin/activate

**4. 安装 PyTorch**

根据你的 CUDA 版本安装 PyTorch。例如，CUDA 11.2 的安装命令如下：

pip install torch torchvision torchaudio --extra-index-url xxx://download.pytorch.org/whl/cu112

**5. 克隆 DeepSeek 仓库**

从 GitHub 克隆 DeepSeek 的代码库：

git clone xxxx://github.xxx/deepseek-ai/deepseek.git

cd deepseek

**6. 安装项目依赖**

安装项目所需的 Python 依赖：

pip install -r requirements.txt

**7. 下载预训练模型**

下载 DeepSeek 的预训练模型权重，并将其放置在 models/ 目录下。你可以从guan方提供的链接下载，或使用以下命令（假设模型权重已上传到某个服务器）：

wget xxxx://example.xxx/path/to/deepseek_model.pth -O models/deepseek_model.pth

**8. 配置环境变量**

设置必要的环境变量，例如模型路径和 GPU 设备号：

export MODEL_PATH=models/deepseek_model.pth

export CUDA_VISIBLE_DEVICES=0

**9. 运行模型**

使用以下命令启动模型推理或训练：

python run.py --model_path $MODEL_PATH --input "你的输入文本"

**10. 测试模型**

你可以通过提供输入文本来测试模型的输出：

python run.py --model_path $MODEL_PATH --input "你好，DeepSeek！"

**11. 训练模型（可选）**

如果你想从头训练或微调模型，可以使用以下命令：

python train.py --model_path $MODEL_PATH --data_path path/to/your/data

**12. 部署模型（可选）**

你可以将模型部署为 API 服务，使用 Flask 或 FastAPI 等框架：

pip install fastapi uvicorn

uvicorn api:app --reload

**13. 访问 API**

如果部署成功，你可以通过 xxx://localhost:8000 访问 API，并通过 POST 请求发送输入文本。

**使用 Ollama 进行本地部署（简化版）Windows系统**

如果你觉得上述步骤过于复杂，可以使用 **Ollama** 来简化本地部署过程。Ollama 是一个用于管理 AI 模型的工具，特别适合初学者。

![](https://i0.hdslb.com/bfs/new_dyn/890ba2e16ac8954b9a18644f3085dbc52142503379.png@1192w.webp)

**1. 安装 Ollama**

打开浏览器，搜索 **Ollama**，进入guan网。

点击 **Download**，根据你的操作系统选择对应的版本（Windows、macOS 或 Linux）。

下载并安装 Ollama。安装完成后，桌面会出现一个羊驼图标。

![](https://i0.hdslb.com/bfs/new_dyn/136871751fdfc76b335c27fd16fc78202142503379.png@382w.webp)

特别说明：最好安装在C盘，安装在其它盘，需要重新配置环境变量。

**2. 选择并安装模型**

打开 Ollama  guan网，点击右上角的 **Models**。

选择 **deepseek-r1** 模型，并根据你的电脑性能选择合适的参数版本（如 1.5b、7b、14b 等）。

![](https://i0.hdslb.com/bfs/new_dyn/9de6f83217e8b8b9eee3f5cfe6ce46dc2142503379.png@1192w.webp)

![](https://i0.hdslb.com/bfs/new_dyn/539a396daf0c4317b0e93583054e0d7e2142503379.png@1192w.webp)

复制安装命令，例如：

ollama run deepseek-r1:1.5b

打开命令行（Windows 用户按 Win + R，输入 cmd），粘贴并运行上述命令。模型将自动下载并安装。

![](https://i0.hdslb.com/bfs/new_dyn/90bcd5243eb4bfe19e7980ad03e8771e2142503379.png@780w.webp)

![](https://i0.hdslb.com/bfs/new_dyn/02316833835da746b86aa1ee2d3f23b62142503379.png@1192w.webp)

点击键盘上的“Enter”键，模型会自动下载。

![](https://i0.hdslb.com/bfs/new_dyn/8ef893a8201eaa43ce8c7736f373a5e42142503379.png@1192w.webp)

**3. 与模型对话**

安装完成后，你可以直接在命令行中与模型对话：

ollama run deepseek-r1:1.5b

输入你的问题，模型会立即给出回答。

![](https://i0.hdslb.com/bfs/new_dyn/d7d614f41951689357f6c74c9b35641a2142503379.png@1192w.webp)

此时大模型安装在你的电脑上，就算断网也可以继续用，也不用担心数据泄露。

后续运行模型操作注意事项：

当你关闭电脑后，下次再打开ollama。会发现点击ollama的图标，电脑没反应。

因为你点击图标，只是启动了ollama，想要和大模型聊天，还是需要打开命令行。

 继续通过命令行和大模型聊天：

同时按下键盘上的Win和R键，在弹出的窗口里输入cmd，点击确定打开命令行。在命令行界面，输入刚刚的命令“ollama run deepseek-r1:1.5b”。因为你之前已经下载过，这次无需下载，可以直接和模型聊天。

![](https://i0.hdslb.com/bfs/new_dyn/d4001f6c0c6da5ce978073fd43b33b3a2142503379.png@1192w.webp)

**四、安装 Open-WebUI（可选）**

Open-WebUI 可以为 Ollama 提供一个更友好的图形界面，但安装过程较为复杂，适合有一定技术基础的用户 （只是让交互界面更好看，可以不必安装）

这里就给大家简单的演示讲解下：

**1. 安装 Docker**

打开浏览器，搜索 **Docker**，进入guan网，根据你的电脑系统下载并安装 Docker 桌面版。

![](https://i0.hdslb.com/bfs/new_dyn/5fe173117a36f1104c5dfb1a5227038f2142503379.png@1192w.webp)

![](https://i0.hdslb.com/bfs/new_dyn/2344b46e45ca78a4320ec541a34695692142503379.png@1192w.webp)

安装完成后，需要重新启动电脑，才能正常使用docker。重新启动后，如果你的桌面上出现了docker的图标，就表示安装成功了。

![](https://i0.hdslb.com/bfs/new_dyn/552df972021d80b94729f4ef215f31e92142503379.png@500w_258h.webp)

**2. 安装 Open-WebUI**

打开命令行，输入以下命令安装 Open-WebUI：（linux系统）

docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main

安装完成后，打开浏览器，访问 xxx://localhost:3000，注册一个账号并登录。

在界面左上角选择你的模型，即可开始对话。

Windows：浏览器搜索Open-WebUI，进入guan网，并复制红框中的命令。

![](https://i0.hdslb.com/bfs/new_dyn/c8de379bc68d153fd8bcf87c90e053b62142503379.png@1192w.webp)

按照上面提到的步骤，打开命令行，输入复制的命令，等待安装完成。

运行Open-WebUI

双击docker的桌面图标，打开软件。点击红框端口，即可运行Open-WebUI。 

![](https://i0.hdslb.com/bfs/new_dyn/e25051522c52d39b41c162b4478bda482142503379.png@1192w.webp)

初次访问时，需要注册一个账号。这些信息会储存在你的电脑里。

在界面左上角，选择你的模型，就可以开始对话啦。 

![](https://i0.hdslb.com/bfs/new_dyn/a91ca75ead37cb1bdeb9ea2eddee6eb62142503379.png@1192w.webp)

**五、常见问题**

**1. 如何查看已安装的模型？**

在命令行中输入以下命令：

ollama list

**2. 如何删除模型？**

在命令行中输入以下命令：

ollama rm deepseek-r1:1.5b

在命令行输入，ollama rm + 模型名称，例如：ollama rm deepseek-r1:1.5b，就会自动删除对应模型。

 **3. ollama的其它功能**

命令行输入ollama，展示出ollama的其它功能。

![](https://i0.hdslb.com/bfs/new_dyn/2b1c128be72f7188bffa4fef198384182142503379.png@738w_442h.webp)

比如：输入“ollama stop”是停止模型运行，“run + 模型名”是运行对应模型。

**六、总结**

通过以上步骤，你可以轻松在本地部署 DeepSeek 模型。无论是通过手动安装还是使用 Ollama，本地部署都能为你提供更高的灵活性和数据安全性。

今天的分享就到这里了，希望AI能在将来或是现在为您的生活有质的提升，也希望大家可以通过AI学习并运用到自己的生活工作中。我是艾西我们下期见！@驰网艾西@艾西@艾西服务器论坛 拥有一台服务器可以做很多自己想做的事情