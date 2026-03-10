# Pulse Drama

短剧应用平台

## 项目结构

```
pulse-drama/
├── apps/
│   ├── mobile/     # React Native + Expo 移动端
│   │   ├── app.json
│   │   ├── App.tsx
│   │   └── package.json
│   └── server/     # NestJS 后端服务
│       ├── src/
│       │   ├── main.ts
│       │   ├── app.module.ts
│       │   └── app.controller.ts
│       └── package.json
├── specs/          # 功能规格和设计文档
└── .specify/       # Speckit 配置
```

## 快速开始

### 前置条件

- Node.js 18+
- 全局安装 @nestjs/cli: `npm i -g @nestjs/cli`
- 全局安装 expo-cli: `npm i -g expo-cli`

### 移动端

```bash
cd apps/mobile
npm install    # 已安装依赖可跳过
npx expo start
# 按 'i' 启动 iOS 模拟器，或 'a' 启动 Android 模拟器
```

### 后端服务

```bash
cd apps/server
npm install    # 已安装依赖可跳过
npm run start:dev
# 访问 http://localhost:3000
```

## 技术栈

| 层级 | 技术 | 版本 |
|------|------|------|
| 语言 | TypeScript | 5.x |
| 移动端 | React Native + Expo | SDK 52+ |
| 后端 | NestJS | 10+ |
| 数据库 | PostgreSQL | 15+ (后续接入) |

## 开发规范

详见 `.specify/memory/constitution.md`

## 端口

- 后端服务: 3000
- Expo 开发服务器: 8081 (默认)
