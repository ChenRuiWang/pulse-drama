# Quickstart: 项目骨架初始化

## 前置条件

- Node.js 18+ (LTS)
- 全局安装 `@nestjs/cli`: `npm i -g @nestjs/cli`
- 全局安装 `expo-cli`: `npm i -g expo-cli`
- (可选) iOS 开发: Xcode 15+
- (可选) Android 开发: Android Studio + SDK

## 实际执行记录 (2026-03-09)

### 1. 创建项目目录结构

```bash
mkdir -p apps
```

### 2. 初始化 Expo 移动端项目

```bash
cd apps
npx create-expo-app@latest mobile --template blank-typescript
```

**实际版本**:
- Expo SDK: 52
- React Native: 0.76.x
- TypeScript: 5.x

验证:
```bash
cd mobile
npx expo start
# 按 'i' 启动 iOS 模拟器，或 'a' 启动 Android 模拟器
```

### 3. 初始化 NestJS 后端项目

```bash
nest new server --package-manager npm --skip-git
```

**实际版本**:
- NestJS: 10.x
- TypeScript: 5.x

验证:
```bash
cd server
npm run start:dev
# 访问 http://localhost:3000 应返回 "Hello World!"
```

## 目录结构验证

初始化完成后，目录结构如下:

```
pulse-drama/
├── apps/
│   ├── mobile/
│   │   ├── App.tsx
│   │   ├── app.json
│   │   ├── assets/
│   │   ├── package.json
│   │   └── tsconfig.json
│   └── server/
│       ├── src/
│       │   ├── main.ts
│       │   ├── app.module.ts
│       │   ├── app.controller.ts
│       │   └── app.service.ts
│       ├── test/
│       ├── nest-cli.json
│       ├── package.json
│       └── tsconfig.json
├── specs/
│   └── 001-init-projects/
│       ├── spec.md
│       ├── plan.md
│       ├── research.md
│       ├── quickstart.md
│       └── tasks.md
├── .gitignore
└── README.md
```

## 常见问题

### Q: Expo 启动失败，提示端口占用
A: 修改端口: `npx expo start --port 8082`

### Q: NestJS 启动失败，提示依赖问题
A: 删除 node_modules 并重新安装: `rm -rf node_modules && npm install`

### Q: TypeScript 编译错误
A: 确保使用 Node.js 18+ 和最新版 TypeScript: `npm install -D typescript@latest`

## 下一步

1. 配置 ESLint + Prettier（可选）
2. 添加共享类型包（packages/shared-types）
3. 配置数据库连接（Prisma + PostgreSQL）
4. 实现第一个 API 端点
