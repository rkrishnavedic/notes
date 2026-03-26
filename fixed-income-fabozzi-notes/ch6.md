**Pull to Par**
- Bond price = present value of remaining cashflows, not total lifetime cashflows.
- Coupons get paid out and disappear from the bond → they are not part of price anymore.
- As time passes, fewer cashflows remain, so valuation converges to the final payment.
- At maturity, only principal (par) is left → hence price → par.
- “Pull-to-par” = effect of time decay + constant yield, not accumulation of coupons.

For a mathematician entering the fixed income space, Chapter 6 (and its link to Chapter 5) moves from the "static" world of bond yields into the "stochastic" reality of realized returns. Traders don't get paid on YTM; they get paid on realized P&L, which is the actual performance of capital at risk. 

By the end of these notes, you will distinguish between promised yields and realized returns, understand the mechanics of money-weighted versus time-weighted performance, and see how reinvestment rates dictate your ultimate trading P&L.

---

## 1. BIG IDEA
*   **Return $\neq$ Yield:** A bond’s total return is the actual growth of a dollar invested over a specific horizon.
*   **Total Return Components:**
    *   **Coupon Income:** Periodic cash flow.
    *   **Capital Gain/Loss:** Change in the bond's market value over the holding period.
    *   **Reinvestment Income:** The "interest-on-interest" earned by reinvesting coupons at prevailing market rates.

---

## 2. SINGLE-PERIOD RETURN
*   **Holding Period Return (HPR):** The percentage change in value between two valuation dates.
*   **Mathematical Form:**
    $R = \frac{(MVE + AI_E) - (MVB + AI_B)}{(MVB + AI_B)}$
    *(Where $MVE$ = ending market value, $MVB$ = beginning market value, and $AI$ = accrued income)*.
*   **Quant Note:** This incorporates both realized gains (from trading) and unrealized gains (mark-to-market), ensuring every dollar at risk is accounted for.

---

## 3. REINVESTMENT EFFECT (CRITICAL)
*   **The Flaw in YTM:** Yield-to-Maturity mathematically assumes all interim coupons are reinvested at the YTM rate until maturity—a scenario rarely realized in volatile markets.
*   **Interest-on-Interest:** For long-term bonds in high-rate environments, reinvestment income can comprise up to **80% of the total dollar return**.
*   **Reinvestment Risk:** The risk that market rates will be lower than the YTM at the time coupons are received, dragging down the realized return.

---

## 4. MONEY-WEIGHTED RETURN (MWR / IRR)
*   **Definition:** The Internal Rate of Return (IRR) that equates the present value of all cash flows (contributions and withdrawals) to the initial investment.
*   **Sensitivity:** MWR is highly sensitive to the **timing and magnitude** of cash flows.
*   **Use Case:** Measures the actual return experienced by the investor (the "money owner").

---

## 5. TIME-WEIGHTED RETURN (TWR)
*   **Definition:** The geometric compounding of sub-period returns, where each sub-period is defined by an external cash flow event.
*   **Mathematical Form:**
    $TWR = [(1 + R_1)(1 + R_2)\dots(1 + R_n)] - 1$.
*   **Elimination of Bias:** TWR removes the impact of external cash flows, isolating the performance attributable solely to the manager’s decisions or the market’s movement.
*   **Standard:** This is the industry standard for comparing different managers or strategies.

---

## 6. MULTI-PERIOD RETURNS
*   **Cumulative Returns:** Found by chain-linking (compounding) single-period wealth relatives ($1+R$).
*   **Geometric Mean:** The $n$-th root of the cumulative growth rate; it represents the "steady" rate that would have produced the same terminal value.
*   **Annualization:**
    $R_{annual} = (1 + R_{cumulative})^{1/n} - 1$.

---

## 7. KEY INSIGHT: YIELD $\neq$ RETURN
*   **Static vs. Dynamic:** Yield is a "snapshot" estimate based on current price; return is a "video" of path-dependent performance.
*   **Path Dependency:** Your realized P&L depends on the exact path interest rates take between coupon dates (affecting reinvestment) and at your exit horizon (affecting capital gain).

---

## 8. DESK CONNECTION
*   **Scenario Analysis:** Quants use the Total Return framework to stress-test how a portfolio will perform under different reinvestment and exit yield assumptions.
*   **Relative Value (RV):** When comparing a 5% 10-year bond and a 4% 30-year bond, the "Yield Pickup" is irrelevant if the reinvestment of the 5% coupons occurs at 2%.
*   **P&L Attribution:** Breaking down the total return into "Carry" (coupon + rolldown) and "Market Move" (price change) is the daily bread of a strategist.

---

## 9. 5 CRITICAL TAKEAWAYS
1.  **Interest-on-interest** is often the single largest driver of long-term bond P&L.
2.  **YTM is a promised rate**, not a guaranteed one, because of reinvestment risk.
3.  **TWR** is for judging the strategy/manager; **MWR** is for judging the account's actual growth.
4.  **Dirty Price** (Market Value + Accrued) is the only correct basis for calculating returns; ignoring accruals creates artificial volatility.
5.  Realized return is **path-dependent**; the timing of rate changes matters as much as the magnitude.

Does the mathematical distinction between geometric linking (TWR) and the root-finding of the IRR (MWR) make sense for your P&L models, or should we look at how **Modified Dietz** approximates these values?
