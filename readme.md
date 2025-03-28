# 什么是SillyTavern？

![SillyTavern - LLM前端，专为高级用户设计](/static/banner.png)

SillyTavern（简称ST）是一个本地安装的用户界面，允许您与文本生成大语言模型（LLM）、图像生成引擎以及TTS语音模型进行交互。我们的目标是为用户提供尽可能多的实用功能和对LLM提示的控制权，将陡峭的学习曲线视为乐趣的一部分。

SillyTavern 是一个由一群热衷于LLM的社区成员打造的热情项目，将始终保持免费和开源。从2023年2月开始，SillyTavern 作为 TavernAI 1.2.8 的一个分支启动，现已有超过200名贡献者和两年的独立开发经验，继续作为精通AI的爱好者的领先软件。

## 截图

|   [![API连接](/static/screenshot1.jpg)](/static/screenshot1.jpg)    |  [![聊天界面](/static/screenshot2.jpg)](/static/screenshot2.jpg)   |
|:--------------------------------------------------------------------:|:------------------------------------------------------------------:|
| [![高级格式化](/static/screenshot3.jpg)](/static/screenshot3.jpg)   | [![世界信息](/static/screenshot4.jpg)](/static/screenshot4.jpg)    |

## 安装要求

硬件要求极低：只要能运行 NodeJS 18 或更高版本的设备即可。如果您打算在本地机器上进行LLM推理，我们推荐使用至少6GB显存的NVIDIA 3000系列显卡。

请根据您的平台遵循安装指南：

* [Windows](/Installation/Windows.md)
* [Linux 和 Mac](/Installation/LinuxMacOS.md)
* [Android](/Installation/Android.md)
* [Docker](/Installation/Docker.md)

## 分支

SillyTavern 采用双分支系统开发，以确保所有用户获得流畅的体验。

* `Release` - 🌟 **推荐大多数用户使用。** 这是最稳定且推荐的分支，仅在重大版本发布时更新。适合大多数用户。通常每月更新一次。
* `staging` - ⚠️ **不推荐普通用户使用。** 此分支拥有最新功能，但需谨慎使用，因为它可能随时出现问题。仅适合高级用户和爱好者。每天更新多次。

## 除了SillyTavern我还需要什么？

由于SillyTavern只是一个界面，您需要访问LLM后端来提供推理能力。您可以使用AI Horde实现开箱即用的即时聊天。此外，我们还支持许多其他本地和基于云的LLM后端：OpenAI兼容API、KoboldAI、Tabby等。有关我们支持的API的更多信息，请参阅[API连接](/Usage/API_Connections/index.md)部分。

## 角色卡

SillyTavern 围绕“角色卡”概念构建。角色卡是一组提示，用于设定LLM的行为，是在SillyTavern中进行持久对话的必要条件。它们的功能类似于ChatGPT的GPTs或Poe的机器人。角色卡的内容可以是任何东西：抽象场景、为特定任务定制的助手、名人或虚构角色。

角色卡的名称字段是唯一必填项。要与语言模型开始中立对话，只需创建一个名为“Assistant”的新卡片，并将其余字段留空即可。要进行更具主题性的聊天，您可以为语言模型提供各种背景细节、行为和写作模式，以及一个启动聊天的场景。

若想在不选择角色卡的情况下进行快速对话，或仅测试LLM连接，只需在打开SillyTavern后，在欢迎屏幕的输入栏中键入您的提示。请注意，此类聊天是临时的，不会保存。

要了解如何定义角色卡，可查看默认角色（Seraphina）或从“下载扩展和资产”菜单中下载社区制作的精选卡片。

您也可以从头开始创建自己的角色卡。有关更多信息，请参阅[角色设计](/Usage/Characters/characterdesign.md)指南。

## 主要功能

* 高级[文本生成设置](/Usage/Prompts/advancedformatting.md)，包含许多社区制作的预设
* [世界信息支持](Usage/worldinfo.md)：创建丰富的背景故事或节省角色卡的令牌
* [群聊](/Usage/Characters/groupchats.md)：多机器人房间，让角色与您或彼此交谈
* [丰富的界面定制选项](/Usage/User_Settings/uicustomization.md)：主题颜色、背景图片、自定义CSS等
* [用户角色](/Usage/personas.md)：让AI了解一些关于您的信息，以增强沉浸感
* [内置RAG支持](/Usage/Characters/data-bank.md)：为您的聊天添加文档供AI参考
* 广泛的[聊天命令](/Usage/Chatting/slashcommands.md)子系统和自有[脚本引擎](/For_Contributors/st-script.md)

## 扩展

SillyTavern 支持扩展功能。

* [角色情感表情（精灵图）](/extensions/Expression-Images.md)
* [聊天历史自动摘要](/extensions/Summarize.md)
* 自动界面和[聊天翻译](extensions/Translation.md)
* [Stable Diffusion/FLUX/DALL-E图像生成](/extensions/Stable-Diffusion.md)
* [AI回复消息的文本转语音（通过ElevenLabs、Silero或操作系统的系统TTS）](/extensions/TTS.md)
* [网络搜索功能，为您的提示添加额外的现实世界上下文](/extensions/WebSearch.md)
* 更多扩展可从“下载扩展和资产”菜单中下载。

## 如何直接联系开发者？

* Discord: cohee, rossascends, wolfsblvt
* Reddit: [/u/RossAscends](https://www.reddit.com/user/RossAscends/), [/u/sillylossy](https://www.reddit.com/user/sillylossy/), [u/Wolfsblvt](https://www.reddit.com/user/Wolfsblvt/)
* [提交GitHub问题](https://github.com/SillyTavern/SillyTavern/issues)

## 我喜欢你们的项目！如何贡献？

* 我们欢迎拉取请求！请遵循[贡献指南](https://github.com/SillyTavern/SillyTavern/blob/release/CONTRIBUTING.md)开始。
* 我们也欢迎使用GitHub提供的模板提交有帮助且信息完整的错误报告。
* 我们不接受针对项目本身的货币捐款。

## 个人捐款

我们感谢您对个别贡献者的支持，但这不会影响SillyTavern的整体开发方向。

* RossAscends 有个人 [Patreon](https://www.patreon.com/RossAscends) 和 [Kofi](https://ko-fi.com/rossascends)

## 许可证

SillyTavern 是一个免费且开源的项目，根据 [AGPL-3.0许可证](https://github.com/SillyTavern/SillyTavern/blob/release/LICENSE) 发布。