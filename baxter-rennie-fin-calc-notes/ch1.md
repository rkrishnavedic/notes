### 🔑 Core Principle
> **Prices are determined by arbitrage, NOT by expectations.**

---

### ⚖️ Two Competing Views

- **Expectation-based (wrong for pricing):**
  - Uses real-world drift $\( \mu \)$
  - Based on beliefs about future growth
  - Example: $\( S_0 e^{(\mu + \tfrac{1}{2}\sigma^2)T} \)$

- **Arbitrage-free (correct):**
  - Uses risk-free rate $\( r \)$
  - Based on replication and tradable strategies
  - Example: $\( S_0 e^{rT} \)$

---

### 💥 Key Insight

> Even if $\( \mu > r \)$, **forward prices do NOT depend on $\( \mu \)$**

- Expected return ≠ pricing input  
- Beliefs ≠ enforceable market prices  

---

### 🔒 “Enforced Price” Meaning

- If price ≠ arbitrage-free price:
  - Traders exploit it immediately
  - Riskless profit opportunity appears
- Therefore:
  > **Only arbitrage-free price can survive in the market**

---

### 🧠 Deep Intuition

- $\( \mu \)$ → subjective (depends on model, beliefs)
- $\( r \)$ → objective (locked by trading strategies)

> **Markets eliminate opinions, but enforce arbitrage.**

---

### 🚀 Quant Mental Model

- Pricing = **No-Arbitrage + Replication**
- NOT = Expectation / Forecasting

---

### ⚡ One-Liner

> “If an arbitrage price exists, any other price is too dangerous to quote.”

---
## 📌 Essence: Expectation vs Arbitrage

### 🔑 Core Shift
> **Expectation (μ) fails for pricing derivatives → Arbitrage + replication takes over**

---

### ❌ Why Expectation Fails
- Works for simple products (e.g., forwards)
- Breaks for **nonlinear payoffs** (e.g., options)
- Cannot replicate options by “buy and hold”

---

### ⚙️ What Replaces It
- **Replication strategies** (dynamic trading)
- **No-arbitrage principle**
- Prices determined by **constructing the payoff**

---

### 🧠 Role of Expectation (Subtle Point)
> Expectation is NOT discarded — it is reinterpreted

- Used later as:
  - **Risk-neutral expectation**
- Not based on real-world drift \( \mu \), but on \( r \)

---

### 📉 Historical Insight
- Pre-1973: Pricing via expectation seemed reasonable  
- Post-Black–Scholes: Arbitrage framework dominates  

---

### 🧩 Big Structural Idea
> **All derivatives can be replicated using underlying + cash**

→ Therefore:
> **Price = cost of replication**

---

### ⚡ One-Liner
> “We don’t price by predicting outcomes, we price by eliminating arbitrage.”
