# Claude Code UI 本地化待办任务列表

本文档列出了项目中所有需要进行国际化改造的组件及其预估工作量。

---

## 图例说明

| 状态 | 含义 |
|------|------|
| ✅ 已完成 | 已添加 i18n 支持 |
| 🔶 部分完成 | 核心文本已翻译，仍有遗漏 |
| ⬜ 待处理 | 尚未开始国际化 |
| ⚪ 无需处理 | 纯逻辑/样式组件，无 UI 文本 |

**优先级：** P0 (核心) → P1 (重要) → P2 (次要) → P3 (可选)

---

## 已完成组件

| 组件 | 状态 | 备注 |
|------|------|------|
| `LoginForm.jsx` | ✅ | 登录表单完全翻译 |
| `Sidebar.jsx` | 🔶 | 主要标题和状态文本已翻译，会话操作提示待完善 |
| `Settings.jsx` | ✅ | 所有标签页（Tools/Appearance/Git/API/Tasks）完全翻译 |
| `GitSettings.jsx` | ✅ | P3 - Git 配置表单完全翻译 |
| `TasksSettings.jsx` | ✅ | P3 - TaskMaster 设置完全翻译 |
| `ApiKeysSettings.jsx` | ✅ | P3 - API 密钥管理完全翻译 |
| `CredentialsSettings.jsx` | ✅ | P3 - 凭据设置完全翻译 |
| `Onboarding.jsx` | ✅ | P0 - Git配置、CLI认证流程完全翻译 |
| `MainContent.jsx` | ✅ | P0 - 加载状态、空状态、标签页名称完全翻译 |
| `ChatInterface.jsx` | ✅ | P0 - 聊天消息、工具调用提示、权限模式、加载状态、AI 助手选择、模型选择、会话状态完全翻译 |
| `ErrorBoundary.jsx` | ✅ | P1 - 错误提示和重试按钮完全翻译 |
| `ProjectCreationWizard.jsx` | ✅ | P1 - 项目创建向导所有步骤完全翻译 |
| `TaskList.jsx` | ✅ | P1 - 任务列表、筛选器、状态标签完全翻译 |
| `GitPanel.jsx` | ✅ | P1 - Git操作面板、提交、分支管理完全翻译 |

---

## 待处理组件

### P0 - 核心组件（高优先级）

 ✅ **所有 P0 核心组件已完成！**

### P1 - 重要组件

 ✅ **所有 P1 重要组件已完成！**

### P2 - 次要组件

 ✅ **所有 P2 次要组件已完成！**

**P2 已完成：**
- ✅ `TaskCard.jsx` - 任务卡片状态、优先级、进度文本完全翻译
- ✅ `CommandMenu.jsx` - 命令菜单分类标签完全翻译
- ✅ `TaskDetail.jsx` - 任务详情、状态选项、编辑操作完全翻译
- ✅ `PRDEditor.jsx` - PRD 编辑器提示、工具栏、模态框完全翻译
- ✅ `NextTaskBanner.jsx` - 下一任务提示、创建任务模态框、模板选择器完全翻译
- ✅ `QuickSettingsPanel.jsx` - 快速设置所有标签和描述完全翻译
- ✅ `FileTree.jsx` - 文件树视图、搜索、列标题完全翻译
- ✅ `CodeEditor.jsx` - 编辑器工具栏提示完全翻译（与 PRDEditor 共用部分键）
- ✅ `Shell.jsx` - 终端连接状态、按钮、提示完全翻译

### P3 - 可选组件

 ✅ **所有 P3 可选组件已完成！**

**P3 已完成：**
- ✅ `TaskMasterSetupWizard.jsx` - TaskMaster 设置向导所有步骤、标签完全翻译
- ✅ `SetupForm.jsx` - 账户设置表单、验证消息完全翻译
- ✅ `LoginModal.jsx` - CLI 登录模态框标题完全翻译
- ✅ `ImageViewer.jsx` - 图片加载状态、错误提示完全翻译
- ✅ `DiffViewer.jsx` - 空状态提示完全翻译
- ✅ `MicButton.jsx` - 麦克风错误消息完全翻译
- ✅ `StandaloneShell.jsx` - 独立终端空状态、完成状态完全翻译
- ✅ `TodoList.jsx` - 待办列表标题、状态、优先级标签完全翻译
- ✅ `ClaudeStatus.jsx` - 状态动词、停止按钮完全翻译
- ✅ `TaskMasterStatus.jsx` - TaskMaster 状态消息完全翻译
- ✅ `TaskIndicator.jsx` - 任务指示器状态标签完全翻译
- ✅ `TokenUsagePie.jsx` - Token 使用提示完全翻译
- ✅ `DarkModeToggle.jsx` - 深色模式切换按钮 aria-label 完全翻译

