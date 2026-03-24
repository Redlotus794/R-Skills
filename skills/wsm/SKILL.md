---
name: wsm
description: 当用户需要创建、整理、校验或说明统一的项目工作空间目录时使用；用于在项目根目录下建立标准 project 结构，并约束代码、文档、知识和任务等内容的归档位置。
---

# 目标
为项目建立一套统一、清晰、可扩展的 `project/` 工作空间目录规范，并在用户需要时完成初始化、补齐、校验或结构说明。

边界：
- 只负责工作空间目录结构与归档规则，不负责生成业务代码或撰写长篇正式内容。
- 默认创建最小可用骨架，不擅自添加未定义的业务子目录。

# 输入
最小输入：
- 项目根目录路径，或明确说明以当前目录作为项目根目录
- 操作目标：`init`、`repair`、`audit`、`explain`

可选输入：
- 是否创建根目录 `project/`
- 是否初始化 `README.md`
- 是否初始化 `Agents.md`
- 是否补充各子目录中的占位文件
- 用户已有目录结构或命名约束

缺失输入处理规则：
- 未提供项目根目录时，默认使用当前工作目录。
- 未说明操作目标时，默认按 `init` 处理。
- 未说明是否写入内容时，仅创建目录；`README.md` 只写最小说明。

# 输出
- 一个可验证的结果清单，至少包含：
  - 实际创建或检查的路径
  - 已存在并复用的路径
  - 未处理项及原因（若有）
- 当操作目标为 `explain` 时，输出目录结构说明和各目录用途。

质量标准：
- 目录命名必须与规范完全一致。
- 所有项目开发内容统一归档到 `codebase/`。
- 输出结果能映射到具体路径，避免笼统描述。

# 执行步骤
1. 识别用户目标是初始化、补齐、校验还是解释目录规范。
2. 以项目根目录为基准，定位或创建 `project/`。
3. 按以下标准结构执行：

```text
project/
├── README.md
├── Agents.md
├── archives/
├── inbox/
├── codebase/
├── knowledge-base/
├── runbook/
├── documents/
├── references/
├── tasks/
└── assets/
```

4. 处理目录规则：
   - `README.md`：项目总说明，简述工作空间用途与目录约定。
   - `Agents.md`：AI 助手工作说明、约束、协作约定。
   - `archives/`：归档文件，存放历史资料、旧版本和已归档内容。
   - `inbox/`：临时笔记、随手记、待整理材料的缓冲区。
   - `codebase/`：所有代码、脚本、开发内容统一存放。
   - `knowledge-base/`：业务知识、规范、架构、决策记录。
   - `runbook/`：操作手册、排障记录、SOP、故障记录。
   - `documents/`：需求、方案、报告、会议纪要等正式文档。
   - `references/`：参考资料、模板、截图、样例数据。
   - `tasks/`：任务管理、看板、待办、进度记录。
   - `assets/`：图表、流程图、PPT 素材、附件。
5. 若为 `repair` 或 `audit`，逐项检查缺失、误放和命名偏差，并给出最小修复建议。
6. 自检输出，确保路径、用途说明和处理结果一致。

# 约束与注意事项
- 所有开发实现类内容默认进入 `codebase/`，不要散落到其他目录。
- 临时材料先进入 `inbox/`，整理完成后再迁移到正式目录。
- 历史资料与失效内容优先归档到 `archives/`，不要长期混放在工作目录。
- 不要将正式文档、知识沉淀、操作手册和任务记录混放。
- 除非用户明确要求，不创建二级业务子目录。
- 若现有项目结构与本规范冲突，优先保留用户已有内容，并在结果中标注差异。
- 根目录固定使用 `project`。
- 文档文件名默认使用 `README.md` 与 `Agents.md`。
- 目录命名固定使用以下名称：`archives`、`inbox`、`codebase`、`knowledge-base`、`runbook`、`documents`、`references`、`tasks`、`assets`。

# 失败与降级
- 输入不足：默认以当前目录执行 `init`，并在结果中说明假设。
- 路径已存在且内容不为空：跳过覆盖，仅报告现状与建议。
- 无法创建目录或文件时，明确返回：
  - `status: failed`
  - `reason: <具体原因>`
  - `next_action: <建议的最小下一步>`

# 快速检查清单
- [ ] frontmatter 仅包含 `name` 和 `description`
- [ ] `project/` 标准结构完整
- [ ] `codebase/` 被明确指定为开发内容唯一归档目录
- [ ] `inbox/` 与 `archives/` 职责明确
- [ ] 输出包含已处理、已存在、未处理项
- [ ] 未擅自扩展额外目录层级

# 示例
## 示例 1：标准场景
输入：
- 项目根目录：`/project/demo`
- 操作目标：`init`

输出：
- 已创建：
  - `project/`
  - `project/archives/`
  - `project/inbox/`
  - `project/codebase/`
  - `project/knowledge-base/`
  - `project/runbook/`
  - `project/documents/`
  - `project/references/`
  - `project/tasks/`
  - `project/assets/`
  - `project/README.md`
  - `project/Agents.md`
- 未处理项：无

## 示例 2：异常场景
输入：
- 项目根目录：`/project/demo`
- 操作目标：`audit`
- 现状：已有 `project/docs/`，缺少 `project/documents/`

输出：
- 检查结果：
  - 缺少 `project/documents/`
  - 存在非标准命名 `project/docs/`
- 建议：
  - 新建 `project/documents/`
  - 将正式文档逐步从 `docs/` 迁移到 `documents/`
  - 保留原目录，避免直接覆盖
