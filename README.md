# XKSkills

个人收藏的 Agent Skills 集合——可重用的提示模板，用于指导 AI 代理执行特定任务。Skills 以 Markdown 文件形式存储，包含 YAML 头部信息。

## 项目结构

```
XKSkills/
├── skills/                    # Skill 定义文件
│   ├── <skill-name>/
│   │   ├── SKILL.md          # Skill 主定义
│   │   ├── scripts/          # 辅助脚本 (Python, JS)
│   │   ├── examples/         # 使用示例
│   │   ├── reference/        # 文档参考
│   │   └── themes/           # 主题文件
├── AGENTS.md                  # Agent 操作指南
├── README.md                  # 本文件
└── LICENSE.txt                # MIT 许可证
```

## Skill 文件格式

每个 Skill 是包含 YAML 头部信息的 Markdown 文件。必需字段：

| 字段 | 描述 |
|-------|-------------|
| `name` | 唯一标识符 (kebab-case) |
| `description` | 一句话摘要，用于选择 Skill |
| `tags` | 可搜索标签数组 |
| `version` | 语义化版本字符串 |
| `author` | 作者名称 |

## 已安装的 Skills

| Skill | 描述 |
|-------|-------------|
| `algorithmic-art` | 使用 p5.js 创建算法艺术，支持随机种子和交互式参数探索 |
| `brand-guidelines` | 将 Anthropic 官方品牌配色和排版应用于各种制品 |
| `canvas-design` | 使用设计理念创建 .png 和 .pdf 格式的视觉艺术 |
| `doc-coauthoring` | 引导用户完成文档协作的Structured工作流 |
| `docx` | 创建、读取、编辑 Word 文档 (.docx) |
| `frontend-design` | 创建独特、生产级前端界面 |
| `internal-comms` | 撰写内部通讯（状态报告、Newsletter、更新等） |
| `mcp-builder` | 创建高质量的 MCP (Model Context Protocol) 服务器 |
| `pdf` | 读取、创建、编辑、合并、拆分、水印处理 PDF 文件 |
| `pptx` | 创建、读取、编辑 PowerPoint 演示文稿 (.pptx) |
| `skill-creator` | 创建新 Skill、修改现有 Skill、测量性能 |
| `slack-gif-creator` | 创建适用于 Slack 的动画 GIF |
| `theme-factory` | 为幻灯片、文档和制品应用专业主题 |
| `web-app-testing` | 使用 Playwright 测试本地 Web 应用 |
| `web-artifacts-builder` | 使用 React、Tailwind、shadcn/ui 构建复杂的 HTML 制品 |
| `xlsx` | 创建、读取、编辑电子表格 (.xlsx, .csv, .tsv) |

## 开发指南

详细开发规范请参阅 [AGENTS.md](AGENTS.md)。

## 许可证

MIT 许可证 — 见 [LICENSE.txt](LICENSE.txt)
