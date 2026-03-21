## 🧱 1. Core Pricing Equation

### Arbitrage-Free Form (Term Structure)

$$
P = \sum_{t=1}^{T} \frac{CF_t}{(1 + r_t)^t}
$$

- $CF_t$ = cashflow at time $t$
- $r_t$ = spot rate for maturity $t$

---

### YTM Approximation

$$
P = \sum_{t=1}^{T} \frac{C}{(1+i)^t} + \frac{M}{(1+i)^T}
$$

- $i$ = yield to maturity

👉 Used for quoting, not true pricing

---

## 🔍 2. Yield (YTM)

Defined implicitly:

$$
P_{\text{market}} = P_{\text{model}}(i)
$$

---

### Root-Finding Form

$$
f(i) = P_{\text{model}}(i) - P_{\text{market}} = 0
$$

---

### Properties:
- Nonlinear equation  
- No closed-form solution  
- Requires numerical methods  

---

### ⚠️ YTM Assumptions

- Flat yield curve  
- Reinvestment at $i$  
- Hold to maturity  

👉 Hence: not a true return measure

---

## 📉 3. Price–Yield Relationship

$$
\frac{dP}{di} < 0, \quad \frac{d^2P}{di^2} > 0
$$

---

### Interpretation:
- Price decreases as yield increases  
- Relationship is convex (nonlinear)  

---

## 🧩 4. Special Cases

### Zero-Coupon Bond

$$
P = \frac{M}{(1+i)^T}
$$

---

### Perpetuity

$$
P = \frac{C}{i}
$$

---

### Relative Pricing

- $C > i \Rightarrow P > M$ (Premium)  
- $C < i \Rightarrow P < M$ (Discount)  
- $C = i \Rightarrow P = M$ (Par)  

---

## 💰 5. Clean vs Dirty Price

$$
P_{\text{dirty}} = P_{\text{clean}} + AI
$$

$$
AI = C \cdot \frac{\text{Time Elapsed}}{\text{Coupon Period}}
$$

---

### Insight:
- Models compute dirty price  
- Market quotes clean price  

---

## 🔄 6. Return Insight

$$
\text{Return} \neq \text{YTM}
$$

---

### Reason:
- Reinvestment rate ≠ YTM  
- Holding period may differ  

---

## 🔥 7. Critical Quant Insights

### 1. Bond = Sum of Zero-Coupon Bonds
Each cashflow discounted separately

---

### 2. Price → Yield
Yield is implied from price

---

### 3. Bond = Function

$$
P = P(i)
$$

→ enables differentiation → risk

---

### 4. Pull-to-Par

If $i$ constant:

$$
P \to M \quad \text{as } t \to T
$$

---

### 5. Convexity Exists
Second-order effects matter

---

## 🚀 ONE-LINE

Bond = discounted cashflows (term structure) with yield as IRR approximation
---
# Book Summary
### **1. CORE PRICING FRAMEWORK**
*   **Main Equation (General DCF):** $P = \sum_{t=1}^{n} \frac{c}{(1+i)^t} + \frac{M}{(1+i)^n}$.
*   **Variable Definitions:**
    *   $P$: Present value (Price).
    *   $c$: Periodic coupon payment.
    *   $n$: Number of discounting periods (Years $\times$ Frequency).
    *   $i$: Periodic discount rate (Annual Yield / Frequency).
    *   $M$: Maturity (Par) value.
*   **Zero-Coupon Form:** $P = \frac{M}{(1+i)^n}$.
*   **Coupon Bond (Fractional Period):** $P = \frac{c}{(1+i)^w} + \frac{c}{(1+i)^{1+w}} + \dots + \frac{M}{(1+i)^{n-1+w}}$ where $w = \frac{\text{Days to next coupon}}{\text{Basis}}$.

### **2. YIELD AS A SOLUTION (CRITICAL)**
*   **Root-Finding Problem:** $f(i) = \left[ \sum_{t=1}^{n} \frac{c}{(1+i)^t} + \frac{M}{(1+i)^n} \right] - P_{market} = 0$.
*   **Nature of Solution:** YTM is the value $i$ that satisfies the equation above.
*   **Complexity:** It is a polynomial equation of degree $n$. Since $n$ usually exceeds 4, there is no closed-form algebraic solution (Abel-Ruffini theorem context); it requires iterative numerical methods (e.g., Newton-Raphson).

### **3. PRICE–YIELD RELATIONSHIP**
*   **Mathematical Direction:** $\frac{dP}{di} < 0$ (Monotonically decreasing).
*   **Nonlinearity:** The relationship is **convex** ($\frac{d^2P}{di^2} > 0$ for option-free bonds).
*   **Reasoning:** Price is a summation of convex functions $(1+i)^{-t}$. Consequently, the absolute price appreciation for a yield decrease $(-\Delta i)$ is greater than the price depreciation for an equivalent yield increase $(+\Delta i)$.

### **4. SPECIAL CASES**
*   **Zero-Coupon:** $P = M(1+i)^{-n}$ (Maximizes $\frac{dP}{di}$ sensitivity for a given $n$).
*   **Premium Bond:** $c > i \iff P > M$.
*   **Discount Bond:** $c < i \iff P < M$.
*   **Par Bond:** $c = i \iff P = M$.

### **5. CLEAN VS DIRTY PRICE**
*   **Mathematical Identity:** $P_{dirty} = P_{clean} + AI$.
*   **Accrued Interest (AI):** $AI = c \times \left( \frac{\text{Days since last coupon}}{\text{Days in coupon period}} \right)$.
*   **Quant Note:** Models compute $P_{dirty}$ (PV of all future flows); $P_{clean}$ is a quote convention to remove "sawtooth" price jumps on coupon dates.

### **6. WHAT TO IGNORE**
*   **Current Yield:** Mathematically useless; ignores capital gains/losses and TVM.
*   **Manual Trial-and-Error:** Quants use algorithmic root-finders.
*   **Naming Conventions:** "Anheuser Busch 8 5/8s" labels do not affect stochastic modeling.
*   **Bond Tables:** Arithmetical look-up tables are replaced by code.
*   **Time Value of Money (Basic Intro):** Prerequisite knowledge.

### **7. 5 CRITICAL INSIGHTS**
1.  **Bond as a Package of Zeros:** Arbitrage ensures a coupon bond's price equals the sum of its component zero-coupon cash flows discounted at their respective spot rates.
2.  **The Reinvestment Trap:** YTM mathematically assumes interim cash flows are reinvested at the YTM rate—a significant source of realized return variance if rates shift.
3.  **Total Return (Horizon Return):** This is the only measure that captures actual realized return by explicitly modeling the reinvestment rate and the terminal exit yield.
4.  **Pull-to-Par (Convergence):** If $i$ is constant, $P \to M$ as $t \to n$. This "rolldown" is a deterministic component of return often used in "carry" strategies.
5.  **Convexity Advantage:** Positive convexity means the "tangent line" (Duration) always underestimates the actual price of an option-free bond regardless of yield move direction.
