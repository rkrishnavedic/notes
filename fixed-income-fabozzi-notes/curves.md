# Fixed Income Curves — Quant Cheat Sheet

## 1. Price–Yield Curve (Single Bond)
- Definition: $\( P = f(y) \)$ for a given bond  
- X-axis: yield $\( y \)$, Y-axis: price $\( P \)$  
- Shape: downward sloping, convex  
- Use: duration, convexity, P&L approximation  
- Interpretation: sensitivity of price to yield changes  

---

## 2. Spot Curve (Zero Curve)
- Definition: $\( z_t \)$ for each maturity $\( t \)$  
- Built via bootstrapping  
- Pricing equation:
  $$P = \sum_{t} \frac{CF_t}{(1+z_t)^t}$$
- Use: valuation, discounting, arbitrage-free pricing  
- Interpretation: true term structure of interest rates  

---

## 3. Yield Curve (Par Curve)
- Definition: yields of par bonds across maturities  
- Market convention for quoting yields  
- Derived from spot curve  
- Use: benchmarking, communication  
- Interpretation: simplified view of interest rates  

---

## 4. Forward Curve
- Definition: implied future rates $f(t_1, t_2)$
- Derived from spot curve  
- Use: expectations, trading, relative value  
- Interpretation: market-implied future interest rates  

---

## Key Distinctions
- Price–Yield Curve ≠ Spot Curve  
- Yield = single-number summary  
- Spot curve = full term structure used for pricing  

---

## Quant Mapping

| Concept        | Curve             |
|----------------|------------------|
| Pricing        | Spot curve        |
| Risk ($\Delta P$)      | Price–yield curve |
| Market quotes  | Par yield curve   |
| Expectations   | Forward curve     |

---

## One-Liner

Spot curve prices bonds, price–yield curve measures risk, forward curve encodes expectations, and par curve is a market quoting convention.

---

# Roll-down vs Convexity — Core Insight

## 1. Price–Yield Curve (Risk View)
- Shape: **Downward sloping and convex**
- Relationship:
  $$P = f(y), \quad \frac{dP}{dy} < 0, \quad \frac{d^2P}{dy^2} > 0$$
- Interpretation:
  - Yield ↑ → Price ↓
  - Convexity → nonlinear (asymmetric) price response
- Use:
  - Duration (first-order sensitivity)
  - Convexity (second-order sensitivity)
- Dimension: **Yield changes (no time evolution)**

---

## 2. Yield Curve (Spot / Par Curve — Time View)
- Shape: Typically **upward sloping and mildly concave**
- Representation:
  $$y = y(t) \quad \text{or} \quad z_t$$
- Interpretation:
  - Longer maturity → higher yield (in normal markets)
- Use:
  - Discounting
  - Relative value
  - Carry and roll-down
- Dimension: **Maturity (time structure of rates)**

---

## 3. Roll-down (Time Evolution Effect)
- Mechanism:
  - Bond maturity decreases over time: $$T \to T - \Delta t$$
  - Bond is repriced using a **different point on the yield curve**
- Condition:
  - Yield curve is **upward sloping**
- Effect:
  - Shorter maturity → lower yield
  - Lower yield → higher price
- Return component:
  - **Roll-down = price gain due to curve shape, not rate change**

---

## Key Distinction

| Concept     | Curve            | Driver              | Interpretation              |
|------------|------------------|---------------------|-----------------------------|
| Convexity  | Price–Yield      | Yield changes       | Nonlinear price sensitivity |
| Roll-down  | Yield Curve      | Time (maturity)     | Curve-shape-driven return   |

---

## Final One-Liner

Convexity belongs to the price–yield curve and measures how price reacts to yield changes, while roll-down occurs along the yield curve as maturity shortens, generating return from the curve’s shape even if yields do not move.
