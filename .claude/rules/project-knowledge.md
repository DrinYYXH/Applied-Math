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
