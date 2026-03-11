# 🎮 赛博游乐场 - 设计规范 v1.0

**设计师：** 小 U  
**日期：** 2026-03-11  
**风格：** Cyberpunk Arcade / 霓虹赛博风

---

## 🎨 1. 核心配色方案

### 主色调 (Primary Palette)

```css
/* 霓虹紫 - 主色 */
--neon-purple: #8B5CF6;        /* RGB: 139, 92, 246 */
--neon-purple-glow: #A78BFA;    /* RGB: 167, 139, 250 - 发光效果 */
--neon-purple-dark: #7C3AED;    /* RGB: 124, 58, 237 - 深色变体 */

/* 荧光粉 - 强调色 */
--neon-pink: #EC4899;           /* RGB: 236, 72, 153 */
--neon-pink-glow: #F472B6;      /* RGB: 244, 114, 182 - 发光效果 */
--neon-pink-hot: #FF1493;       /* RGB: 255, 20, 147 - 深粉红 */

/* 电光蓝 - 辅助色 */
--neon-blue: #06B6D4;           /* RGB: 6, 182, 212 */
--neon-blue-glow: #22D3EE;      /* RGB: 34, 211, 238 - 发光效果 */
--neon-blue-dark: #0891B2;      /* RGB: 8, 145, 178 - 深色变体 */
```

### 辅助色 (Secondary Palette)

```css
/* 赛博青 - 成功/完成状态 */
--cyber-cyan: #10B981;          /* RGB: 16, 185, 129 */

/* 警告橙 - 注意状态 */
--arcade-orange: #F97316;       /* RGB: 249, 115, 22 */

/* 错误红 - 翻车/错误状态 */
--glitch-red: #EF4444;          /* RGB: 239, 68, 68 */
```

### 背景色 (Background)

```css
/* 深空黑 - 主背景 */
--deep-space: #0A0A0F;          /* RGB: 10, 10, 15 */
--void-dark: #050508;           /* RGB: 5, 5, 8 - 更深 */

/* 半透明层 */
--glass-purple: rgba(139, 92, 246, 0.1);
--glass-pink: rgba(236, 72, 153, 0.1);
--glass-blue: rgba(6, 182, 212, 0.1);
```

### 渐变方案 (Gradients)

```css
/* 霓虹彩虹 - 主渐变 */
--neon-rainbow: linear-gradient(
  135deg, 
  #8B5CF6 0%, 
  #EC4899 50%, 
  #06B6D4 100%
);

/* 赛博辉光 */
--cyber-glow: linear-gradient(
  135deg,
  rgba(139, 92, 246, 0.6) 0%,
  rgba(236, 72, 153, 0.6) 100%
);

/* 电光脉冲 */
--electric-pulse: linear-gradient(
  90deg,
  #06B6D4 0%,
  #8B5CF6 50%,
  #EC4899 100%
);
```

---

## 🎭 2. 故障艺术效果 (Glitch Art)

### CSS Glitch 动画

```css
@keyframes glitch {
  0% {
    transform: translate(0);
    clip-path: inset(0 0 0 0);
  }
  20% {
    transform: translate(-2px, 2px);
    clip-path: inset(20% 0 60% 0);
  }
  40% {
    transform: translate(2px, -2px);
    clip-path: inset(60% 0 20% 0);
  }
  60% {
    transform: translate(-2px, -2px);
    clip-path: inset(40% 0 40% 0);
  }
  80% {
    transform: translate(2px, 2px);
    clip-path: inset(80% 0 10% 0);
  }
  100% {
    transform: translate(0);
    clip-path: inset(0 0 0 0);
  }
}

@keyframes glitch-skew {
  0% { transform: skew(0deg); }
  20% { transform: skew(-2deg); }
  40% { transform: skew(2deg); }
  60% { transform: skew(-1deg); }
  80% { transform: skew(1deg); }
  100% { transform: skew(0deg); }
}

/* 应用示例 */
.glitch-text {
  position: relative;
  animation: glitch-skew 0.3s infinite;
}

.glitch-text::before,
.glitch-text::after {
  content: attr(data-text);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.glitch-text::before {
  animation: glitch 0.3s infinite;
  color: #06B6D4;
  z-index: -1;
  opacity: 0.7;
}

.glitch-text::after {
  animation: glitch 0.3s infinite reverse;
  color: #EC4899;
  z-index: -2;
  opacity: 0.7;
}
```

