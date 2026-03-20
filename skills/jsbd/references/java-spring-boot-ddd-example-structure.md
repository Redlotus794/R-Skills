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
|-- docs/
|   `-- README.md
`-- src/
    |-- main/
    |   |-- java/
    |   `-- resources/
    `-- test/
        |-- java/
        `-- resources/
```

## 项目完整目录模版

以下目录基于 `2026-03-20` 拉取的 `main` 分支实际结构整理，已排除 `.git/` 等版本控制内部目录。

```text
<project-root>/
|-- .gitignore                         # Git 忽略规则
|-- AGENTS.md                          # 仓库代理/协作说明
|-- CODE_OF_CONDUCT.md                 # 社区行为准则
|-- CONTRIBUTING.md                    # 贡献规范
|-- FAQ.md                             # 常见问题
|-- LICENSE                            # 开源许可证
|-- README.md                          # 项目总说明
|-- pom.xml                            # Maven 构建配置
|-- docs/                              # 项目文档根目录
|   |-- README.md                      # 文档总入口
|   |-- ai/                            # AI 相关说明
|   |   |-- ai.md                      # AI 文档首页
|   |   `-- prompt/                    # Prompt 参考
|   |       `-- [ai] prompt.md         # Prompt 模版
|   |-- archive/                       # 归档文档
|   |   `-- archive.md                 # 归档说明
|   |-- dev/                           # 开发文档
|   |   |-- development.md             # 开发文档入口
|   |   |-- architecture/              # 架构设计
|   |   |   `-- [dev] architecture.md  # 架构说明
|   |   |-- convention/                # 研发约定
|   |   |   `-- [dev] convention.md    # 规范说明
|   |   `-- openapi/                   # OpenAPI 文档
|   |       |-- [dev] openapi.md       # OpenAPI 说明
|   |       |-- examples/              # OpenAPI 示例
|   |       |   `-- [dev-openapi] examples.md
|   |       |-- html/                  # OpenAPI HTML 产物说明
|   |       |   `-- [dev-openapi] html.md
|   |       `-- json/                  # OpenAPI JSON 产物说明
|   |           `-- [dev-openapi] json.md
|   |-- ops/                           # 运维文档
|   |   |-- ops.md                     # 运维文档入口
|   |   |-- automation/                # 自动化运维
|   |   |   `-- README.md
|   |   |-- backup-restore/            # 备份与恢复
|   |   |   `-- README.md
|   |   |-- changelog/                 # 变更记录
|   |   |   |-- README.md
|   |   |   `-- release-note/          # 发布说明
|   |   |       |-- 1.0.0.RELEASE.md
|   |   |       `-- [changelog] release-note.md
|   |   |-- configuration/             # 配置管理
|   |   |   `-- README.md
|   |   |-- deployment/                # 部署文档
|   |   |   |-- README.md
|   |   |   |-- docker/                # Docker 部署
|   |   |   |   `-- docker.md
|   |   |   `-- k8s/                   # Kubernetes 部署
|   |   |       `-- README.md
|   |   |-- incident-troubleshooting/  # 事故与排障
|   |   |   `-- README.md
|   |   |-- log/                       # 日志管理
|   |   |   `-- README.md
|   |   |-- monitor/                   # 监控
|   |   |   `-- README.md
|   |   |-- network/                   # 网络相关
|   |   |   `-- README.md
|   |   |-- performance/               # 性能优化
|   |   |   `-- README.md
|   |   |-- resource-cost/             # 资源成本
|   |   |   `-- README.md
|   |   |-- runbook/                   # 运维手册
|   |   |   `-- README.md
|   |   |-- security/                  # 安全文档
|   |   |   `-- README.md
|   |   `-- storage-data/              # 存储与数据
|   |       `-- README.md
|   |-- project-managament/            # 项目管理文档
|   |   |-- project-management.md      # 项目管理入口
|   |   |-- meeting-notes/             # 会议纪要
|   |   |   `-- [pm] meeting-notes.md
|   |   |-- plans/                     # 计划文档
|   |   |   `-- [pm] plans.md
|   |   |-- process/                   # 流程文档
|   |   |   `-- [pm] process.md
|   |   |-- risk-management/           # 风险管理
|   |   |   |-- [pm] risk-management.md
|   |   |   `-- reference.md
|   |   |-- roadmap/                   # 路线图
|   |   |   `-- [pm] project-roadmap.md
|   |   `-- todo/                      # 待办事项
|   |       `-- [pm] todo.md
|   |-- requirements/                  # 需求文档
|   |   |-- requirements.md            # 需求文档入口
|   |   |-- backlog/                   # 需求池
|   |   |   `-- backlog.md
|   |   |-- product/                   # 产品需求
|   |   |   |-- [req] product.md
|   |   |   |-- prd/                   # PRD
|   |   |   |   `-- [req-product] prd.md
|   |   |   `-- ul/                    # 用户清单/用户旅程
|   |   |       `-- [req-product] ul.md
|   |   |-- prototypes/                # 原型文档
|   |   |   `-- [req] prototypes.md
|   |   `-- technical/                 # 技术需求
|   |       `-- [req] technical.md
|   |-- template/                      # 模版资源
|   |   `-- config/                    # 配置模版
|   |       |-- log4j.properties
|   |       |-- log4j2.xml
|   |       |-- logback-spring.xml
|   |       `-- logging.properties
|   `-- test/                          # 测试文档
|       |-- test.md                    # 测试文档入口
|       |-- case/                      # 测试用例
|       |   |-- [test] case.md
|       |   |-- bdd_case_template.md
|       |   `-- case_template.md
|       |-- plan/                      # 测试计划
|       |   `-- [test] plan.md
|       `-- report/                    # 测试报告
|           `-- [test] report.md
`-- src/                               # 源码根目录
    |-- main/
    |   `-- java/
    |       `-- com/
    |           `-- rdlts/
    |               `-- jsbs/
    |                   `-- ddd/
    |                       |-- Application.java              # Spring Boot 启动类
    |                       |-- package-info.java            # 顶层包说明
    |                       |-- applicationservice/          # 应用服务层
    |                       |   `-- package-info.java
    |                       |-- domain/                      # 领域层
    |                       |   |-- package-info.java
    |                       |   |-- aggregate/               # 聚合
    |                       |   |   `-- DomainAggregate.java
    |                       |   |-- entity/                  # 实体
    |                       |   |   `-- DomainEntity.java
    |                       |   `-- valueobject/             # 值对象
    |                       |       `-- ValueObject.java
    |                       |-- infrastructure/              # 基础设施层
    |                       |   |-- package-info.java
    |                       |   `-- repository/              # 仓储相关
    |                       |       |-- repository.md
    |                       |       |-- jpa/                 # JPA 仓储
    |                       |       |   `-- jpa.md
    |                       |       `-- po/                  # 持久化对象
    |                       |           `-- po.md
    |                       `-- userinterface/               # 用户接口层
    |                           `-- package-info.java
    `-- test/
        |-- java/
        |   `-- com/
        |       `-- rdlts/
        |           `-- jsbs/
        |               `-- ddd/
        |                   |-- TestApplication.java         # 测试入口类
        |                   |-- convention.md                # 测试约定
        |                   `-- package-info.java
        `-- resources/
            |-- application-test.yml        # 测试配置
            |-- dcs-logback-spring.xml      # 测试日志配置
            |-- resources.md                # 测试资源说明
            |-- data/                       # 测试数据
            |   `-- data.md
            |-- documents/                  # 测试文档
            |   `-- documents.md
            `-- images/                     # 测试图片
                `-- images.md
```


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

帮我创建运维部署目录

```text
已创建目录：
- docs/
- docs/development/

已创建文件：
- docs/development/README.md

未创建项：
- docs/development/docker/ （原因：用户未指明要求创建docker部署目录）
- src/main/java/com/example/order/applicationservice/（原因：用户未要求）
```

## 使用边界

- 本文件用于 `jsbd` 执行前的结构对照。
- 本文件不要求执行者完整复制 `java-spring-boot-ddd-example`。
- 若用户明确要求“完整结构”，也应先以当前模版为基线，再补充用户点名部分，而不是默认全量展开。