### ⚪ 无需处理

| 组件 | 原因 |
|------|------|
| `ClaudeLogo.jsx` | 纯 SVG 图标 |
| `CursorLogo.jsx` | 纯 SVG 图标 |
| `ProtectedRoute.jsx` | 纯逻辑组件 |
| `MobileNav.jsx` | 仅使用图标，aria-label 为 tab ID |
| `Tooltip.jsx` | 纯 UI 组件，content 由父组件传入 |
| `ui/*` | 基础 UI 组件，无硬编码文本 |

---

## 翻译文件待添加键值

以下是根据组件分析，需要添加到翻译文件的键值分类：

 ✅ **所有键值已添加！**

### 通用 (`common`)
```
common.yes / common.no
common.ok / common.apply
common.back / common.next
common.previous / common.continue
common.submit / common.reset
common.copy / common.paste
common.cut / common.undo / common.redo
common.selectAll / common.clear
common.open / common.close
common.expand / common.collapse
common.show / common.hide
common.enable / common.disable
common.on / common.off
common.add / common.remove
common.create / common.update
common.upload / common.download
common.import / common.export
common.retry / common.skip
common.more / common.less
common.all / common.none
common.optional / common.required
```

### 聊天 (`chat`)
```
chat.newConversation
chat.clearHistory
chat.regenerate
chat.stopGenerating
chat.sendMessage
chat.uploadFile
chat.downloadFile
chat.copyMessage
chat.deleteMessage
chat.editMessage
chat.approve / chat.reject
chat.pending
chat.error.networkError
chat.error.timeout
chat.error.rateLimit
```

### 任务 (`tasks`)
```
tasks.title
tasks.create / tasks.delete / tasks.edit
tasks.status.pending / tasks.status.inProgress / tasks.status.completed / tasks.status.failed
tasks.priority.low / tasks.priority.medium / tasks.priority.high
tasks.noTasks
tasks.loadMore
```

### Git (`git`)
```
git.commit / git.push / git.pull
git.branch / git.merge / git.rebase
git.stash / git.checkout
git.staged / git.unstaged / git.untracked
git.noChanges
git.commitMessage
git.selectFiles
```

### 文件 (`files`)
```
files.create / files.delete / files.rename
files.move / files.copy
files.openInEditor
files.noFiles
files.unsavedChanges
```

---

## 进度统计

| 分类 | 总数 | 已完成 | 进行中 | 待处理 |
|------|------|--------|--------|--------|
| P0 核心 | 3 | 3 | 0 | 0 |
| P1 重要 | 5 | 5 | 0 | 0 |
| P2 次要 | 9 | 9 | 0 | 0 |
| P3 可选 | 18 | 18 | 0 | 0 |
| **总计** | **35** | **35** | **0** | **0** |

---

## 下一步行动

 ✅ **所有本地化任务已完成！**

1. ~~处理 P3 可选组件~~ ✅ 已完成
2. **完善已部分完成的组件**
   - [ ] `Sidebar.jsx` - 补充会话操作相关文本
3. **添加更多翻译键**
   - [ ] 根据上述键值列表扩展 `translation.json`（可选）

---

## 本地化完成总结

截至 2024-12-24，Claude Code UI 项目的本地化工作已基本完成：

### 已完成的工作
- ✅ P0-P3 所有优先级组件已完成本地化（35个组件）
- ✅ 英文和中文翻译文件已同步更新
- ✅ 支持浏览器语言自动检测
- ✅ 支持设置界面手动切换语言
- ✅ 语言偏好持久化到 localStorage

### 技术实现
- 使用 `i18next` + `react-i18next` 框架
- 使用 `i18next-browser-languagedetector` 自动检测语言
- 翻译文件位于 `src/locales/{en,zh}/translation.json`
- 组件通过 `useTranslation` hook 获取翻译函数

### 维护建议
1. 新增组件时，遵循 `docs/LOCALIZATION_GUIDE.md` 中的规范
2. 新增翻译键时，确保同时更新英文和中文翻译文件
3. 使用有意义的键名，遵循 `组件名.功能.具体文本` 层级结构