### RGB 分离效果

```css
.rgb-split {
  position: relative;
  display: inline-block;
}

.rgb-split::before {
  content: attr(data-text);
  position: absolute;
  left: 2px;
  text-shadow: -1px 0 #FF00C1;
  top: 0;
  color: white;
  background: var(--deep-space);
  overflow: hidden;
  clip: rect(0, 900px, 0, 0);
  animation: noise-anim 2s infinite linear alternate-reverse;
}

@keyframes noise-anim {
  0% { clip: rect(12px, 9999px, 56px, 0); }
  5% { clip: rect(89px, 9999px, 12px, 0); }
  10% { clip: rect(34px, 9999px, 78px, 0); }
  /* ... 更多关键帧 */
  100% { clip: rect(67px, 9999px, 23px, 0); }
}
```

---

## 📐 3. 动态网格背景

### CSS 网格动画

```css
.cyber-grid {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: 
    linear-gradient(
      rgba(139, 92, 246, 0.1) 1px, 
      transparent 1px
    ),
    linear-gradient(
      90deg, 
      rgba(6, 182, 212, 0.1) 1px, 
      transparent 1px
    );
  background-size: 50px 50px;
  background-position: center center;
  animation: grid-move 20s linear infinite;
  perspective: 500px;
  transform-style: preserve-3d;
  z-index: -2;
}

@keyframes grid-move {
  0% {
    background-position: 0 0;
    transform: perspective(500px) rotateX(60deg) translateY(0);
  }
  100% {
    background-position: 0 50px;
    transform: perspective(500px) rotateX(60deg) translateY(50px);
  }
}

/* 扫描线效果 */
.scanlines {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: repeating-linear-gradient(
    0deg,
    rgba(0, 0, 0, 0.15),
    rgba(0, 0, 0, 0.15) 1px,
    transparent 1px,
    transparent 2px
  );
  pointer-events: none;
  z-index: 9999;
  animation: scanline-move 8s linear infinite;
}

@keyframes scanline-move {
  0% {
    background-position: 0 0;
  }
  100% {
    background-position: 0 100vh;
  }
}
```

---

## 👾 4. 像素风图标风格

### 像素字体推荐

```css
/* Google Fonts */
@import url('https://fonts.googleapis.com/css2?family=Press+Start+2P&display=swap');
@import url('https://fonts.googleapis.com/css2?family=VT323&display=swap');

.pixel-title {
  font-family: 'Press Start 2P', cursive;
  font-size: 24px;
  line-height: 1.5;
}

.pixel-body {
  font-family: 'VT323', monospace;
  font-size: 20px;
}
```

### 像素边框

```css
.pixel-border {
  position: relative;
  background: var(--deep-space);
  image-rendering: pixelated;
}

.pixel-border::before {
  content: '';
  position: absolute;
  top: -4px;
  left: -4px;
  right: -4px;
  bottom: -4px;
  background: 
    linear-gradient(90deg, var(--neon-purple) 4px, transparent 4px) 0 0,
    linear-gradient(90deg, var(--neon-purple) 4px, transparent 4px) 0 100%,
    linear-gradient(0deg, var(--neon-purple) 4px, transparent 4px) 0 0,
    linear-gradient(0deg, var(--neon-purple) 4px, transparent 4px) 100% 0;
  background-size: 100% 4px, 100% 4px, 4px 100%, 4px 100%;
  background-repeat: no-repeat;
  pointer-events: none;
}
```

---

## 🎴 5. 团队成员卡片专属视觉

### 卡片配色方案

