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
  $$\[
  P = \sum_{t} \frac{CF_t}{(1+z_t)^t}
  \]$$
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
- Definition: implied future rates $\( f(t_1, t_2) \)$
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
