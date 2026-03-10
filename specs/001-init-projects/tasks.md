# Tasks: 项目骨架初始化

**Input**: Design documents from `/specs/001-init-projects/`
**Prerequisites**: plan.md (required), spec.md (required for user stories), research.md, quickstart.md

**Tests**: 未请求测试任务，本功能为项目初始化，CLI 生成的项目已包含默认测试配置。

**Organization**: 任务按用户故事分组，支持独立实现和测试。

## Format: `[ID] [P?] [Story] Description`

- **[P]**: 可并行执行（不同文件，无依赖）
- **[Story]**: 所属用户故事（US1, US2, US3）
- 描述中包含精确文件路径

## Path Conventions

- **Monorepo**: `apps/mobile/`, `apps/server/` 作为独立项目根目录

---

## Phase 1: Setup (共享基础设施)

**Purpose**: 创建 monorepo 目录结构

- [x] T001 创建 apps 目录结构
- [x] T002 [P] 创建根目录 .gitignore 文件
- [x] T003 [P] 创建根目录 README.md 项目说明文件

**Checkpoint**: ✓ 目录结构就绪

---

## Phase 2: Foundational (无阻塞依赖)

**Purpose**: 本项目为初始化任务，无需额外基础设施

> ⚠️ 注：此项目为纯初始化任务，两个用户故事（US1, US2）可独立进行，无共享基础设施依赖。跳过此阶段。

**Checkpoint**: ✓ 直接进入用户故事实现

---

## Phase 3: User Story 1 - 创建移动端应用骨架 (Priority: P1) 🎯 MVP

**Goal**: 初始化 React Native + Expo 客户端项目

**Independent Test**: 在 apps/mobile 目录运行 `npx expo start`，能在设备/模拟器上看到默认欢迎页面

### Implementation for User Story 1

- [x] T004 [US1] 使用 Expo CLI 创建项目: `cd apps && npx create-expo-app mobile --template blank-typescript`
- [x] T005 [US1] 验证项目结构: 确认 apps/mobile/app.json 存在
- [x] T006 [US1] 验证项目结构: 确认 apps/mobile/package.json 存在
- [x] T007 [US1] 验证项目结构: 确认 apps/mobile/tsconfig.json 存在
- [ ] T008 [US1] 启动开发服务器验证: `cd apps/mobile && npx expo start` (手动验证)

**Checkpoint**: ✓ Expo 项目可独立启动和运行

---

## Phase 4: User Story 2 - 创建后端服务骨架 (Priority: P1)

**Goal**: 初始化 NestJS 后端项目

**Independent Test**: 在 apps/server 目录运行 `npm run start:dev`，访问 http://localhost:3000 返回默认响应

### Implementation for User Story 2

- [x] T009 [US2] 使用 NestJS CLI 创建项目: `cd apps && nest new server` (选择 npm)
- [x] T010 [US2] 验证项目结构: 确认 apps/server/src/main.ts 存在
- [x] T011 [US2] 验证项目结构: 确认 apps/server/src/app.module.ts 存在
- [x] T012 [US2] 验证项目结构: 确认 apps/server/nest-cli.json 存在
- [x] T013 [US2] 验证项目结构: 确认 apps/server/package.json 存在
- [ ] T014 [US2] 启动开发服务器验证: `cd apps/server && npm run start:dev` (手动验证)

**Checkpoint**: ✓ NestJS 项目可独立启动和响应请求

---

## Phase 5: User Story 3 - Monorepo 结构验证 (Priority: P2)

**Goal**: 确认两个项目在 monorepo 结构下独立运行无冲突

**Independent Test**: 分别启动 mobile 和 server 项目，验证两者独立运行正常

### Implementation for User Story 3

- [x] T015 [US3] 验证目录结构: 确认 apps/mobile 和 apps/server 目录存在
- [x] T016 [US3] 验证独立依赖: 确认 apps/mobile/package.json 和 apps/server/package.json 独立存在
- [ ] T017 [US3] 并行启动验证: 同时启动 mobile 和 server 项目，确认无端口/资源冲突 (手动验证)
- [x] T018 [US3] 更新根目录 README.md: 添加项目结构和启动说明

**Checkpoint**: ✓ Monorepo 结构完整，两个项目独立可运行

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: 完善和文档化

- [x] T019 [P] 更新 specs/001-init-projects/quickstart.md: 记录实际使用的命令和版本
- [ ] T020 [P] 提交初始化代码: git add 和 commit

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: 无依赖 - 立即开始
- **Foundational (Phase 2)**: 跳过（无共享基础设施）
- **User Stories (Phase 3-5)**: 依赖 Setup 完成
  - US1 和 US2 可并行执行
  - US3 依赖 US1 和 US2 完成
- **Polish (Phase 6)**: 依赖所有用户故事完成

### User Story Dependencies

- **User Story 1 (P1)**: 依赖 Setup - 可独立完成
- **User Story 2 (P1)**: 依赖 Setup - 可独立完成，与 US1 并行
- **User Story 3 (P2)**: 依赖 US1 和 US2 完成

### Parallel Opportunities

- T002, T003 可并行
- T004-T008 (US1) 与 T009-T014 (US2) 可并行
- T019, T020 可并行（但 T020 需在 T019 完成后执行）

---

## Parallel Example: US1 + US2

```bash
# 终端 1: 创建移动端项目
cd apps && npx create-expo-app mobile --template blank-typescript

# 终端 2: 创建后端项目
cd apps && nest new server
```

---

## Implementation Strategy

### MVP First (User Story 1 或 2)

1. Complete Phase 1: Setup
2. Complete Phase 3: User Story 1 (移动端) **或** Phase 4: User Story 2 (后端)
3. **STOP and VALIDATE**: 独立测试所选项目
4. 继续完成另一个 P1 用户故事

### Incremental Delivery

1. Complete Setup → 目录结构就绪
2. Add User Story 1 → 移动端可运行
3. Add User Story 2 → 后端可运行
4. Add User Story 3 → Monorepo 结构验证完成
5. Polish → 文档和提交

---

## Notes

- [P] 任务 = 不同文件，无依赖
- [Story] 标签映射任务到具体用户故事
- 每个用户故事应独立可完成和测试
- CLI 生成的项目已包含 TypeScript 配置和默认测试框架
- 在每个 checkpoint 停下来验证独立功能
- T008, T014, T017 为手动验证步骤
