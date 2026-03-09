<!--
  SYNC IMPACT REPORT
  ==================
  Version change: N/A → 1.0.0 (initial creation)

  Added principles:
  - I. TypeScript Full-Stack Unification
  - II. Cost-First Strategy
  - III. PostgreSQL Single-Database Strategy
  - IV. AI-Driven Development
  - V. Scale on Demand

  Added sections:
  - Technology Stack
  - Development Workflow
  - Governance

  Removed sections: None (initial creation)

  Templates status:
  - .specify/templates/plan-template.md: ✅ Compatible (Constitution Check section present)
  - .specify/templates/spec-template.md: ✅ Compatible (no changes needed)
  - .specify/templates/tasks-template.md: ✅ Compatible (no changes needed)

  Follow-up TODOs: None
-->

# Pulse Drama Constitution

## Core Principles

### I. TypeScript Full-Stack Unification

前后端统一使用 TypeScript，消除语言切换成本，实现代码和类型共享。

**规则**：
- 前端：React Native（iOS/Android 跨平台）
- 后端：NestJS（模块化、可扩展）
- 共享类型定义通过 monorepo 或独立包管理
- 禁止 `any` 类型，必须显式定义接口

**理由**：单一语言栈降低认知负担，类型安全减少运行时错误，提升 AI 代码生成质量。

### II. Cost-First Strategy

成本控制是架构决策的首要约束，优先利用免费层服务。

**规则**：
- 托管：优先选择免费层（Supabase/Neon/Render 等）
- 存储：免费额度内优化，避免过早付费
- 第三方服务：必须有免费层选项
- 架构决策必须附上成本估算

**理由**：初期项目无收入，免费层足够验证 MVP，付费服务需有明确 ROI 证明。

### III. PostgreSQL Single-Database Strategy

单一 PostgreSQL 实例承载所有数据需求，避免多数据库复杂性。

**规则**：
- 主数据：关系型存储
- 缓存需求：PostgreSQL 内置缓存机制
- 全文搜索：PostgreSQL FTS（需验证性能）
- 时序数据：TimescaleDB 扩展（如需）
- 分库仅在设计文档中证明必要时允许

**理由**：单数据库降低运维复杂度和成本，PostgreSQL 功能足够覆盖大部分场景。

### IV. AI-Driven Development

AI 辅助开发是核心生产力，代码必须 AI 友好。

**规则**：
- 可读性优先：清晰的命名、模块化结构
- 可测试性：每个模块必须有单元测试入口
- 文档同步：API 变更必须更新文档
- 避免"聪明"代码：选择显式而非隐式
- 复杂逻辑必须注释意图

**理由**：AI 生成代码的质量取决于上下文清晰度，可读可测的代码让 AI 迭代更高效。

### V. Scale on Demand

初期采用单体架构，按需拆分，避免过早优化。

**规则**：
- 起点：单体 NestJS 应用
- 拆分触发条件：单模块负载 > 70% 或团队 > 3 人
- 微服务拆分必须有监控数据支撑
- 所有模块保持低耦合，便于未来拆分

**理由**：过早微服务化增加复杂度和成本，单体足够支撑早期用户规模。

## Technology Stack

**语言**：TypeScript 5.x
**前端**：React Native + Expo
**后端**：NestJS
**数据库**：PostgreSQL 15+
**ORM**：Prisma 或 TypeORM
**缓存**：Redis（可选，免费层后引入）
**部署**：容器化，优先免费托管平台

## Development Workflow

**分支策略**：trunk-based，feature branch 短生命周期
**代码审查**：所有变更需审查，AI 生成的代码需人工验证
**测试要求**：
- 核心业务逻辑必须有单元测试
- API 端点必须有集成测试
- 关键用户流程必须有 E2E 测试

**提交规范**：Conventional Commits，AI 辅助生成 commit message

## Governance

**原则优先级**：本 constitution 高于个人偏好，所有架构决策必须符合上述原则
**修订流程**：
1. 提出修订并说明理由
2. 评估对现有代码的影响
3. 更新版本号（语义化版本）
4. 同步更新相关文档

**合规检查**：每个 feature plan 必须通过 constitution check

**Version**: 1.0.0 | **Ratified**: 2026-03-09 | **Last Amended**: 2026-03-09