```css
/* 小品 - 紫色系 */
.team-xiaopin {
  --card-accent: #8B5CF6;
  --card-glow: rgba(139, 92, 246, 0.4);
  --card-icon: 🎯;
}

/* 小 U - 粉色系 */
.team-xiaou {
  --card-accent: #EC4899;
  --card-glow: rgba(236, 72, 153, 0.4);
  --card-icon: 🎨;
}

/* 小码 - 蓝色系 */
.team-xiaoma {
  --card-accent: #06B6D4;
  --card-glow: rgba(6, 182, 212, 0.4);
  --card-icon: 👨‍💻;
}

/* 大六 - 青色系 */
.team-daliu {
  --card-accent: #10B981;
  --card-glow: rgba(16, 185, 129, 0.4);
  --card-icon: 📊;
}

/* 小云 - 橙色系 */
.team-xiaoyun {
  --card-accent: #F97316;
  --card-glow: rgba(249, 115, 22, 0.4);
  --card-icon: 📣;
}
```

### 卡片悬停效果

```css
.team-card {
  position: relative;
  overflow: hidden;
  transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.team-card::after {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: conic-gradient(
    from 0deg,
    transparent,
    var(--card-accent),
    transparent
  );
  animation: rotate-border 3s linear infinite;
  opacity: 0;
  transition: opacity 0.4s ease;
}

.team-card:hover::after {
  opacity: 0.3;
}

@keyframes rotate-border {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

.team-card:hover {
  transform: translateY(-12px) scale(1.02);
  box-shadow: 
    0 0 30px var(--card-glow),
    0 0 60px var(--card-glow),
    inset 0 0 20px var(--card-glow);
}
```

---

## 📜 6. 翻车实录 Error Log 风格

### Terminal 风格容器

```css
.error-log {
  background: #0D0D12;
  border: 2px solid #EF4444;
  border-radius: 8px;
  padding: 20px;
  font-family: 'VT323', 'Courier New', monospace;
  font-size: 14px;
  line-height: 1.8;
  box-shadow: 
    0 0 20px rgba(239, 68, 68, 0.3),
    inset 0 0 10px rgba(239, 68, 68, 0.1);
  position: relative;
  overflow: hidden;
}

.error-log::before {
  content: 'ERROR_LOG_v1.0';
  position: absolute;
  top: 0;
  right: 0;
  background: #EF4444;
  color: #000;
  padding: 4px 12px;
  font-size: 10px;
  font-weight: bold;
}

.error-line {
  display: flex;
  gap: 12px;
  margin-bottom: 8px;
}

.error-timestamp {
  color: #64748B;
  white-space: nowrap;
}

.error-type {
  color: #EF4444;
  font-weight: bold;
  min-width: 80px;
}

.error-message {
  color: #F472B6;
}

.error-code {
  color: #06B6D4;
  font-family: monospace;
  background: rgba(6, 182, 212, 0.1);
  padding: 2px 6px;
  border-radius: 4px;
}

/* 闪烁光标 */
@keyframes blink {
  0%, 100% { opacity: 1; }
  50% { opacity: 0; }
}

.cursor-blink::after {
  content: '_';
  animation: blink 1s step-end infinite;
  color: #10B981;
}
```

---

## 🎯 7. 可交互 CTA 按钮动画

### 霓虹按钮

```css
.btn-neon {
  position: relative;
  padding: 16px 40px;
  font-size: 16px;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 2px;
  color: #fff;
  background: transparent;
  border: 3px solid var(--neon-purple);
  border-radius: 8px;
  cursor: pointer;
  overflow: hidden;
  transition: all 0.3s ease;
  box-shadow: 
    0 0 10px var(--neon-purple),
    0 0 20px var(--neon-purple),
    inset 0 0 10px rgba(139, 92, 246, 0.2);
}

.btn-neon::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    90deg,
    transparent,
    rgba(139, 92, 246, 0.8),
    transparent
  );
  transition: left 0.5s ease;
}

.btn-neon:hover::before {
  left: 100%;
}

.btn-neon:hover {
  background: var(--neon-purple);
  box-shadow: 
    0 0 20px var(--neon-purple),
    0 0 40px var(--neon-purple),
    0 0 60px var(--neon-purple),
    inset 0 0 20px rgba(139, 92, 246, 0.4);
  transform: translateY(-4px) scale(1.05);
}

.btn-neon:active {
  transform: translateY(-2px) scale(1.02);
}

/* 粉色变体 */
.btn-neon.pink {
  border-color: var(--neon-pink);
  box-shadow: 
    0 0 10px var(--neon-pink),
    0 0 20px var(--neon-pink),
    inset 0 0 10px rgba(236, 72, 153, 0.2);
}

.btn-neon.pink:hover {
  background: var(--neon-pink);
  box-shadow: 
    0 0 20px var(--neon-pink),
    0 0 40px var(--neon-pink),
    0 0 60px var(--neon-pink),
    inset 0 0 20px rgba(236, 72, 153, 0.4);
}

/* 蓝色变体 */
.btn-neon.blue {
  border-color: var(--neon-blue);
  box-shadow: 
    0 0 10px var(--neon-blue),
    0 0 20px var(--neon-blue),
    inset 0 0 10px rgba(6, 182, 212, 0.2);
}

.btn-neon.blue:hover {
  background: var(--neon-blue);
  box-shadow: 
    0 0 20px var(--neon-blue),
    0 0 40px var(--neon-blue),
    0 0 60px var(--neon-blue),
    inset 0 0 20px rgba(6, 182, 212, 0.4);
}
```

