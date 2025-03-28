---
label: MacOS & Linux
order: 5
---

# Linux/MacOS 安装

## 手动 Git 安装

对于 MacOS / Linux，所有步骤都将在终端中完成。

1. 安装 Git 和 NodeJS（具体方法因您的操作系统而异）
2. 克隆仓库

   - 对于 Release 分支：`git clone https://github.com/SillyTavern/SillyTavern -b release`
   - 对于 Staging 分支：`git clone https://github.com/SillyTavern/SillyTavern -b staging`

3. 使用 `cd SillyTavern` 进入安装文件夹。
4. 使用以下任一命令运行 `start.sh` 脚本：

- `./start.sh`
- `bash start.sh`

## SillyTavern 启动器

### 对于 Linux 用户
1. 打开您喜欢的终端并安装 Git
2. 使用以下命令下载 SillyTavern 启动器：`git clone https://github.com/SillyTavern/SillyTavern-Launcher.git`
3. 使用以下命令进入 SillyTavern-Launcher 文件夹：`cd SillyTavern-Launcher`
4. 使用以下命令启动安装程序：`chmod +x install.sh && ./install.sh`，然后选择您想安装的内容
5. 安装完成后，使用以下命令启动启动器：`chmod +x launcher.sh && ./launcher.sh`

### 对于 Mac 用户
1. 打开终端并使用以下命令安装 Brew：`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
2. 然后使用以下命令安装 Git：`brew install git`
3. 使用以下命令下载 SillyTavern 启动器：`git clone https://github.com/SillyTavern/SillyTavern-Launcher.git`
4. 使用以下命令进入 SillyTavern-Launcher 文件夹：`cd SillyTavern-Launcher`
5. 使用以下命令启动安装程序：`chmod +x install.sh && ./install.sh`，然后选择您想安装的内容
6. 安装完成后，使用以下命令启动启动器：`chmod +x launcher.sh && ./launcher.sh`