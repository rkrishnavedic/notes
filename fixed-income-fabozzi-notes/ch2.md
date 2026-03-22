## 🧱 1. Core Framework

Bond price is a function of multiple risk factors:

$$
P = f(r_1, r_2, ..., r_T; s; \sigma; CF)
$$

- $r_t$ = spot rates (yield curve)
- $s$ = credit spread
- $\sigma$ = volatility (for optionality)
- $CF$ = cashflows (possibly stochastic)

---

### Risk Definition

Risk = sensitivity of price to inputs:

$$
\frac{\partial P}{\partial r_t}, \quad \frac{\partial^2 P}{\partial r_t^2}, \quad \frac{\partial P}{\partial s}
$$

---

## 📉 2. Interest Rate Risk (Duration)

### Definition

$$
D = -\frac{1}{P} \frac{dP}{dy}
$$

---

### First-Order Approximation

$$
\frac{\Delta P}{P} \approx -D \Delta y
$$

---

### Insight

- Measures price sensitivity to yield  
- Increases with maturity  
- Decreases with coupon  

---

## 📈 3. Convexity (Second-Order Risk)

### Definition

$$
C = \frac{1}{P} \frac{d^2P}{dy^2}
$$

---

### Approximation

$$
\frac{\Delta P}{P} \approx -D \Delta y + \frac{1}{2} C (\Delta y)^2
$$

---

### Insight

- Captures nonlinearity  
- Improves large-move estimates  
- Positive for option-free bonds  

---

## 🔗 4. Yield Curve Risk

### Multi-Factor Pricing

$$
P = \sum_{t=1}^{T} \frac{CF_t}{(1 + r_t)^t}
$$

---

### Interpretation

- Each maturity has its own rate  
- Risk comes from:
  - parallel shifts  
  - twists  
  - curvature changes  

---

### Quant View

$$
P = P(r_1, r_2, ..., r_T)
$$

---

## 🔄 5. Reinvestment Risk

### Future Value of Coupons

$$
FV = \sum_{t=1}^{h} C (1 + r_t)^{h-t}
$$

---

### Insight

- Depends on future interest rates  
- Drives difference between:
  - YTM  
  - realized return  

---

## 🔁 6. Embedded Option Risk

### Callable Bond

$$
P_{callable} = P_{straight} - P_{option}
$$

---

### Effects

- Cashflows become stochastic  
- Duration becomes unstable  
- Convexity can become negative  

---

### Modeling

- Use effective duration  
- Requires interest rate models  

---

## ⚠️ 7. Credit Risk

### Expected Cashflow

$$
E[CF_t] = CF_t (1 - PD) + RR \cdot M \cdot PD
$$

---

### Spread Decomposition

$$
y = r + s
$$

---

### Risk

- Spread widening → price falls  

---

## 💧 8. Liquidity Risk

### Proxy

$$
\text{Spread} = \text{Ask} - \text{Bid}
$$

---

### Insight

- Cost of execution  
- Observed price ≠ theoretical price  

---

## 🔥 9. Critical Quant Insights

### 1. Risk = Derivatives of Price
All risks reduce to sensitivities

---

### 2. Duration ≈ First Derivative
Convexity ≈ Second Derivative

---

### 3. Multi-Factor Reality
Rates are not one variable

---

### 4. Optionality Breaks Linearity
Cashflows become path-dependent

---

### 5. Return ≠ Yield
Reinvestment risk drives divergence

---

## 🚀 ONE-LINE

Risk = sensitivity of bond price to yield curve, credit, volatility, and liquidity factors

## Minute Notes:
- Nominal = quoted (inflation-included), Notional = principal amount
- Inflation risk = uncertainty in real discount rate, reducing real value of fixed nominal cashflows.
---
# Book Summary
For a fixed-income quantitative strategist, risk is the **sensitivity of the price function** to stochastic and deterministic market inputs.

### **1. CORE FRAMEWORK**
*   **Pricing Function:** $P = f(r_1, r_2, ..., r_T; s; \sigma; \text{Cashflows})$.
*   **Bond Price (Spot Rate Form):** $P = \sum_{t=1}^{T} \frac{CF_t}{(1+z_t)^t}$.
*   **Risk Definition:** The partial derivatives (Greeks) of the price function with respect to input variables: $\frac{\partial P}{\partial z_t}$ (Duration), $\frac{\partial^2 P}{\partial z_t^2}$ (Convexity), and $\frac{\partial P}{\partial \sigma}$ (Volatility Risk).

