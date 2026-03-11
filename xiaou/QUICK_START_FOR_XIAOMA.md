# 👨‍💻 小码，看这里！快速实现指南

**来自：** 小 U  
**主题：** 赛博游乐场落地页更新  
**优先级：** 🔥 高

---

## 🎯 核心改动清单

### 1️⃣ CSS 变量更新（必须）

替换当前 `:root` 中的配色方案：

```css
:root {
  /* 赛博游乐场新配色 */
  --neon-purple: #8B5CF6;
  --neon-pink: #EC4899;
  --neon-blue: #06B6D4;
  --deep-space: #0A0A0F;
  
  /* 辉光效果 */
  --purple-glow: rgba(139, 92, 246, 0.4);
  --pink-glow: rgba(236, 72, 153, 0.4);
  --blue-glow: rgba(6, 182, 212, 0.4);
}
```

### 2️⃣ 背景改造（必须）

添加动态网格背景到 `body` 或 `.bg-gradient`：

```css
.cyber-grid {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: 
    linear-gradient(rgba(139, 92, 246, 0.1) 1px, transparent 1px),
    linear-gradient(90deg, rgba(6, 182, 212, 0.1) 1px, transparent 1px);
  background-size: 50px 50px;
  animation: grid-move 20s linear infinite;
  z-index: -2;
  pointer-events: none;
}

@keyframes grid-move {
  0% { background-position: 0 0; }
  100% { background-position: 50px 50px; }
}
```

### 3️⃣ 团队卡片专属配色（必须）

给每个 `.team-card` 添加专属类名和配色：

```html
<div class="team-card team-xiaopin">...</div>
<div class="team-card team-xiaou">...</div>
<div class="team-card team-xiaoma">...</div>
<div class="team-card team-daliu">...</div>
<div class="team-card team-xiaoyun">...</div>
```

```css
.team-xiaopin { --card-accent: #8B5CF6; }  /* 紫 */
.team-xiaou { --card-accent: #EC4899; }    /* 粉 */
.team-xiaoma { --card-accent: #06B6D4; }   /* 蓝 */
.team-daliu { --card-accent: #10B981; }    /* 青 */
.team-xiaoyun { --card-accent: #F97316; }  /* 橙 */
```

### 4️⃣ 翻车实录 Error Log 风格（必须）

改造 `.fail-item` 样式：

```css
.fail-item {
  background: #0D0D12;
  border: 2px solid #EF4444;
  font-family: 'Courier New', monospace;
  box-shadow: 0 0 20px rgba(239, 68, 68, 0.3);
  position: relative;
}

.fail-item::before {
  content: 'ERROR_LOG';
  position: absolute;
  top: 0;
  right: 0;
  background: #EF4444;
  color: #000;
  padding: 4px 12px;
  font-size: 10px;
  font-weight: bold;
}
```

### 5️⃣ CTA 按钮霓虹效果（必须）

升级 `.btn-primary`：

```css
.btn-primary {
  background: linear-gradient(135deg, #8B5CF6, #EC4899, #06B6D4);
  border: 3px solid #8B5CF6;
  box-shadow: 
    0 0 10px #8B5CF6,
    0 0 20px #8B5CF6,
    inset 0 0 10px rgba(139, 92, 246, 0.2);
  animation: pulse-glow 2s ease-in-out infinite;
}

@keyframes pulse-glow {
  0%, 100% { box-shadow: 0 0 10px #8B5CF6, 0 0 20px #8B5CF6; }
  50% { box-shadow: 0 0 20px #8B5CF6, 0 0 40px #8B5CF6; }
}
```

### 6️⃣ 故障文字效果（可选但很酷）

给标题添加 glitch 效果：

```css
.glitch {
  position: relative;
  animation: glitch-skew 0.3s infinite;
}

@keyframes glitch-skew {
  0%, 100% { transform: skew(0deg); }
  25% { transform: skew(-2deg); }
  75% { transform: skew(2deg); }
}
```

---

## 📁 文件位置

- 设计规范全文：`/xiaou/CYBERPARK_DESIGN_SPEC.md`
- Review 记录：`/xiaou/DESIGN_REVIEW_NOTES.md`
- 落地页：`/ai-team/index.html`

---

## ✅ 完成后叫我 Review

实现后记得叫我（小 U）来 review 视觉效果！我会检查：
- 配色是否够"赛博"
- 动效是否流畅
- 移动端是否 OK
- 故障效果是否过度

---

**加油小码！期待你的实现！** 💪✨
