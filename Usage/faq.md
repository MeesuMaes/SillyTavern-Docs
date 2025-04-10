---
order: 180
icon: question
---

# 常见问题解答

## 解释一下 SillyTavern 是什么

现代 AI 语言模型（如 ChatGPT）变得如此强大，以至于其中一些现在能够令人信服地模拟您创建的角色，您可以与之聊天、一起创作小说等。例如，您可以告诉 AI 假装自己是中世纪日本的围棋教练“十兵卫”，它会根据此设定行动和回应。您可以与十兵卫进行长时间的聊天，一起去酒馆，决定与武士打一架，只要您能想象到的任何事情，AI 都会配合并围绕这些内容进行创作/反应，充当您的陪衬和地下城主。您的想象力是唯一的限制。您可以让 AI 假装自己是神奇女侠。您还可以指定一个场景（“神奇女侠和我正在抢银行”）、写作风格（“神奇女侠用黑人英语说话”）或任何您能想到的其他内容。

SillyTavern 是一个便于这些用途的应用程序：

* 它是一个用户界面，负责与 AI 语言模型通信。
* 它允许您创建新的角色卡（提示），并轻松在它们之间切换。
* 它允许您导入其他人创建的角色。
* 它会保存您与角色的聊天历史，允许您随时恢复、新建聊天、回顾旧聊天等。
* 在后台，它会为您准备 AI 提示所需的内容。具体来说，它会发送一个系统提示（AI 的指令），引导 AI 遵循某些规则以提高响应的准确性。

## 给我一个 AI 模型选项的概览

SillyTavern 可以与两种类型的 AI 交互：

1. [网络服务](/Usage/API_Connections/openai.md)（基于云，通常付费，专有，封闭）
2. [自托管](/Usage/API_Connections/self-hosted.md)（本地，免费，开源）

### 付费网络服务 AI

付费网络模型是黑盒子。您向公司付费以使用他们的 AI 服务。您在 SillyTavern 中输入账户信息，它会代表您连接到提供商以使用 AI。

优点：

* 开始使用非常简单。
* AI 写作质量最高。

缺点：

* 使用需要花钱。
* 一切都在他们的服务器上记录。存在隐私问题。
* 它们通常受到审查，会拒绝与您讨论某些话题。

### 自托管 AI

自托管模型是您可以在自己电脑上运行的免费模型，但需要强大的电脑和更多的设置工作。

优点：

* 一旦设置好，即使没有网络也可以免费使用。
* 完全隐私。您写的所有内容都留在您的电脑上。
* 模型种类繁多。作为社区驱动的技术，您可以找到适合特定任务或行为的模型。

缺点：

* 它们不如 <abbr title="最先进">SOTA</abbr> 模型强大（即对话写作较差，创造力较低等）。
* 运行本地模型需要至少 6GB VRAM 的 GPU。

如果您有兴趣使用这些，请参考专用指南：[如何使用自托管模型](/Usage/API_Connections/self-hosted.md)。

## 我可以在手机或平板上使用 SillyTavern 吗？

iPhone 和 iPad 无法运行整个 SillyTavern 应用程序，但由于它只是一个 Web 界面，您可以在家用 Wi-Fi 上的另一台电脑上运行它，然后通过移动浏览器访问。有关更多信息，请参考 [远程连接](/Administration/remote-connections.md)。

对于 Android 用户，除了上述方法外，您还可以使用 Termux 应用程序直接在手机上运行整个 SillyTavern，无需电脑。参考 [安装 (Android)](/Installation/Android.md)。（注意：Termux 安装未得到官方支持，我们无法保证其正常运行。）

## 我尝试导入 PNG 角色卡，但收到无效的错误。为什么？

有两种可能：

1. 该卡内未嵌入定义，只是普通的图像文件。某些程序或文件管理器在保存时会剥离卡中的嵌入定义。确保使用分享者发布的原始 PNG 文件。
2. 该 PNG 文件实际上是带有 `.png` 文件名的 WEBP 文件。您可以尝试在导入前将卡重命名为 `.webp`，或寻找该图像的正确 PNG 版本。

## 如何创建我自己的 AI 角色？

1. 点击角色管理按钮
2. 点击创建新角色
3. 在角色名称下，输入一个名字，例如 Amanda
4. （可选）点击选择头像按钮，为该角色选择一张图像肖像
5. 在描述下，描述角色，并包含您认为与聊天相关的任何信息。例如：```Amanda 是一名在间隔年旅行的学生。她身高 6 英尺，是排球运动员。她身材健美。她有长长的棕色头发。她喜欢维多利亚时期的英格兰，喜欢看电视和阅读与那个时期相关的小说。```
   例如，如果您希望 Amanda 友好，可以添加：```Amanda 非常开朗外向。```
6. 在首条消息下，编写角色在新聊天开始时的问候语。例如：```*Amanda 向你挥手* 嘿！你也是背包客吗？```
7. 点击创建角色按钮

您现在有了一个可以聊天的基本角色。从角色列表中选择 Amanda，将开始一个新聊天。

请注意，您可以使用描述和/或首条消息创建更具体的场景，并/或在描述中包含自己。例如：

