---
order: 10
label: Windows
---
# Windows 安装

!!!warning
请勿安装到任何受 Windows 控制的文件夹（例如 Program Files、System32 等）。

请勿以管理员权限运行 START.BAT

Windows 7 无法安装，因为它无法运行 NodeJS 18.16
!!!

## 通过 Git 安装

1. 安装 [NodeJS](https://nodejs.org/en)（推荐使用最新的 LTS 版本）
2. 安装 [Git for Windows](https://gitforwindows.org/)
3. 打开 Windows 资源管理器（`Win+E`）
4. 浏览或创建一个不受 Windows 控制或监控的文件夹。（例如：C:\MySpecialFolder\）
5. 在该文件夹内打开命令提示符，方法是点击顶部“地址栏”，输入 `cmd`，然后按 Enter 键。
6. 当黑色框（命令提示符）弹出后，输入以下之一并按 Enter 键：

   - 对于 Release 分支：`git clone https://github.com/SillyTavern/SillyTavern -b release`
   - 对于 Staging 分支：`git clone https://github.com/SillyTavern/SillyTavern -b staging`

7. 克隆完成后，双击 `Start.bat` 以让 NodeJS 安装其所需依赖。
8. 然后服务器将启动，SillyTavern 将在您的浏览器中弹出。

## 通过 SillyTavern Launcher 安装

1. 在键盘上：按 **`WINDOWS + R`** 打开“运行”对话框。然后，运行以下命令以安装 Git：
    ```shell
    cmd /c winget install -e --id Git.Git
    ```
2. 在键盘上：按 **`WINDOWS + E`** 打开文件资源管理器，然后导航到您想要安装启动器的文件夹。进入目标文件夹后，在地址栏中输入 `cmd` 并按 Enter 键。然后，运行以下命令：
   ```shell
    git clone https://github.com/SillyTavern/SillyTavern-Launcher.git && cd SillyTavern-Launcher && start installer.bat
    ```

## 通过 GitHub Desktop 安装
（此方法仅允许在 GitHub Desktop 中使用 Git，如果您还想在命令行中使用 `git`，则需额外安装 [Git for Windows](https://gitforwindows.org/)）

1. 安装 [NodeJS](https://nodejs.org/en)（推荐使用最新的 LTS 版本）
2. 安装 [GitHub Desktop](https://central.github.com/deployments/desktop/desktop/latest/win32)
3. 安装 GitHub Desktop 后，点击 `Clone a repository from the internet....`（注意：此步骤**无需**创建 GitHub 账户）
  
    ![image](/static/windows-1.png)

4. 在菜单中，点击 URL 选项卡，输入此 URL `https://github.com/SillyTavern/SillyTavern`，然后点击 Clone。您可以更改本地路径以选择 SillyTavern 的下载位置。

    ![image](/static/windows-2.png)

5. 要打开 SillyTavern，使用 Windows 资源管理器浏览到您克隆仓库的文件夹。默认情况下，仓库将被克隆到此处：`C:\Users\[您的 Windows 用户名]\Documents\GitHub\SillyTavern`
  
6. 双击 `start.bat` 文件。（注意：文件名中的 `.bat` 部分可能被您的操作系统隐藏，在这种情况下，它看起来像一个名为“`Start`”的文件。这是您需要双击运行 SillyTavern 的文件）

    ![image](/static/windows-3.png)

7. 双击后，一个大的黑色命令控制台窗口应会打开，SillyTavern 将开始安装其运行所需的内容。
  
8. 安装过程完成后，如果一切正常，命令控制台窗口应如下所示，并且您的浏览器中应打开一个 SillyTavern 标签：

    ![image](/static/windows-4.png)

9. 连接到任何[支持的 API](/Usage/API_Connections/index.md)，即可开始聊天！