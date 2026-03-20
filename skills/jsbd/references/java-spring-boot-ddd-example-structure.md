# java-spring-boot-ddd-example 参考模版

- 技能：`jsbd`
- 对应文件：`skills/jsbd/SKILL.md`
- 参考来源：`https://github.com/Redlotus794/java-spring-boot-ddd-example`
- 当前仓库适配时间：`2026-03-20`
- 用途：为 `jsbd` 提供“最小化创建”时的目录映射参考，不作为完整脚手架清单。

## 说明
- 本文件已按当前仓库中的 `jsbd` 规则收敛，不再保留外部仓库的完整目录快照。
- 目标是帮助执行者从用户需求中提取“必要父目录 + 指定目标目录/文件”，而不是一次性生成完整工程。
- 当用户需求与本模版冲突时，以用户明确要求为准。

## 最小目录模版

```text
<project-root>/
|-- docs/                              # 按需创建
|   |-- development/
|   |   `-- openapi/
|   |-- requirements/
|   `-- ops/
`-- src/                               # 按需创建
    |-- main/
    |   |-- java/
    |   `-- resources/
    `-- test/
        |-- java/
        `-- resources/
```

## Java 包路径模版

当用户提供包根路径（例如 `com.example.order`）时，可在 `src/main/java/` 与 `src/test/java/` 下继续展开：

```text
src/main/java/com/example/order/
|-- applicationservice/
|-- domain/
|   |-- aggregate/
|   |-- entity/
|   `-- valueobject/
|-- infrastructure/
`-- userinterface/
```

说明：
- `applicationservice`、`domain`、`infrastructure`、`userinterface` 仅在用户明确要求时创建。
- `aggregate`、`entity`、`valueobject` 仅在用户明确要求细分 `domain/` 时创建。
- 未提供包根路径时，不自动补包层级；最多创建到 `src/main/java/` 或用户指定的直接子目录。

## docs 侧最小映射

适用场景：
- 用户要补项目文档目录
- 用户只要 OpenAPI、需求、运维等文档骨架

建议按需映射：

```text
docs/
|-- development/
|   `-- openapi/
|-- requirements/
`-- ops/
```

规则：
- 如果用户只提到 `docs/development/openapi/`，只创建该路径及必要父目录。
- 如果用户只要求单个文档文件，例如 `docs/requirements/prd.md`，只创建必要目录并写入最小标题。
- 不自动补齐 `docs/ai/`、`docs/archive/`、`docs/test/` 等目录，除非用户明确提出。

## engineering 侧最小映射

适用场景：
- 用户要初始化 Spring Boot 工程目录
- 用户要补齐 DDD 分层包目录

建议按需映射：

```text
src/
|-- main/
|   |-- java/
|   `-- resources/
`-- test/
    |-- java/
    `-- resources/
```

规则：
- 用户只要求工程基础结构时，只创建 `src/main/java`、`src/main/resources`、`src/test/java`、`src/test/resources`。
- 用户明确要求 DDD 分层时，再在包路径下创建对应目录。
- 不生成业务代码、配置文件、实体类、仓储实现或测试代码。

## mixed 场景模版

当用户同时要求 `docs` 与 `engineering` 时，按以下方式处理：

1. 先拆分为文档需求与工程需求。
2. 分别生成最小创建清单。
3. 合并去重，只保留必要父目录。
4. 先创建目录，再创建文件。

示例：

```text
<project-root>/
|-- docs/
|   `-- development/
|       `-- openapi/
`-- src/
    `-- main/
        `-- java/
            `-- com/
                `-- example/
                    `-- order/
                        |-- domain/
                        `-- infrastructure/
```

## 文档文件最小写入模版

当用户要求创建文档文件但未指定正文时，仅写 1 行标题：

```md
# <文件主题>
```

示例：
- `docs/requirements/prd.md` -> `# PRD`
- `docs/development/openapi/overview.md` -> `# Overview`

## 执行时检查点

- 只创建用户点名项及必要父目录。
- 不镜像外部参考仓库的完整树。
- 不补齐未要求的 DDD 子目录。
- 不生成业务实现代码。
- 输出结果必须区分：
  - 已创建目录
  - 已创建文件
  - 未创建项及原因

## 输出示例

```text
已创建目录：
- docs/
- docs/development/
- docs/development/openapi/
- src/main/java/com/example/order/domain/

已创建文件：
- docs/development/openapi/overview.md

未创建项：
- src/main/java/com/example/order/applicationservice/（原因：用户未要求）
```

## 使用边界

- 本文件用于 `jsbd` 执行前的结构对照。
- 本文件不要求执行者完整复制 `java-spring-boot-ddd-example`。
- 若用户明确要求“完整结构”，也应先以当前模版为基线，再补充用户点名部分，而不是默认全量展开。
