# Advanced Applied Mathematics — Detailed Lecture Notes

> Based on lecture notes PDF + self-compiled outline (Title.txt) | Spring 2026 | Instructor: MengFei He
>
> Notation: **🔥 High probability exam topic** | **⭐ Must master** (emphasized in review session)
>
>
> ### Exam Information (from instructor's oral remarks)
> - **Format**: ~7–8 problems, each with guiding sub-problems, graded strictly by steps
> - **Cheat Sheet**: 1 A4 sheet (double-sided), handwritten with any content you find helpful
> - **Formulas**: Required formulas will be provided directly in the exam
> - **Grading emphasis**: Mathematical understanding > Computational skill. An unsolved integral costs only the last 1–2 points; the key is explaining steps, physical meaning, fundamental assumptions, and advantages/disadvantages of methods. Basic integration ability is sufficient
> - **Language**: Answer in English; ask the instructor if unsure
> - **Coverage**: Asymptotic Expansion → Laplace/Stationary Phase → Rescaling+Bifurcation → Boundary Layer → WKB → Multiple Scale → Discretization

---

## Context Overview: Five Parts + Three Logic Chains

> The course is organized around **"Three Types of Failure → Three Methods"**, spanning from asymptotic integrals to dynamical systems bifurcation.

```
                    Transcendentally Small Term e^{-1/ε} (Global Logical Origin)
                              │
              ┌───────────────┼───────────────┐
              ▼               ▼               ▼
         Laplace Method   Integration by Parts   Stationary Phase
        (Real exponential   (No stationary       (Imaginary exponential
            spike)           point strategy)         oscillation)
              │               │               │
              └───────────────┼───────────────┘
                              ▼
                  Dominant Balance + Rescaling
                     (Universal Foundation)
                              │
          ┌───────────────────┼───────────────────┐
          ▼                   ▼                   ▼
   ① Boundary Layer      ② WKB Method        ③ Multiple Scale
   (Spatial local         (Global collapse)    (Long-time
    breakdown)                                      breakdown)
          │                   │                   │
          └───────────────────┼───────────────────┘
                              ▼
                        Normal Form
                         (Normal Form)
                              ▼
                        Bifurcation
                    S-N / TC / Pitchfork
```

| Part | Context Map Theme | Corresponding Sections | Core Question |
|------|-------------------|------------------------|---------------|
| **I** | Asymptotic Theory Foundations | §1–§3 | Asymptotic sequences → Asymptotic expansions → Transcendentally small terms (global logical origin) |
| **II** | Universal Foundation | §4–§5 | ODE singularity classification + Dominant Balance (bridge from integrals to ODEs) |
| **III-①** | Singular Perturbation · Boundary Layer | §6–§11 | Spatial local breakdown → Stretching transformation + MAE matching |
| **III-②** | WKB Method | §12–§14 | Global collapse → Ansatz + Airy connection + Quantization |
| **IV** | Dynamical Systems & Bifurcation | §15–§17 | Qualitative behavior of solutions: fixed points → stability → bifurcation panorama |
| **III-③** | Multiple Scale Analysis | §18–§22 | Long-time breakdown → Elimination of secular terms → Amplitude equation → Limit cycle |

> **Reading tip**: §15–§17 (Bifurcation) and §18–§22 (Multiple Scale) can be read in either order. In the context map, Multiple Scale comes before Bifurcation (as the endpoint of qualitative analysis); in the lecture notes, Bifurcation comes first (to lay groundwork for understanding the bifurcation structure of the Van der Pol amplitude equation). Both paths converge at the limit cycle.

---

## Table of Contents

