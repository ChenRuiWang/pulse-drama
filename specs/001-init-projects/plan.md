# Implementation Plan: 项目骨架初始化

**Branch**: `001-init-projects` | **Date**: 2026-03-09 | **Spec**: [spec.md](./spec.md)
**Input**: Feature specification from `/specs/001-init-projects/spec.md`

## Summary

使用 CLI 工具初始化 monorepo 项目骨架，包含 React Native + Expo 移动端（apps/mobile）和 NestJS 后端服务（apps/server），遵循 TypeScript 全栈统一原则。

## Technical Context

**Language/Version**: TypeScript 5.x, Node.js 18+
**Primary Dependencies**: React Native, Expo SDK 52+, NestJS 10+
**Storage**: PostgreSQL 15+（后续阶段接入，初始化阶段暂不需要）
**Testing**: Jest（NestJS 内置）, Jest + React Native Testing Library（移动端）
**Target Platform**: iOS/Android（移动端）, Node.js server（后端）
**Project Type**: monorepo（mobile-app + web-service）
**Performance Goals**: 移动端启动 < 60s，后端启动 < 30s
**Constraints**: 需预装 @nestjs/cli 和 expo-cli 全局包
**Scale/Scope**: 初期单人开发，monorepo 结构支持后续扩展

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

| Principle | Status | Notes |
|-----------|--------|-------|
| I. TypeScript Full-Stack Unification | ✅ Pass | 前后端均使用 TypeScript |
| II. Cost-First Strategy | ✅ Pass | 使用免费 CLI 工具，无付费依赖 |
| III. PostgreSQL Single-Database Strategy | ⚠️ N/A | 初始化阶段不涉及数据库 |
| IV. AI-Driven Development | ✅ Pass | CLI 生成的标准结构，清晰可读 |
| V. Scale on Demand | ✅ Pass | monorepo 结构便于后续拆分 |

**Gate Result**: ✅ PASS

## Project Structure

### Documentation (this feature)

```text
specs/001-init-projects/
├── plan.md              # This file
├── research.md          # Phase 0 output
├── data-model.md        # Phase 1 output（N/A - 无数据模型）
├── quickstart.md        # Phase 1 output
├── contracts/           # Phase 1 output（N/A - 初始化阶段无外部接口）
└── tasks.md             # Phase 2 output
```

### Source Code (repository root)

```text
apps/
├── mobile/              # React Native + Expo 项目
│   ├── app/             # Expo Router 文件路由
│   ├── assets/          # 静态资源
│   ├── components/      # 可复用组件
│   ├── constants/       # 常量定义
│   ├── hooks/           # 自定义 hooks
│   ├── scripts/         # 脚本
│   ├── app.json         # Expo 配置
│   ├── package.json     # 依赖配置
│   └── tsconfig.json    # TypeScript 配置
│
└── server/              # NestJS 后端项目
    ├── src/
    │   ├── main.ts          # 应用入口
    │   ├── app.module.ts    # 根模块
    │   ├── app.controller.ts
    │   └── app.service.ts
    ├── test/             # 测试文件
    ├── nest-cli.json     # NestJS CLI 配置
    ├── package.json      # 依赖配置
    └── tsconfig.json     # TypeScript 配置
```

**Structure Decision**: 采用 monorepo 结构，apps/ 目录下分别放置 mobile 和 server 两个独立项目，保持各自独立的依赖和配置，便于独立开发、测试和部署。

## Complexity Tracking

> 无 Constitution 违规，无需记录。