```txt
描述：
Amanda 是一名在间隔年旅行的学生。她身高 6 英尺，是排球运动员。她身材健美。她有长长的棕色头发。她喜欢维多利亚时期的英格兰，喜欢看电视和阅读与那个时期相关的小说。她一直保守着一个沉重压在她灵魂上的秘密。她在等待合适的人来倾诉，但这可能会导致与一个强大的秘密社团展开猫鼠游戏。她最近抵达加尔各答。

你是 Rajesh Nahasmapetilon，一位世界著名的印度排球巨星。你在加尔各答散步。Amanda 看到你，兴奋地尖叫。

首条消息：
*Amanda 跑向你，笑容满面。* Rajesh！我不敢相信！我超级崇拜你。我的卧室里有你的海报。
```

您包含的任何相关信息都可以被使用。其使用效果取决于 AI 模型的能力。

注意：创建角色后，您可以回去编辑除名称外的任何信息。

## 我的 API 密钥存储在哪里？为什么我看不到它们？

SillyTavern 将您的 API 密钥保存到服务器目录中的 `secrets.json` 文件中。

默认情况下，输入密钥并重新加载页面后，它们不会暴露给前端。

要通过点击 API 块中的按钮查看您的密钥：

1. 在 `config.yaml` 文件中将 `allowKeysExposure` 的值设置为 `true`。
2. 重启 SillyTavern 服务器。

## 性能建议

### 为什么界面这么慢/卡顿？

* 尝试在用户设置面板中启用“无模糊效果（快速界面）”模式。
* 在界面主题设置中启用“减少动态效果”以移除装饰性动画。
* 确保您的浏览器启用了硬件加速。

### 我遇到输入延迟怎么办？

性能下降，尤其是输入延迟，最常见的原因是浏览器扩展。已知有问题的扩展包括：

* iCloud 密码管理器
* DeepL 翻译
* 基于 AI 的语法校正工具
* 各种广告拦截扩展

如果您遇到性能问题且无法确定原因，或怀疑是 SillyTavern 本身的问题，请：

1. [记录性能配置文件](https://developer.chrome.com/docs/devtools/performance/reference)
2. 将配置文件导出为 JSON 文件
3. 提交给开发团队进行分析

我们建议首先禁用所有浏览器扩展和第三方 SillyTavern 扩展进行测试，以隔离性能下降的来源。

### 当我导入大量角色时，应用变慢了。为什么？

不幸的是，SillyTavern 并非设计用来处理庞大的角色库。角色越多，加载角色列表所需的时间就越长。证据表明，当您拥有超过 1000 个角色时，性能下降开始变得明显。

不过，您可以采取一些措施来缓解这个问题：

**1. 使用懒加载。**

在 `config.yaml` 文件中将 `performance.lazyLoadCharacters` 的值设置为 true 以启用角色懒加载。下次服务器重启后，角色列表将仅加载您与之交互的角色的完整数据。请注意，如果某些第三方扩展未更新以支持此设置，启用此功能可能会导致其无法正常工作（请联系扩展开发者获取更多信息）。

**2. 使用内存缓存。**

如果您有多余的 RAM，可以增加内存缓存容量。这将允许服务器在内存中保留更多角色，减少加载时间。您可以在 `config.yaml` 文件中调整 `performance.memoryCacheCapacity` 的值到更高的数字。默认值为 `100mb`。大致经验法则是：每拥有 3000 个角色，将值增加 100mb。

**限制：**

1. 启用懒加载时，高级（模糊）角色搜索将不起作用，仅搜索角色名称。
2. 由于可用内存有限，Android 设备上禁用了内存缓存。

## 如何让 AI 写更多？

有时 AI 只回复一句话，而您希望它更详细。
这通常是本地运行模型的问题。

如果您只是想让机器人从其最近回复的结尾处继续写作，您可以在输入栏中不输入任何内容并点击发送，以发送一条空用户消息。这将强制机器人继续故事。

解决策略：

* 增加 `响应长度` 设置的值
* 为角色设计一个好的 `首条消息`，展示他们以冗长的方式说话。AI 模型在获得您期望的写作风格指导时会有很大改进。
* 在角色的描述框中添加诸如“喜欢多说话”或“非常啰嗦的发言者”之类的短语
* 在 `作者笔记` 或 `对话后指令提示` 中做同样的事情
* 作为最后手段，您可以尝试开启 `自动继续`（在用户设置面板中），但这会使响应变慢，因为它让 AI 连续生成小段回复，然后将它们组合成一个大回复。它也可能与某些 API 选项不兼容。

## 如何让 AI 写更少？

这主要对 ChatGPT 或 Claude 等模型是个问题。可以应用相反的策略。

* 减少 `响应长度` 设置的值
* 在角色描述中给角色添加诸如“言简意赅”或“不爱说话”的短语。
* 给角色一个简短的首条消息，以设定聊天的基调和期望。
* 确保 `自动继续` 已关闭。

## 如何让 AI 停止编写我角色的动作，并独自推动剧情？

这应在 `作者笔记` 中通过以下短语组合处理：

* \{\{char\}\} 的回应应仅对 \{\{user\}\} 的行动做出被动和反应。
* 你的下一次回应应仅从 \{\{char\}\} 的视角出发。
* 你永远不允许为 \{\{user\}\} 指定行动或言语。