# pulse-drama Development Guidelines

Auto-generated from all feature plans. Last updated: 2026-03-10

## Active Technologies

- TypeScript 5.x, Node.js 18+
- React Native + Expo SDK 52+ (mobile)
- NestJS 10+ (server)

## Project Structure

```text
pulse-drama/
├── apps/
│   ├── mobile/         # React Native + Expo 移动端
│   │   ├── App.tsx
│   │   ├── app.json
│   │   └── package.json
│   └── server/         # NestJS 后端服务
│       ├── src/
│       │   ├── main.ts
│       │   ├── app.module.ts
│       │   └── app.controller.ts
│       └── package.json
├── specs/              # 功能规格和设计文档
└── .specify/           # Speckit 配置
```

## Commands

### Mobile (apps/mobile)

```bash
npx expo start          # 启动开发服务器
npx expo start --tunnel # USB 连接手机时使用隧道模式
```

### Server (apps/server)

```bash
npm run start           # 启动生产模式
npm run start:dev       # 启动开发模式 (热重载)
npm run test            # 运行测试
npm run lint            # 代码检查
```

## Code Style

- TypeScript strict mode
- ESLint + Prettier (server 已配置)
- Conventional Commits

## Architecture Principles

详见 `.specify/memory/constitution.md`:
- TypeScript 全栈统一
- 成本优先（免费层服务）
- PostgreSQL 单数据库
- AI 友好代码
- 单体架构起步，按需拆分

## Ports

- Server: 3000
- Expo: 8081 (默认)

<!-- MANUAL ADDITIONS START -->
<!-- MANUAL ADDITIONS END -->
