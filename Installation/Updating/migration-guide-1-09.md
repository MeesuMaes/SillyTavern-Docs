---
order: 109
---

# 1.9.0 迁移指南

## 如果我使用的是 main/dev 分支，如何迁移到新分支？

_**建议进行全新安装。**_ 然而，如果您希望使用现有的 SillyTavern 副本，请按照以下说明操作。

**重要！** 在进行任何操作之前，请*完整备份*您的安装。在这个过程中，您可能会*丢失数据*，所以不要忽视此警告。

不确定需要备份哪些文件？请查看此处列表：[如何更新 SillyTavern](/Installation/Updating/index.md#updating-from-1120-to-1120)

### Git 安装

1. 在您的 SillyTavern 安装文件夹中打开终端提示符（cmd、PowerShell、Termux 等）。
2. 输入 `git fetch` 然后 `git pull` 以拉取更新。
3. 您可能会丢失设置。您备份了吗？`git switch release` 或 `git switch staging` 将分别切换到对应的分支。
4. 如果没有错误，请跳到下一步。如果出现类似以下内容：
   ```
   error: Your local changes to the following files would be overwritten by checkout:
        config.conf
        public/css/bg_load.css
        public/settings.json
   ```
   您将看到受影响的文件列表。如果您不在意这些设置文件被替换，`git switch -f release` 或 `git switch -f staging` 将设置您的分支。
   如果您希望保存这些更改，请从备份中恢复。

5. 输入 `npm install` 然后 `npm run start` 以测试一切是否正常运行。
6. 尽情享受吧！如有需要，从备份中恢复您的数据。

### fatal: invalid reference: release

如果您从旧远程仓库（迁移到组织仓库之前）仅克隆了单一分支，可能会发生这种情况。要修复此问题，您需要添加并从新远程仓库获取分支：

```
git remote add st https://github.com/SillyTavern/SillyTavern
git fetch st
git checkout -t st/release
```

然后从步骤 5 继续。

### ZIP 安装

对您来说没有任何变化。只需像往常一样下载分支/发布版的 ZIP 文件即可。