---
label: 更新
icon: repo-pull
order: -1
expanded: false
---

# 如何更新 SillyTavern

找到您使用的操作系统，按照以下说明更新 ST。

!!! 安装说明请参见 [安装](/Installation/index.md) 页面。

本指南假设您已经至少安装并运行过一次 SillyTavern。
!!!

----

## Linux/Termux 或 MacOS

您肯定是通过 Git 安装的，因此只需在 SillyTavern 目录内运行 `git pull`。

- `cd SillyTavern` 进入正确的文件夹。
- `git pull` 获取更新。
- `./start.sh` 或 `bash start.sh` 启动 ST。

----

## Windows

> 首先尝试使用位于 SillyTavern 安装根文件夹中的 `UpdateAndStart.bat`。

如果失败，请返回此处继续阅读。

### 方法 1 - GIT

我们始终推荐用户使用 `git` 安装。原因如下：

当您通过 `git clone` 安装后，只需在 ST 文件夹内[打开命令行](https://www.google.com/search?q=how+to+open+command+prompt+in+a+folder)并输入 `git pull` 即可更新。
或者，如果命令提示符出现问题（且已安装 GitHub Desktop），您可以使用 `Repository` 菜单并选择 `Pull`。

更新将自动且安全地应用。

#### “救命！我最初通过 Zip 安装，现在想转换为 Git 安装”

您选择了一条明智的道路。

由于您的安装是通过 Zip 完成的，您需要使用 Git 进行全新安装。

幸运的是，我们提供了[说明](/Installation/Windows.md)来指导您完成此操作。

一旦您使用 Git 在一个不同的文件夹中安装了新的 SillyTavern，请返回本页面并按照下方“Zip 更新”说明的 **步骤 4** 继续操作。

### 方法 2 - ZIP

如果您坚持使用 Zip 安装，以下是更新时的繁琐过程：

1. 下载新的发布版 Zip 文件。
2. 将其解压到当前 ST 安装之外的一个文件夹中。
3. 按照您操作系统的常规设置步骤安装 NodeJS 依赖。

4. 根据需要(*)从旧 ST 安装中复制以下文件/文件夹：

    (*) “根据需要” = “如果您对这些文件夹创建了任何自定义内容”。

    #### 更新至 >=1.12.0
    
    将 `/data` 目录和 `config.yaml` 文件从一个安装复制到另一个安装。
    
    #### 从 <1.12.0 更新至 >1.12.0
    
    1.12.0 包含自动迁移程序。以下步骤仅在迁移中断或出错时需要执行。

5. 运行更新后的服务器安装至少一次，以创建 `/data/default-user` 目录。
6. 根据需要将旧 `/public` 中的文件转移到新 `/data/default-user` 中。
    
    没有文件夹是强制性的，因此只复制您需要的部分。
    
    **注意：不要复制整个 /public/ 文件夹**
    
    这样做可能会破坏新安装并阻止新功能的出现。
    
    ```plaintext
    Assets
    Backgrounds
    Characters
    Chats
    Context
    Groups
    Group chats
    Instruct
    movingUI
    KoboldAI Settings
    NovelAI Settings
    OpenAI Settings
    QuickReplies
    TextGen Settings (textgen = ooba)
    Themes
    User Avatars
    Worlds
    User
    settings.json
    secrets.json <---- 这个文件在根文件夹中，而不是 /public/
    ```

7. 将这些文件夹/文件复制后，将它们粘贴到新安装的 /data/default-user 文件夹中（secrets.json 放入文件夹根目录）。
8. 使用适合您操作系统的方法再次启动 SillyTavern，并祈祷一切顺利。
9. 如果一切正常显示，您可以安全删除旧 ST 文件夹。

### 常见更新问题

#### “工作目录中存在未解决的冲突。”

这意味着您修改了远程仓库中已更改的默认文件（例如设置预设）。

要解决此问题，请在终端中运行以下命令。请谨慎使用，因为这可能具有破坏性。如有需要，请先备份。

```bash
git merge --abort
git reset --hard
git pull --rebase --autostash
```

#### 文件更改阻止 git pull

- 如果您更改了 SillyTavern 系统文件，`git pull` 可能无法工作。
- 有时更新可能需要我们更改重要文件，也会导致同样的问题。
- 通常是默认预设文件或 `package-lock.json`。
- 在这种情况下，您可以尝试将文件移动到其他文件夹（或删除文件），然后执行 `git pull`。
- 另一种解决方案是使用 `git pull --rebase --autostash`

#### 启动服务器时出错：“无法找到模块 ‘***’”

- 这意味着 SillyTavern 添加了新的 npm 包依赖。
- 在 SillyTavern 目录中运行 `npm install` 以解决问题。提供的 Start.bat 和 start.sh 脚本会自动执行此操作。
- 没用？删除 node_modules 文件夹

**Windows**

```bash
rmdir /s /q node_modules
npm cache clean --force
npm install
```

**Unix/Linux**

```bash
rm -rf node_modules
npm cache clean --force
npm install
```

## Docker

1. 打开终端窗口并导航到您的 Docker 目录 `cd SillyTavern/docker`
2. 使用 `docker compose down` 删除您的容器
3. 从缓存中删除 SillyTavern Docker 镜像 `docker rmi ghcr.io/sillytavern/sillytavern:latest`（如果您目标是 staging 分支，请将 `sillytavern:latest` 替换为 `sillytavern:staging`。）
4. 使用 `sudo docker compose up -d` 重建容器

如果一切顺利，Docker 应开始重新下载镜像，您很快就能正常运行。如果遇到任何问题，请参考本指南的下一部分。

### 常见更新问题
#### 我使用 Docker，更新后所有数据都丢失了！

您必须按照 [Docker 容器的迁移指南](/Installation/Updating/ST-1.12.0-Migration-Guide.md#containerized-docker-installs) 更新 1.12.0 引入的新数据模型的卷映射。

#### 运行 Docker 命令时出现“权限被拒绝”

这是 Linux 的问题，表明您的权限未正确设置。有两种解决方法：

1. **简单方法**：如果您的用户有 sudo 权限，只需在命令前加上 `sudo`（例如：`sudo docker compose down`）
2. **正确方法**：修复您的权限。这取决于您使用的 Linux 版本。网上有许多指南可以帮助您解决此问题。