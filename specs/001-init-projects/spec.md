# Feature Specification: 项目骨架初始化

**Feature Branch**: `001-init-projects`
**Created**: 2026-03-09
**Status**: Draft
**Input**: User description: "创建项目骨架：React Native + Expo 客户端在 apps/mobile，NestJS 后端在 apps/server"

## User Scenarios & Testing *(mandatory)*

### User Story 1 - 创建移动端应用骨架 (Priority: P1)

开发人员需要初始化 React Native + Expo 客户端项目，以便快速开始移动端开发。

**Why this priority**: 移动端是面向用户的核心入口，需要优先搭建以支持后续功能开发。

**Independent Test**: 可以通过在 apps/mobile 目录下运行 Expo 开发服务器并加载默认应用界面来验证。

**Acceptance Scenarios**:

1. **Given** apps/mobile 目录不存在，**When** 执行初始化命令，**Then** apps/mobile 目录下生成可运行的 Expo 项目结构
2. **Given** 项目已初始化，**When** 启动开发服务器，**Then** 能够在移动设备或模拟器上看到默认欢迎页面

---

### User Story 2 - 创建后端服务骨架 (Priority: P1)

开发人员需要初始化 NestJS 后端项目，以便构建 API 服务。

**Why this priority**: 后端服务为移动端提供数据支持，是系统的基础设施。

**Independent Test**: 可以通过在 apps/server 目录下运行 NestJS 开发服务器并访问健康检查端点来验证。

**Acceptance Scenarios**:

1. **Given** apps/server 目录不存在，**When** 执行初始化命令，**Then** apps/server 目录下生成可运行的 NestJS 项目结构
2. **Given** 服务已启动，**When** 访问服务端点，**Then** 返回预期的响应

---

### User Story 3 - Monorepo 结构验证 (Priority: P2)

开发人员需要确认两个项目在 monorepo 结构下能够独立运行且互不干扰。

**Why this priority**: 确保项目结构清晰，便于后续维护和扩展。

**Independent Test**: 可以分别启动 mobile 和 server 项目，验证两者独立运行正常。

**Acceptance Scenarios**:

1. **Given** 两个项目都已初始化，**When** 分别进入各目录运行开发命令，**Then** 各项目独立启动且无冲突
2. **Given** monorepo 根目录，**When** 查看目录结构，**Then** 清晰展示 apps/mobile 和 apps/server 两个子项目

---

### Edge Cases

- 如果 apps 目录已存在同名子目录怎么办？→ 应提示用户并中止或要求确认覆盖
- 如果 CLI 工具版本不兼容怎么办？→ 应记录版本要求并在文档中说明

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: 系统 MUST 在 apps/mobile 目录下创建完整的 React Native + Expo 项目结构
- **FR-002**: 系统 MUST 在 apps/server 目录下创建完整的 NestJS 项目结构
- **FR-003**: 移动端项目 MUST 能够通过 Expo CLI 启动并在设备/模拟器上运行
- **FR-004**: 后端项目 MUST 能够通过 NestJS CLI 启动并响应 HTTP 请求
- **FR-005**: 两个项目 MUST 相互独立，各自拥有独立的依赖配置

### Key Entities

- **Mobile App**: 移动端应用，基于 Expo 框架，位于 apps/mobile
- **Server App**: 后端服务，基于 NestJS 框架，位于 apps/server

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: 移动端项目初始化后，首次启动时间在 60 秒内完成
- **SC-002**: 后端项目初始化后，服务启动时间在 30 秒内完成
- **SC-003**: 开发人员能在 5 分钟内完成两个项目的初始化和首次运行验证
- **SC-004**: 两个项目均能通过各自的默认健康检查（Expo 应用加载成功、NestJS 返回默认响应）

## Assumptions

- 开发环境已预装 Node.js（推荐 v18+）
- 开发环境已预装 @nestjs/cli 和 expo-cli 全局包
- 目标平台为 iOS 和 Android 双端支持
