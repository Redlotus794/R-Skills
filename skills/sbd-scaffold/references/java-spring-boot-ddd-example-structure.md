# java-spring-boot-ddd-example 目录结构参考

- 技能：`sbd-scaffold`
- 参考仓库：`https://github.com/Redlotus794/java-spring-boot-ddd-example`
- 读取时间：`2026-03-06`
- 读取方式：GitHub Trees API (`main` 分支，`recursive=1`)，提取 `type=tree` 的目录路径

## 目录清单（树形结构）

```text
java-spring-boot-ddd-example/
|-- docs/
|   |-- ai/
|   |   `-- prompt/
|   |-- archive/
|   |-- development/
|   |   |-- architecture/
|   |   |-- convention/
|   |   `-- openapi/
|   |       |-- examples/
|   |       |-- html/
|   |       `-- json/
|   |-- ops/
|   |   |-- deployment/
|   |   |   |-- docker/
|   |   |   `-- release-note/
|   |   `-- scripts/
|   |       |-- backup/
|   |       |-- deployment/
|   |       |-- maintenance/
|   |       `-- monitor/
|   |-- project-managament/
|   |   |-- meeting-notes/
|   |   |-- plans/
|   |   |-- process/
|   |   |-- risk-management/
|   |   |-- roadmap/
|   |   `-- todo/
|   |-- requirements/
|   |   |-- backlog/
|   |   |-- product/
|   |   |   |-- prd/
|   |   |   `-- ul/
|   |   |-- prototypes/
|   |   `-- technical/
|   |-- template/
|   |   `-- config/
|   `-- test/
|       |-- case/
|       |-- plan/
|       `-- report/
`-- src/
    |-- main/
    |   `-- java/
    |       `-- com/
    |           `-- rdlts/
    |               `-- jsbs/
    |                   `-- ddd/
    |                       |-- applicationservice/
    |                       |-- domain/
    |                       |   |-- aggregate/
    |                       |   |-- entity/
    |                       |   `-- valueobject/
    |                       |-- infrastructure/
    |                       |   `-- repository/
    |                       |       |-- jpa/
    |                       |       `-- po/
    |                       `-- userinterface/
    `-- test/
        |-- java/
        |   `-- com/
        |       `-- rdlts/
        |           `-- jsbs/
        |               `-- ddd/
        `-- resources/
            |-- data/
            |-- documents/
            `-- images/
```

## 用法说明
- 本文件用于 `sbd-scaffold` 执行前的目录对照，不代表必须全量创建。
- 实际创建时遵循“最小化原则”：仅创建用户明确要求的目录/文件及必要父目录。
