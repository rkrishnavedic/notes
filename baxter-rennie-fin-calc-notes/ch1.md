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
---

## Why probability theory is still needed

---

### 1. Arbitrage gives structure, not numbers

No-arbitrage tells you:

- prices must be consistent
- replication must exist
- there is a unique “fair price”

But it does NOT tell you directly:
- what the price is in complex situations
- how to compute it efficiently

---

### 2. Replication becomes dynamic

For simple cases (like forwards):
- replication is trivial
- one trade at time 0 is enough

For options:
- replication requires continuous rebalancing
- hedge ratios change with time and price

So you need a model for:
- how $S_t$ evolves

---

### 3. This is where stochastic processes enter

We model the stock as:
- a random process (e.g. Brownian motion)

This lets us:
- describe all possible paths of $S_t$
- compute how hedging strategies behave over time

---

### 4. Risk-neutral expectation (key bridge)

Arbitrage implies:

> there exists a probability measure under which discounted prices are martingales

Under this measure:

$$ \text{Price} = \mathbb{E}^{\mathbb{Q}}[\text{payoff discounted at } r] $$

This is where expectation comes back — but:
- not with $\mu$
- with $r$

---

### 5. Why this is powerful

Instead of explicitly constructing hedges, we can:

- switch to risk-neutral world
- compute expectations

This is much easier mathematically for complex derivatives.

---

### 6. Role of stochastic calculus

Needed to:
- define continuous-time trading
- handle Brownian motion
- apply Ito’s lemma
- derive PDEs (e.g. Black–Scholes)

---

### 7. Final picture

- Arbitrage → tells you **what must be true**
- Probability → gives a **language to compute it**
- Stochastic calculus → makes it **work in continuous time**

---

### Bottom line

Markets enforce prices.

But to *calculate* those prices in realistic models,  
you need probability and stochastic calculus.
