---
name: final-review-notes
description: 期末复习文档创建和审查过程中的发现与修正
metadata:
  type: project
---

## 2026-06-02 — Final 期末复习文档创建与审查

### 产出文件

- `Final/课程总结.md`：22 节详版课程笔记，涵盖从 Laplace 方法到 Van der Pol 方程的全部内容
- `CLAUDE.md`：项目说明文件（由 `/init` 生成）
- `.claude/rules/`：项目规则目录

### PDF 提取方法

用 `pdftotext -layout` 提取扫描笔记 PDF，注意编码警告 "Unknown character collection 'Adobe-GB1'" 不影响文本提取。

### 审查中发现的 5 处错误（已修正）

1. **§4.3 $n=0$ 的 $P(x)$**：应为 $P(x)=x$（$1/x^{-1}=x$），非 $1/x$
2. **§6.4 负根展开**：$\epsilon^1$ 系数应为 $+\epsilon$，非 $-2\epsilon$
3. **§20.2 $\cos 3\tau$ 符号**：中间行应为 $-\frac{1}{4}\cos 3\tau$
4. **§21.2 实部/虚部归属**：$R'=0$ 来自虚部，$\theta'=3R_0^2/2$ 来自实部
5. **§10.3 内层 ODE 中间式**：多余了 $\delta^2$ 分母和重复的 $X$

### 审查中发现的 4 处不精确（已修正）

1. Riemann-Lebesgue：$O(1/x)$ 需 $C^1$ 条件，仅可积只能 $o(1)$
2. Airy 主导平衡中 $S'$ 求导符号
3. "丢弃 Bi"需加"有界性要求"前提
4. S-L 理论不需要 $q\leq 0$ 约束

**How to apply**：后续修改文档时注意上述精度标准；审查数学文档时应独立验证公式而非盲信源文件。

## 2026-06-05 — 脉络图 OCR 提取与结构化整理

### 产出文件

- `Final/脉络图整理.md`：从同学手绘脉络图 OCR 提取文字后整理的结构化文档

### 脉络图核心发现

图按 **"失效类型"** 组织 ODE 摄动方法，形成三条纵向逻辑链：

```
超越小量 e^{-1/ε}（全局源头）
    ↓
Laplace / 分部积分 / 稳定相
    ↓
Dominant Balance + Rescaling（通用前置）
    ↓
┌───────────────┬───────────────┬────────────────┐
│ Boundary Layer │ WKB 方法      │ Multiple Scale │
│ (空间局部失效) │ (全局坍塌)     │ (长时间失效)    │
└───────────────┴───────────────┴────────────────┘
    ↓
Normal Form → 一维分岔（S-N / Transcritical / Pitchfork）
```

五大部分：渐近理论根基 → 积分渐近 → ODE 奇异摄动三部曲 → 动力系统分岔 → 一维分岔标准四步

图中注释的实用技巧：分部积分是"无驻点情形"的标准对策，也是从积分渐近过渡到边界层分析的关键桥梁。

### 图像 OCR 技术经验

- **EasyOCR**：无需 tesseract 二进制，直接 `pip install easyocr`，支持中英文混合，首次运行需下载检测模型（~100MB）
- **Windows 中文路径**：Python 传给 EasyOCR 的中文文件名会因编码问题导致 `cv2.imread` 返回 None → 用 `cp 中文名.png ascii名.png` 规避
- **Claude 环境不支持 PNG 渲染**时，可通过像素密度热力图 + ASCII 映射获取布局概貌，再对关键区域 OCR
- **OCR 后处理**：EasyOCR 对数学符号（$e^{-1/\epsilon}$、$\phi'(t)=0$ 等）识别有损，需结合课程知识修正

**How to apply**：复习时按"失效类型"串联三大部分（边界层/WKB/多尺度），而非按章节死记；处理含中文文件名的图像时优先复制为 ASCII 文件名。

## 2026-06-05（续）— 课程总结按脉络图框架 + 老师考点标注全面优化

### 产出文件

- `Final/课程总结.md`：经脉络图框架重组 + 老师考点标注（🔥+⭐）+ 考试提示框 + 2 个补充知识
- `Final/期末考提示_transcript.txt`：老师复习课录音转文字
- `Final/要求内容.txt`：同学整理的考点清单

### 课程总结文档改动汇总

1. **顶部新增考试信息栏**：~7-8 题、cheat sheet A4 正反面、公式会给、步骤分 > 计算分、英文答卷
2. **脉络总览**：ASCII 逻辑链图 + 五部分映射表 + 阅读顺序提示
3. **目录按脉络图五部分重组**，每节标注 🔥/⭐
4. **22 节全部使用显式锚点** `<a id="sec-N">`，跨渲染器可跳转
5. **五个分部引言含考试重点提示框**，覆盖全部 6 条考试线路
6. **补充 1：Rayleigh-Lorentz 振子**（能量不守恒 + adiabatic invariant）
7. **补充 2：离散化 Discretization**（差分格式 + 三类应用）
8. **总结重写**：按"三种失效 → 三种方法"框架组织

### 老师口述关键考点（来自 transcript，已融入课程总结）

- **非标准渐近展开**：$\sqrt{25+x}$ 展为 $\{1,\cos x,\sin x,\sin^2 x\}$，按定义逐项求系数
- **Laplace 四步**：缩上限 → 延展 ±∞ → Taylor → 高斯终结
- **Characteristic equation**：常系数线性 ODE 的求解基础（边界层的前置技能）
- **Boundary Layer 五条要求**：基本假设、matching 定系数、自己判位置、dominant balance 定厚度（$\delta=\epsilon^\gamma$）、五步流程
- **WKB 逻辑链**：会推 → turning point → 不 work → **回到 boundary layer** → inner layer → 确定 thickness $\epsilon^{2/3}$
- **分岔考试路径**：在 rescaled 方程上 → identify bifurcation parameter → 画 bifurcation diagram → 识别类型（含 imperfect pitchfork）
- **Two-timing 够用**：$t$ 和 $\epsilon t$ 掌握就基本掌握了多尺度，不需更复杂

### 文档锚点修复经验

- Markdown 自动生成的锚点（`#1-拉普拉斯方法-laplaces-method`）在不同渲染器中行为不一致（中文编码、括号处理）
- **可靠性方案**：用显式 `<a id="sec-N"></a>` + `[text](#sec-N)`，简单位置无关

**How to apply**：考前按 transcript 中老师口述的考点逐条自检；非标准序列展开和 WKB→boundary layer 回退是老师特别强调的可能失分点。
