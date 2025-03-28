---
order: 112
route: /installation/st-1.12.0-migration-guide/
---

# 1.12.0 迁移指南

SillyTavern 1.12.0（代号“Neo Server”更新）包含若干关键更改，可能会影响您使用 SillyTavern 的方式。

本指南将帮助您为更新做好准备，并提供进一步的指导。

## 数据存储更新

1.12.0 更改了 SillyTavern 处理用户数据的方式。

之前，所有持久数据都与前端部分一起存储在 `/public` 目录中，这造成了混乱和潜在的故障点，同时也使得容器化和系统范围的应用安装变得相当具有挑战性。

### 发生了什么变化？

所有来自 `/public` 的持久信息，例如设置和聊天记录（完整列表见下文），都被移动到一个独立的、可配置路径的目录中，使其便携且独立于 Web 服务器本身。为了兼容性需要，例如托管扩展、全尺寸角色卡、用户上传的图片等，已设置智能重定向，自动从数据目录中托管用户文件。

### 设置数据根目录

您可以通过 `config.yaml` 或在启动服务器时使用 `--dataRoot` 控制台参数，提供数据根目录的绝对路径或相对路径（相对于 ST 仓库目录）。

> YAML 示例

```yaml
# -- 数据配置 --
# 用户数据存储的根目录
dataRoot: C:\Users\Harry\Documents\ST-Data
```

> 控制台示例

```bash
node server.js --dataRoot="/Users/harry/ST-Data"
# 或
npm run start -- --dataRoot="/Users/harry/ST-Data"
```

默认数据根路径是 `./data`，即 SillyTavern 仓库中的 `data` 目录。

!!! info 注意
数据根路径应为**完整的绝对路径**或**完整的相对路径**。您_不能_使用像 `~` 或 `%APP_DATA%` 这样的路径快捷方式，因为这些是由 shell 而非操作系统解析的。
!!!

### 迁移

#### **重要！** 开始之前

1. **仅当您想将 dataRoot 从默认位置移动时执行此部分，否则跳过。** 在拉取更新后首次运行服务器之前设置数据根目录。运行 `npm install` 以使 `config.yaml` 更新为新值，或传递控制台参数。
2. 所有数据将迁移到 `default-user` 账户中。有关更多信息，请参见下文的 [用户](#users)。

#### 无容器（裸机）安装

您无需做任何操作！当您启动 ST 服务器并检测到旧存储格式（通过检查 `/public/characters` 目录是否存在）时，自动迁移将为您处理一切。

在移动任何文件时，将在 `/backups/_migration/YYYY-MM-DD`（解析为当前日期）目录中自动创建备份，但运行迁移前进行完整的手动备份始终是一个好习惯。

#### 容器化（Docker）安装

在 Docker 卷中迁移数据稍显复杂，但相当直接。虽然仓库提供的 `docker-compose.yml` 已更新以反映这些变化，但您可能需要调整自定义工作流程/部署。

**步骤 1.** 创建一个新卷，并将其挂载到容器内的 "/home/node/app/data" 路径。不要移除 `config` 卷。

```yaml
volumes:
    - "./config:/home/node/app/config"
    - "./data:/home/node/app/data"
```

**步骤 2.** 将 `config` 卷中的所有内容（除了 `config.yaml` 文件）移动到 `data` 卷的 `default-user` 子目录中。

**步骤 3.** 重建容器并启动。

!!! info 注意
`/public` 目录与 `config` 卷之间的软链接不再需要，也未内置于 Docker 容器中！
!!!

#### 需要迁移的内容？

以下文件和目录需要进行数据迁移。假设使用默认配置，下表提供了迁移前后的路径。

| 之前                                   | 之后                                 |
|----------------------------------------|--------------------------------------|
| /secrets.json                          | /data/default-user/secrets.json      |
| /thumbnails                            | /data/default-user/thumbnails        |
| /vectors                               | /data/default-user/vectors           |
| /public/settings.json                  | /data/default-user/settings.json     |
| /public/stats.json                     | /data/default-user/stats.json        |
| /public/assets                         | /data/default-user/assets            |
| /public/backgrounds                    | /data/default-user/backgrounds       |
| /public/characters                     | /data/default-user/characters        |
| /public/chats                          | /data/default-user/chats             |
| /public/context                        | /data/default-user/context           |
| /public/scripts/extensions/third-party | /data/default-user/extensions        |
| /public/group chats                    | /data/default-user/group chats       |
| /public/groups                         | /data/default-user/groups            |
| /public/instruct                       | /data/default-user/instruct          |
| /public/KoboldAI Settings              | /data/default-user/KoboldAI Settings |
| /public/movingUI                       | /data/default-user/movingUI          |
| /public/NovelAI Settings               | /data/default-user/NovelAI Settings  |
| /public/OpenAI Settings                | /data/default-user/OpenAI Settings   |
| /public/QuickReplies                   | /data/default-user/QuickReplies      |
| /public/TextGen Settings               | /data/default-user/TextGen Settings  |
| /public/themes                         | /data/default-user/themes            |
| /public/worlds                         | /data/default-user/worlds            |
| /default/content/content.log           | /data/default-user/content.log       |

## 用户

1.12.0 添加了一个（完全可选的）功能，允许在同一服务器上创建多用户设置，使多个用户能够同时使用各自完全隔离的 SillyTavern 实例。用户账户还可以设置密码保护，以增加额外的隐私层。

请参阅 [用户](/Administration/multi-user.md) 文档以获取更多信息。