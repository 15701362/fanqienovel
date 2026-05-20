# Fanqie Novel Skills

这是一个面向番茄小说生产流程的 Codex/OpenSpec Skills 仓库，用于把网文创作拆成可复用、可编排、可质检的专业能力模块。

目标不是做单次“AI 写小说”，而是沉淀一套面向长篇连载的小说工业化生产系统，覆盖选题、开篇、正文续写、爽点增强、节奏检查、记忆管理、留存优化和评论互动。

## 项目结构

```text
.
├── .agents/
│   └── rules/
│       └── global-language-openspec.md
├── skills/
│   ├── */SKILL.md
│   └── */agents/openai.yaml
├── .gitignore
└── README.md
```

说明：

- `.agents/rules/global-language-openspec.md`：全局语言与提交规范。
- `skills/*/SKILL.md`：每个 skill 的核心说明、输入输出、流程和规则。
- `skills/*/agents/openai.yaml`：每个 skill 的界面展示名称、简介和默认提示词。

## 全局约定

- 所有对话、说明、OpenSpec skill 文档默认使用简体中文。
- Git 提交信息必须使用简体中文。
- 代码标识符、文件路径、URL、专有名词原文可以保留。

## Skills 列表

### 策划与开篇

| Skill | 中文名 | 作用 |
| --- | --- | --- |
| `fanqie-hot-analyzer` | 番茄爆款分析师 | 分析题材、爽点、读者群、留存机制和爆款公式。 |
| `novel-topic-generator` | 爆款选题生成器 | 生成符合番茄流量逻辑的商业网文选题。 |
| `golden-three-chapters` | 黄金三章生成器 | 设计或撰写高点击、高留存的前三章。 |

### 正文生产

| Skill | 中文名 | 作用 |
| --- | --- | --- |
| `auto-novel-writer` | 自动续写器 | 根据上一章、当前目标和记忆库续写章节。 |
| `cool-point-enhancer` | 爽点增强器 | 增强打脸、反转、财富刺激和情绪释放。 |
| `fanqie-style-converter` | 番茄文风转换器 | 把普通文本改成短句、高对白、强冲突的番茄风。 |
| `chapter-hook-builder` | 断章钩子生成器 | 生成提升下一章点击率的章节结尾。 |
| `chapter-title-manager` | 章节标题管理器 | 生成高点击、不重复、有情绪的章节标题。 |
| `ai-flavor-cleaner` | AI味清洗器 | 清理套话、机械情绪、重复句式和口水文。 |

### 质检与留存

| Skill | 中文名 | 作用 |
| --- | --- | --- |
| `novel-rule-controller` | 小说规则控制器 | 总质检字数、节奏、爽点、钩子、AI味和标题。 |
| `pacing-inspector` | 节奏检查器 | 检查章节节奏、爽点密度和中后期崩盘风险。 |
| `plot-duplicate-checker` | 剧情重复检测器 | 检测套路、爽点、打脸和装逼循环重复。 |
| `emotion-curve-analyzer` | 情绪曲线分析器 | 分析情绪波动、爽感密度和高潮位置。 |
| `retention-optimizer` | 留存优化器 | 优化读完率、下一章点击率和追更率。 |
| `reader-addiction-controller` | 读者上瘾控制器 | 设计延迟满足、压抑释放和悬念循环。 |
| `comment-engagement-builder` | 评论互动诱导器 | 设计站队、争议点和评论互动触发。 |

### 记忆系统

| Skill | 中文名 | 作用 |
| --- | --- | --- |
| `novel-memory-manager` | 小说记忆库 | 维护角色、人设、伏笔、时间线和一致性。 |
| `hot-memory-manager` | 热库管理器 | 维护当前卷、目标、冲突、情绪和最近伏笔。 |
| `cold-memory-manager` | 冷库管理器 | 维护世界观、角色库、剧情摘要、伏笔和时间线。 |
| `story-memory-retriever` | 剧情记忆检索器 | 从冷库检索相关记忆并注入热库。 |

## 推荐工作流

### 第一阶段：策划

```text
爆款分析
→ 选题生成
→ 黄金三章
→ 章节标题方向
→ 长篇记忆结构初始化
```

### 第二阶段：正文生产

```text
读取热库
→ 从冷库检索相关记忆
→ 自动续写
→ 爽点增强
→ 番茄文风转换
→ AI味清洗
→ 断章钩子生成
→ 标题生成
```

### 第三阶段：质检优化

```text
小说规则总检
→ 情绪曲线分析
→ 节奏检查
→ 剧情重复检测
→ 留存优化
→ 读者上瘾机制增强
→ 评论互动设计
```

### 第四阶段：记忆维护

```text
更新热库
→ 归档冷库
→ 标记伏笔状态
→ 更新角色关系
→ 记录爽点历史
```

## 热库、冷库与检索器

本仓库把长篇记忆拆成三层：

- 热库：只保存当前最重要剧情状态，例如当前卷、当前目标、当前冲突、当前情绪、最近伏笔和最近 5 章摘要。
- 冷库：保存完整长期档案，例如世界观、角色库、剧情摘要库、伏笔库、势力库、时间线和爽点历史。
- 检索器：根据当前剧情目标，从冷库中提取强相关记忆，整理后注入热库或续写提示。

这样可以避免把全部历史内容塞进上下文，同时减少长篇续写的人设崩坏、伏笔遗忘和剧情重复。

## 校验

创建或修改 skill 后，可以使用 skill-creator 的校验脚本检查结构：

```powershell
$env:PYTHONUTF8='1'
$validator='C:\Users\PC\AppData\Local\JetBrains\IntelliJIdea2025.3\aia\codex\skills\.system\skill-creator\scripts\quick_validate.py'
Get-ChildItem skills -Directory | ForEach-Object { py $validator $_.FullName }
```

通过时会输出：

```text
Skill is valid!
```
