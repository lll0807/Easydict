# Easy Translation 个人版

本版本基于 [Easydict](https://github.com/tisfeng/Easydict)，仅在主窗口、划词窗口、迷你窗口
和翻译服务设置中显示 DeepSeek。原有 OCR 与语音能力保留。

## 安装

Apple Silicon Mac 使用以下命令从个人软件源安装：

```bash
brew install --cask lll0807/tap/easy-translation
```

首次安装后，可以使用短名称管理：

```bash
brew upgrade --cask easy-translation
brew uninstall --cask easy-translation
```

安装项与原版 `easydict` 冲突；应用仍为 `Easydict.app`，保留现有 bundle ID。
安装包使用 ad-hoc 签名，没有 Apple 公证。首次打开如被系统拦截，在系统设置的
“隐私与安全性”中允许打开。

## 设置

打开应用设置 → 翻译服务 → DeepSeek，填写自己的 API Key；无需在仓库或安装脚本中保存密钥。
三个窗口默认都启用 DeepSeek 自动查询；不再提供添加其他翻译服务的按钮。
第一次启动个人版会启用 DeepSeek，此后尊重用户的启用/停用设置。

默认划词快捷键为 `Option + D`。截图翻译为 `Option + S`，输入翻译为 `Option + A`。
按功能授予辅助功能或屏幕录制权限。

## 发布与更新

个人源码分支为 `feat/deepseek-only-homebrew`；推送源码会触发 `Personal DeepSeek build`。
构建使用 GitHub 的 Xcode 27 macOS runner，运行 Release 构建和现有回归测试，
再生成 Apple Silicon 安装包及 SHA-256 校验和。仅在构建、检查和审查后发布到本 Fork。

Homebrew 配置位于 `lll0807/homebrew-tap` 的 `Casks/easy-translation.rb`。
发布新版后同步更新该配置中的版本、下载地址与校验和。
应用更新源为空的个人 feed，避免应用内更新将个人版覆盖为原版；请通过 Homebrew 更新。

遵循原项目 GPL-3.0 许可证，发布安装包对应的源码保留在本 Fork 的发布 tag 中。
