# AGENTS.md

## 目的
这个仓库用于管理我个人的通用 skills 集合，不绑定单一模型或平台。
支持的对象包括但不限于 Claude、Codex，以及未来可能接入的 Google、阿里等模型或代理系统。

## 范围
- 存储、版本化并维护可复用的 skill 定义。
- 保持 skill 指令清晰、简短、可执行。
- 优先保证所有 skills 的一致性。
- 以通用 skill 为主，在必要时提供模型专用扩展。

## Skill 目录结构
每个 skill 应遵循以下结构：

```text
skills/
  <skill-name>/
    SKILL.md                 # 通用版本（默认）
    assets/        # 可选
    scripts/       # 可选
    references/    # 可选
    models/                   # 可选，模型专用扩展
      claude/
        SKILL.md
      codex/
        SKILL.md
      google/
        SKILL.md
      ali/
        SKILL.md
```

目录约定：
- 默认优先维护根目录下的通用 `SKILL.md`。
- 仅当某模型存在明显差异（工具调用、提示格式、限制条件等）时，再在 `models/<provider>/SKILL.md` 中定义专用内容。
- 模型专用文件应仅覆盖差异部分，避免复制整份通用内容。

## 编写规则
- 每个 skill 使用独立目录，并采用清晰的 kebab-case 命名。
- 必须包含 `SKILL.md`，且应包括：
  - skill 的用途
  - 适用场景
  - 分步骤工作流程
  - 约束与注意事项
- 指令应具体且可直接执行。
- 优先更新已有 skills，避免重复创建同类 skill。
- 新增模型专用版本前，先确认是否可通过通用规则覆盖。

## 模板规范
- 新建 skill 时，默认基于模板文件：
  - `skills/_template/SKILL.md`
- 创建流程建议：
  1. 复制模板到 `skills/<skill-name>/SKILL.md`
  2. 替换 frontmatter 占位符（`<skill-name>`、`description`）
  3. 填写“目标/输入/输出/执行步骤/约束/失败与降级/示例”
  4. 仅在存在明显模型差异时新增 `models/<provider>/SKILL.md`

## 维护原则
- 保持 skills 小而可组合。
- 及时删除过时指令。
- 使用清晰的提交信息记录有意义的变更。
- 当通用与模型专用规则冲突时，优先修正结构，确保职责边界清晰。
