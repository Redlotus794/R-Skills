---
name: sbd-scaffold
description: "根据用户指定需求，在 Spring Boot Java 项目中按 DDD 基准结构最小化创建目录或文档。用于创建 docs/ 或 src 分层目录骨架、避免过度生成内容，并支持参考仓库 java-spring-boot-ddd-example。"
---

# 目标
在 Spring Boot Java 项目中，基于参考仓库 `https://github.com/Redlotus794/java-spring-boot-ddd-example` 的目录思想，按用户指定范围最小化创建目录或文档。

边界：
- 只做目录和文档骨架初始化，不生成业务实现代码。
- 只创建用户明确要求的部分，不擅自补齐完整工程。

# 输入
最小输入：
- 项目根目录路径
- 创建目标类型：`docs`、`engineering`、`mixed`
- 用户明确要求创建的目录/文件列表

可选输入：
- Java 包根路径（如 `com.example.demo`）
- DDD 分层偏好（如 `domain/applicationservice/infrastructure/userinterface`）
- 文档模板偏好（仅文件名或是否写入初始标题）

缺失输入处理规则：
- 未给包根路径时，不创建包层级目录，只创建到 `src/main/java`。
- 未给文件内容要求时，仅创建空目录；文档文件只写 1 行标题。
- 用户描述模糊时，先输出最小创建清单并请求确认，再执行创建。

# 输出
- 一个“最小创建结果”清单，包含：
  - 实际创建的目录
  - 实际创建的文件
  - 未创建项及原因（若有）
- 输出必须可验证：每一项都能映射到具体路径。

质量标准：
- 不创建未请求内容。
- 路径命名与用户输入一致。
- 与参考仓库结构理念一致（docs 与 src 分层清晰）。

# 执行步骤
1. 解析用户目标，拆分为 `docs` 与 `engineering` 两类需求。
2. 从参考仓库抽取最小结构映射：
  - 优先读取本地参考：`references/java-spring-boot-ddd-example-structure.md`
   - `docs/` 及其子目录（按需）
   - `src/main/java`、`src/main/resources`、`src/test/java`、`src/test/resources`（按需）
   - DDD 常见包层：`domain`、`applicationservice`、`infrastructure`、`userinterface`（仅在用户要求时创建）
3. 生成“最小创建计划”：只保留用户点名项和其必要父目录。
4. 执行创建：
   - 先建目录，再建文件。
   - 文档文件默认仅写标题，不填充长模板。
5. 自检：
   - 检查是否存在多建目录/文件。
   - 检查是否遗漏用户明确要求。
6. 返回结果清单与后续可选扩展建议（可选，不自动执行）。

# 约束与注意事项
- 严禁一次性生成完整脚手架，除非用户明确要求“完整结构”。
- 不复制参考仓库业务代码、配置内容或大段文档文本。
- 仅将参考仓库用作目录组织基准，不做内容镜像。
- 若用户需求与基准结构冲突，以用户需求优先，并在结果中标注偏差点。

# 失败与降级
- 输入不足：输出“待确认最小清单”，暂停创建。
- 无法访问参考链接：使用已知 DDD 通用最小结构执行，并标注“基于通用结构降级”。
- 路径冲突（已存在同名文件/目录）：跳过冲突项并在结果中列出。
- 无法完成时反馈格式：
  - `status: failed`
  - `reason: <具体原因>`
  - `next_action: <用户可执行的最小下一步>`

# 快速检查清单
- [ ] 仅创建用户请求项及必要父目录
- [ ] 未生成业务代码
- [ ] 文档内容保持最小化
- [ ] 结果清单包含“已创建/未创建及原因”
- [ ] 与 DDD 分层和 Spring Boot 基础目录不冲突

# 示例
## 示例 1：标准场景
输入：
- 项目根目录：`/workspace/order-service`
- 创建目标：`mixed`
- 需求：
  - `docs/development/openapi/`
  - `src/main/java/com/example/order/domain/`
  - `src/main/java/com/example/order/infrastructure/`

输出：
- 已创建目录：
  - `docs/`
  - `docs/development/`
  - `docs/development/openapi/`
  - `src/main/java/com/example/order/domain/`
  - `src/main/java/com/example/order/infrastructure/`
- 已创建文件：无
- 未创建项：无

## 示例 2：异常场景
输入：
- 项目根目录：`/workspace/payment-service`
- 创建目标：`engineering`
- 需求：`src/main/java` 下建立 DDD 分层（未提供包名）

输出：
- 降级处理：
  - 仅创建 `src/main/java/domain/`、`src/main/java/applicationservice/`、`src/main/java/infrastructure/`、`src/main/java/userinterface/`
  - 标注“未提供包名，未创建包路径层级”
