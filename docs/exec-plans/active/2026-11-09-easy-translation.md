# DeepSeek 单服务与个人 Homebrew 安装

- 状态：active
- 创建日期：2026-11-09
- 负责人：lll0807
- 关联 Issue/PR：none

## 执行上下文

- **Agent Name:** `Codex`
- **Model:** `GPT-6`
- **Environment:** `macOS 26.5 / Xcode Unknown (Unknown)`

## 背景

用户希望在自己的 Easydict Fork 中只显示 DeepSeek 翻译，并通过 easy-translation 安装。
本机只有 Command Line Tools；使用 GitHub macOS runner 构建和运行现有测试。

## 目标与范围

- 目标结果：三个查询窗口及服务设置仅显示 DeepSeek；提供个人 Homebrew Cask 并安装。
- 允许修改路径：服务存储、配置、服务设置、发布来源、个人构建工作流及相关文档。
- 同任务 history：`docs/histories/2026-11/2026-11-09-easy-translation.md`
- 用户限制：安装项名称使用 `easy-translation`；仅显示 DeepSeek 翻译。
- 非目标：新增翻译服务、自动划词交互变更、删除现有 OCR/TTS 支持。
- 验收标准：构建成功、现有相关测试通过、安装成功、实际界面仅显示 DeepSeek。

## 工作计划

1. 收敛各查询窗口的服务为 DeepSeek，并保留 API Key 设置。
2. 配置 Fork 更新来源与 macOS 构建工作流，验证产物。
3. 发布个人安装包，创建 lll0807/homebrew-tap 并安装 easy-translation。
4. 实测界面、审查差异、记录结果。

## 风险与决策

- 保留服务工厂，避免破坏系统 OCR 与语音播放。
- 保留现有 bundle ID 与应用名；Homebrew 安装项独立命名并声明与原版冲突。
- 不使用上游的更新包；个人版本通过 Homebrew 更新。
- 没有开发者证书时使用 ad-hoc 签名，明确记录签名及启动验证结果。
- DeepSeek API Key 由用户在应用设置中填写，不写入仓库或发布包。

## 进度

- [x] 单服务修改与审查。
- [ ] GitHub 构建及现有测试。
- [ ] Homebrew 发布与本机安装。
- [ ] 界面验证与记录。

## 验证

- 初始 HEAD：`f5b61fafb4ba4d4778e9360df846f6c29ae368f0`，工作树干净。
- 本机 `xcodebuild -version` 受阻：未安装完整 Xcode。
- Swift 语法解析、工作流 YAML/Shell 解析、Info.plist 与个人 feed XML 检查通过。
- Standards 与 Spec 两项源码审查未发现确定缺陷；尚不构成构建或运行通过证据。
- GitHub Actions run `42591262402` 的 Release 构建通过；Debug 测试完成编译，但宿主启动失败
  （NSPOSIXErrorDomain 162 / Runningboard 5），测试用例未执行。
- Debug 默认 inference entitlement 需要开发者授权；CI 改用现有空 entitlement 文件，待复验。
- 后续记录实际构建、测试和界面验证结果。

## 完成条件

- 核心修改、个人分发和安装已完成，实际验证结果已记录。
- 将计划归档到 completed/2026-11，并更新同名 history。
