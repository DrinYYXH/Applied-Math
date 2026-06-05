# 高等应用数学 · 个人学习仓库

2026 春季 | 授课：MengFei He | 计算环境：Wolfram Mathematica 14.3

---

## 目录结构

```
.
├── HW1/                    # 第一次作业：函数展开与反函数级数
│   ├── HW1.pdf             #   - 题目
│   ├── hw1_12532299.pdf    #   - 提交答案
│   └── hw1_*.nb            #   - Mathematica 计算笔记本
├── HW2/                    # 第二次作业：ODE 边界层分析、匹配渐近展开
│   ├── HW2.pdf
│   └── hw2_*.nb
├── Final/                  # 期末复习资料
│   ├── 课程总结.md          #   - 22 节详版课堂笔记 ★
│   ├── 脉络图整理.md        #   - 课程逻辑脉络（同学手绘 + OCR 结构化） ★
│   ├── Title.txt            #   - 自编课程大纲
│   └── notes_text.txt       #   - 课堂笔记 PDF 文本提取
├── 脉络图.png               # 脉络图原始图片
├── CLAUDE.md               # 项目说明（供 Claude Code 使用）
└── README.md
```

## 核心文档

| 文件 | 说明 |
|------|------|
| **[Final/课程总结.md](Final/课程总结.md)** | 22 节完整课程笔记，从 Laplace 方法到 Van der Pol 方程，带 ★/▲ 重要度标记 |
| **[Final/脉络图整理.md](Final/脉络图整理.md)** | 课程逻辑脉络——按 **"三种失效 → 三种方法"** 串联全部内容 |

## 课程主题

### 积分的渐近方法
Laplace 方法 · 渐近展开与超越小量 · 稳定相方法 · Stirling 公式 · Riemann-Lebesgue 引理

### ODE 的摄动分析
正则摄动 · 奇异摄动 · 主导平衡 · 边界层理论（匹配渐近展开 MAE） · 内层/角层 · WKB 方法 · 转折点与 Airy 函数 · Bohr-Sommerfeld 量子化 · Schrödinger 方程 · Liouville-Green 变换

### 动力系统与非线性振子
分岔理论（鞍结/跨临界/叉形/Hopf） · 规范型 · 极限环 · Duffing 振子 · Poincaré-Lindstedt 方法 · 多尺度分析 · Van der Pol 方程 · Mathieu 方程

### 核心逻辑链（来自脉络图）

```
超越小量 e^{-1/ε}（全局逻辑源头）
         ↓
Laplace / 分部积分 / 稳定相
         ↓
Dominant Balance + Rescaling
         ↓
┌────────────┬────────────┬────────────┐
│ Boundary   │   WKB      │ Multiple   │
│ Layer      │   方法      │ Scale      │
│ (空间失效) │ (全局失效)  │ (长时失效)  │
└────────────┴────────────┴────────────┘
         ↓
   Normal Form → Bifurcation
```

## 工具链

- **Mathematica 14.3** — 所有符号计算与数值验证（`.nb` 文件）
- **Git + GitHub** — 版本管理与跨设备同步
- **Claude Code** — AI 辅助整理笔记、审查公式

---

*Last updated: 2026-06-05*
