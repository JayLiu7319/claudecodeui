# Claude Code UI 本地化开发指南

本文档为开发者提供完整的国际化 (i18n) 开发指南，帮助为项目添加多语言支持。

---

## 目录

1. [技术栈概述](#技术栈概述)
2. [文件结构](#文件结构)
3. [快速开始](#快速开始)
4. [翻译键命名规范](#翻译键命名规范)
5. [组件改造步骤](#组件改造步骤)
6. [常见场景处理](#常见场景处理)
7. [测试与验证](#测试与验证)

---

## 技术栈概述

| 库 | 版本 | 用途 |
|---|---|---|
| `i18next` | latest | 核心国际化框架 |
| `react-i18next` | latest | React 集成层 |
| `i18next-browser-languagedetector` | latest | 自动语言检测 |

**核心功能：**
- 自动检测浏览器语言
- 语言偏好持久化到 localStorage
- 即时语言切换（无需刷新页面）

---

## 文件结构

```
src/
├── i18n/
│   └── index.js              # i18n 配置入口
├── locales/
│   ├── en/
│   │   └── translation.json  # 英文翻译
│   └── zh/
│       └── translation.json  # 中文翻译
├── components/
│   └── *.jsx                 # 需要国际化的组件
└── main.jsx                  # 导入 i18n 配置
```

---

## 快速开始

### 1. 添加翻译键值

**英文 (`src/locales/en/translation.json`):**
```json
{
  "myComponent": {
    "title": "My Title",
    "description": "This is a description"
  }
}
```

**中文 (`src/locales/zh/translation.json`):**
```json
{
  "myComponent": {
    "title": "我的标题",
    "description": "这是一段描述"
  }
}
```

### 2. 在组件中使用

```jsx
import { useTranslation } from 'react-i18next';

function MyComponent() {
  const { t } = useTranslation();
  
  return (
    <div>
      <h1>{t('myComponent.title')}</h1>
      <p>{t('myComponent.description')}</p>
    </div>
  );
}
```

---

## 翻译键命名规范

### 层级结构

采用 **组件名.功能.具体文本** 的层级结构：

```json
{
  "sidebar": {                    
    "projects": "Projects",       
    "searchProjects": "Search projects...",
    "newProject": "New Project"
  },
  "settings": {
    "tabs": {                    
      "tools": "Tools",
      "appearance": "Appearance"
    },
    "appearance": {
      "darkMode": "Dark Mode"
    }
  }
}
```

### 命名规则

| 规则 | 示例 |
|-----|------|
| 使用 camelCase | `searchProjects` ✅, `search_projects` ❌ |
| 按组件/功能分组 | `sidebar.title`, `settings.appearance.darkMode` |
| 避免重复前缀 | `login.username` ✅, `login.loginUsername` ❌ |
| 通用文本放 common | `common.save`, `common.cancel` |

---

## 组件改造步骤

### Step 1: 导入 Hook

```jsx
import { useTranslation } from 'react-i18next';
```

### Step 2: 调用 Hook

```jsx
function MyComponent() {
    const {t, i18n} = useTranslation();
    // t: 翻译函数
    // i18n: i18n 实例（用于切换语言等）
}
```

### Step 3: 替换硬编码文本

| 场景 | 原代码 | 改造后 |
|-----|--------|--------|
| 静态文本 | `<h1>Title</h1>` | `<h1>{t('key')}</h1>` |
| 属性值 | `placeholder="Search"` | `placeholder={t('key')}` |
| 条件文本 | `{loading ? 'Loading...' : 'Done'}` | `{loading ? t('common.loading') : t('common.done')}` |

---

## 常见场景处理

### 1. 带变量的文本

**翻译文件：**
```json
{
  "greeting": "Hello, {{name}}!",
  "itemCount": "{{count}} items"
}
```

**使用：**
```jsx
t('greeting', { name: 'Alice' })     // "Hello, Alice!"
t('itemCount', { count: 5 })         // "5 items"
```

### 2. 复数形式

**翻译文件：**
```json
{
  "sessions": "{{count}} session",
  "sessions_plural": "{{count}} sessions"
}
```

**使用：**
```jsx
t('sessions', { count: 1 })   // "1 session"
t('sessions', { count: 5 })   // "5 sessions"
```

### 3. 切换语言

```jsx
const { i18n } = useTranslation();

// 切换到中文
i18n.changeLanguage('zh');

// 切换到英文
i18n.changeLanguage('en');

// 获取当前语言
console.log(i18n.language);  // "zh" 或 "en"
```

### 4. 在非组件中使用

```jsx
import i18n from '../i18n';

// 直接使用
const message = i18n.t('common.error');
```

---

## 测试与验证

### 本地测试

1. 启动开发服务器：`npm run dev`
2. 打开设置 → 外观 → 语言
3. 切换语言，验证 UI 即时更新
4. 刷新页面，验证语言偏好保持

### 检查遗漏

搜索项目中仍存在的硬编码文本：

```bash
# 搜索常见硬编码模式
grep -r "\"[A-Z][a-z]" src/components --include="*.jsx" | head -20
```

### 验证翻译完整性

确保两个翻译文件的键完全一致：

```bash
# 比较键结构
diff <(jq 'keys' src/locales/en/translation.json) <(jq 'keys' src/locales/zh/translation.json)
```

---

## 常见问题

### Q: 翻译不生效？
- 检查是否在 `main.jsx` 中导入了 `'./i18n'`
- 检查翻译键是否正确

### Q: 如何添加新语言？
1. 创建 `src/locales/{lang}/translation.json`
2. 在 `src/i18n/index.js` 中导入并添加到 resources

### Q: 如何处理日期/数字格式化？
使用 i18next 的格式化功能或结合 `Intl` API。

---

## 相关资源

- [react-i18next 文档](https://react.i18next.com/)
- [i18next 文档](https://www.i18next.com/)