### 脉冲动画按钮

```css
.btn-pulse {
  animation: pulse-glow 2s ease-in-out infinite;
}

@keyframes pulse-glow {
  0%, 100% {
    box-shadow: 
      0 0 10px var(--neon-purple),
      0 0 20px var(--neon-purple),
      0 0 30px var(--neon-purple);
  }
  50% {
    box-shadow: 
      0 0 20px var(--neon-purple),
      0 0 40px var(--neon-purple),
      0 0 60px var(--neon-purple);
  }
}
```

---

## 🎬 8. 额外动效参考

### 浮动粒子

```css
.particle {
  position: absolute;
  width: 4px;
  height: 4px;
  background: var(--neon-purple);
  border-radius: 50%;
  box-shadow: 0 0 10px var(--neon-purple);
  animation: float-particle 15s linear infinite;
}

@keyframes float-particle {
  0% {
    transform: translateY(100vh) scale(0);
    opacity: 0;
  }
  10% {
    opacity: 1;
  }
  90% {
    opacity: 1;
  }
  100% {
    transform: translateY(-100vh) scale(1);
    opacity: 0;
  }
}
```

### 文字打字机效果

```css
@keyframes typing {
  from { width: 0; }
  to { width: 100%; }
}

@keyframes blink-cursor {
  50% { border-color: transparent; }
}

.typewriter {
  overflow: hidden;
  border-right: 2px solid var(--neon-blue);
  white-space: nowrap;
  animation: 
    typing 3.5s steps(40, end),
    blink-cursor 0.75s step-end infinite;
}
```

---

## 📱 9. 响应式断点

```css
/* 移动端优先 */
@media (max-width: 768px) {
  .cyber-grid {
    background-size: 30px 30px;
  }
  
  .team-grid {
    grid-template-columns: 1fr;
  }
  
  .btn-neon {
    padding: 14px 28px;
    font-size: 14px;
  }
}

/* 平板 */
@media (min-width: 769px) and (max-width: 1024px) {
  .team-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* 桌面 */
@media (min-width: 1025px) {
  .team-grid {
    grid-template-columns: repeat(5, 1fr);
  }
}
```

---

## 🎯 10. 实现优先级

### Phase 1 - 核心视觉 (高优先级)
- [ ] 更新配色方案到 CSS 变量
- [ ] 实现动态网格背景
- [ ] 添加霓虹按钮动画
- [ ] 团队成员卡片专属配色

### Phase 2 - 特效增强 (中优先级)
- [ ] 故障艺术文字效果
- [ ] 扫描线覆盖层
- [ ] Error Log 风格翻车实录
- [ ] 浮动粒子背景

### Phase 3 - 细节打磨 (低优先级)
- [ ] 像素字体集成
- [ ] 打字机效果
- [ ] RGB 分离效果
- [ ] 更多微交互

---

## 💡 灵感参考

- **Tron: Legacy** - 霓虹网格美学
- **Cyberpunk 2077** - 故障艺术和 UI
- **Blade Runner 2049** - 赛博朋克氛围
- **Ready Player One** - 游乐场/街机元素
- **Stranger Things** - 80 年代霓虹风格

---

**小码，按这个规范来实现！有问题随时找我~** 🎨✨
