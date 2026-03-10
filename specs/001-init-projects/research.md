# Research: 项目骨架初始化

**Feature**: 001-init-projects
**Date**: 2026-03-09

## Research Items

### 1. Expo 项目初始化最佳实践

**Decision**: 使用 `npx create-expo-app` 命令，选择 blank TypeScript 模板

**Rationale**:
- 官方推荐方式，保证最新版本
- blank TypeScript 模板提供最小化起点，便于自定义
- 内置 Expo Router 支持文件路由

**Alternatives Considered**:
- `expo init`（已弃用，现为 create-expo-app 别名）
- with-router 模板（blank + 手动添加更灵活）

### 2. NestJS 项目初始化最佳实践

**Decision**: 使用 `nest new` 命令，选择 npm 或 pnpm 作为包管理器

**Rationale**:
- 官方 CLI 生成标准项目结构
- 内置 ESLint、Prettier、Jest 配置
- 模块化结构便于扩展

**Alternatives Considered**:
- 手动创建（不推荐，缺少最佳实践配置）
- NestJS starter 仓库（CLI 更新更及时）

### 3. Monorepo 工具选择

**Decision**: 暂不引入 monorepo 工具（如 Nx、Turborepo），保持简单结构

**Rationale**:
- 初期项目简单，两个独立项目足够
- 避免额外学习成本和配置复杂度
- 后续需要时可平滑迁移

**Alternatives Considered**:
- Nx（功能强大但初期过重）
- Turborepo（轻量但暂无必要）
- pnpm workspaces（可后续引入）

### 4. 共享类型定义方案

**Decision**: 后续创建 packages/shared-types 目录，使用 TypeScript path aliases 或 npm workspace 引用

**Rationale**:
- 遵循 Constitution I（TypeScript 全栈统一）
- 初期可暂缓，待有实际共享需求时再创建

**Alternatives Considered**:
- 独立 npm 包（初期过于复杂）
- 复制类型定义（违反 DRY 原则）

## Commands Reference

### 创建 Expo 项目
```bash
cd apps
npx create-expo-app mobile --template blank-typescript
```

### 创建 NestJS 项目
```bash
cd apps
nest new server
```

## Dependencies Summary

| 项目 | 核心依赖 | 开发依赖 |
|------|----------|----------|
| mobile | expo, react-native, expo-router | typescript, @types/react |
| server | @nestjs/core, @nestjs/common | typescript, @nestjs/cli, jest |

## Notes

- Node.js 版本建议 18+ (LTS)
- Expo SDK 52+ 支持 React Native 0.76+
- NestJS 10+ 支持 TypeScript 5.x
