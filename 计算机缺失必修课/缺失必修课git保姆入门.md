## [Git常用命令](https://blog.csdn.net/qtiao/article/details/97783243)


Git是一个广泛使用的版本控制系统，它允许多个用户在各自的工作区域中使用同一个代码库进行工作。Git提供了一系列命令来管理代码库，包括创建和克隆仓库、配置用户信息、管理文件、提交更改、处理分支和标签、与远程仓库同步等。

# 创建和克隆仓库

要**初始化**一个新的Git仓库，可以使用_git init_命令。这将在当前目录下创建一个新的_.git_目录，其中包含了所有的版本控制信息。例如：

git init

要**克隆**一个现有的Git仓库，可以使用_git clone_命令，后面跟上仓库的URL。这会在本地创建一个仓库的副本，包括所有的分支和历史记录。例如：

git clone git://github.com/schacon/grit.git

# 配置用户信息

在提交代码之前，需要配置用户的**用户名**和**邮箱地址**，这样每次提交都会包含这些信息。可以使用_git config_命令来设置这些信息。例如：

git config --global user.name '你的用户名'

git config --global user.email '你的邮箱'

# 文件管理

使用_git add_命令可以将文件**添加**到暂存区，准备下一次提交。例如，添加所有更改过的文件：

git add

使用_git rm_命令可以从Git中**删除**文件，同时也从工作目录中删除。例如：

git rm 文件名

使用_git mv_命令可以**移动**或**重命名**文件。例如：

git mv 原文件名 新文件名

# 提交更改

使用_git commit_命令可以将暂存区的更改**提交**到仓库中。通常会附上一条提交信息来描述这次更改。例如：

git commit -m "提交信息"

如果想要跳过暂存区直接提交所有更改，可以使用_-a_选项。例如：

git commit -am "提交信息"

# 分支管理

使用_git branch_命令可以查看或创建**分支**。例如，创建一个新分支：

git branch 新分支名

使用_git checkout_命令可以**切换**到另一个分支。例如：

git checkout 分支名

使用_git merge_命令可以将一个分支的更改**合并**到当前分支。例如：

git merge 其他分支名

# 标签

使用_git tag_命令可以创建一个**标签**，以标记重要的提交点。例如，创建一个带有注释的标签：

git tag -a v1.0 -m "版本1.0"

# 远程仓库

使用_git remote add_命令可以添加一个**远程仓库**。例如：

git remote add 别名 仓库URL

使用_git push_命令可以将本地分支的更改**推送**到远程仓库。例如：

git push 别名 分支名

使用_git pull_命令可以从远程仓库**拉取**更改并合并到本地分支。例如：

git pull 别名 分支名

以上是Git的一些常用命令，它们涵盖了日常开发中的大部分需求。更多详细的命令和选项可以在Git的官方文档中找到[1](https://blog.csdn.net/qtiao/article/details/97783243)[2](https://www.runoob.com/note/56524)[3](https://www.ruanyifeng.com/blog/2015/12/git-cheat-sheet.html)。



### 1. 安装 Git 和 VSCode

- 安装 Git

  ：

  - 访问 [Git 官方下载页面](https://git-scm.com/downloads)，根据你的操作系统选择对应的版本进行下载和安装。安装过程中按照默认设置进行即可。
  - 安装完成后，打开命令行工具（如 Windows 的 cmd 或 PowerShell，Mac 的终端），输入 `git --version` 命令，如果能显示 Git 的版本号，说明安装成功。

- 安装 VSCode

  ：

  - 访问 [VSCode 官方下载页面](https://code.visualstudio.com/Download)，选择适合你操作系统的版本进行下载和安装。

### 2. 在 VSCode 中配置 Git

- 打开 VSCode，点击左侧边栏的 “源代码管理” 图标（像一个分支图标）。如果是第一次使用，VSCode 会提示你配置 Git，按照提示完成配置。
- 配置用户信息：打开终端（在 VSCode 中可以通过 `Ctrl + `或 `Cmd + `打开），输入以下命令配置你的用户名和邮箱：

收起



bash
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### 3. 创建本地仓库

- 初始化仓库

  ：

  - 打开 VSCode，通过 “文件” -> “打开文件夹” 选择一个你要进行版本控制的文件夹。
  - 打开终端，输入 `git init` 命令，该命令会在当前文件夹下创建一个 `.git` 隐藏文件夹，这意味着该文件夹已成为一个 Git 仓库。
  - 在 VSCode 的 “源代码管理” 面板中，你会看到当前仓库的状态。

### 4. 添加和提交文件

- 添加文件到暂存区

  ：

  - 在你的项目文件夹中创建或修改一些文件。在 VSCode 的 “源代码管理” 面板中，你会看到有未跟踪（Untracked）的文件。
  - 点击文件旁边的 “+” 号，或者在终端中输入 `git add <文件名>`（如果要添加所有文件，可以使用 `git add .`），将文件添加到暂存区。

- 提交暂存区的文件到本地仓库

  ：

  - 在 “源代码管理” 面板的消息输入框中输入本次提交的描述信息，比如 “Initial commit”（首次提交）。
  - 点击 “对勾” 图标，或者在终端中输入 `git commit -m "提交描述信息"`，将暂存区的文件提交到本地仓库。

### 5. 查看提交历史

- 在 VSCode 中，点击 “源代码管理” 面板中的 “…” 按钮，选择 “显示提交历史记录”，可以查看当前仓库的提交历史。
- 也可以在终端中输入 `git log` 命令查看提交历史。

### 6. 连接远程仓库（以 GitHub 为例）

- **创建 GitHub 仓库**：登录 [GitHub](https://github.com/)，点击右上角的 “+” 号，选择 “New repository”，按照提示创建一个新的仓库。
- **关联本地仓库和远程仓库**：在终端中输入以下命令，将本地仓库与远程仓库关联：

收起

```bash
git remote add origin <远程仓库的 URL>
```

其中，`<远程仓库的 URL>` 可以在 GitHub 仓库页面中找到。

- **推送本地仓库到远程仓库**：在终端中输入以下命令，将本地仓库的内容推送到远程仓库：

收起


bash









```bash
git push -u origin master
```

如果是第一次推送，需要输入你的 GitHub 用户名和密码进行身份验证。之后，你可以使用 `git push` 命令快速推送更新。

### 7. 从远程仓库拉取代码

- 当远程仓库有更新时，你可以在终端中输入 `git pull origin master` 命令，将远程仓库的更新拉取到本地。

### 8. 分支管理

- **创建新分支**：在终端中输入 `git branch <分支名>` 命令，创建一个新的分支。
- **切换分支**：输入 `git checkout <分支名>` 命令，切换到指定的分支。
- **查看分支**：输入 `git branch` 命令，查看当前仓库的所有分支。
- **合并分支**：切换到要合并到的目标分支，输入 `git merge <要合并的分支名>` 命令，将指定分支的更改合并到当前分支。

通过以上步骤，你就可以使用 Git 并配合 VSCode 进行基本的版本控制了。随着使用的深入，你可以学习更多高级的 Git 操作。



分享