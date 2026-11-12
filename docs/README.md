# Barbie - Personal Finance Management Platform

**🌐 Live: [uofa.ink](https://uofa.ink)** · Preview: [uofa.ink/preview](https://uofa.ink/preview/)

**Language / 语言**: [English](#english) | [中文](#中文)

---

<a name="english"></a>
## 🇺🇸 English

A full-stack personal finance management application with subscription tracking, expense management, budget planning, income recording, and multi-currency conversion.

Live at [uofa.ink](https://uofa.ink) (self-hosted).

### ✨ Core Features

| Module | Description |
|--------|-------------|
| **Subscription Management** | Track subscription services (Netflix, Spotify, etc.), auto-calculate renewal dates |
| **Expense Tracking** | Record daily expenses, analyze by month/category |
| **Budget Planning** | Set monthly budget limits, real-time spending progress monitoring |
| **Income Recording** | Manage multiple income sources, generate income summaries |
| **Currency Conversion** | Real-time exchange rates, custom currency pairs |
| **Data Analytics** | Dashboard visualization of financial overview |

---

### 🛠️ Tech Stack

#### Frontend
| Technology | Purpose |
|------------|---------|
| **React 19** | Core UI framework |
| **Vite 7** | Next-gen build tool with lightning-fast HMR |
| **TanStack Query (React Query)** | Server state management with smart caching |
| **Zustand** | Lightweight client-side state management |
| **Tailwind CSS 4** | Utility-first CSS framework |
| **Framer Motion** | Smooth animation library |
| **Axios** | HTTP client |
| **Vitest** | Modern unit testing framework |

#### Backend
| Technology | Purpose |
|------------|---------|
| **Node.js 20+** | Server-side runtime |
| **Express.js** | Web framework |
| **MongoDB + Mongoose 9** | NoSQL database with ODM |
| **JWT** | Stateless authentication |
| **Joi** | Data validation |
| **Arcjet** | Security (Rate Limiting, Bot Detection, Shield) |
| **Jest** | Unit testing |

#### DevOps
| Technology | Purpose |
|------------|---------|
| **Monorepo Architecture** | Unified frontend/backend code management |
| **ESLint** | Code linting |
| **dotenv** | Environment variable management |

---

### 🏗️ Architecture Advantages

#### 1. Modular Backend Design

```
modules/
├── auth/          # Authentication
├── user/          # User management
├── subscription/  # Subscription management
├── expenses/      # Expense tracking
├── budgets/       # Budget management
├── income/        # Income recording
├── currency/      # Exchange rate service
└── convertPair/   # Currency pair management
```

Each module follows a consistent layered architecture:
- **Controller** → HTTP request handling
- **Service** → Business logic
- **Repository** → Data access layer
- **Model** → Data model definition
- **Validation** → Request validation rules

#### 2. Smart Caching System

The frontend implements a complete caching architecture (see [cache_architecture.md](./cache_architecture.md)):

- **In-memory Cache** - Reduce network requests
- **Request Deduplication** - Identical requests share the same Promise
- **Precise Invalidation** - Prefix-based batch invalidation, auto-update after CUD operations
- **Multi-user Isolation** - Cache keys include userId to prevent data leakage
- **Debounce Mechanism** - Fast month switching triggers only one request

#### 3. Security Features

- **JWT Authentication** - Stateless token-based auth
- **Password Encryption** - bcrypt hash storage
- **Input Validation** - Strict Joi schema validation
- **Arcjet Protection** - Rate limiting + Bot detection + Shield
- **CORS Configuration** - Cross-origin resource sharing control

#### 4. Developer Experience

- **Environment Isolation** - Development / Production config separation
- **Hot Reload** - Vite HMR + Nodemon
- **Type Hints** - JSDoc type annotations
- **Comprehensive Testing** - 72+ unit test cases

---

### 🔌 Port Configuration

> **Note**: Vite uses different default ports for development (`vite`) and preview (`vite preview`) modes.

| Service | Development | Production/Preview |
|---------|-------------|-------------------|
| Frontend (Vite) | http://localhost:5173 (`npm run dev`) | http://localhost:4173 (`npm run preview`) |
| Backend | http://localhost:5500 (`npm run dev`) | http://localhost:4273 (`npm start`) |
| Data Science | http://localhost:8000 | http://localhost:8000 |

**How it works:**
- `npm run dev` → Frontend on :5173, proxies API requests to Backend :5500
- `npm run preview` → Frontend on :4173, proxies API requests to Backend :4273

---

### 📚 Documentation Index

- **[System Architecture](ARCHITECTURE.md)** - High-level design, tech stack, data flow
- **[Backend API](api/Backend-api.md)** - All backend endpoint details
- **[Cache Architecture](cache_architecture.md)** - Frontend caching design principles
- **[Backend Service](../apps/backend/README.md)** - Backend setup guide
- **[Frontend Service](../apps/frontend/README.md)** - Frontend app structure

---

### 🚀 Quick Start

#### 1. Install Dependencies
```bash
cd apps/backend && npm install
cd apps/frontend && npm install
```

#### 2. Configure Environment
```bash
cp apps/backend/.env.example apps/backend/.env.development.local
```

#### 3. Start Services

**Development Mode:**
```bash
# Terminal 1: Backend (port 5500)
cd apps/backend && npm run dev

# Terminal 2: Frontend (port 5173)
cd apps/frontend && npm run dev
```

**Production Mode:**
```bash
# Terminal 1: Backend (port 4273)
cd apps/backend && npm start

# Terminal 2: Frontend (port 4173)
cd apps/frontend && npm run build && npm run preview
```

---

### 🧪 Testing

```bash
# Backend tests
cd apps/backend && npm test

# Frontend tests
cd apps/frontend && npm run test:run
```

---

<a name="中文"></a>
## 🇨🇳 中文

一个功能完整的全栈个人财务管理应用，支持订阅管理、支出追踪、预算规划、收入记录和多币种转换。

线上地址：[uofa.ink](https://uofa.ink)（自建服务器部署）

### ✨ 核心功能

| 模块 | 功能描述 |
|------|----------|
| **订阅管理** | 追踪各类订阅服务（Netflix, Spotify等），自动计算续费日期 |
| **支出追踪** | 记录日常支出，按月份/类别统计分析 |
| **预算规划** | 设置月度预算限制，实时监控支出进度 |
| **收入记录** | 管理多种收入来源，生成收入摘要 |
| **货币转换** | 实时汇率查询，支持自定义货币对 |
| **数据分析** | Dashboard 可视化展示财务概览 |

---

### 🛠️ 技术栈

#### 前端
| 技术 | 用途 |
|------|------|
| **React 19** | 核心 UI 框架 |
| **Vite 7** | 下一代构建工具，极速 HMR |
| **TanStack Query (React Query)** | 服务端状态管理与智能缓存 |
| **Zustand** | 轻量级客户端状态管理 |
| **Tailwind CSS 4** | 原子化 CSS 框架 |
| **Framer Motion** | 流畅动画库 |
| **Axios** | HTTP 客户端 |
| **Vitest** | 现代化单元测试框架 |

#### 后端
| 技术 | 用途 |
|------|------|
| **Node.js 20+** | 服务端运行时 |
| **Express.js** | Web 框架 |
| **MongoDB + Mongoose 9** | NoSQL 数据库与 ODM |
| **JWT** | 无状态身份认证 |
| **Joi** | 数据验证 |
| **Arcjet** | 安全防护 (速率限制、机器人检测、Shield) |
| **Jest** | 单元测试 |

#### DevOps
| 技术 | 用途 |
|------|------|
| **Monorepo 架构** | 前后端代码统一管理 |
| **ESLint** | 代码规范检查 |
| **dotenv** | 环境变量管理 |

---

### 🏗️ 架构优势

#### 1. 模块化后端设计

```
modules/
├── auth/          # 认证模块
├── user/          # 用户管理
├── subscription/  # 订阅管理
├── expenses/      # 支出追踪
├── budgets/       # 预算管理
├── income/        # 收入记录
├── currency/      # 汇率服务
└── convertPair/   # 货币对管理
```

每个模块遵循统一的分层架构：
- **Controller** → HTTP 请求处理
- **Service** → 业务逻辑
- **Repository** → 数据访问层
- **Model** → 数据模型定义
- **Validation** → 请求验证规则

#### 2. 智能缓存系统

前端实现了一套完整的缓存架构，详见 [cache_architecture.md](./cache_architecture.md)：

- **内存缓存** - 减少网络请求
- **请求去重** - 相同请求共享 Promise
- **精准失效** - 按前缀批量失效，CUD 操作后自动更新
- **多用户隔离** - Cache Key 包含 userId，防止数据泄露
- **防抖机制** - 快速切换月份只触发一次请求

#### 3. 安全特性

- **JWT 认证** - 无状态 Token 认证
- **密码加密** - bcrypt 哈希存储
- **输入验证** - Joi Schema 严格校验
- **Arcjet 防护** - 速率限制 + 机器人检测 + Shield 防护
- **CORS 配置** - 跨域资源共享控制

#### 4. 开发体验优化

- **环境隔离** - Development / Production 配置分离
- **热更新** - Vite HMR + Nodemon
- **TypeScript 类型提示** - JSDoc 类型注释
- **完善测试** - 72+ 单元测试用例

---

### 🔌 端口配置

> **注意**: Vite 在开发模式 (`vite`) 和预览模式 (`vite preview`) 使用不同的默认端口。

| 服务 | 开发环境 | 生产环境/预览 |
|------|----------|--------------|
| 前端 (Vite) | http://localhost:5173 (`npm run dev`) | http://localhost:4173 (`npm run preview`) |
| 后端 | http://localhost:5500 (`npm run dev`) | http://localhost:4273 (`npm start`) |
| 数据科学 | http://localhost:8000 | http://localhost:8000 |

**工作原理:**
- `npm run dev` → 前端运行在 :5173，API 请求代理到后端 :5500
- `npm run preview` → 前端运行在 :4173，API 请求代理到后端 :4273

---

### 📚 文档索引

- **[系统架构](ARCHITECTURE.md)** - 高层架构设计、技术栈、数据流
- **[Backend API](api/Backend-api.md)** - 所有后端接口详情
- **[缓存架构详解](cache_architecture.md)** - 前端缓存设计原理与最佳实践
- **[Backend Service](../apps/backend/README.md)** - 后端安装与配置
- **[Frontend Service](../apps/frontend/README.md)** - 前端应用结构

---

### 🚀 快速开始

#### 1. 安装依赖
```bash
cd apps/backend && npm install
cd apps/frontend && npm install
```

#### 2. 配置环境变量
```bash
cp apps/backend/.env.example apps/backend/.env.development.local
```

#### 3. 启动服务

**开发模式:**
```bash
# Terminal 1: 后端 (端口 5500)
cd apps/backend && npm run dev

# Terminal 2: 前端 (端口 5173)
cd apps/frontend && npm run dev
```

**生产模式:**
```bash
# Terminal 1: 后端 (端口 4273)
cd apps/backend && npm start

# Terminal 2: 前端 (端口 4173)
cd apps/frontend && npm run build && npm run preview
```

---

### 🧪 测试

```bash
# 后端测试
cd apps/backend && npm test

# 前端测试
cd apps/frontend && npm run test:run
```

---

**Last Updated**: January 2026  
**Version**: 1.0.0