---

### **2. INTEREST RATE RISK**
*   **Mathematical Interpretation:** Duration—the approximate percentage change in price for a 100 basis point change in yields.
*   **Duration Estimation:** $D = \frac{V_- - V_+}{2V_0(\Delta y)}$.
*   **First-Order Approximation:** $\frac{\Delta P}{P} \approx -D \times \Delta y$.
*   **Pricing Impact:** Market value moves in the opposite direction of rate changes.

---

### **3. SECOND-ORDER EFFECT (CONVEXITY)**
*   **Second Derivative:** $C = \frac{V_- + V_+ - 2V_0}{2V_0(\Delta y)^2}$.
*   **Improved Approximation:** $\frac{\Delta P}{P} \approx [-D \times \Delta y] + [\frac{1}{2}C \times (\Delta y)^2]$.
*   **Mathematical Necessity:** The relationship is nonlinear (convex); duration alone systematically underestimates the new price for large yield changes.

---

### **4. YIELD CURVE (TERM STRUCTURE) RISK**
*   **Vector Sensitivity:** Replaces a single yield with a vector of spot rates $\vec{z} = [z_{0.5}, z_1, ..., z_T]$.
*   **Modeling Implication:** Risks arise from non-parallel shifts (twists or humps) where yields at different maturities move by unequal amounts.
*   **Pricing:** $P = \sum_{t=1}^{n} \frac{c}{(1+z_t)^t} + \frac{M}{(1+z_n)^n}$.

---

### **5. REINVESTMENT RISK**
*   **Uncertain Future Value:** Realized return depends on the stochastic rate $r_{reinvest}$ for all interim "interest-on-interest".
*   **Impact:** $FV_{horizon} = \sum_{t=1}^{h} c(1+r_t)^{h-t}$.
*   **Risk Scaling:** Risk increases with longer holding periods and larger/earlier cash flows (high-coupon bonds).

---

### **6. EMBEDDED OPTION RISK (CALL/PREPAYMENT)**
*   **Option-Adjusted Pricing:** $P_{callable} = P_{straight} - P_{call\_option}$.
*   **Convexity Impact:** At low yields, the bond exhibits **negative convexity** (price appreciation is truncated because the issuer is likely to call).
*   **Modeling Implication:** Effective duration ($D_{eff}$) must be used to account for changes in expected cash flow timing as rates move.

---

### **7. CREDIT RISK (BASIC)**
*   **Expected Cash Flow:** $E[CF_t] = CF_t(1 - PD) + M(PD)(RR)$, where $PD$ is probability of default and $RR$ is recovery rate.
*   **Spread Sensitivity:** $Spread = Base Rate + Risk Premium$.
*   **Credit Spread Risk:** The risk that the market demands a higher spread due to perceived default probability or rating agency downgrades.

---

### **8. LIQUIDITY RISK**
*   **Execution Cost:** The wedge between observed theoretical price and the price at which an investor must sell.
*   **Mathematical Proxy:** The **Bid-Ask Spread**.
*   **Market Spread:** $Lowest Ask - Highest Bid$.
* Mark-to-market pricing depends on observable market prices, but for illiquid bonds, prices are often estimated using dealer quotes or models, introducing uncertainty and dispersion. Liquidity risk therefore manifests as both execution cost and ambiguity in true valuation, making observed prices potentially unreliable and artificially smooth.
---

### **9. WHAT TO IGNORE**
*   Descriptive taxonomy of rating agency symbols (e.g., Baa vs BBB).
*   Historical anecdotes of industrial accidents or specific LBOs (e.g., RJR Nabisco).
*   Internal syndicate structures, "running the books," and T+3 settlement logistics.
*   Descriptive issuer histories (Anheuser Busch examples).

---

### **10. 5 CRITICAL QUANT INSIGHTS**
1.  **Immunization Logic:** Interest-rate risk and reinvestment risk oppose each other; a portfolio is immunized when these effects offset.
2.  **Duration as Volatility Proxy:** Duration is the price sensitivity of a zero-coupon bond with that specific maturity.
3.  **Convexity Advantage:** Positive convexity is desirable; high-convexity bonds can offer a given expected return at a lower yield level.
4.  **Yield-to-Worst:** In securities with multiple options, the only conservative valuation metric is the minimum of all potential exercise outcomes.
5.  **Volatility Scaling:** Duration is meaningless without yield volatility; the risk of a position is its price sensitivity multiplied by the probability of rate movement.
