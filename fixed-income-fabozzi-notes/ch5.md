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
