# Context Engineering 模板

一个全面的模板，用于开始使用 Context Engineering（上下文工程）- 为 AI 编程助手设计上下文的学科，使它们拥有完成端到端工作所需的信息。

> **Context Engineering 比 prompt engineering 好 10 倍，比 vibe coding 好 100 倍。**

## 🚀 快速开始

```bash
# 1. 克隆此模板
git clone https://github.com/coleam00/Context-Engineering-Intro.git
cd Context-Engineering-Intro

# 2. 设置项目规则（可选 - 提供模板）
# 编辑 CLAUDE.md 添加项目特定指南

# 3. 添加示例（强烈推荐）
# 在 examples/ 文件夹中放置相关代码示例

# 4. 创建初始功能请求
# 编辑 INITIAL.md 包含功能需求

# 5. 生成全面的 PRP（产品需求提示）
# 在 Claude Code 中运行：
/generate-prp INITIAL.md

# 6. 执行 PRP 实现功能
# 在 Claude Code 中运行：
/execute-prp PRPs/your-feature-name.md
```

## 📚 目录

- [什么是 Context Engineering？](#什么是-context-engineering)
- [模板结构](#模板结构)
- [分步指南](#分步指南)
- [编写有效的 INITIAL.md 文件](#编写有效的-initialmd-文件)
- [PRP 工作流程](#prp-工作流程)
- [有效使用示例](#有效使用示例)
- [最佳实践](#最佳实践)

## 什么是 Context Engineering？

Context Engineering 代表了从传统 prompt engineering 的范式转变：

### Prompt Engineering vs Context Engineering

**Prompt Engineering：**
- 专注于巧妙的措辞和特定短语
- 仅限于如何表述任务
- 就像给别人一张便利贴

**Context Engineering：**
- 提供全面上下文的完整系统
- 包括文档、示例、规则、模式和验证
- 就像写一个包含所有细节的完整剧本

### 为什么 Context Engineering 重要

1. **减少 AI 失败**：大多数代理失败不是模型失败 - 而是上下文失败
2. **确保一致性**：AI 遵循您的项目模式和约定
3. **实现复杂功能**：AI 可以通过适当的上下文处理多步实现
4. **自我纠正**：验证循环允许 AI 修复自己的错误

## 模板结构

```
context-engineering-intro/
├── .claude/
│   ├── commands/
│   │   ├── generate-prp.md    # 生成全面的 PRP
│   │   └── execute-prp.md     # 执行 PRP 实现功能
│   └── settings.local.json    # Claude Code 权限
├── PRPs/
│   ├── templates/
│   │   └── prp_base.md       # PRP 基础模板
│   └── EXAMPLE_multi_agent_prp.md  # 完整 PRP 示例
├── examples/                  # 您的代码示例（关键！）
├── CLAUDE.md                 # AI 助手的全局规则
├── INITIAL.md               # 功能请求模板
├── INITIAL_EXAMPLE.md       # 功能请求示例
└── README.md                # 本文件
```

此模板不专注于 RAG 和工具的上下文工程，因为我很快会有更多相关内容。;)

## 分步指南

### 1. 设置全局规则（CLAUDE.md）

`CLAUDE.md` 文件包含 AI 助手在每次对话中都会遵循的项目范围规则。模板包括：

- **项目意识**：阅读规划文档，检查任务
- **代码结构**：文件大小限制，模块组织
- **测试要求**：单元测试模式，覆盖率期望
- **风格约定**：语言偏好，格式化规则
- **文档标准**：文档字符串格式，注释实践

**您可以使用提供的模板，也可以为您的项目自定义。**

### 2. 创建初始功能请求

编辑 `INITIAL.md` 描述您想要构建的内容：

```markdown
## 功能：
[描述您想要构建的内容 - 具体说明功能和需求]

## 示例：
[列出 examples/ 文件夹中的任何示例文件，并解释如何使用]

## 文档：
[包含相关文档、API 或 MCP 服务器资源的链接]

## 其他考虑：
[提及任何陷阱、特定要求或 AI 助手经常遗漏的内容]
```

**查看 `INITIAL_EXAMPLE.md` 获取完整示例。**

### 3. 生成 PRP

PRP（产品需求提示）是全面的实现蓝图，包括：

- 完整的上下文和文档
- 带验证的实现步骤
- 错误处理模式
- 测试要求

它们类似于 PRD（产品需求文档），但更具体地设计用于指导 AI 编程助手。

在 Claude Code 中运行：
```bash
/generate-prp INITIAL.md
```

**注意：** 斜杠命令是在 `.claude/commands/` 中定义的自定义命令。您可以查看它们的实现：
- `.claude/commands/generate-prp.md` - 查看它如何研究和创建 PRP
- `.claude/commands/execute-prp.md` - 查看它如何从 PRP 实现功能

这些命令中的 `$ARGUMENTS` 变量接收您在命令名称后传递的任何内容（例如，`INITIAL.md` 或 `PRPs/your-feature.md`）。

此命令将：
1. 读取您的功能请求
2. 研究代码库的模式
3. 搜索相关文档
4. 在 `PRPs/your-feature-name.md` 中创建全面的 PRP

### 4. 执行 PRP

生成后，执行 PRP 实现您的功能：

```bash
/execute-prp PRPs/your-feature-name.md
```

AI 编程助手将：
1. 从 PRP 读取所有上下文
2. 创建详细的实现计划
3. 执行每个步骤并进行验证
4. 运行测试并修复任何问题
5. 确保满足所有成功标准

## 编写有效的 INITIAL.md 文件

### 关键部分说明

**功能**：具体且全面
- ❌ "构建网络爬虫"
- ✅ "使用 BeautifulSoup 构建异步网络爬虫，从电商网站提取产品数据，处理速率限制，并将结果存储在 PostgreSQL 中"

**示例**：利用 examples/ 文件夹
- 在 `examples/` 中放置相关代码模式
- 引用要遵循的特定文件和模式
- 解释应该模仿哪些方面

**文档**：包含所有相关资源
- API 文档 URL
- 库指南
- MCP 服务器文档
- 数据库模式

**其他考虑**：捕获重要细节
- 认证要求
- 速率限制或配额
- 常见陷阱
- 性能要求

## PRP 工作流程

### /generate-prp 如何工作

命令遵循以下过程：

1. **研究阶段**
   - 分析您的代码库模式
   - 搜索类似实现
   - 识别要遵循的约定

2. **文档收集**
   - 获取相关 API 文档
   - 包含库文档
   - 添加陷阱和怪癖

3. **蓝图创建**
   - 创建逐步实现计划
   - 包含验证门
   - 添加测试要求

4. **质量检查**
   - 评分置信度（1-10）
   - 确保包含所有上下文

### /execute-prp 如何工作

1. **加载上下文**：读取整个 PRP
2. **计划**：使用 TodoWrite 创建详细任务列表
3. **执行**：实现每个组件
4. **验证**：运行测试和代码检查
5. **迭代**：修复发现的任何问题
6. **完成**：确保满足所有要求

查看 `PRPs/EXAMPLE_multi_agent_prp.md` 获取生成内容的完整示例。

## 有效使用示例

`examples/` 文件夹对成功**至关重要**。当 AI 编程助手可以看到要遵循的模式时，表现会更好。

### 在示例中包含什么

1. **代码结构模式**
   - 如何组织模块
   - 导入约定
   - 类/函数模式

2. **测试模式**
   - 测试文件结构
   - 模拟方法
   - 断言风格

3. **集成模式**
   - API 客户端实现
   - 数据库连接
   - 认证流程

4. **CLI 模式**
   - 参数解析
   - 输出格式化
   - 错误处理

### 示例结构

```
examples/
├── README.md           # 解释每个示例演示的内容
├── cli.py             # CLI 实现模式
├── agent/             # 代理架构模式
│   ├── agent.py      # 代理创建模式
│   ├── tools.py      # 工具实现模式
│   └── providers.py  # 多提供者模式
└── tests/            # 测试模式
    ├── test_agent.py # 单元测试模式
    └── conftest.py   # Pytest 配置
```

## 最佳实践

### 1. 在 INITIAL.md 中明确
- 不要假设 AI 知道您的偏好
- 包含特定要求和约束
- 大量引用示例

### 2. 提供全面的示例
- 更多示例 = 更好的实现
- 展示做什么 AND 不做什么
- 包含错误处理模式

### 3. 使用验证门
- PRP 包含必须通过的测试命令
- AI 将迭代直到所有验证成功
- 这确保第一次尝试就能获得工作代码

### 4. 利用文档
- 包含官方 API 文档
- 添加 MCP 服务器资源
- 引用特定文档部分

### 5. 自定义 CLAUDE.md
- 添加您的约定
- 包含项目特定规则
- 定义编码标准

## 资源

- [Claude Code 文档](https://docs.anthropic.com/en/docs/claude-code)
- [Context Engineering 最佳实践](https://www.philschmid.de/context-engineering)