# AGENTS.md - XKSkills

本文档为在 XKSkills 仓库中运行的智能编码代理提供操作指南。

## 项目概述

XKSkills 是一个个人收藏的 Agent Skills 集合——可重用的提示模板，用于指导 AI 代理执行特定任务。Skills 以 Markdown 文件形式存储，包含 YAML 头部信息。部分 Skills 包含辅助脚本（Python/JavaScript）用于自动化。

## 项目结构

```
XKSkills/
├── skills/                    # Skill 定义文件
│   ├── <skill-name>/
│   │   ├── SKILL.md          # Skill 主定义
│   │   ├── scripts/          # 辅助脚本 (Python, JS)
│   │   ├── examples/         # 使用示例
│   │   ├── reference/        # 文档参考
│   │   └── themes/           # 主题文件 (设计类 Skills)
├── AGENTS.md                  # 本文件
├── README.md                  # 项目文档
└── LICENSE.txt                # MIT 许可证
```

## 构建 / 测试命令

这是一个文档/仓库项目。各个 Skills 可能包含自己的测试脚本。

### Skill 脚本 (Python)

- **语法检查**: `python -m py_compile <file.py>`
- **运行脚本**: `python skills/<skill>/scripts/<script>.py <args>`
- **安装依赖**: 检查 `skills/<skill>/requirements.txt` 是否存在

### Skill 脚本 (TypeScript/Node.js)

- **构建**: `npm run build` (在包含 package.json 的 skill 目录下)
- **类型检查**: `npx tsc --noEmit`
- **运行**: `node dist/<file>.js` 或 `npx ts-node src/<file>.ts`

### MCP 服务器测试

- **MCP Inspector**: `npx @modelcontextprotocol/inspector`

### 代码检查

- **Python**: 使用 `ruff check .` 或 `flake8` (如果配置了)
- **TypeScript**: 使用 `npm run lint` 或 `npx eslint .` (如果配置了)

## Skill 文件格式

每个 Skill 是包含 YAML 头部信息的 Markdown 文件。请遵循以下格式：

```yaml
---
name: skill-name
description: 简要描述该 Skill 的功能 (1-2 句话)
tags:
  - tag1
  - tag2
version: "1.0.0"
author: XKSkills
---

# Skill 内容 (Markdown 格式)
```

### 必需的头部字段

| 字段 | 描述 | 示例 |
|-------|-------------|---------|
| `name` | 唯一标识符 (kebab-case) | `frontend-design` |
| `description` | 一句话摘要，用于选择 Skill | `Create distinctive...` |
| `tags` | 可搜索标签数组 | `- frontend`, `- ui` |
| `version` | 语义化版本字符串 | `"1.0.0"` |
| `author` | 作者名称 | `XKSkills` |

## 代码风格指南

### YAML 头部

- 使用 2 空格缩进 (不要使用 Tab)
- 版本字符串需要加引号: `"1.0.0"` 而不是 `1.0.0`
- 名称使用 kebab-case: `skill-name` 而不是 `skillName`
- 标签数组使用连字符前缀，2 空格缩进

### Markdown 内容

- 使用 ATX 风格标题 (`#`, `##`, `###`)
- 最大行长度: 100 字符
- 使用带语言标识的代码块

### Python 脚本 (Skills 内)

**导入顺序**: 标准库、第三方库、本地模块。

**类型提示**: 为所有函数参数使用类型提示。优先使用现代联合语法 (`X | None`)。

**命名**: 函数/变量用 `snake_case`，类用 `PascalCase`，常量用 `SCREAMING_SNAKE_CASE`。

**格式**: 4 空格缩进，最大行长度 100，使用尾随逗号。

**错误处理**: 对于可能失败的操作，返回元组 `(result, error_message)`。

### JavaScript/TypeScript 脚本

**命名**: 变量/函数用 `camelCase`，类用 `PascalCase`。

**类型**: 尽可能使用 TypeScript 而不是纯 JavaScript。

**格式**: 2 空格缩进，如配置了 ESLint/Prettier 则使用。

## 命名约定

- **Skill 文件名**: `kebab-case.md` (例如 `frontend-design.md`)
- **Skill 名称**: kebab-case
- **标签**: 小写，多个单词用 kebab-case

## 一般指南

1. **保持简洁** - Skills 应聚焦且可操作
2. **避免代理特定引用** - 使用"the agent"而不是"Claude"、"ChatGPT"等
3. **包含示例** - 演示而不是仅说明
4. **版本更新** - 更新 Skills 时递增版本 (遵循 semver)
5. **使用英文** - Skill 内容应使用英文以确保广泛兼容性

## Git 工作流

1. 每次添加/修改 Skill 创建新分支
2. 使用描述性的提交信息:
   - `Add new skill: <skill-name>`
   - `Update skill: <skill-name> to v1.1.0`
   - `Fix: <skill-name> - description of fix`
3. 合并到 main 前创建 Pull Request
4. 永不提交敏感信息

## 添加新 Skill

1. 创建目录: `skills/<skill-name>/`
2. 创建包含必需头部和内容的 `SKILL.md`
3. 如需要，在 `scripts/` 添加辅助脚本
4. 如需要 Python 依赖，添加 `requirements.txt`
5. 更新根目录 `README.md` 列出新 Skill
6. 按 Git 工作流提交并推送

## 错误处理

- **YAML 语法错误**: 使用 YAML 验证器检查头部
- **链接失效**: 验证所有内部链接有效
- **字段缺失**: 确保所有必需的头部字段存在
