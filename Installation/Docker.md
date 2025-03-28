---
# icon: container
label: Docker
---

# Docker 安装

!!! info
本指南假设您将 SillyTavern 安装在非根（非管理员）文件夹中。如果您将 SillyTavern 安装在根文件夹中，可能需要以管理员权限运行部分命令（例如 `sudo`、`doas` 或以管理员身份运行命令提示符）。
!!!

## 安装

### Linux

1. 按照 Docker 安装指南 [此处](https://docs.docker.com/engine/install/) 安装 Docker。
   !!! danger
   **不要** 安装 Docker Desktop。
   !!!
2. 按照 Docker [安装后指南](https://docs.docker.com/engine/install/linux-postinstall/) 中的 **以非根用户管理 Docker** 步骤操作。
3. 使用您的包管理器安装 [Git](https://git-scm.com/download/linux)。

    - Debian (Ubuntu/Pop! OS 等)

        ```sh
        sudo apt install git
        ```

    - Arch Linux (Manjaro/EndeavourOS 等)

        ```sh
        sudo pacman -S git
        ```

    - Fedora, Red Hat Enterprise Linux (RHEL) 等
        ```sh
        sudo dnf install git
        ```

4. 克隆 SillyTavern 仓库。

    - Release (稳定分支)

        ```sh
        git clone https://github.com/SillyTavern/SillyTavern && cd SillyTavern/docker
        ```

    - Staging (开发分支)
        ```sh
        git clone https://github.com/SillyTavern/SillyTavern -b staging && cd SillyTavern/docker
        ```

5. 在 Docker 文件夹内运行以下命令执行 `docker compose`。

    ```sh
    docker compose up -d
    ```

6. 执行以下 Docker 命令以获取 SillyTavern Docker 容器的 IP。

    ```sh
    docker network inspect docker_default
    ```

    您应该会看到类似于以下内容的输出。

    ```json
    [
        {
            "Name": "docker_default",
            "IPAM": {
                "Config": [
                    {
                        "Subnet": "172.18.0.0/16",
                        "Gateway": "172.18.0.1"
                    }
                ]
            }
        }
    ]
    ```

    记下 _Gateway_ 中显示的 IP，这将很重要。

7. 使用 `sudo` 打开 `nano`，并运行以下命令。

    ```sh
    sudo nano config/config.yaml
    ```

    在 `nano` 中，找到 `whitelist`。您应该会看到类似于以下内容。

    ```yaml
    whitelist:
        - 127.0.0.1
    ```

    在 _127.0.0.1_ 下方添加一行，输入您从 Docker 复制的 IP。完成后应类似于以下内容。

    ```yaml
    whitelist:
        - 127.0.0.1
        - 172.18.0.1
    ```

    按 _Ctrl+S_ 保存文件，然后按 _Ctrl+X_ 退出 `nano`。

    !!! info
    请注意，如果您将 Docker 网络配置为桥接模式，您也可以照常将外部 IP 地址添加到白名单。
    !!!

8. 重启 Docker 容器以应用新配置。

    ```sh
    docker compose restart sillytavern
    ```

9. 打开一个新浏览器，访问 [http://localhost:8000](http://localhost:8000)。几秒钟后，您应该会看到 SillyTavern 加载完成。

10. 尽情享受吧！ :D

### Windows

!!! warning 关于在 Windows 上使用 Docker
在 Windows 上使用 Docker **非常** 复杂。您不仅需要在“启用或关闭 Windows 功能”中激活 _Windows 子系统 Linux_，还需要为您的系统配置虚拟化（Intel VT-d/AMD SVM），而这因 PC 制造商或主板制造商而异。有时，某些系统上可能没有此选项。

强烈建议您按照我们的 [Windows](/Installation/Windows.md) 指南安装 SillyTavern。本节仅提供在 Windows 上实现的大致思路。
!!!

1. 按照 Docker 安装指南 [此处](https://docs.docker.com/desktop/setup/install/windows-install/) 安装 Docker Desktop。
2. 安装 [Git for Windows](https://git-scm.com/download/win)。
3. 克隆 SillyTavern 仓库。

    - Release (稳定分支)

        ```sh
        git clone https://github.com/SillyTavern/SillyTavern && cd SillyTavern/docker
        ```

    - Staging (开发分支)
        ```sh
        git clone https://github.com/SillyTavern/SillyTavern -b staging && cd SillyTavern/docker
        ```

4. 在 Docker 文件夹内运行以下命令执行 `docker compose`。

    ```sh
    docker compose up -d
    ```

5. 执行以下 Docker 命令以获取 SillyTavern Docker 容器的 IP。

    ```sh
    docker network inspect docker_default
    ```

    您应该会看到类似于以下内容的输出。

    ```json
    [
        {
            "Name": "docker_default",
            "IPAM": {
                "Config": [
                    {
                        "Subnet": "172.18.0.0/16",
                        "Gateway": "172.18.0.1"
                    }
                ]
            }
        }
    ]
    ```

    记下 _Gateway_ 中显示的 IP，这将很重要。

6. 以管理员权限运行 _记事本_ 或您选择的代码编辑器，进入 `config` 文件夹并打开 _config.yaml_。

    在您选择的编辑器中，您应该会看到类似于以下内容。

    ```yaml
    whitelist:
        - 127.0.0.1
    ```

    在 _127.0.0.1_ 下方添加一行，输入您从 Docker 复制的 IP。完成后应类似于以下内容。

    ```yaml
    whitelist:
        - 127.0.0.1
        - 172.18.0.1
    ```

    按 _Ctrl+S_ 保存文件，然后退出编辑器。

    !!! info
    请注意，如果您将 Docker 网络配置为桥接模式，您也可以照常将外部 IP 地址添加到白名单。
    !!!

7. 重启 Docker 容器以应用新配置。

    ```sh
    docker compose restart sillytavern
    ```

8. 打开一个新浏览器，访问 [http://localhost:8000](http://localhost:8000)。几秒钟后，您应该会看到 SillyTavern 加载完成。

9. 尽情享受吧！ :D

### macOS

!!!
尽管 macOS 与 Linux 相似，但它没有 Docker Engine。您需要像 Windows 一样安装 Docker Desktop。
您还需要安装 [Homebrew](https://brew.sh/) 以在 Mac 上安装 Git。本节仅提供在 macOS 上实现的大致思路。
!!!

1. 按照 Docker 安装指南 [此处](https://docs.docker.com/desktop/setup/install/mac-install/) 安装 Docker Desktop。
2. 使用 Homebrew 安装 `git`。

    ```sh
    brew install git
    ```

3. 克隆 SillyTavern 仓库。

    - Release (稳定分支)

        ```sh
        git clone https://github.com/SillyTavern/SillyTavern && cd SillyTavern/docker
        ```

    - Staging (开发分支)
        ```sh
        git clone https://github.com/SillyTavern/SillyTavern -b staging && cd SillyTavern/docker
        ```

4. 在 Docker 文件夹内运行以下命令执行 `docker compose`。

    ```sh
    docker compose up -d
    ```

5. 执行以下 Docker 命令以获取 SillyTavern Docker 容器的 IP。

    ```sh
    docker network inspect docker_default
    ```

    您应该会看到类似于以下内容的输出。

    ```json
    [
        {
            "Name": "docker_default",
            "IPAM": {
                "Config": [
                    {
                        "Subnet": "172.18.0.0/16",
                        "Gateway": "172.18.0.1"
                    }
                ]
            }
        }
    ]
    ```

    记下 _Gateway_ 中显示的 IP，这将很重要。

6. 使用 `sudo` 打开 `nano`，并运行以下命令。

    ```sh
    sudo nano config/config.yaml
    ```

    !!!
    如果您无法运行 `nano`，可以通过 Homebrew 安装它，或使用 TextEdit。
    !!!

    在 `nano` 中，找到 `whitelist`。您应该会看到类似于以下内容。

    ```yaml
    whitelist:
        - 127.0.0.1
    ```

    在 _127.0.0.1_ 下方添加一行，输入您从 Docker 复制的 IP。完成后应类似于以下内容。

    ```yaml
    whitelist:
        - 127.0.0.1
        - 172.18.0.1
    ```

    按 _Ctrl+S_ 保存文件，然后按 _Ctrl+X_ 退出 `nano`。

    !!! info
    请注意，如果您将 Docker 网络配置为桥接模式，您也可以照常将外部 IP 地址添加到白名单。
    !!!

7. 重启 Docker 容器以应用新配置。

    ```sh
    docker compose restart sillytavern
    ```

8. 打开一个新浏览器，访问 [http://localhost:8000](http://localhost:8000)。几秒钟后，您应该会看到 SillyTavern 加载完成。

9. 尽情享受吧！ :D

## 配置 SillyTavern

SillyTavern 的配置文件 (config.yaml) 位于 `config` 文件夹中。配置此文件与不使用 Docker 的情况没有区别，但您需要以管理员权限运行 `nano` 或代码编辑器才能保存更改。

!!! warning
不要忘记重启 SillyTavern 的 Docker 容器以应用您的更改！请确保在 `docker` 文件夹内执行此命令。

```sh
docker compose restart sillytavern
```

!!!

## 定位用户数据

SillyTavern 的数据文件夹位于 `data` 文件夹中。备份文件应该很简单，但恢复或添加内容可能需要以管理员权限操作。

## 运行服务器插件

在 Docker 中运行插件（如 [HoYoWiki-Scraper-TS](https://github.com/Bronya-Rand/HoYoWiki-Scraper-TS) 或 [SillyTavern-Fandom-Scraper](https://github.com/SillyTavern/SillyTavern-Fandom-Scraper)）与不使用 Docker 在系统上运行没有区别，但我们需要对 Docker Compose 脚本进行轻微修改。

!!! Note
如果您已在 `docker` 文件夹中看到 _plugins_ 文件夹，可以跳过步骤 1-2。
!!!

1. 使用 `nano` 或代码编辑器，打开 _docker-compose.yml_，并在 `volumes` 下添加以下行。

    ```sh
        volumes:
            - "./config:/home/node/app/config"
            - "./data:/home/node/app/data"
            - "./plugins:/home/node/app/plugins"
    ```

2. 在 `docker` 文件夹内创建一个名为 _plugins_ 的新文件夹。
3. 按照插件的安装说明安装插件。
4. 使用以管理员权限运行的 `nano` 或代码编辑器，打开 `config` 文件夹中的 _config.yaml_，并启用 `enableServerPlugins`。

    ```sh
    enableServerPlugins: true
    ```

5. 重启 Docker 容器。

    ```sh
    docker compose restart sillytavern
    ```

6. 搞定。