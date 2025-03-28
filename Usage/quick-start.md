---
order: 190
icon: rocket
---

# 快速入门

!!!light
我完全不懂。请直接告诉我使用 SillyTavern 最简单、最快的方法。—— *匿名用户*
!!!

您可以在几分钟内开始使用 SillyTavern。以下是两种简单的方法：

* 您可以免费[使用 AI Horde](#使用-ai-horde-快速入门)。AI Horde 是一个社区驱动的 AI 服务，提供多种 AI 模型的访问。
* 如果您有 OpenAI 账户或想注册一个，可以[使用 OpenAI](#使用-openai-快速入门)。

## 使用 AI Horde 快速入门

1. 按照 [安装指南](/Installation/index.md) 安装并启动 SillyTavern。

2. 在 SillyTavern 的欢迎屏幕中，输入您的角色名称。此名称将用于聊天。

   ![这是一个可选标题](/static/quick-start/1_name.png)
3. 点击顶部栏中的 API 连接按钮。

   ![这是一个可选标题](/static/quick-start/2_api_conn.png)
4. 输入 AI Horde 的 API 密钥。您可以暂时使用 `0000000000`，或者从 [AI Horde](https://aihorde.net/) 获取一个免费密钥。

   ![这是一个可选标题](/static/quick-start/3_horde_key.png)
5. 选择一些要使用的 AI 模型。只需从顶部挑选几个即可，您可以稍后更改它们。

   ![这是一个可选标题](/static/quick-start/4_horde_models.png)
6. 关闭 API 连接窗口。在底部的聊天框中输入一条消息，然后按 Enter 键。

   ![这是一个可选标题](/static/quick-start/5_msg.png)
7. 您的 AI 将在几秒钟后回复。您可以继续与它[聊天](/Usage/Chatting/index.md)。成功！

   ![这是一个可选标题](/static/quick-start/6_success.png)

## 使用 OpenAI 快速入门

### 安装 SillyTavern

按照 [安装指南](/Installation/index.md) 安装并启动 SillyTavern。

### 获取 OpenAI 访问权限

1. 注册 OpenAI。
2. 前往 <https://platform.openai.com>
3. 点击右上角的账户图标，然后选择“查看 API 密钥”。
4. 点击“创建新的密钥”。立即将其复制到某处。**不要分享此密钥。拥有它的人可以使用您的账户调用 GPT，费用将由您承担。**

### 配置 SillyTavern 使用您的 API

1. 在 SillyTavern 的顶部栏中，点击 API 连接。
2. 在 API 下，选择聊天完成 (OpenAI)。
3. 在聊天完成来源下，选择 OpenAI。
4. 粘贴您在上一步中保存的 API 密钥。
5. 点击连接按钮。确认显示“有效”。
6. 默认情况下，SillyTavern 将使用 GPT-4 Turbo。您可以选择其他模型，但请先了解定价信息。

### 测试您的设置

1. 在 SillyTavern 的顶部栏中，点击最右侧的角色管理。
2. 选择一个现有角色，例如 Seraphina。
3. 在底部的文本框中，向 Seraphina 写点什么，然后按 Enter 键或点击发送按钮。

如果您一切操作正确，几秒钟后，Seraphina 应该会回复。