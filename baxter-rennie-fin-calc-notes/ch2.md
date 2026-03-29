## Binomial + Replication

---

### 1. Setup

- Stock today: $S_1$  
- Next step:
  - up → $S_3$  
  - down → $S_2$  

- Derivative payoff:
  - up → $f_3$  
  - down → $f_2$  

---

### 2. Goal

Find price today: $f_1$

---

### 3. Replication idea

Construct portfolio:

$$ \Pi = \Delta S + B $$

such that:

- Up state:
  $$\Delta S_3 + B e^{r\Delta t} = f_3$$

- Down state:
  $$\Delta S_2 + B e^{r\Delta t} = f_2$$

Solve → get unique $(\Delta, B)$

---

### 4. Price

$$ f_1 = \Delta S_1 + B $$

---

### 5. What is really happening

- We are NOT making $f_2 = f_3$  
- We are matching:
  > portfolio payoff = derivative payoff (state-by-state)

---

### 6. Where “riskless” comes in

- Portfolio − Derivative = 0 in all states  
- ⇒ riskless position  
- ⇒ must have zero cost  

⇒ prices must match

---

### 7. Role of $\Delta$ and $B$

- $\Delta$:
  - $>0$ → long stock  
  - $<0$ → short stock  

- $B$:
  - $>0$ → lend (invest)  
  - $<0$ → borrow  

---

### 8. No-arbitrage principle

If:
- same payoff in all states  

Then:
> same price today

---

### 9. Expectation vs pricing

- Expectation uses $\mu$ → not reliable  
- Pricing uses replication → enforced  

Correct price comes from:
- tradable strategy  
- not beliefs

---

### 10. Risk-neutral form (derived, not assumed)

Price can be written as:

$$f_1 = e^{-r\Delta t} \left( q f_3 + (1-q) f_2 \right)$$

$q$ is:
- not real probability  
- comes from no-arbitrage  

---

### 11. Delta hedging intuition

- $\Delta$ = units of stock needed to match derivative locally  
- Adjust $\Delta$ as $S$ changes  
- Portfolio becomes locally riskless  

---

### 12. Big picture

- Price = cost of replication  
- Replication = stock + bond  
- Arbitrage enforces consistency  
- Probability appears later as a tool
