<div align="center">

<img src="public/f1-logo-white.png" alt="F1 Logo" width="120" />

# F1 Flying Lap · 飞驰圈

### F1 队友排位赛差距可视化 — 2025 赛季

一个沉浸式、数据驱动的 Web 应用，通过电影级 3D 视觉效果、实时统计和交互式分析面板，比较 **一级方程式赛车队友的排位赛表现**。

**[在线演示](https://f1-flyinglap.vercel.app)** · **[English](README.md)**

![Next.js](https://img.shields.io/badge/Next.js-16.1-black?logo=nextdotjs)
![React](https://img.shields.io/badge/React-19.2-61DAFB?logo=react&logoColor=white)
![Three.js](https://img.shields.io/badge/Three.js-0.183-black?logo=threedotjs)
![TypeScript](https://img.shields.io/badge/TypeScript-5.9-3178C6?logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4.1-06B6D4?logo=tailwindcss&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green)

</div>

---

## 应用截图

### 车队网格 — 车队选择转盘

浏览全部 10 支 F1 制造商车队，按积分榜排名排列。悬停预览车队详情，点击进入队友对比分析。

![车队网格 — 选择转盘](public/screenshots/01-grid-stage.png)

### 对决模式 — 队友头对头比较

队友排位赛直接对决：车手肖像、中位排位赛差距、头对头战绩，以及飞驰圈播客的红黑榜评分。

![对决模式 — 迈凯伦 NOR vs PIA](public/screenshots/02-versus-stage.png)

![对决模式 — 法拉利 LEC vs HAM](public/screenshots/04-versus-ferrari.png)

### 图表模式 — 深度数据分析面板

完整的排位赛分析：赛季差距折线图、Q3 打入率、逐站成绩表，以及可交互的 3D 赛车模型。

![图表模式 — 排位赛分析](public/screenshots/03-graph-stage.png)

---

## 这是什么？

**F1 Flying Lap** 是一个粉丝自制的交互式 Web 应用，可视化 2025 赛季一级方程式赛车队友的排位赛表现。它回答了每个 F1 车迷都会问的核心问题：**"谁更快——车手还是他的队友？"**

该应用计算**中位排位赛差距**（基于百分比），以消除极端值的影响，为驾驶同一台赛车的两位车手提供公平、客观的比较指标。数据通过 [FastF1](https://github.com/theOehrly/Fast-F1) 从 F1 官方计时系统获取，每个比赛周末后自动更新。

### 核心功能

- **3D 赛车模型** — Three.js 渲染的 10 支制造商赛车，支持俯视、电影级旋转和侧面三种视角
- **F1 起步灯** — 真实的五灯熄灭起步动画作为应用加载器
- **车队转盘** — 水平滚动的车队网格，实时显示制造商积分榜
- **对决模式** — 车手并排对比，包含肖像、国旗和中位排位差距
- **数据分析面板** — 赛季排位差距折线图、头对头战绩、Q3 打入率和逐站成绩
- **时间维度切换** — 在"全赛季"和"最近 5 站"之间切换，追踪近期状态
- **飞驰圈播客集成** — 红黑榜评分徽章，显示播客中对每位车手的评价
- **自动化数据管道** — GitHub Actions 定时任务，每周一通过 FastF1 更新数据
- **官方 F1 字体** — 全界面使用 Formula 1 Bold、Regular 和 Wide 字体
- **车队主题色** — 动态匹配每支制造商品牌色的强调色
- **彩蛋音频** — 特定车手的电台录音片段

---

## 技术栈

| 层级 | 技术 |
|------|------|
| **框架** | [Next.js 16](https://nextjs.org)（App Router、React Server Components） |
| **UI** | [React 19](https://react.dev)、[TypeScript 5.9](https://typescriptlang.org) |
| **3D 图形** | [Three.js](https://threejs.org)，Draco 压缩，后处理特效 |
| **动画** | [GSAP](https://gsap.com) 时间线动画、[Framer Motion](https://motion.dev) 弹簧物理动画 |
| **样式** | [Tailwind CSS 4](https://tailwindcss.com)、[shadcn/ui](https://ui.shadcn.com)、[Radix UI](https://radix-ui.com) |
| **状态管理** | [Zustand](https://zustand.docs.pmnd.rs)（阶段、车队、车手、相机状态） |
| **图表** | [Recharts](https://recharts.org) + 自定义 SVG 排位差距折线图 |
| **数据管道** | Python + [FastF1](https://github.com/theOehrly/Fast-F1) + GitHub Actions |
| **字体** | Formula 1 官方字体（Bold/Regular/Wide）、Titillium Web、Northwell |
| **代码检查** | [Biome](https://biomejs.dev)、[Prettier](https://prettier.io) |
| **测试** | [Playwright](https://playwright.dev) E2E 测试 |

---

## 项目结构

```
f1-flyinglap/
├── app/                        # Next.js App Router
│   ├── layout.tsx              # 根布局，F1 字体配置
│   ├── page.tsx                # 主页面（单页应用）
│   ├── globals.css             # 全局样式 & Tailwind 指令
│   └── assets/                 # 字体、音乐、纹理、背景图
│
├── components/
│   ├── stages/                 # 阶段导航视图
│   │   ├── TeamCarousel.tsx    # 网格阶段 — 车队选择转盘
│   │   ├── VersusMode.tsx      # 对决阶段 — 队友头对头
│   │   └── GraphMode.tsx       # 图表阶段 — 数据分析面板
│   └── ui/                     # 30+ 可复用 UI 组件
│       ├── TopDownCarShowcase   # Three.js 3D 赛车渲染器
│       ├── FiveLightsOut        # F1 起步灯加载动画
│       ├── DriverProfileCard    # 车手信息卡（含播客徽章）
│       ├── QualifyingGapChart   # 排位差距可视化
│       ├── SimpleGraph          # 赛季差距折线图
│       └── ...                  # HUD、自定义光标、背景特效
│
├── data/
│   └── generated/2025/         # 预计算 JSON 数据集
│       ├── teams.json          # 10 支制造商车队信息
│       ├── drivers.json        # 20 位车手元数据
│       ├── qualifying-results.json
│       ├── races.json          # 24 场比赛周末
│       └── computed/           # 派生统计数据
│           ├── teammate-gaps.json
│           ├── head-to-head.json
│           ├── q3-rates.json
│           └── driver-standings.json
│
├── pipeline/                   # Python 数据提取管道
│   └── src/f1pipeline/         # 基于 FastF1 的数据采集与统计计算
│
├── store/
│   └── useAppStore.ts          # Zustand 全局状态
│
├── lib/                        # 工具函数（GSAP、预加载器、风洞特效）
├── types/                      # TypeScript 类型定义
├── public/
│   ├── 3d-model/               # GLB 赛车模型（Draco 压缩）
│   ├── f1_2025_driver_portraits/  # 车手肖像
│   ├── f1-2025-cars/           # 赛车侧视图
│   ├── team-logos/             # 车队标志
│   └── sound/                  # 音频片段
│
└── .github/workflows/
    └── update-f1-data.yml      # 定时数据管道（每周一）
```

---

## 快速开始

### 环境要求

- **Node.js** 20+（推荐 24 LTS）
- **pnpm**、**npm** 或 **yarn**
- **Python 3.11+** 和 [uv](https://docs.astral.sh/uv/)（仅在运行数据管道时需要）

### 安装

```bash
# 克隆仓库
git clone https://github.com/zhongth/f1-flyinglap.git
cd f1-flyinglap

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

打开 [http://localhost:3000](http://localhost:3000) — 你将看到 F1 起步灯动画，然后进入车队选择转盘。

### 可用脚本

| 命令 | 说明 |
|------|------|
| `npm run dev` | 启动 Next.js 开发服务器（Turbopack） |
| `npm run build` | 生产环境构建 |
| `npm run start` | 启动生产服务器 |
| `npm run lint` | 运行 Biome 代码检查 |
| `npm run format` | 使用 Prettier 格式化 |

---

## 数据管道

排位赛数据通过基于 [FastF1](https://github.com/theOehrly/Fast-F1) 的 Python 管道从 F1 官方计时系统提取。

```bash
# 进入管道目录
cd pipeline

# 使用 uv 安装
uv sync

# 运行管道
uv run python -m f1pipeline.main
```

### 自动更新

GitHub Actions 工作流（`update-f1-data.yml`）**每周一 UTC 时间 06:00** 自动运行——通常在比赛周末结束之后。它会：

1. 通过 FastF1 获取最新排位赛数据
2. 计算队友差距、头对头战绩和 Q3 打入率
3. 将预计算的 JSON 输出到 `data/generated/2025/`
4. 自动提交变更到仓库

也支持通过 `workflow_dispatch` 手动触发。

---

## 系统架构

```
┌─────────────┐     ┌──────────────┐     ┌──────────────┐
│   FastF1    │────▶│  数据管道     │────▶│  JSON 数据    │
│  (F1 API)   │     │  (Python)    │     │  (静态文件)    │
└─────────────┘     └──────────────┘     └──────┬───────┘
                                                │
                    ┌───────────────────────────┘
                    ▼
┌──────────────────────────────────────────────────────┐
│                   Next.js 应用                        │
│                                                       │
│  ┌─────────┐   ┌──────────┐   ┌──────────────────┐  │
│  │ 网格阶段 │──▶│ 对决阶段  │──▶│    图表阶段       │  │
│  │  GRID   │   │ VERSUS   │   │    GRAPH         │  │
│  └─────────┘   └──────────┘   └──────────────────┘  │
│       │              │                │               │
│       ▼              ▼                ▼               │
│  车队转盘       对决模式          分析面板            │
│  3D 赛车模型   车手卡片          差距折线图           │
│  车队信息      中位差距          H2H / Q3 率         │
│               头对头战绩         逐站成绩             │
│                                                       │
│  ┌───────────────────────────────────────────────┐   │
│  │            Zustand 状态管理                     │   │
│  │  阶段 · 选中车队 · 相机模式 · 时间维度          │   │
│  └───────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────┘
```

---

## 贡献

欢迎贡献代码！无论是 Bug 修复、功能建议还是设计改进：

1. Fork 本仓库
2. 创建功能分支（`git checkout -b feature/amazing-feature`）
3. 提交你的修改
4. 推送到分支（`git push origin feature/amazing-feature`）
5. 创建 Pull Request

---

## 致谢

- **数据来源**：[FastF1](https://github.com/theOehrly/Fast-F1) — 开源 F1 数据库
- **播客**：[飞驰圈 Flying Lap Podcast](https://www.youtube.com/playlist?list=PL3g6oz4W-l1k0YrzaNaaGoI3MXwx96PoC) — 红黑榜车手评分
- **3D 模型**：F1 2025 赛车资产
- **车手肖像**：F1 官方媒体素材
- **设计灵感**：F1 转播画面、F1 TV 计时塔

---

## 许可证

本项目基于 [MIT License](LICENSE) 开源。

---

<div align="center">

**为 Formula 1 热情而生** · 作者 [Edward](https://github.com/zhongth)

粉丝作品，献给 [飞驰圈播客](https://www.youtube.com/playlist?list=PL3g6oz4W-l1k0YrzaNaaGoI3MXwx96PoC)

*F1、Formula 1 及相关标识为 Formula One Licensing BV 的商标。*

</div>