### Part I: Asymptotic Theory Foundations — Global Logical Starting Point
1. [Laplace's Method](#sec-1) 🔥 ⭐
2. [Asymptotic Expansion](#sec-2) 🔥 ⭐
3. [Method of Stationary Phase](#sec-3) 🔥 ⭐

### Part II: Universal Foundation — Bridge from Integrals to ODEs
4. [Local Analysis of ODEs](#sec-4) ⭐
5. [Dominant Balance](#sec-5) 🔥 ⭐

### Part III-①: Singular Perturbation · Boundary Layer — Spatial Local Breakdown
6. [Perturbation Methods · Algebraic Equations](#sec-6)
7. [Perturbation Methods · ODEs](#sec-7)
8. [Singular Perturbation & Matched Asymptotic Expansion](#sec-8) 🔥 ⭐
9. [Boundary Layer Location & Thickness](#sec-9) 🔥
10. [Interior / Corner Layer](#sec-10)
11. [Boundary Layer in Nonlinear Systems](#sec-11)

### Part III-②: WKB Method — Global Collapse
12. [WKB Method](#sec-12) 🔥 ⭐
13. [Eigenvalue Problems](#sec-13) 🔥
14. [Schrödinger Equation & Double Turning Points](#sec-14)

### Part IV: Dynamical Systems & Bifurcation — Paradigm Shift to Qualitative Analysis
15. [Dynamical Systems & Bifurcation](#sec-15) 🔥 ⭐
16. [2D Systems & Limit Cycles](#sec-16)
17. [Fixed Point Dynamics & Hysteresis](#sec-17) ⭐

### Part III-③: Multiple Scale Analysis — Long-Time Evolution Breakdown
18. [Forced Harmonic Oscillator](#sec-18)
19. [Nonlinear Spring & Duffing Oscillator](#sec-19) ⭐
20. [Poincaré-Lindstedt Method](#sec-20) ⭐
21. [Multiple Scale Analysis](#sec-21) 🔥 ⭐
22. [Van der Pol Equation](#sec-22) ⭐

### Supplementary Knowledge (instructor requires familiarity)
- [Supplement 1: Rayleigh-Lorentz Oscillator](#supplement-1-rayleigh-lorentz-oscillator) ⭐
- [Supplement 2: Discretization](#supplement-2-discretization) ⭐

---

---

# Part I: Asymptotic Theory Foundations — Global Logical Starting Point

> Three-layer foundation: Asymptotic sequences (legitimacy) → Asymptotic expansions (remainder control) → Transcendentally small terms (global origin)
> Core logic chain: Exponential amplification → Compress interval → Peak dominance → Taylor approximation → Gaussian integral finale
>
> ### 🔥 Exam Focus (instructor's emphasis)
> **Laplace standard operating procedure** (instructor's oral description): ① First shrink the integration upper limit (determine the maximum point $t_c$ of $\phi(t)$, compress to a small neighborhood of $t_c$) → ② Extend integration limits to $\pm\infty$ (tails are exponentially small, negligible) → ③ Local Taylor expansion at the stationary point → ④ Gaussian integral termination.
> **Laplace + Stationary Phase = a two-step method**: ① Determine stationary point $\phi'(t_c)=0$ → ② Local expansion at stationary point + Gaussian integral termination. Both methods share the same technical chain, differing only in real exponential (spike) vs imaginary exponential (oscillatory cancellation). Cases without stationary points are handled by **integration by parts**. Classic examples: Gamma → Stirling, Bessel $J_0(x)$ large-$x$ asymptotics. Required integral formulas will be provided in the exam.
> ### ⭐ Required Mastery
> Definition of asymptotic sequences · Poincaré definition of asymptotic expansions with remainder control · **Non-standard sequence expansion** (given $\{\phi_n\}$, compute coefficients term by term from the definition, e.g., expand $\sqrt{25+x}$ in $\{1,\cos x,\sin x,\sin^2 x\}$) · Properties and consequences of transcendentally small terms $e^{-1/\epsilon}$

<a id="sec-1"></a>
## 1. Laplace's Method 🔥

### 1.1 Problem Form

Consider the integral (as $x \to \infty$):

$$I(x) = \int_a^b f(t)\, e^{x\phi(t)} dt$$

### 1.2 Core Intuition

As $x \to \infty$, $e^{x\phi(t)}$ forms an **infinitely sharp peak** at the point $t_c \in (a,b)$ where $\phi(t)$ attains its **maximum**. The peak width $\sim 1/\sqrt{x}$, and only a small neighborhood around $t_c$ contributes to the integral. Contributions from the tails (regions far from $t_c$) are **exponentially small** and negligible.

### 1.3 Example 1: Gaussian Integral (Rough Estimate)

$$I = \int_{-\infty}^{\infty} e^{-xt^2} dt$$

- The integrand has a sharp peak at $t=0$, width $\sim 1/\sqrt{x}$, height $=1$
- Rough estimate: $I \sim O(1/\sqrt{x})$
- **Exact value**: $I = \sqrt{\pi/x}$
- **Tail verification**: $\int_{10}^{\infty} e^{-xt^2} dt < \int_{10}^{\infty} e^{-10xt} dt = \frac{e^{-100x}}{10x} \ll O(1/\sqrt{x})$, negligible

### 1.4 Example 2: $\int_{-\infty}^{\infty} e^{-x\cosh t} dt$

- $\cosh t = (e^t + e^{-t})/2$, attains minimum $1$ at $t=0$ (so $-\cosh t$ attains maximum $-1$)
- Expand at $t=0$: $\cosh t = 1 + t^2/2! + t^4/4! + \cdots$
- **Only keep up to $t^2$** is sufficient (higher-order terms $\times$ exponential decay → negligible)
- Approximation: $I(x) \approx \int_{-\infty}^{\infty} e^{-x(1 + t^2/2)} dt = \sqrt{\frac{2\pi}{x}} e^{-x}$
- For higher-order corrections, substitute $\cosh t = 1 + 2\sigma^2$, transforming the integral into a family of Gaussian integrals, yielding the **complete asymptotic series**:
  $$I(x) \sim \sqrt{\frac{2\pi}{x}} e^{-x} \left(1 - \frac{1}{8x} + \frac{9}{128x^2} + \cdots\right)$$

> **Key note**: No matter how "wrong" the $O(\sigma^4)$ terms are, they are all multiplied by the exponentially small $e^{-x\sigma^2}$.

### 1.5 Example 3: Gamma Function and Stirling's Formula

**Gamma function definition**:

$$\Gamma(x+1) = \int_0^{\infty} t^x e^{-t} dt$$

- For integer $n$: $\Gamma(n+1) = n!$
- No simple closed form — a classic example of "functions represented by integrals"
- Other examples: Error function $\text{erf}(x) = \frac{2}{\sqrt{\pi}}\int_0^x e^{-t^2}dt$, Bessel function $J_0(x) = \frac{1}{\pi}\int_0^\pi \cos(x\sin t)dt$

**Finding asymptotics via Laplace's method**:

1. Rewrite in Laplace form: $\Gamma(x+1) = \int_0^{\infty} e^{x\ln t - t} dt$ ($\phi(t) = \ln t - t/x$, or more naturally written as $\int_0^{\infty} e^{x\ln t - t} dt$)
2. Differentiate the exponent to find critical point: $\frac{d}{dt}(x\ln t - t) = \frac{x}{t} - 1 = 0 \Rightarrow t_c = x$
3. Substitute $t = x\tau$, $dt = x d\tau$: $\Gamma(x+1) = x^{x+1} e^{-x} \int_0^{\infty} e^{x(\ln\tau - \tau)} d\tau$
4. Expand at $\tau=1$: $\ln\tau - \tau = -1 - \frac{(\tau-1)^2}{2} + \frac{(\tau-1)^3}{3} - \cdots$
5. Keep to Gaussian term: $\Gamma(x+1) \sim x^{x+1} e^{-x} \sqrt{\frac{2\pi}{x}}$

**Stirling's Formula**:

$$n! \sim n^n e^{-n} \sqrt{2\pi n}, \qquad \ln n! = n\ln n - n + O(\ln n)$$

---

<a id="sec-2"></a>
## 2. Asymptotic Expansion 🔥

### 2.1 Three Core Notations

| Notation | Meaning | Definition |
|------|------|------|
| $f \ll g$ (little-o / much smaller than) | $f$ decays much faster than $g$ | $\lim_{x\to x_0} f/g = 0$ |
| $f \sim g$ (asymptotically equivalent) | $f$ and $g$ are of the same order | $\lim_{x\to x_0} f/g = 1$ |
| $f = O(g)$ (big-O) | magnitude of $f$ does not exceed that of $g$ | $\limsup_{x\to x_0} \|f/g\| < \infty$ |

**Example**: $\sin x - x = O(x^3)$ as $x \to 0$

### 2.2 Key Distinctions

- $\sim$ does **not** imply numerical approximation: $e^x + x \sim e^x$ ($x\to\infty$), but the numerical difference is enormous
- $f \ll g$ also does not imply $\sim$: $x^2 \ll x^3$ near $x=0$, but they are not asymptotically equivalent
- A nonzero function **cannot** be asymptotic to zero

### 2.3 Poincaré Definition of Asymptotic Expansion

$f(x)$ has an asymptotic expansion with respect to the asymptotic sequence $\{\phi_n(x)\}$ ($\phi_{n+1} \ll \phi_n$):

$$f(x) \sim \sum_{n=1}^{\infty} a_n \phi_n(x) \quad (x \to x_0)$$

if and only if for every $N$:

$$R_N(x) \equiv f(x) - \sum_{n=1}^N a_n \phi_n(x) = O(\phi_{N+1}(x))$$

i.e., **the remainder is much smaller than the last retained term**.

### 2.4 Example: $I(x) = \int_0^{\infty} \frac{e^{-xt}}{1+t} dt$

This is the core example that runs throughout.

**Derivation**:
1. Geometric series expansion: $\frac{1}{1+t} = 1 - t + t^2 - t^3 + \cdots$ (converges for $|t|<1$)
2. $I(x) \sim \sum_{n=0}^{\infty} (-1)^n \int_0^{\infty} e^{-xt} t^n dt$
3. Integrate by parts $n$ times: $\int_0^{\infty} e^{-xt} t^n dt = \frac{n!}{x^{n+1}}$
4. Hence $I(x) \sim \sum_{n=0}^{\infty} (-1)^n \frac{n!}{x^{n+1}} = \frac{1}{x} - \frac{1}{x^2} + \frac{2!}{x^3} - \frac{3!}{x^4} + \cdots$

**This series is divergent**: $|a_{n+1}/a_n| = (n+1)/x \to \infty$. Source of divergence: the geometric series $\frac{1}{1+t}$ diverges for $|t|>1$.

**Numerical example**: For $x=10$, the true value $=0.09156$; the partial sum gives $0.0914$, error only $0.00016$.

**Relation to incomplete Gamma function**: Substituting $\sigma = (1+t)x$ yields $I(x) = e^x \Gamma(0, x)$ (upper incomplete Gamma function).

### 2.5 Remainder Estimate & Truncation Criterion

For the $N$-term partial sum $S_N(x)$ of the above series, the remainder is:

$$R_N = (-1)^N \int_0^{\infty} e^{-xt} \frac{t^N}{1+t} dt$$

Using $\frac{1}{1+t} \leq 1$, we obtain:

$$|R_N| < \int_0^{\infty} e^{-xt} t^N dt = \frac{N!}{x^{N+1}} = |a_{N+1}|$$

**The absolute value of the remainder does not exceed the absolute value of the first omitted term.**

Since $R_N$ alternates in sign, the true value is sandwiched between two consecutive partial sums:

$$S_{N-1} < I(x) < S_N \quad \text{or} \quad S_N < I(x) < S_{N-1}$$

**Optimal truncation**: Stop when the two-term sandwich is tightest.

### 2.6 General Properties of Asymptotic Expansions

#### (1) Convergent Series vs Asymptotic Series

| | Convergent Series | Asymptotic Series |
|---|---|---|
| Limit process | Fixed $x$, $N \to \infty$ | Fixed $N$, $x \to x_0$ |
| Concern | Whether infinite sum tends to $f(x)$ | Whether finitely many terms approximate $f(x)$ |

**A convergent Taylor series is a special case of an asymptotic expansion.**

#### (2) Uniqueness of Coefficients (given an asymptotic sequence)

$$a_1 = \lim_{x\to x_0} \frac{f(x)}{\phi_1(x)}, \quad a_2 = \lim_{x\to x_0} \frac{f(x) - a_1\phi_1(x)}{\phi_2(x)}, \quad \cdots$$

However, the choice of asymptotic sequence $\{\phi_n\}$ is **not unique**.

**Non-standard sequence example** (exam topic named by instructor): $f(x) = \sqrt{25+x}$ as $x \to 0$, given the asymptotic sequence $\{1, \cos x, \sin x, \sin^2 x\}$.

**Standard procedure for expanding from the definition**:
1. $a_1 = \lim_{x\to 0} f(x)/1 = 5$
2. $a_2 = \lim_{x\to 0} \frac{f(x) - 5}{\cos x} = \lim_{x\to 0} \frac{\sqrt{25+x} - 5}{\cos x} = \frac{1/10}{1} = \frac{1}{10}$ (numerator Taylor: $5(1 + x/50 - x^2/5000 + \cdots) - 5 = x/10 - x^2/200$)
3. $a_3 = \lim_{x\to 0} \frac{f(x) - 5 - \frac{1}{10}\cos x}{\sin x} = \cdots$
4. Decompose successively; each coefficient is uniquely determined by the limit

**Key point**: The asymptotic sequence $\{\phi_n\}$ is **not uniquely chosen** — the same $f(x)$ has different $a_n$ for different asymptotic sequences. But given a sequence, the coefficients are unique. The exam requires mastering the complete steps of "expanding from the definition", not memorizing expansion formulas.

> Original notes example: $f(x) = \sqrt{1+x}$, with $\{\cos x, \sin x, \sin^3 x\}$. Same procedure as above.

#### (3) Transcendentally Small Terms

If $f(x) \ll 1/x^\alpha$ holds for **every** $\alpha > 0$, then $f$ is **transcendentally small**.

**Example**: $e^{-x}$ ($x \to \infty$), because $\lim_{x\to\infty} e^{-x} / x^{-\alpha} = 0$.

**Consequence**: $f(x)$ and $f(x) + ce^{-x}$ share the same power-law asymptotic expansion — transcendentally small terms are "invisible" in power-law asymptotic series.

#### (4) Valid/Invalid Operations on Asymptotic Expansions

| Allowed | Use Caution / Not Allowed |
|------|---------------|
| Addition & subtraction | Term-by-term substitution $f(g(x))$ |
| Multiplication & division | Term-by-term differentiation |
| Term-by-term integration | — |

---

<a id="sec-3"></a>
## 3. Method of Stationary Phase 🔥

### 3.1 Basic Problem

$$I(x) = \int_a^b f(t)\, e^{ix\psi(t)} dt, \quad x \to \infty$$

### 3.2 Riemann-Lebesgue Lemma

If $f(t)$ is integrable on $[a,b]$, the classical R-L lemma gives:

$$\lim_{x \to \infty} \int_a^b f(t) e^{ixt} dt = 0 \quad \text{i.e., } o(1)$$

If, furthermore, $f \in C^1$ (once continuously differentiable), integration by parts yields a stronger estimate:

$$I(x) = O\left(\frac{1}{x}\right)$$

**Intuition**: Rapid oscillation causes positive-negative cancellation.

For the special case $\psi(t) = t$:

$$\int_a^b f(t) e^{ixt} dt = O\left(\frac{1}{x}\right)$$

**Integration by parts proof**: $\int_a^b f(t) e^{ix\psi(t)} dt = \left.\frac{f(t)}{ix\psi'(t)} e^{ix\psi(t)}\right|_a^b - \frac{1}{ix}\int_a^b e^{ix\psi(t)} \frac{d}{dt}\left(\frac{f(t)}{\psi'(t)}\right) dt$

The first term is $O(1/x)$; the second is $O(1/x^2)$ (if $f/\psi'$ is smooth).

### 3.3 Stationary Phase Point

If $\psi'(t_s) = 0$ ($t_s \in [a,b]$), then the oscillation "slows down" near $t_s$, cancellation is weakest, and this region becomes the main source of contribution to the integral. $t_s$ is called a **stationary phase point**.

### 3.4 Example 1: $\int_0^{\infty} \cos(x(t^3/3 - t)) dt$

- $\psi(t) = t^3/3 - t$, $\psi'(t_s) = t_s^2 - 1 = 0 \Rightarrow t_s = 1$
- Expand at $t_s=1$: $\psi(t) = -2/3 + (t-1)^2 + O((t-1)^3)$
- $I(x) \approx \cos(2x/3) \int_{-\infty}^{\infty} \cos(xu^2) du + \sin(2x/3) \int_{-\infty}^{\infty} \sin(xu^2) du$

Using **Fresnel integrals**:

$$\int_0^{\infty} \sin(xt^2) dt = \sqrt{\frac{\pi}{8x}}, \quad \int_{-\infty}^{\infty} e^{-is^2} ds = \sqrt{\pi} e^{-i\pi/4}$$

Finally $I(x) = O(1/\sqrt{2x})$ (larger than $O(1/x)$, because the stationary phase point weakens cancellation).

### 3.5 Example 2: Asymptotics of Bessel Function $J_0(x)$

**Integral representation**: $J_0(x) = \frac{1}{\pi}\int_0^{\pi} \cos(x\sin t) dt = \frac{1}{\pi}\text{Re}\int_0^{\pi} e^{ix\sin t} dt$

- $\psi(t) = \sin t$, $\psi'(t_s) = \cos t_s = 0 \Rightarrow t_s = \pi/2$
- Expansion: $\sin t = 1 - \frac{1}{2}(t - \pi/2)^2 + \cdots$
- Substituting gives $J_0(x) \sim \frac{1}{\pi} \text{Re}\left[e^{ix} \int e^{-ix(t-\pi/2)^2/2} dt\right]$

Substitute $s = \sqrt{x/2}(t-\pi/2)$, using **Fresnel integrals with complex contours**:

$$\int_0^{\infty} e^{-is^2} ds = e^{-i\pi/4} \int_0^{\infty} e^{-r^2} dr = \frac{\sqrt{\pi}}{2} e^{-i\pi/4}$$

(Contour integration along the ray $z = re^{-i\pi/4}$, using the analyticity of $e^{-iz^2}$.)

**Final result**:

$$J_0(x) \sim \sqrt{\frac{2}{\pi x}} \cos\left(x - \frac{\pi}{4}\right), \qquad x \to \infty$$

---

---

# Part II: Universal Foundation — Bridge from Integrals to ODEs

> Three tools: Integration by Parts + Rescaling + Dominant Balance
> Integration by parts is the standard strategy for "no stationary point" cases, and is also the **key bridge** from asymptotic integrals to boundary layer analysis
>
> ### 🔥 Exam Focus (instructor's emphasis)
> **Rescaling + Dominant Balance** is the technical foundation for all subsequent ODE perturbation methods:
> - Involves stretching transformations to determine boundary layer thickness $\delta = \epsilon^\gamma$, where $\gamma$ is determined via dominant balance
> - $y = e^S$ ansatz → $S'' \ll (S')^2$ → $(S')^2 \sim f(x)$ → successive corrections
> - Application to the Airy equation at an irregular singular point is a typical exam problem

<a id="sec-4"></a>
## 4. Local Analysis of ODEs ⭐

### 4.1 Second-Order Linear Homogeneous ODE

$$y'' + P(x)y' + Q(x)y = 0$$

General solution: $y = c_1 y_1(x) + c_2 y_2(x)$ (linear combination of two linearly independent solutions)

### 4.2 Classification of $x_0$

Based on the analyticity of $P(x)$ and $Q(x)$ at $x_0$:

| Type | Condition | Method |
|------|------|------|
| **Ordinary Point** | $P, Q$ analytic at $x_0$ | Taylor expansion |
| **Regular Singular Point** | $(x-x_0)P(x)$ and $(x-x_0)^2 Q(x)$ analytic at $x_0$ | **Frobenius series** $y = \sum_{n=0}^{\infty} a_n (x-x_0)^{n+\alpha}$, $\alpha$ is the indicial root |
| **Irregular Singular Point** | Neither of the above | No general method; must use dominant balance |

### 4.3 Example 1: $x^n y'' + xy' + y = 0$

Convert to standard form: $y'' + \frac{1}{x^{n-1}} y' + \frac{1}{x^n} y = 0$, analyze $x_0 = 0$:

- $n=0$: $P(x)=x$ ($1/x^{-1}=x$), $Q(x)=1$ → **Ordinary point**
- $n=1$: $P(x)=1$, $Q(x)=1/x$ → **Regular singular point**
- $n=2$: $P(x)=1/x$, $Q(x)=1/x^2$ → **Regular singular point**
- $n \geq 3$: $P(x)=1/x^{n-1}$, $Q(x)=1/x^n$ → **Irregular singular point**

### 4.4 Example 2: Local Analysis of Airy Equation at Infinity

$y'' = xy$, study $x \to \infty$. Let $t = 1/x$, then $x = 1/t$, $dx/dt = -1/t^2$.

$$y' = \frac{dy}{dx} = \frac{dy}{dt}\frac{dt}{dx} = -t^2 \dot{y}$$

$$y'' = \frac{d}{dx}(-t^2 \dot{y}) = (-t^2 \ddot{y} - 2t\dot{y})(-t^2) = t^4 \ddot{y} + 2t^3 \dot{y}$$

Substitute: $t^4 \ddot{y} + 2t^3 \dot{y} = \frac{1}{t} y$

Divide by $t^4$: $\ddot{y} + \frac{2}{t}\dot{y} - \frac{1}{t^5}y = 0$

At $t_0 = 0$, this is an **irregular singular point**. For such singularities, the strategy is the **exponential ansatz** $y = e^{S(x)}$, i.e., the dominant balance method discussed below.

---

<a id="sec-5"></a>
## 5. Dominant Balance 🔥

### 5.1 Method Idea

For ODEs like $y'' = x^{-3} y$ ($x \to 0^+$), assume the solution has the form:

$$y(x) = e^{S(x)}$$

Derivatives:
$$y' = S' e^S, \quad y'' = [S'' + (S')^2] e^S$$

Substitute into the ODE: $S'' + (S')^2 - f(x) = 0$ (with $f(x) = x^{-3}$)

**Core assumption**: $S'' \ll (S')^2$ (dominant balance), thus:

$$(S')^2 \sim x^{-3} \quad\Rightarrow\quad S' \sim \pm x^{-3/2}$$

Integrate: $S \sim \mp 2x^{-1/2}$

### 5.2 General Rule

If $S' \sim 1/x^n$ ($x \to 0^+$), integration behavior:

| $n$ | Behavior of $S(x)$ |
|-----|--------------|
| $n > 1$ | $S \sim \frac{1}{n-1} x^{-(n-1)}$ |
| $n = 1$ | $S \sim \ln x$ |
| $n < 1$ | $S \sim x^{1-n}$ |

### 5.3 Dominant Balance for Airy Equation (Detailed)

(Taking $y'' = x^{-3}y$ as an example, $x \to 0^+$.) Assume an expansion for $S$, take the negative branch $S \sim -2x^{-1/2}$. Set $S = -2x^{-1/2} + C(x)$, where $C$ varies slowly.

Iterative correction:
1. $S' = x^{-3/2} + C'$, $S'' = -\frac{3}{2}x^{-5/2} + C''$
2. Substitute into $S'' + (S')^2 - x^{-3} = 0$:
   $$-\frac{3}{2}x^{-5/2} + C'' + (x^{-3/2} + C')^2 - x^{-3} = 0$$
3. Expand the square and retain dominant terms, obtaining $C' \sim \frac{3}{4}\frac{1}{x}$, so $C \sim \frac{3}{4}\ln x$
4. Substitute back for the next order: $D' \sim -\frac{3}{32x}$, $D \sim -\frac{3}{16}x^{-1/2}$

**Final solution**:

$$y(x) \sim C e^{\pm 2x^{-1/2}} x^{3/4} \left(1 \mp \frac{3}{16}x^{1/2} + \cdots\right)$$

---

---

# Part III-①: Singular Perturbation · Boundary Layer — Spatial Local Breakdown

> **Failure type**: Highest derivative multiplied by small parameter → equation order reduction as $\epsilon \to 0$ → loss of boundary conditions
> **Five-step procedure**: Outer solution → Determine boundary layer location → Inner solution (stretching transformation) → MAE matching → Composite solution
> **Generality**: From linear ($a(x)$ sign determines location) to nonlinear (phase plane geometry determines location)
>
> ### 🔥 Exam Focus (instructor's emphasis)
> **Boundary Layer → Turning Points → WKB** is a complete exam thread.
>
> **Boundary Layer exam requirements** (instructor's itemized oral remarks):
> 1. Know the **fundamental assumptions** of boundary layer theory
> 2. Be able to perform **asymptotic matching** to determine unknown coefficients
> 3. Be able to **judge for yourself** where the boundary layer is (the problem won't tell you)
> 4. Determine boundary layer thickness via **dominant balance** (scale with $\epsilon$, determine $\delta = \epsilon^\gamma$)
> 5. **Complete five-step procedure**: Outer solution → Determine location → Inner solution → MAE matching → Composite solution
>
> **Prerequisite**: For constant-coefficient linear ODEs, solve using the **characteristic equation** — set $y = e^{\lambda x}$, substitute to obtain the characteristic equation, solve for $\lambda$. This is the fundamental solution method for outer and inner solutions in boundary layer analysis.
>
> **Thread extensions**:
> - §10 Interior/corner layer ($a(x)$ changes sign): dominant balance gives $\delta = \epsilon^{1/2}$
> - §11 Nonlinear boundary layer: phase plane geometric method for location, shares perspective with bifurcation theory (§15)
> - **WKB turning point → fall back to Boundary Layer** (instructor's emphasis): WKB fails at turning point → revisit boundary layer thinking → there is an **inner layer** near the turning point → treat it specially → dominant balance determines thickness $\delta = \epsilon^{2/3}$<a id="sec-6"></a>
## 6. Perturbation Methods — Algebraic Equations

### 6.1 Regular Perturbation

For equations containing a small parameter $\epsilon$, assume the solution expands in powers of $\epsilon$:

$$x = x_0 + \epsilon x_1 + \epsilon^2 x_2 + \cdots$$

Substitute into the original equation, collect terms by powers of $\epsilon$ into linear equations.

**Core goal**: Transform nonlinear equations into a sequence of linear equations.

**Drawback**: Requires guessing the correct asymptotic sequence in advance.

### 6.2 Example 1: $x^2 + \epsilon x - 1 = 0$

Exact solution: $x = \frac{-\epsilon \pm \sqrt{\epsilon^2 + 4}}{2} = \pm 1 \mp \frac{\epsilon}{2} \pm \frac{\epsilon^2}{8} + \cdots$

Perturbation expansion (positive root, $x=1$ when $\epsilon=0$):
$$x = 1 + \epsilon x_1 + \epsilon^2 x_2 + \cdots$$

Substitute:
- $O(1)$: $1 - 1 = 0$ ✓
- $O(\epsilon)$: $2x_1 + 1 = 0 \Rightarrow x_1 = -1/2$
- $O(\epsilon^2)$: $x_1^2 + 2x_2 + x_1 = 0 \Rightarrow x_2 = 1/8$

$$x = 1 - \frac{\epsilon}{2} + \frac{\epsilon^2}{8} + \cdots$$

### 6.3 Iterative Method

Without assuming an asymptotic sequence, iterate from an initial guess. For $x^2 = 1 - \epsilon x$:

- 0th iteration: $x_0 = 1$
- 1st iteration: $x_1 = \sqrt{1 - \epsilon} = 1 - \frac{\epsilon}{2} - \frac{\epsilon^2}{8} + \cdots$
- 2nd iteration: $x_2 = \sqrt{1 - \epsilon x_1}$, continue iterating...

Advantage: Automatically generates the correct sequence. Disadvantage: Higher-order corrections become increasingly difficult; iteration may not converge.

### 6.4 Example 2: Singular Perturbation Equation $\epsilon x^2 + x - 1 = 0$

**Key**: When $\epsilon = 0$, the equation reduces to $x - 1 = 0$, with only **one** root. But when $\epsilon \neq 0$, there are two roots.

Exact solution:
$$x = \frac{-1 \pm \sqrt{1 + 4\epsilon}}{2\epsilon}$$

Expanding the two roots:
- Positive root ($O(1)$): $x \sim 1 - \epsilon + 2\epsilon^2 + \cdots$
- Negative root ("evaporates to infinity"): $x \sim -\frac{1}{\epsilon} - 1 + \epsilon - 2\epsilon^2 + \cdots$

**Singular perturbation**: The qualitative behavior fundamentally changes as $\epsilon \to 0$ (order reduction).

### 6.5 Example 3: Non-Integer Power Expansion $(1-\epsilon)x^2 - 2x + 1 = 0$

When $\epsilon = 0$, $x=1$ is a **double root**. The naive integer-power expansion $x = 1 + \epsilon x_1 + \epsilon^2 x_2 + \cdots$ fails (the $O(\epsilon)$ equation cannot be satisfied).

Exact solution: $x = \frac{1 \pm \sqrt{\epsilon}}{1 - \epsilon} = 1 \pm \epsilon^{1/2} + \epsilon \pm \epsilon^{3/2} + \cdots$

**The correct asymptotic sequence involves non-integer powers**: General form $x = 1 + \mu_1(\epsilon) x_1 + \mu_2(\epsilon) x_2 + \cdots$, where $\{\mu_n(\epsilon)\}$ is an asymptotic sequence, and exponents and coefficients must be determined simultaneously.

---

<a id="sec-7"></a>
## 7. Perturbation Methods — ODEs

### 7.1 Projectile Problem

An object launched vertically upward from the ground with initial velocity $v_0$, considering gravitational variation with height.

**Governing equation**: $m\ddot{x} = -\frac{GMm}{(R+x)^2} = -mg\frac{R^2}{(R+x)^2}$, where $g = GM/R^2$

**Initial conditions**: $x(0) = 0$, $\dot{x}(0) = v_0$

If gravitational variation is ignored ($x \ll R$): $\ddot{x} = -g$, giving parabolic motion:
$$x(t) = -\frac{1}{2}gt^2 + v_0 t$$

Maximum height $v_0^2/(2g)$, flight time $2v_0/g$.

### 7.2 Nondimensionalization

Characteristic scales: $t_c = v_0/g$, $x_c = v_0^2/g$, $\epsilon = x_c/R = v_0^2/(gR) \ll 1$

Dimensionless variables: $y = x/x_c$, $\tau = t/t_c$

**Dimensionless ODE**: $\ddot{y}(\tau) = -\frac{1}{(1 + \epsilon y)^2}$, IC $y(0)=0$, $\dot{y}(0)=1$

### 7.3 Regular Perturbation Solution

Expand $y = y_0 + \epsilon y_1 + \epsilon^2 y_2 + \cdots$

Expand the RHS: $-\frac{1}{(1+\epsilon y)^2} = -1 + 2\epsilon y - 3\epsilon^2 y^2 + \cdots$

- $O(1)$: $\ddot{y}_0 = -1$, $y_0(0)=0$, $\dot{y}_0(0)=1$
  $\Rightarrow y_0(\tau) = -\tau^2/2 + \tau$

- $O(\epsilon)$: $\ddot{y}_1 = 2y_0 = -\tau^2 + 2\tau$, $y_1(0)=0$, $\dot{y}_1(0)=0$
  $\Rightarrow y_1(\tau) = -\tau^4/12 + \tau^3/3$

First-order solution: $y(\tau) = -\frac{\tau^2}{2} + \tau + \epsilon\left(-\frac{\tau^4}{12} + \frac{\tau^3}{3}\right) + O(\epsilon^2)$

### 7.4 Corrected Flight Time

Solve $y(\tau) = 0$, assume $\tau = 2 + \epsilon \tau_1 + \cdots$, substitute to get $\tau_1 = 4/3$.

$$\tau = 2 + \frac{4}{3}\epsilon + O(\epsilon^2)$$

### 7.5 Characteristics of Regular Perturbation

1. The zeroth-order solution comes from the **unperturbed problem** ($\epsilon = 0$)
2. Nonlinear → linear sequence; higher orders determined by lower orders
3. One can artificially introduce $\epsilon$ and finally set $\epsilon = 1$ (e.g., $y'' = f(x)y$, set $\epsilon y'' = f(x)y$)
4. **Uniform Validity**: Error is simultaneously small for all $x$, the only requirement being $\epsilon$ sufficiently small

Counterexample: $f(x,\epsilon) = e^{-x/\epsilon} + x$; at $x = 10^{-2}$, needs $\epsilon \ll 10^{-2}$; at $x = 10^{-6}$, needs $\epsilon \ll 10^{-6}$ — different degrees of $\epsilon$ are required for different $x$, hence not uniformly valid.

---

<a id="sec-8"></a>
## 8. Singular Perturbation Methods 🔥

### 8.1 Boundary Layer in Linear ODEs

**Main example**: $\epsilon y'' + (1+\epsilon)y' + y = 0$, $y(0)=0$, $y(1)=1$

**Exact solution** (constant coefficients → exponential ansatz $y = e^{\lambda x}$):
$\epsilon\lambda^2 + (1+\epsilon)\lambda + 1 = 0 \Rightarrow (\lambda+1)(\epsilon\lambda+1) = 0 \Rightarrow \lambda = -1, -1/\epsilon$

$$y = c_1 e^{-x} + c_2 e^{-x/\epsilon}$$

From boundary conditions:
$$y(0)=0 \Rightarrow c_1 = -c_2，\quad y(1)=1 \Rightarrow c_1(e^{-1} - e^{-1/\epsilon}) = 1$$

$$y(x) = \frac{e^{-x} - e^{-x/\epsilon}}{e^{-1} - e^{-1/\epsilon}}$$

**Key observation**: $e^{-1/\epsilon}$ is **transcendentally small** ($\epsilon \to 0$) and has no Taylor expansion. This is the hallmark of singular perturbation.

For fixed $x > 0$: $y(x) \to e^{1-x}$ (outer solution). But convergence is **not uniform** — to have $e^{-x/\epsilon} < \delta$, one needs $x > \epsilon \ln(1/\delta)$.

### 8.2 Matched Asymptotic Expansion (MAE)

#### Outer Solution (usually easy, regular perturbation)

Set $\epsilon = 0$: $y_0' + y_0 = 0 \Rightarrow y_{\text{out}} = c e^{-x}$

Use only the BC at $x=1$: $y_{\text{out}}(1) = 1 \Rightarrow c = e$, so $y_{\text{out}} = e^{1-x}$

Higher orders: $y_n = 0$ ($n \ge 1$).

#### Inner Solution (boundary layer, stretching transformation)

Boundary layer near $x=0$, width $O(\epsilon)$. Introduce **stretching variable**:

$$X = \frac{x}{\epsilon}$$

Derivative transformation:
$$y' = \frac{dy}{dx} = \frac{dY}{dX}\frac{dX}{dx} = \frac{1}{\epsilon} Y_X, \quad y'' = \frac{1}{\epsilon^2} Y_{XX}$$

Substitute into the original ODE:
$$\frac{1}{\epsilon} Y_{XX} + \frac{1+\epsilon}{\epsilon} Y_X + Y = 0$$

Multiply by $\epsilon$:
$$Y_{XX} + (1+\epsilon)Y_X + \epsilon Y = 0$$

Regular perturbation expansion:
- $O(1)$: $Y_{0,XX} + Y_{0,X} = 0 \Rightarrow Y_0 = C e^{-X} + D$

Use the BC at $x=0$: $Y_0(0) = 0 \Rightarrow C + D = 0 \Rightarrow Y_{\text{in}} = C(e^{-X} - 1)$

#### Matching

$$\lim_{X \to \infty} Y_{\text{in}} = \lim_{x \to 0} y_{\text{out}}$$

$$-C = e \Rightarrow C = -e$$

$$Y_{\text{in}} = -e(e^{-X} - 1) = e - e^{1-X} = e - e^{1-x/\epsilon}$$

#### Composite Solution

$$y_{\text{match}} = y_{\text{in}} + y_{\text{out}} - y_{\text{overlap}}$$

Overlap $y_{\text{overlap}} = e$ (the value both solutions tend to in the matching region):

$$y_{\text{match}} = (e - e^{1-x/\epsilon}) + e^{1-x} - e = e^{1-x} - e^{1-x/\epsilon}$$

This matches the exact solution!

---

<a id="sec-9"></a>
## 9. Boundary Layer Location & Thickness 🔥

### 9.1 Example 2: $\epsilon y'' - y' + y = 0$

BC: $y(0)=0$, $y(1)=1$

#### Attempt: Boundary layer at $x=0$

Outer solution ($\epsilon=0$): $-y_0' + y_0 = 0 \Rightarrow y_0 = A e^x$

Use BC at $x=1$: $A e^1 = 1 \Rightarrow y_{\text{out}} = e^{x-1}$

Inner solution (stretching $X = x/\epsilon$):
$$Y_{XX} - Y_X + \epsilon Y = 0$$

$O(1)$: $Y_{0,XX} - Y_{0,X} = 0 \Rightarrow Y_0 = B + C e^X$

$Y_0(0) = 0 \Rightarrow B + C = 0 \Rightarrow Y_{\text{in}} = B(1 - e^X)$

When matching, $Y_{\text{in}}$ grows exponentially → **cannot match**. The boundary layer location was guessed incorrectly.

#### Correct Location: Boundary layer at $x=1$

Outer solution: $y_0 = c e^x$, use BC at $x=0$: $y_0(0) = 0 \Rightarrow c = 0$, so $y_{\text{out}} = 0$

Stretching $X = (1-x)/\epsilon$ (note direction! $x=1$ is the right endpoint):
$$Y_{XX} + Y_X + \epsilon Y = 0$$

$O(1)$: $Y_{0,XX} + Y_{0,X} = 0 \Rightarrow Y_0 = C + D e^{-X}$

$Y_0(0) = 1 \Rightarrow C + D = 1$

Matching: $\lim_{X \to \infty} Y_0 = C = \lim_{x \to 1} y_{\text{out}} = 0 \Rightarrow C = 0, D = 1$

$$Y_{\text{in},0} = e^{-X}$$

Composite solution: $y_{\text{match}} = e^{-(1-x)/\epsilon}$

### 9.2 General Rule

For $\epsilon y'' + a(x)y' + b(x)y = 0$:

- If $a(x) > 0$: boundary layer at **$x = 0$** (left boundary)
- If $a(x) < 0$: boundary layer at **$x = 1$** (right boundary)

---

<a id="sec-10"></a>
## 10. Interior / Corner Layer

### 10.1 When $a(x)$ Changes Sign

**Example 3**: $\epsilon y'' + xy' - y = 0$, $x \in [-1, 1]$, $y(-1)=1$, $y(1)=2$

$a(x) = x$:
- $x \in [-1, 0)$: $a(x) < 0$ → expect boundary layer at right end (i.e., toward $x=0$)
- $x \in (0, 1]$: $a(x) > 0$ → expect boundary layer at left end (i.e., toward $x=0$)

→ The boundary layers merge at **$x=0$**, forming an **interior/corner layer**.

### 10.2 Outer Solution

Set $\epsilon = 0$: $x y_0' - y_0 = 0 \Rightarrow \frac{dy_0}{y_0} = \frac{dx}{x} \Rightarrow y_0 = cx$

- Left BC: $y(-1)=1 \Rightarrow y_{\text{out}}^L = -x$
- Right BC: $y(1)=2 \Rightarrow y_{\text{out}}^R = 2x$

### 10.3 Inner Solution — "Thick" Boundary Layer

Stretch $X = x/\delta$. Since $y' = \frac{1}{\delta}Y_X$, $y'' = \frac{1}{\delta^2}Y_{XX}$, $x = \delta X$, substituting gives:
$$\frac{\epsilon}{\delta^2} Y_{XX} + X Y_X - Y = 0$$

Dominant balance requires three terms of the same order: $\frac{\epsilon}{\delta^2} = 1 \Rightarrow \delta = \epsilon^{1/2}$

This is **thicker** than the usual boundary layer ($\delta = \epsilon$).

Inner layer ODE: $Y_{XX} + XY_X - Y = 0$ (**no term may be discarded**)

### 10.4 Solution and Matching

$Y = X$ is one solution. Using reduction of order to find the second solution:

$$Y_{\text{in}} = C_1 X + C_2\left[e^{-X^2/2} + X\sqrt{\frac{\pi}{2}}\text{erf}\left(\frac{X}{\sqrt{2}}\right)\right]$$

Matching yields $C_1 = 1/2$, $C_2 = -3/(2\sqrt{2\pi})$.

---

<a id="sec-11"></a>
## 11. Boundary Layer in Nonlinear Systems

### 11.1 Problem Setup

$\epsilon y'' = y y' - y$, $y(0)=1$, $y(1)=-1$

Nonlinear system — **no ready-made theory for determining boundary layer location**. Use **geometric method (phase plane analysis)**.

### 11.2 Phase Plane Analysis

Let $z = y'$, convert to a 2D first-order system:

$$\begin{cases} y' = z \\ z' = \frac{1}{\epsilon} y(z - 1) \end{cases}$$

Treat $x$ as "time", $(y, z)$ as the phase plane. Trajectories represent solutions.

**Key**:
- $z = 1$: $z' = 0$ (no vertical velocity)
- $y = 0$: $y' = 0$ (no horizontal velocity)
- $y \to -y$ symmetry → trajectories symmetric about the $y$-axis

**Fast/slow region division**:
- $z$ not near $1$: $z - 1 = O(1)$, $z' = O(1/\epsilon)$ → **fast region** (boundary layer)
- $z \approx 1$: $z - 1 = O(\epsilon)$, $z' = O(1)$ → **slow region** (outer solution)

Geometry indicates the boundary layer is at **$x = 1/2$**.

### 11.3 Matched Asymptotic Expansion

**Outer solution** (slow region, $z \approx 1$): $\epsilon = 0 \Rightarrow y_0(y_0' - 1) = 0$
- $y_0' = 1$ (nontrivial) $\Rightarrow y_0 = x + C$
- Left BC: $y(0)=1 \Rightarrow y_{\text{out},L} = x + 1$
- Right BC: $y(1)=-1 \Rightarrow y_{\text{out},R} = x - 2$

**Inner solution** (boundary layer, near $x = 1/2$): Stretch $X = (x-1/2)/\epsilon$

Substituting gives $\ddot{Y} = Y\dot{Y} - Y$ ($\epsilon$ eliminated)

Regular perturbation $O(1)$: $\ddot{Y}_0 = Y_0 \dot{Y}_0$

Note that $\ddot{Y}_0 = \frac{d}{dX}(\frac{1}{2}Y_0^2) = Y_0 \dot{Y}_0$. By symmetry $Y_0(0) = 0$.

Integrate $\ddot{Y}_0 = Y_0 \dot{Y}_0$ once:
$$\dot{Y}_0 = \frac{1}{2}Y_0^2 + B, \quad B < 0$$

Let $B = -b^2/2$, separate variables:
$$\frac{\dot{Y}_0}{Y_0^2 - b^2} = \frac{1}{2} \Rightarrow Y_0(X) = -b \tanh\left(\frac{bX}{2}\right)$$

**Matching**:
$$\lim_{x \to 1/2^-} y_{\text{out},L} = \frac{3}{2} = b \Rightarrow b = \frac{3}{2}$$

**Composite solution**:
$$y_{\text{match}} = x + 1 - \frac{3}{2}\tanh\left(\frac{3}{4}\frac{x-1/2}{\epsilon}\right) - \frac{3}{2} + \cdots$$

---

---

# Part III-②: WKB Method — Global Collapse

> **Failure type**: $\epsilon^2 y'' = Q(x)y$ fails globally where $Q(x)$ changes sign
> **Difference from boundary layer**: Boundary layer handles **local** rapid variation; WKB handles **global** slow-variation failure (modulated oscillation/exponential decay)
> **Unity**: $y = e^{S/\delta}$ ansatz = $\epsilon$-parameterized version of dominant balance
>
> ### 🔥 Exam Focus (instructor's emphasis)
> **Complete WKB workflow**: Ansatz $y = e^{S/\epsilon}$ → $S_0' = \pm\sqrt{Q}$ → $S_1' = -Q'/4Q$ → general solution → **Turning Point** $Q(x_0)=0$ where WKB fails → inner layer scaling $\epsilon^{2/3}$ → **Airy equation** → Airy function asymptotic connection on both sides → **Double turning point Bohr-Sommerfeld quantization** $\oint\sqrt{Q}dx = (n+1/2)\pi\epsilon$
>
> **Instructor's oral WKB logic chain (key points)**:
> 1. Be able to derive WKB (starting from $y = e^{S/\epsilon}$, solve order by order via dominant balance)
> 2. Know what a **turning point** is ($Q(x_0)=0$) and why WKB doesn't work there ($1/Q^{1/4}$ diverges)
> 3. **When WKB fails → fall back to boundary layer**: there is an **inner layer** near the turning point that must be treated specially
> 4. In the treatment, know **how to obtain the thickness** (dominant balance → $\delta = \epsilon^{2/3}$)
> 5. Airy function connection formulas: $x>x_0$ exponential decay (boundedness → keep only Ai), $x<x_0$ oscillatory

<a id="sec-12"></a>
## 12. WKB Method 🔥

### 12.1 Positioning

- **Boundary Layer**: handles **local** rapid variation (matching inner and outer solutions)
- **WKB**: handles **global** slow-variation failure (modulated oscillation/exponential decay)

### 12.2 Basic Equation

$\epsilon^2 y'' = Q(x) y$ ($\epsilon \to 0$), equivalent to the Schrödinger equation:
$$i\hbar\frac{\partial\psi}{\partial t} = -\frac{\hbar^2}{2m}\frac{\partial^2\psi}{\partial x^2} + V(x)\psi$$

### 12.3 Dominant Balance Derivation

Assume $y = e^{S/\epsilon}$, $S = S_0 + \epsilon S_1 + \epsilon^2 S_2 + \cdots$

Derivatives:
$$y' = \frac{S'}{\epsilon} e^{S/\epsilon}$$
$$y'' = \left[\frac{S''}{\epsilon} + \frac{(S')^2}{\epsilon^2}\right] e^{S/\epsilon} = \frac{1}{\epsilon^2}\left[\epsilon S'' + (S')^2\right] e^{S/\epsilon}$$

Substitute into the ODE: $\epsilon S'' + (S')^2 - Q(x) = 0$

Substitute the expansion for $S$ and collect by powers of $\epsilon$:

- **$O(1)$**: $(S_0')^2 = Q$
  $$\Rightarrow S_0' = \pm \sqrt{Q}, \quad S_0 = \pm \int_0^x \sqrt{Q(s)} ds$$

- **$O(\epsilon)$**: $S_0'' + 2S_0' S_1' = 0$
  $$\Rightarrow S_1' = -\frac{S_0''}{2S_0'} = -\frac{Q'}{4Q} \Rightarrow S_1 = -\frac{1}{4}\ln Q + \text{const}$$

- Higher orders: $S_1'' + (S_1')^2 + 2S_0' S_2' = 0$ → solvable order by order

### 12.4 General WKB Solution

$$y = \frac{1}{Q^{1/4}}\left[C_1 e^{\frac{1}{\epsilon}\int\sqrt{Q}dx} + C_2 e^{-\frac{1}{\epsilon}\int\sqrt{Q}dx}\right]$$

Depending on the sign of $Q(x)$:

| $Q(x) > 0$ (Exponential type) | $Q(x) < 0$ (Oscillatory type) |
|---|---|
| $y \sim \frac{1}{Q^{1/4}}\left[c_3 e^{-\frac{1}{\epsilon}\int\sqrt{Q}dx} + c_4 e^{\frac{1}{\epsilon}\int\sqrt{Q}dx}\right]$ | $y \sim \frac{1}{(-Q)^{1/4}}\left[c_1\cos\left(\frac{1}{\epsilon}\int\sqrt{-Q}dx\right) + c_2\sin\left(\frac{1}{\epsilon}\int\sqrt{-Q}dx\right)\right]$ |

### 12.5 Example: $x'' + e^{-t} x = 0$

Set $\epsilon^2 \ddot{x} + e^{-t}x = 0$, $\omega = e^{-t/2}$ slowly decaying. When $t \gg 1/\epsilon$, $\omega \to 0$, oscillation ceases.

Change of variable $T = \epsilon t$, $X(T) = x(t)$, $\ddot{x} = \epsilon^2 \ddot{X}$:

$\epsilon^2 \ddot{X} + e^{-T} X = 0$. Using WKB:
$$X \sim e^{T/4}\left[c_1\sin\left(\frac{2}{\epsilon}e^{-T/2}\right) + c_2\cos\left(\frac{2}{\epsilon}e^{-T/2}\right)\right]$$

Note: WKB can also re-derive boundary layer results (e.g., the example in §8.1).

### 12.6 Turning Point

**$Q(x_0) = 0$**, the solution transitions from oscillatory to exponential type. $1/Q^{1/4}$ diverges → WKB fails near $x_0$.

**WKB validity condition**: $(S_0')^2 / \epsilon \gg S_0''$, i.e., $|Q| \gg \sqrt{\epsilon} |Q'|$.

For $Q \approx a(x-x_0)$, the failure region is: $|x - x_0| < O(\epsilon^{2/3})$.

### 12.7 Airy Connection Formulas

Near the turning point, introduce inner layer scaling: $x - x_0 = \epsilon^{2/3} Z$

This yields the Airy equation: $Y_{ZZ} = ZY$

**Asymptotic behavior of Airy functions**:

| Region | $\text{Ai}(Z)$ | $\text{Bi}(Z)$ |
|------|----------------|----------------|
| $Z \to +\infty$ | $\frac{1}{2\sqrt{\pi}}Z^{-1/4}e^{-\frac{2}{3}Z^{3/2}}$ (decay) | $\frac{1}{\sqrt{\pi}}Z^{-1/4}e^{\frac{2}{3}Z^{3/2}}$ (growth) |
| $Z \to -\infty$ | $\frac{1}{\sqrt{\pi}}(-Z)^{-1/4}\sin\left(\frac{2}{3}(-Z)^{3/2} + \frac{\pi}{4}\right)$ | $\frac{1}{\sqrt{\pi}}(-Z)^{-1/4}\cos\left(\frac{2}{3}(-Z)^{3/2} + \frac{\pi}{4}\right)$ |

**If physics requires the solution to be bounded on the $x > x_0$ side (e.g., bound states of the Schrödinger equation) → must discard Bi (because Bi grows exponentially as $Z \to +\infty$) → keep only Ai**.

**Single turning point matching** (assuming $x \to -\infty$ is unbounded → must use Ai):

- $x < x_0$ ($Q < 0$, oscillatory):
  $$y_L \sim \frac{2C_3}{(-Q)^{1/4}}\sin\left(\frac{1}{\epsilon}\int_x^{x_0}\sqrt{-Q}dt + \frac{\pi}{4}\right)$$

- $x > x_0$ ($Q > 0$, exponential decay):
  $$y_R \sim \frac{C_3}{Q^{1/4}}e^{-\frac{1}{\epsilon}\int_{x_0}^x\sqrt{Q}dt}$$

$C_3$ is determined through Airy function matching.

---

<a id="sec-13"></a>
## 13. Eigenvalue Problems 🔥

### 13.1 Basic Concepts

An ODE has nontrivial solutions (**eigenfunctions**) only for specific parameter values (**eigenvalues**).

**Example 1**: $y'' + E y = 0$, $y(0) = y(\pi) = 0$

General solution: $y = \sin(\sqrt{E} x)$ (already satisfies $y(0)=0$)

$y(\pi) = 0 \Rightarrow \sin(\sqrt{E}\pi) = 0 \Rightarrow \sqrt{E}\pi = n\pi$

$$E_n = n^2, \quad y_n = \sin(nx), \quad n = 1, 2, 3, \ldots$$

### 13.2 Example 2: Transcendental Eigenvalues

$y'' + (E - x)y = 0$, $y(0) = y(\pi) = 0$

Rewrite: $y'' = (x - E)y$. Let $X = x - E$, obtaining $Y'' = XY$ (Airy equation).

General solution: $y = \text{Ai}(x - E)$

$y(0) = 0 \Rightarrow \text{Ai}(-E) = 0$. $E$ values are the zeros of $\text{Ai}(-z)$: $E_1 \approx 2.3$, $E_2 \approx 4$, $E_3 \approx 5.5$, ...

### 13.3 WKB Approximation for Large Eigenvalues

$\epsilon^2 y'' + Q(x) y = 0$ ($\epsilon = 1/\sqrt{E} \ll 1$), $Q > 0$, $y(0) = y(\pi) = 0$

WKB oscillatory solution: $y \sim \frac{1}{Q^{1/4}}\left[c_1\cos\left(\frac{1}{\epsilon}\int\sqrt{Q}dx\right) + c_2\sin\left(\frac{1}{\epsilon}\int\sqrt{Q}dx\right)\right]$

$y(0)=0 \Rightarrow c_1 = 0$. $y(\pi)=0 \Rightarrow \sin\left(\frac{1}{\epsilon}\int_0^\pi\sqrt{Q}dx\right) = 0$

$$\frac{1}{\epsilon}\int_0^\pi\sqrt{Q}dx = n\pi \Rightarrow E_n \sim \frac{n^2\pi^2}{\left(\int_0^\pi\sqrt{Q}dx\right)^2}$$

### 13.4 Sturm-Liouville Theory

A general second-order eigenvalue problem can be cast in S-L form:

$$\frac{d}{dx}\left(p(x)\frac{dy}{dx}\right) + q(x)y = -\lambda w(x)y$$

where $p > 0$, $w > 0$ (on the interval considered). Under appropriate boundary conditions:
- There are infinitely many eigenvalues $\lambda_0 < \lambda_1 < \lambda_2 < \cdots$, all real
- The eigenfunctions $\{y_n\}$ are **orthonormal** with respect to the weight function $w(x)$: $\int y_n(x) y_m(x) w(x) dx = \delta_{nm}$
- If $\{y_n\}$ is complete, any function can be expanded: $y(x) = \sum c_n y_n(x)$, $c_n = \int y(x) y_n(x) w(x) dx$

---

<a id="sec-14"></a>
## 14. Schrödinger Equation & Double Turning Points

### 14.1 Problem

$\epsilon^2 y'' = (V(x) - E) y$, $y(\pm\infty) \to 0$

$Q(x) = V(x) - E$. For a potential well $V(x)$, the energy $E$ intersects $V(x)$ at two turning points $A, B$ ($V(A) = V(B) = E$):

- Inside the well ($A < x < B$): $V(x) < E$ → $Q < 0$ → oscillatory
- Outside the well ($x < A$ and $x > B$): $V(x) > E$ → $Q > 0$ → exponential decay

### 14.2 Matching Strategy

1. From $x=B$, use Airy connection: to the right $x>B$ decay ($\text{Ai}$), to the left $x<B$ oscillatory
2. From $x=A$, use Airy connection: to the left $x<A$ decay ($\text{Ai}$), to the right $x>A$ oscillatory
3. In the interior region of the well, the two oscillatory solutions must be matched consistently

### 14.3 Quantization Condition (Bohr-Sommerfeld)

Phase matching requires:

$$\frac{1}{\epsilon}\int_A^B \sqrt{E - V(x)} dx = \left(n + \frac{1}{2}\right)\pi, \quad n = 0, 1, 2, \ldots$$

**Intuition**: The number of half-wavelengths inside the well must be $n + 1/2$ (the $\pi/4$ phase shifts at both ends each contribute a "half").

---

---

# Part IV: Dynamical Systems & Bifurcation — Paradigm Shift to Qualitative Analysis

> From "specific form of the solution" to "qualitative behavior of the solution". Prerequisite tool: Normal Form
> Three classic paradigms: Saddle-Node (fixed point annihilation) | Transcritical (exchange of stability) | Pitchfork (symmetry breaking)
> In the context map, this part serves as the final convergence point — all asymptotic/perturbation/multiple-scale methods converge to understanding the qualitative behavior of systems
>
> ### 🔥 Exam Focus (instructor's emphasis)
> **Exam pathway** (instructor's oral description): **On the rescaled equation** → identify **bifurcation parameters** → based on bifurcation parameters sketch the **bifurcation diagram** → identify which type of bifurcation (pitchfork / saddle-node / transcritical / imperfect pitchfork).
>
> **Standard 4-step for 1-D Bifurcation**: ① Select Bifurcation Parameter $r$ → ② Find Fixed Points $f(x^*, r)=0$ → ③ Determine Stability (sign of $f'(x^*)$) → ④ Sketch Bifurcation Diagram ($x^*$ vs $r$)
>
> **Three canonical forms must be memorized and recognizable**:
> - Saddle-Node: $\dot{x}=r+x^2$ (two fixed points collide and annihilate)
> - Transcritical: $\dot{x}=rx-x^2$ (fixed points exchange stability)
> - Pitchfork: $\dot{x}=rx-x^3$ supercritical / $\dot{x}=rx+x^3$ subcritical (symmetry breaking)
> - **Imperfect Pitchfork** must also be understood: $\dot{x}=s+rx-x^3$, cusp structure in parameter space $(r,s)$
>
> **Relationship between Rescaling and Bifurcation**: Rescaling yields simplified equations → extract Normal Form → identify bifurcation type. Hence Rescaling (§5) is the direct prerequisite for bifurcation analysis.
>
> - **Delayed Bifurcation** (§17): $\Delta s \sim 2.338\,\epsilon^{2/3}$, Riccati → Airy transformation (same technique as §12.7)<a id="sec-15"></a>
## 15. Dynamical Systems & Bifurcation 🔥

### 15.1 One-Dimensional Bifurcation

#### Saddle-Node Bifurcation

**Normal form**: $\dot{x} = x^2 + r$

| $r$ | Fixed Points |
|-----|--------|
| $r < 0$ | $x = \pm\sqrt{-r}$ (one stable, one unstable) |
| $r = 0$ | $x = 0$ (**half-stable**) |
| $r > 0$ | No fixed points |

As $r$ increases through 0, the two fixed points annihilate.

**General case**: $\dot{x} = f(x; r)$, near $(x_*, r_c)$:
$$f(x; r) \approx a(r - r_c) + b(x - x_*)^2$$

#### Transcritical Bifurcation

**Normal form**: $\dot{x} = rx - x^2$

Fixed points: $x=0$ and $x=r$ (always exist). As $r$ passes through 0, they exchange stability.

**Example**: $\dot{x} = r\ln x + x - 1$. $x=1$ is a permanent fixed point. Set $x = u+1$, expand:
$$\dot{u} = r\ln(u+1) + u \approx r\left(u - \frac{u^2}{2}\right) + u = (r+1)u - \frac{r}{2}u^2$$

Change of variable to normal form: $w' = (r+1)w - w^2$

#### Pitchfork Bifurcation

**Supercritical normal form**: $\dot{x} = rx - x^3$

| $r$ | Fixed Points |
|-----|--------|
| $r \le 0$ | $x = 0$ (stable) |
| $r > 0$ | $x = 0$ (unstable), $x = \pm\sqrt{r}$ (stable) |

**$x \to -x$ symmetry**. The bifurcation diagram has a pitchfork shape.

**Subcritical**: $\dot{x} = rx + x^3$ ($\pm\sqrt{-r}$ appear for $r<0$ but are **unstable**).

#### Imperfect Pitchfork Bifurcation

$\dot{x} = s + rx - x^3$ (two parameters: $r$ and asymmetry $s$)

The parameter space $(r, s)$ has a **cusp** structure. When $s \neq 0$, the perfect pitchfork is broken, and the bifurcation becomes of saddle-node type.

### 15.2 Two-Dimensional Bifurcation

In 2D systems, fixed points have richer types:

| Type | Characteristic |
|------|------|
| **Stable Node** | All trajectories approach directly |
| **Unstable Node** | All trajectories depart directly |
| **Saddle** | One direction approaches, one departs |
| **Center** | Family of closed elliptical orbits (neutrally stable) |
| **Stable/Unstable Spiral** | Spiral approach/departure |

Combined with 1D bifurcation normal forms ($y' = -y$ provides the stable direction):

- Saddle-Node: $\dot{x} = r - x^2$, $\dot{y} = -y$
- Transcritical: $\dot{x} = rx - x^2$, $\dot{y} = -y$
- Pitchfork: $\dot{x} = rx - x^3$, $\dot{y} = -y$

---

<a id="sec-16"></a>
## 16. 2D Systems & Limit Cycles

### 16.1 New Phenomena in 2D Systems

Beyond fixed points, 2D systems also feature:

- **Limit cycles**: Isolated closed orbits (distinct from the continuous family of closed orbits around a center)
- Stability of limit cycles: stable (trajectories inside and outside both approach), unstable (both depart), half-stable

### 16.2 Van der Pol Equation & Limit Cycle

$$\ddot{x} + \epsilon(x^2 - 1)\dot{x} + x = 0$$

- $|x| < 1$: negative damping → small oscillations **grow** (excitation)
- $|x| > 1$: positive damping → large oscillations **decay** (dissipation)
- Balance → existence of a **stable limit cycle**

Zeroth order ($\epsilon = 0$): simple harmonic oscillator, $\omega = 1$.

### 16.3 Liénard's Theorem

For $\ddot{x} + f(x)\dot{x} + g(x) = 0$:

- $g$ is odd, $f$ is even
- $F(x) = \int_0^x f(u)du$ satisfies appropriate conditions (single zero, etc.)
→ There exists a **unique stable limit cycle**.

---

<a id="sec-17"></a>
## 17. Fixed Point Dynamics & Hysteresis ⭐

### 17.1 Hysteresis / Catastrophe

Consider an ODE with a slowly varying parameter:

$$\frac{dy}{dt} = y - \frac{y^3}{3} - s(t)$$

where $s(t)$ slowly sweeps ($s = \epsilon t$).

For $s$ constant, fixed points satisfy $s = y - y^3/3$ (S-shaped fold curve). When $s$ crosses the critical value $s = 2/3$, the system jumps abruptly from the upper stable branch to the lower stable branch — a **catastrophe**.

### 17.2 Delayed Bifurcation

At finite sweep rates, the jump does not occur exactly at $s=2/3$ but is **delayed**. The delay is $\propto \epsilon^{2/3}$.

Set $t_c = (s - 2/3)/\epsilon^{2/3}$, expand:
$$Y = 1 + \epsilon^{1/3} Y_{c1} + \epsilon^{2/3} Y_{c2} + \cdots$$

The inner layer ODE evolves into a **Riccati equation**:
$$\frac{dY_{c1}}{dt_c} = -Y_{c1}^2 - t_c$$

Let $Y_{c1} = W'/W$, transforming to the Airy equation $W'' = -t_c W$. The solution is:
$$Y_{c1}(t_c) = -\frac{\text{Ai}'(-t_c)}{\text{Ai}(-t_c)}$$

$Y_{c1}$ diverges (jump) where $\text{Ai}(-t_c) = 0$. The first zero is $t_c \approx 2.338$.

$$\text{Delay } \Delta s = 2.338 \,\epsilon^{2/3}$$

---

---

# Part III-③: Multiple Scale Analysis — Long-Time Evolution Breakdown

> **Failure type**: Regular perturbation expansion over ultra-long intervals → time accumulation → phase/amplitude drift → **Secular Term**
> **Core goal**: Eliminate secular terms → **Amplitude Equation**
> **Two methods**: Poincaré-Lindstedt (periodic solutions only, expand frequency) | Multiple Scale Analysis (periodic + non-periodic, multiple time variables)
>
> ### 🔥 Exam Focus (instructor's emphasis)
> **Multiple Scale Analysis** (instructor's oral description): **The simplest two-timing — $t$ and $\epsilon t$**. Master this and you've essentially mastered the method. The more refined things beyond are icing on the cake.
>
> **Two-Timing Standard Procedure**:
> 1. Introduce $T_0 = t$ (fast scale), $T_1 = \epsilon t$ (slow scale)
> 2. Partial derivative expansion: $\frac{d}{dt} = \frac{\partial}{\partial T_0} + \epsilon\frac{\partial}{\partial T_1}$, $\frac{d^2}{dt^2} = \frac{\partial^2}{\partial T_0^2} + 2\epsilon\frac{\partial^2}{\partial T_0\partial T_1}$
> 3. $O(1)$ gives $Y_0 = A(T_1)e^{iT_0} + c.c.$
> 4. $O(\epsilon)$ remove resonant terms (coefficient of $e^{\pm iT_0}$ = 0) → **Amplitude Equation** $A' = f(A)$
> 5. Solve amplitude equation $A(T_1) = R(T_1)e^{i\theta(T_1)}$, obtain slow-variation evolution
>
> **Exam scope for the two methods**:
> - **Poincaré-Lindstedt**: Expand frequency $\omega = \omega_0 + \epsilon\omega_1 + \cdots$, applicable only to periodic solutions
> - **Multiple Scale Two-Timing**: More general, handles periodic + damping + limit cycle approach
>
> **Classic exam problems**:
> - **Duffing equation** both methods give the unified result: $\omega = 1 + 3\epsilon/8$
> - **Van der Pol** amplitude equation $R' = -R(R^2-1)/2$ → is itself a pitchfork bifurcation structure (converges with §15)
> - **Weakly damped oscillator**: $A' + A = 0 \Rightarrow A = A_0 e^{-T_1}$ → amplitude decays exponentially

<a id="sec-18"></a>
## 18. Forced Harmonic Oscillator

### 18.1 $y'' + \omega_0^2 y = \cos(\omega_f t)$

Homogeneous solution: $y_h = A\cos(\omega_0 t) + B\sin(\omega_0 t)$

Particular solution:
- $\omega_0 \neq \omega_f$: $y_p = \frac{\cos(\omega_f t)}{\omega_0^2 - \omega_f^2}$
- $\omega_0 = \omega_f$ (resonance): **Secular term**
  $$y_p = \frac{t}{2\omega_f} \sin(\omega_f t)$$
  Amplitude grows linearly with time.

**Hallmark of secular terms**: The forcing term is itself a solution of the homogeneous equation.

---

<a id="sec-19"></a>
## 19. Nonlinear Spring & Duffing Oscillator ⭐

### 19.1 Duffing Equation

$$\ddot{y} + y + \epsilon y^3 = 0, \qquad y(0)=1,\; \dot{y}(0)=0$$

- $\epsilon > 0$: hardening spring
- $\epsilon < 0$: softening spring
- No damping, no forcing → expect periodic solution

### 19.2 Failure of Regular Perturbation

Naive expansion $y = y_0 + \epsilon y_1 + \epsilon^2 y_2 + \cdots$

- $O(1)$: $\ddot{y}_0 + y_0 = 0$, $y_0(0)=1$, $\dot{y}_0(0)=0 \Rightarrow y_0 = \cos t$

- $O(\epsilon)$: $\ddot{y}_1 + y_1 = -y_0^3 = -\cos^3 t$

Using trig identity: $\cos^3 t = \frac{1}{4}\cos 3t + \frac{3}{4}\cos t$

$\ddot{y}_1 + y_1 = -\frac{1}{4}\cos 3t - \frac{3}{4}\cos t$

The $\cos t$ term is a **resonant term** → produces **secular term**: $y_1 \sim -\frac{3}{8}t\sin t$

**Problems**:
- The physical solution should be periodic; the secular term destroys periodicity
- When $t = O(1/\epsilon)$, $\epsilon y_1$ is of the same order as $y_0$ → asymptoticity fails
- Secular terms appear at all higher orders

**Root cause**: The Duffing term shifts the oscillation frequency (no longer $\omega=1$), but regular perturbation forces the zeroth-order solution to oscillate at $\omega=1$, causing resonance.

---

<a id="sec-20"></a>
## 20. Poincaré-Lindstedt Method ⭐

### 20.1 Basic Idea

**Expand not only $y$, but also the frequency $\omega$**. Introduce stretched time $\tau = \omega t$:

$$\omega = \omega_0 + \epsilon\omega_1 + \epsilon^2\omega_2 + \cdots$$

The ODE becomes: $\omega^2 Y'' + Y + \epsilon Y^3 = 0$ ($Y' = dY/d\tau$)

### 20.2 P-L Solution for Duffing Equation

Expand $Y = Y_0 + \epsilon Y_1 + \epsilon^2 Y_2 + \cdots$

- $O(1)$: $\omega_0^2 Y_0'' + Y_0 = 0$, $Y_0(0)=1$, $Y_0'(0)=0$
  Physically, when $\epsilon=0$ it's a simple harmonic oscillator → $\omega_0 = 1$, $Y_0 = \cos\tau$

- $O(\epsilon)$: $Y_1'' + Y_1 = -2\omega_1 Y_0'' - Y_0^3$
  Substitute $Y_0 = \cos\tau$ ($Y_0'' = -\cos\tau$) and $\cos^3\tau = \frac{1}{4}\cos 3\tau + \frac{3}{4}\cos\tau$:
  $$Y_1'' + Y_1 = 2\omega_1\cos\tau - \frac{1}{4}\cos 3\tau - \frac{3}{4}\cos\tau$$
  $$= -\frac{1}{4}\cos 3\tau + \left(2\omega_1 - \frac{3}{4}\right)\cos\tau$$

**Resonance elimination condition**: Set the $\cos\tau$ coefficient to zero:
$$2\omega_1 - \frac{3}{4} = 0 \Rightarrow \omega_1 = \frac{3}{8}$$

Remaining: $Y_1'' + Y_1 = -\frac{1}{4}\cos 3\tau$, particular solution $Y_{1p} = \frac{1}{32}\cos 3\tau$

From initial conditions: $Y_1 = \frac{1}{32}(\cos 3\tau - \cos\tau)$

### 20.3 Final Result

$$y(t) \approx \cos\left(\left(1 + \frac{3\epsilon}{8}\right)t\right) + \frac{\epsilon}{32}\left[\cos\left(3\left(1 + \frac{3\epsilon}{8}\right)t\right) - \cos\left(\left(1 + \frac{3\epsilon}{8}\right)t\right)\right]$$

Time stretching $\tau = \omega t = (1 + 3\epsilon/8)t$ → frequency receives an $\epsilon$ correction!

---

<a id="sec-21"></a>
## 21. Multiple Scale Analysis 🔥

### 21.1 Basic Idea

Introduce multiple time scales, treated as **independent variables**:

$$T_0 = t \;\text{(fast)}, \quad T_1 = \epsilon t \;\text{(slow)}, \quad T_2 = \epsilon^2 t \;\text{(slower)}, \ldots$$

**Physical intuition**: The solution is a fast oscillation ($T_0$) whose amplitude/phase is slowly modulated on the slow time $T_1 = \epsilon t$.

Derivative expansion:
$$\frac{d}{dt} = \frac{\partial}{\partial T_0} + \epsilon\frac{\partial}{\partial T_1} + \cdots$$

$$\frac{d^2}{dt^2} = \frac{\partial^2}{\partial T_0^2} + 2\epsilon\frac{\partial^2}{\partial T_0\partial T_1} + \epsilon^2\frac{\partial^2}{\partial T_1^2} + \cdots$$

### 21.2 Multiple Scale Analysis of Duffing Equation

Expand $Y = Y_0 + \epsilon Y_1 + \cdots$

- $O(1)$: $\frac{\partial^2 Y_0}{\partial T_0^2} + Y_0 = 0$ (simple harmonic oscillator in $T_0$)
  $$\Rightarrow Y_0 = A(T_1) e^{iT_0} + \bar{A}(T_1) e^{-iT_0}$$

- $O(\epsilon)$: $\frac{\partial^2 Y_1}{\partial T_0^2} + Y_1 = -Y_0^3 - 2\frac{\partial^2 Y_0}{\partial T_0\partial T_1}$

  The RHS produces resonant terms ($\propto e^{\pm iT_0}$). For the solution to be bounded (eliminate secular terms), the coefficients of resonant terms must be zero:

  $$3A^2\bar{A} + 2i A' = 0 \quad \text{where } A' = \frac{dA}{dT_1}$$

**Amplitude equation**: Let $A(T_1) = R(T_1) e^{i\theta(T_1)}$, substitute $A' = (R' + iR\theta')e^{i\theta}$ to obtain $3R^3 + 2iR' - 2R\theta' = 0$. Separate real and imaginary parts:

- **Imaginary part**: $2R' = 0 \Rightarrow R' = 0 \Rightarrow R = R_0$ (amplitude constant — no damping)
- **Real part**: $-2R\theta' + 3R^3 = 0 \Rightarrow \theta' = \frac{3}{2}R_0^2$

Hence $A(T_1) = R_0 e^{i(3R_0^2 T_1/2 + \theta_0)}$

Substituting back:
$$Y_0 = 2R_0\cos\left(T_0 + \frac{3}{2}R_0^2 T_1 + \theta_0\right)$$

Initial conditions $y(0)=1$, $y'(0)=0 \Rightarrow R_0 = 1/2$, $\theta_0 = 0$:

$$y \approx \cos\left(t + \frac{3\epsilon}{8}t\right) = \cos\left(\left(1 + \frac{3\epsilon}{8}\right)t\right)$$

**Consistent with the P-L method!**

### 21.3 Weakly Damped Oscillator

$\ddot{y} + 2\epsilon\dot{y} + y = 0$, $y(0)=1$, $\dot{y}(0)=0$

Exact solution: $y = A e^{-\epsilon t} \cos(\sqrt{1-\epsilon^2} t + \phi)$

**Regular perturbation**: $y_0 = \cos t$, $y_1$ develops secular term $y_1 = -t\cos t$

**Multiple scale analysis**:
- $O(1)$: $Y_0 = A(T_1)e^{iT_0} + c.c.$
- $O(\epsilon)$: Remove resonance → $A' + A = 0 \Rightarrow A(T_1) = A_0 e^{-T_1}$
- $Y_0 = e^{-\epsilon t}\cos t$ (matches exact solution to $O(\epsilon)$)

### 21.4 Multiple Scale vs P-L Method

| P-L | Multiple Scale |
|-----|--------|
| One stretched time $\tau = \omega t$ | Multiple independent time variables $T_0, T_1, T_2, \ldots$ |
| Adjust $\omega$ to eliminate secular terms | Eliminate resonance to guarantee bounded solution |
| Applicable to periodic motion | Also applicable to asymptotic approach (damping, limit cycle) |
| Effectively equivalent to two-scale analysis | More general, more flexible |

---

<a id="sec-22"></a>
## 22. Van der Pol Equation ⭐

### 22.1 Equation & Physics

$$\ddot{y} + \epsilon(y^2 - 1)\dot{y} + y = 0$$

- **Nonlinear damping** $\epsilon(y^2 - 1)\dot{y}$: $|y| < 1$ negative damping (excitation), $|y| > 1$ positive damping (dissipation)
- $\epsilon = 0$ → simple harmonic oscillator
- $\epsilon > 0$ → existence of a **stable limit cycle**, amplitude $\approx 2$

### 22.2 Multiple Scale Analysis

Fast scale $T_0 = t$, slow scale $T_1 = \epsilon t$

- $O(1)$: $Y_0 = A(T_1) e^{iT_0} + c.c.$

- $O(\epsilon)$: Remove $e^{iT_0}$ resonance → **amplitude equation**:
  $$2A' = -A(|A|^2 - 1)$$

Let $A = R e^{i\theta}$:

Imaginary part: $\theta' = 0 \Rightarrow \theta = \theta_0$ (constant phase)

Real part: $2R' = -R(R^2 - 1)$

### 22.3 Amplitude Dynamics

$$\frac{dR}{dT_1} = -\frac{R}{2}(R^2 - 1)$$

- $R = 0$: **unstable** fixed point
- $R = 1$: **stable** fixed point (→ amplitude $2R = 2$)
- Regardless of initial amplitude, $R \to 1$ ($T_1 \to \infty$)

**Analytic integral**: Let $u = 1/R^2$, then $\dot{u} = u - 1$, solution:

$$R(T_1) = \frac{1}{\sqrt{1 + \left(\frac{1}{R_0^2} - 1\right)e^{-T_1}}}$$

**Zeroth-order solution**:

$$y(t) \approx 2R(\epsilon t) \cos(t + \theta_0) = \frac{2\cos(t + \theta_0)}{\sqrt{1 + \left(\frac{1}{R_0^2} - 1\right)e^{-\epsilon t}}}$$

As $t \to \infty$, the denominator $\to 1$, $y \to 2\cos(t + \theta_0)$ — the limit cycle amplitude is 2.

### 22.4 Physical Mechanism of Limit Cycle Formation

Half a cycle in $|y| < 1$ (excitation), half a cycle in $|y| > 1$ (dissipation), perfectly balanced → stable limit cycle.

---

## Summary: Overall Framework & Section Connections

### I. What Is This Course About?

In one sentence: **When exact solutions are impossible, how to systematically obtain approximate solutions and understand their qualitative behavior.**

The course is organized around the framework of **"Three Types of Failure → Three Methods"**, spanning from asymptotic integrals to dynamical systems bifurcation:

| Failure Type | Manifestation | Method | Core Tool | Relevant Sections |
|----------|------|----------|----------|----------|
| — | (Foundation) Exponential amplification → spike/oscillation | Laplace / Stationary Phase | Taylor expansion + Gaussian integral | §1–§3 |
| — | (Bridge) Traditional methods fail at singularities | Dominant Balance | $y = e^S$ ansatz + $S'' \ll (S')^2$ | §4–§5 |
| **Local Breakdown** | Order reduction → loss of BCs | ① Boundary Layer | Stretching transformation + MAE matching | §6–§11 |
| **Global Breakdown** | $Q(x)$ changes sign → WKB divergence | ② WKB Method | Ansatz + Airy connection | §12–§14 |
| **Long-time Breakdown** | Secular term accumulation → amplitude/phase drift | ③ Multiple Scale | Multiple time scales + elimination of secular terms | §18–§22 |
| — | (Convergence) Qualitative behavior of solutions | Normal Form + Bifurcation | Bifurcation panorama | §15–§17 |

> The two threads ultimately converge: the amplitude dynamics $R' = -R(R^2-1)/2$ of the Van der Pol equation (§22) is essentially a pitchfork bifurcation structure (§15), with the limit cycle corresponding to the stable fixed point.

---

### II. Part I: Asymptotic Theory Foundations (§1–§3)

```
Transcendentally small term e^{-1/ε}  ← Global logical origin (§2.6)
    │  Characteristic: smaller than all ε^n, but physically non-negligible
    │  Consequence: power series expansion "cannot see" it → root of singular perturbation
    │
    ├── Laplace Method (§1)
    │    Core: near φ(t) maximum t_c → Gaussian approximation
    │    Representative example: Gamma function → Stirling's formula
    │    Technical chain: Compress interval → Peak dominance → Taylor expansion → Gaussian integral finale
    │
    ├── Asymptotic Expansion Theory (§2)
    │    Core: Poincaré definition, asymptotic sequence {φ_n}, remainder estimation
    │    Representative example: ∫ e^{-xt}/(1+t) dt → divergent asymptotic series + optimal truncation
    │
    └── Stationary Phase Method (§3)
         Symmetric with Laplace: real exponential peak vs imaginary exponential oscillation
         Key: ψ'(t_s) = 0 where oscillation slows → Fresnel integrals
         Representative example: Bessel J₀(x) ∼ √(2/πx) cos(x - π/4)
         Generalization: no stationary point → integration by parts (bridge to boundary layer)
```

**Cross-section connections**:
- §2 is the theoretical abstraction of §1 — the series produced by Laplace's method is a typical example of asymptotic series
- §3 and §1 are symmetric — technically sharing Taylor expansion + Gaussian integral; complex exponential = real + imaginary, the theory connects seamlessly
- The "transcendentally small term" $e^{-1/\epsilon}$ in §2.6 reappears in §8.1 singular perturbation: the absence of a Taylor expansion is the hallmark of singular perturbation
- **Integration by parts** (§3 no-stationary-point strategy) is the essential prerequisite foundation for subsequent boundary layer analysis

---

### III. Part II: Universal Foundation (§4–§5)

Three tools for transitioning from asymptotic integrals to ODE perturbation: Integration by Parts + Rescaling + Dominant Balance.

```
ODE Local Analysis (§4)
    Ordinary point → Taylor expansion | Regular singular → Frobenius series | Irregular singular → Dominant Balance (enters §5)
         │
         ▼
Dominant Balance (§5)
    Method: set y = e^{S(x)}, use S'' ≪ (S')² to solve order by order
    Representative example: Airy equation → y ∼ C e^{±2x^{-1/2}} x^{3/4}(1 ∓ ...)
         │
         ▼
    [Dominant Balance is the technical foundation for nearly all subsequent methods]
```

**Cross-section connections**:
- §4.4 (Airy equation at infinity is an irregular singular point) → §5 Dominant Balance
- §5 $y = e^S$ ansatz → §12 WKB $y = e^{S/\epsilon}$ ($\epsilon$-parameterized version)
- §8 boundary layer stretching transformation and §12.7 turning point inner layer scaling → both are essentially "re-doing dominant balance near the singularity"

---

### IV. Part III-①: Singular Perturbation · Boundary Layer — Spatial Local Breakdown (§6–§11)

**Failure root**: Highest-order derivative multiplied by $\epsilon$; as $\epsilon \to 0$, the order reduces → unable to satisfy all boundary conditions.

**Standard five-step procedure**: Outer solution → Determine boundary layer location → Inner solution (stretching transformation $X = (x-x_0)/\delta$) → MAE matching → Composite solution.

```
Regular Perturbation (§6–§7)
    Prerequisite: qualitative behavior unchanged as ϵ→0
    Core: expand in powers of ϵ, convert nonlinear to linear sequence
    Drawback: requires knowing the asymptotic sequence (§6.5 non-integer powers); secular terms at resonance (§19)
         │
         └── Not uniformly valid → Singular Perturbation
                 │
                 ▼
Singular Perturbation & Boundary Layer (§8–§11)
    ├── Linear (§8–§10): a(x) sign determines boundary layer location
    │   ├── a(x) > 0 → left boundary (§8, §9)
    │   ├── a(x) < 0 → right boundary (§9)
    │   └── a(x) changes sign → interior/corner layer, δ = ε^{1/2} (§10)
    │
    └── Nonlinear (§11): phase plane geometric method for location
        └── Fast/slow region division → boundary layer at x=1/2
        └── Shares "phase plane" perspective with bifurcation theory (§15)
```

**Cross-section connections**:
- §6.5 (non-integer power expansion failure) → why direct expansion fails → leads to singular perturbation
- §8.1 transcendentally small $e^{-1/\epsilon}$ ← echoes §2.6 (transcendentally small terms)
- §10 (corner layer, $\delta = \epsilon^{1/2}$) ← §12.7 (turning point inner layer, $\delta = \epsilon^{2/3}$) → both use dominant balance to determine scaling
- §11 (nonlinear boundary layer geometric method) → paves the way for §15–§17 phase plane analysis

---

### V. Part III-②: WKB Method — Global Collapse (§12–§14)

**Failure root**: $\epsilon^2 y'' = Q(x)y$ diverges globally where $Q(x)$ changes sign ($1/Q^{1/4}$ blows up). **Difference from boundary layer**: Boundary layer is a local abrupt change; WKB is a global slow-variation failure.

```
WKB Method (§12)
    Ansatz: y = e^{S/ε}, S = S₀ + εS₁ + ...
    Result: Q>0 exponential (trig functions) / Q<0 oscillatory
         │
         ├── Q(x₀) = 0 → Turning Point
         │    Inner layer scaling: x - x₀ = ε^{2/3} Z
         │    Inner layer equation: Airy equation Y_{ZZ} = ZY
         │    Airy function asymptotic behavior ← Laplace/Stationary Phase (§1, §3)
         │    Boundedness requirement → discard Bi, keep only Ai
         │
         ▼
Eigenvalue Problems (§13–§14)
    Single turning point (§13.2): Ai(-E) = 0 → transcendental eigenvalues
    WKB large eigenvalues (§13.3): E_n ∼ n²π²/(∫√Q)²
    Double turning point & Schrödinger (§14): Bohr-Sommerfeld quantization condition
        ∫√(E-V) dx = (n+½)π
```

**Airy function appears three times**: §4.4 (local analysis) → §12.7 (turning point connection) → §17.2 (delayed bifurcation's Riccati→Airy)

**$\epsilon^{2/3}$ scaling appears twice**: turning point inner layer + delayed bifurcation ← both originate from cubic turning, not coincidence

---

### VI. Part IV: Dynamical Systems & Bifurcation — Paradigm Shift to Qualitative Analysis (§15–§17)

From "specific form of the solution" to "qualitative behavior of the solution". Prerequisite tool: **Normal Form**.

```
1D Bifurcation (§15.1) — Three Classic Paradigms
    Saddle-Node: ẋ = x² + r       ← two fixed points annihilate
    Transcritical: ẋ = rx - x²    ← exchange of stability
    Pitchfork: ẋ = rx - x³        ← symmetry breaking (supercritical) / ẋ = rx + x³ (subcritical)
         │
         ├── 2D Bifurcation (§15.2): ẏ = -y → node/saddle/center/spiral
         │
         ├── Limit Cycle (§16): isolated closed orbit
         │   Van der Pol → stable limit cycle ← Liénard's theorem guarantees uniqueness
         │
         └── Slowly Varying Parameter & Hysteresis (§17)
             s = εt slow sweep → Catastrophe
             Delayed bifurcation: Δs ∼ 2.338 ε^{2/3}
             Riccati → Airy transformation (same technique as §12.7)
```

**Standard 4-step for bifurcation**: Select control parameter $r$ → Find fixed points $f(x^*, r)=0$ → Determine stability via sign of $f'(x^*)$ → Sketch bifurcation diagram $x^*$ vs $r$

---

### VII. Part III-③: Multiple Scale Analysis — Long-Time Evolution Breakdown (§18–§22)

**Failure root**: Regular perturbation expansion over ultra-long intervals → time accumulation → cumulative phase error → **Secular Term**. Eliminating secular terms = eliminating resonance = obtaining the Amplitude Equation.

```
Forced Harmonic Oscillator (§18)
    Resonance → t·sin(ωt) secular term → problem origin
         │
         ▼
Duffing Oscillator (§19)
    Nonlinear spring → frequency shift → regular perturbation forces ω=1 → secular terms at every order
    Root cause: true frequency ω ≠ 1; regular perturbation forces the wrong frequency, causing resonance
         │
         ├── Poincaré-Lindstedt (§20)
         │    Simultaneously expand y and ω: ω = 1 + 3ε/8 + ...
         │    Eliminate secular terms by adjusting ω → applicable only to periodic solutions
         │
         └── Multiple Scale Analysis (§21)
              Introduce T₀=t (fast), T₁=εt (slow) → partial derivative expansion
              Resonance elimination condition → Amplitude Equation A' = f(A)
              Scope: periodic + damping + limit cycle approach
              Physical picture: fast oscillation × slow modulation
                  │
                  ▼
Van der Pol Equation (§22)  ← Complete application example of multiple scales
    Nonlinear damping: |y|<1 excitation ↔ |y|>1 dissipation
    Amplitude equation: 2R' = -R(R²-1) → R=0 unstable, R=1 stable
    Limit cycle amplitude = 2 → converges with bifurcation theory (§15–§16)
```

**Cross-section connections**:
- §18 is the problem origin, §19 demonstrates deterioration, §20–§21 provide two solution approaches
- P-L (§20) and Multiple Scale (§21) give identical results for Duffing ($\omega = 1+3\epsilon/8$), but Multiple Scale is more flexible
- §22 Van der Pol amplitude equation $R' = -R(R^2-1)/2$ → is essentially a pitchfork bifurcation (§15) structure
- Van der Pol runs through three places: §16.2 (limit cycle concept) → §11 (phase plane geometry) → §22 (multiple scale quantitative analysis)

---

### VIII. Recurring Tools Overview

| Tool | Appearing Sections | Role |
|------|----------|------|
| **Gaussian Integral** | §1, §3, §5 | Final integral form for various asymptotic estimates |
| **Taylor Expansion** | §1–§8, §19–§21 | Fundamental means of local approximation |
| **Integration by Parts** | §3, §8, §9 | No-stationary-point strategy + bridge to boundary layer analysis |
| **Dominant Balance** | §5, §8, §9, §10, §11, §12 | Determines stretching scales and dominant terms |
| **Exponential Ansatz $y=e^S$** | §5, §12 | Unified method for irregular singular points and WKB |
| **Stretching Transformation + Rescaling** | §8, §9, §10, §11, §12.7, §17.2 | Reveals correct scales for inner layer / boundary layer / turning point |
| **Matching Condition (MAE)** | §8, §9, §10, §11, §12.7, §14 | Connecting inner/outer, left/right solutions |
| **Fresnel Integrals** | §3 | Computational core of the stationary phase method |
| **Airy Function** | §4.4, §12.7, §13.2, §17.2 | Connection for turning point / corner layer / delayed bifurcation |
| **Riccati → Airy** | §12.7, §17.2 | Transformation technique: nonlinear → linear |
| **Phase Plane Analysis** | §11, §15, §16 | Geometric intuition: trajectories, fixed points, limit cycles |
| **Normal Form** | §15 | Topological simplification → standardization, entry point to bifurcation theory |
| **Secular Terms / Resonance** | §18, §19, §20, §21, §22 | Hallmark of regular perturbation failure and target of elimination |
| **Complex Integration / Contour Deformation** | §3, §12.7 | Handling oscillatory integrals and special functions |

---

### IX. Review Suggestions — Connect via "Three Failures → Three Methods"

```
First pass: Main trunk (connected by failure type)
  §1 (Laplace) → §2.6 (Transcendentally small term — global logical origin)
  → §4 (Singularity classification) → §5 (Dominant Balance — technical foundation)
  → §8 (Singular perturbation — ① Spatial local breakdown → Boundary Layer)
  → §12 (WKB — ② Global collapse → Airy connection)
  → §15 (Bifurcation — Normal Form → Qualitative analysis)
  → §18–§19–§20–§21 (Secular terms → ③ Long-time breakdown → Multiple Scale)

Second pass: Branch deeper
  §3 (Stationary Phase, read symmetrically with §1)
  §6–§7 (Regular perturbation fundamentals) + §9–§10–§11 (Boundary layer advanced: location/thickness/corner layer/nonlinear)
  §13–§14 (Eigenvalues + Schrödinger, natural WKB applications)
  §16–§17 (Limit cycles + Liénard + Delayed bifurcation)
  §22 (Van der Pol — complete multiple scale example → convergence with bifurcation)

Third pass: Forge connections
  Pay attention to "transcendentally small term e^{-1/ε}" running throughout (§2.6 → §8.1 → WKB → Multiple Scale)
  Pay attention to "Dominant Balance" repeatedly used in §5, §8, §10, §11, §12
  Pay attention to the three appearances of the Airy function (§4.4 → §12.7 → §17.2)
  Pay attention to the two appearances of the ε^{2/3} scaling (turning point + delayed bifurcation)
  Pay attention to Integration by Parts as the bridge from "asymptotic integrals → boundary layer"
```

---

## Supplement 1: Rayleigh-Lorentz Oscillator ⭐

> Instructor requires: understand core concepts — energy non-conservation, adiabatic invariant

### Equation

$$\ddot{x} + \epsilon(\dot{x}^2 - 1)\dot{x} + x = 0$$

Difference from Van der Pol: the damping term is $\epsilon(\dot{x}^2 - 1)\dot{x}$ (depends on velocity squared), rather than $\epsilon(x^2 - 1)\dot{x}$ (depends on displacement squared).

### Core Physical Concepts

- **Energy non-conservation**: The system is non-conservative; nonlinear damping causes energy to vary within a cycle
- **Adiabatic Invariant**: When parameters vary slowly, the action $J = \oint p\,dq$ is approximately conserved. In oscillatory systems, $E/\omega \approx$ constant
- Connection to Van der Pol: both produce **stable limit cycles**, but the damping mechanisms differ

### Exam Key Points
- Understand the physical meaning of energy non-conservation
- Understand the basic concept of adiabatic invariant: $E/\omega$ remains (approximately) constant under slowly varying parameters
- Full solution not required, but should understand the relationship to Van der Pol/Duffing

---

## Supplement 2: Discretization ⭐

> Instructor requires: master the basic ability to discretize continuous problems

### Core Idea

Convert continuous ODEs/PDEs into discrete difference equations for numerical solution or analysis.

### Basic Methods

**First derivative**:
- Forward difference: $y'(x) \approx \frac{y(x+h) - y(x)}{h}$
- Backward difference: $y'(x) \approx \frac{y(x) - y(x-h)}{h}$
- Central difference: $y'(x) \approx \frac{y(x+h) - y(x-h)}{2h}$ ($O(h^2)$)

**Second derivative**:
$$y''(x) \approx \frac{y(x+h) - 2y(x) + y(x-h)}{h^2}$$

### Applications in the Course

1. **Boundary value problems**: $y'' = f(x,y,y')$ → grid points $x_i$ → difference equations → tridiagonal linear system
2. **Eigenvalue problems**: $y'' = \lambda y$ → discretization → $Ay = \lambda y$ (matrix eigenvalue problem)
3. **Bifurcation analysis**: continuous ODE $\dot{x} = f(x;r)$ → fixed-point iteration $x_{n+1} = F(x_n;r)$

### Exam Key Points
- Be able to write a simple second-order ODE boundary value problem in difference form
- Understand the effect of $h$ choice on accuracy ($O(h)$ vs $O(h^2)$)
- Understand discretization as an iterative tool in bifurcation analysis

---

> For more framework analysis see [`脉络图整理.md`](脉络图整理.md)
