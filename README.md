# 🤖 AI 团队 - 你的智能协作小队

**创建时间**: 2026-03-03  
**位置**: `~/.openclaw/workspace/ai-team/`

---

## 团队成员

### 🎨 小 U (Xiao U) - UI 设计师

**专长**:
- UI/UX 设计
- 产品视觉设计
- 品牌设计
- 交互设计

**能力**:
- 风格独特且与产品融合
- 经验丰富且专业
- 各种应用设计（Web/iOS/Android/小程序）
- 设计系统搭建

**调用方式**:
```bash
# 设计需求
openclaw sessions_spawn --task "小 U，帮我设计一个..."
```

**工作目录**: `workspace/ai-team/xiaou/`

---

### 🎯 小品 (Xiao Pin) - 产品经理

**专长**:
- 产品规划 & 需求分析
- 用户调研 & 痛点挖掘
- 产品形态设计
- PRD 文档撰写

**能力**:
- 精准把握用户需求
- 设计符合用户习惯的产品
- 竞品功能对比分析
- 产品迭代规划

**调用方式**:
```bash
# 产品需求分析
openclaw sessions_spawn --task "小品，帮我设计一个..."
```

**工作目录**: `workspace/ai-team/xiaopin/`

---

### 👨‍💻 小码 (Xiao Ma) - 技术专家

**专长**:
- 全栈开发 (前端/后端/移动端)
- 运维部署 (Docker, K8s, CI/CD)
- 代码审查 & 重构
- 技术选型 & 架构设计

**技术栈**:
- 前端：React, Vue, Next.js, TypeScript
- 后端：Node.js, Python, Go, Rust
- 数据库：PostgreSQL, MySQL, MongoDB, Redis
- 运维：Docker, Kubernetes, AWS, Vercel

**调用方式**:
```bash
# 通过 OpenClaw spawn coding agent
openclaw sessions_spawn --runtime acp --task "小码，帮我做个..."
```

**工作目录**: `workspace/ai-team/xiaoma/`

---

### 📣 小云 (Xiao Yun) - 运营专家

**专长**:
- 创意策划 & 营销方案
- 社交媒体运营
- 用户增长策略
- 内容创作 & 文案

**能力**:
- 脑洞大开的推广点子
- 精准的用户洞察
- 多平台内容适配 (微信/微博/小红书/抖音)
- 活动策划 & 执行

**调用方式**:
```bash
# 通过 Research Agent + 创意 prompt
openclaw sessions_spawn --task "小云，帮我想个推广方案..."
```

**工作目录**: `workspace/ai-team/xiaoyun/`

---

### 📊 大六 (Da Liu) - 市场专家

**专长**:
- 市场调研 & 竞品分析
- 行业趋势判断
- 数据收集 & 整理
- 商业机会识别

**能力**:
- 快速搜集行业信息
- 竞品对比分析
- 市场规模估算
- 用户画像构建

**调用方式**:
```bash
# 通过 Research Agent + web_search
openclaw sessions_spawn --task "大六，帮我查一下..."
```

**工作目录**: `workspace/ai-team/daliu/`

---

## 如何使用

### 方式 1：直接对话

在飞书/微信/Telegram 里直接@我 + 角色名：

```
@OpenClaw 小码，帮我写个待办事项 App
@OpenClaw 小云，帮我想个产品推广方案
@OpenClaw 大六，帮我分析一下 AI 助手市场
```

### 方式 2：批量任务

一次性分配多个任务：

```
1. 小码：做个 landing page
2. 小云：写推广文案
3. 大六：找 10 个竞品分析
```

### 方式 3：协作项目

复杂项目可以三人协作：

```
项目：新产品上线
- 小码：开发产品
- 小云：准备推广材料
- 大六：市场调研 + 竞品分析
```

---

## 工作流程

```
用户提出需求
    ↓
主代理 (我) 分析任务
    ↓
分配给对应角色 (小码/小云/大六)
    ↓
子代理独立执行
    ↓
汇总结果 → 用户
```

---

## 注意事项

- ⚡ 子代理是按需 spawn，用完即销毁（节省资源）
- 📁 每个角色有独立工作目录，互不干扰
- 🔍 所有工作记录保存在 `workspace/ai-team/logs/`
- 💬 可以随时查看某个角色的工作历史

---

*团队由 OpenClaw 驱动，随时待命*
