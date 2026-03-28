## Pricing vs Expectation

---

### 1. Arbitrage

Start with a simple idea:

If there is a way to make money with:
- zero initial cost
- no risk

then the market is inconsistent.

So we impose:
> no-arbitrage

---

From this, we construct a strategy:

- borrow $S_0$
- buy the stock
- hold until $T$

At time $T$:
- repay loan = $S_0 e^{rT}$
- deliver stock

This strategy is **riskless**.

So any forward contract must have the same cost.

Otherwise:
- if forward price is lower → seller arbitrage  
- if higher → buyer arbitrage  

Hence:
$$F = S_0 e^{rT}$$

This is an **enforced price** — it comes from the existence of a replicating strategy.

---

### 2. Expectation vs Arbitrage (Section 1.2 insight)

A natural thought is:

“Stock grows on average at $\mu$, so price should be related to that.”

This leads to:
$$S_0 e^{(\mu + \tfrac{1}{2}\sigma^2)T}$$

This comes from:
- expectation
- strong law type reasoning

But this is not usable for pricing.

Why?

Because:
- $\mu$ is not tradable
- $\mu$ is subjective
- different agents have different $\mu$

So it cannot pin down a unique price.

---

### 3. Breakdown of Expectation

Expectation-based thinking works for simple cases like forwards (coincidentally).

But it fails for derivatives like options.

Reason:
- options have nonlinear payoffs
- cannot be replicated by “buy and hold”

So pricing cannot come from:
> “what do I expect $S_T$ to be?”

Instead it must come from:
> “can I replicate the payoff using tradable assets?”

---

### 4. Role of Expectation (important subtlety)

Expectation is not discarded.

It comes back later as:
> risk-neutral expectation

But:
- not using $\mu$
- using $r$ instead

This is derived from arbitrage, not assumed.

---

### 5. What is actually being priced

We are not trying to estimate $S_T$.

We are computing:

> the cost today of constructing a strategy that delivers the same payoff

That cost determines the price.

---

### 6. Final clarity (forward price)

There are two candidates:

- from expectation: $S_0 e^{(\mu + \tfrac{1}{2}\sigma^2)T}$  
- from arbitrage:   $S_0 e^{rT}$

Correct one:

$$F = S_0 e^{rT}$$

because:
- it comes from a replicating strategy
- it is enforceable in the market

---

### 7. Bottom line

Pricing:
- based on replication
- enforced by arbitrage
- uses $r$

Expectation:
- based on beliefs
- not enforceable
- uses $\mu$

They are fundamentally different objects.
