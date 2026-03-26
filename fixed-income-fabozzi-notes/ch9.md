For a mathematician entering the fixed-income world, Chapter 9 represents the formalization of "Greeks" for the bond market. While Chapter 5 established the pricing engine, Chapter 9 derives the sensitivity measures used to manage multi-billion dollar portfolios. Traders live and breathe **DV01** and **Convexity** because these metrics translate abstract yield moves into concrete P&L.

By the end of these notes, you will understand how to approximate the nonlinear price-yield curve using Taylor expansions, why effective duration is mandatory for securities with optionality, and how to quantify risk as a function of both sensitivity and yield volatility.

---

## 1. BIG IDEA
*   **Pricing Function:** Bond price is a function of its yield, $P = f(y)$.
*   **Risk Definition:** Risk is the sensitivity of the price function to changes in the yield input.
*   **The Quantitative Goal:** Quantify the expected change in value (P&L) for a given change in market rates.

---

## 2. FULL VALUATION APPROACH
*   **Mechanism:** Recompute the bond’s value for every discrete yield scenario (e.g., +50bp, +100bp, +200bp).
*   **Pros/Cons:** It is the most accurate method but is computationally expensive for large portfolios with complex path-dependent securities.
*   **Usage:** Forms the "ground truth" for risk systems and stress testing (extreme scenarios).

---

## 3. PRICE–YIELD RELATIONSHIP
*   **Inverse Correlation:** Price changes in the opposite direction of the change in interest rates.
*   **Convex Shape:** The relationship is not a straight line but is "bowed" or convex.
*   **Volatility Asymmetry:** For a given basis point move, the price increase for a yield decrease is greater than the price decrease for a yield increase.

---

## 4. DURATION (FIRST-ORDER RISK)
*   **Definition:** The approximate percentage change in value for a 100 basis point change in rates.
*   **Estimation Formula:**
    $D = \frac{V_- - V_+}{2V_0(\Delta y)}$
    *(Where $V_-$ and $V_+$ are prices after a downward and upward yield shift, respectively)*.
*   **Linear Approximation:**
    $\frac{\Delta P}{P} \approx -D \cdot \Delta y$
    *(Where $\Delta y$ is the change in yield in decimal)*.
*   **Interpretation:** Geometrically, duration is the negative slope of the tangent line to the price-yield curve at the current yield level.

---

## 5. MODIFIED VS. EFFECTIVE DURATION
*   **Modified Duration:** Assumes bond cash flows are fixed and do not change when yields shift. Flawed for bonds with options.
*   **Effective Duration:** Recognizes that yield changes can alter expected cash flows (e.g., a call being exercised or prepayments speeding up).
*   **Quant Insight:** Effective duration is mandatory for any security with embedded optionality (Callable, Putable, MBS) to capture the true price sensitivity.

---

## 6. CONVEXITY (SECOND-ORDER RISK)
*   **Correction Term:** Duration alone underestimates the new price because it uses a straight line to approximate a curve.
*   **Estimation Formula:**
    $C = \frac{V_- + V_+ - 2V_0}{2V_0(\Delta y)^2}$.
*   **Improved Approximation (Second-Order Taylor):**
    $\frac{\Delta P}{P} \approx -D \cdot \Delta y + \frac{1}{2} C \cdot (\Delta y)^2$.
*   **Interpretation:** Positive convexity is a structural advantage; it causes a bond to gain more in rallies than it loses in equal-sized sell-offs.

---

## 7. DV01 / PV01 (CRITICAL DESK METRIC)
*   **Definition:** The **Dollar Value of an 01** (or PV01) is the absolute dollar change in price for a 1 basis point change in yield.
*   **Mathematical Relation:**
    $DV01 = \text{Initial Price} \cdot \text{Duration} \cdot 0.0001$.
*   **Trader Logic:** In the heat of trading, desks manage dollar-at-risk (DV01) rather than percentage sensitivities.

---

## 8. PRICE VALUE OF A BASIS POINT (PVBP)
*   **Alternative Name:** PVBP is synonymous with DV01.
*   **Application:** Used for hedging (matching the PVBP of a bond with the PVBP of a hedge instrument) and aggregating risk across a portfolio.

---

## 9. YIELD VOLATILITY (IMPORTANT)
*   **The Missing Link:** A bond with high duration but low yield volatility may be less "risky" than a low-duration bond in a volatile market.
*   **Quant Relationship:**
    $\text{Interest Rate Risk} \propto \text{Price Sensitivity (Duration)} \times \text{Yield Volatility}$.
*   **Example:** A 10-year Swiss bond has higher duration but lower total risk than a 10-year US Treasury due to vastly lower yield volatility.

---

## 10. YIELD CURVE RISK
*   **Portfolio Assumption:** Using a single duration assumes the entire yield curve shifts in a parallel fashion.
*   **Non-Parallel Shifts:** Risks arise from curve steepening, flattening, or "twists".
*   **Refinement:** Advanced models use "Key Rate Durations" to measure sensitivity to specific tenors (2Y, 5Y, 10Y).

---

## 11. CONNECTION TO P&L
*   **Daily P&L Attribution:**
    $\Delta \text{Price} \approx -(\text{DV01} \times 10,000 \times \Delta y) + (\text{Convexity Effect})$
*   **Desk Decomposition:** Risk reports decompose the day's P&L into "Delta" (duration move), "Gamma" (convexity effect), and "Theta" (carry/time decay).

---

## 12. DESK APPLICATION
*   **Contribution to Duration:** Portfolio risk is the weighted average of component durations.
    $\text{Contribution} = \text{Weight}_i \cdot \text{Duration}_i$.
*   **Risk Aggregation:** Managers compare their portfolio's sector contributions to a benchmark index to identify relative risk bets.

---

## 13. 5 CRITICAL TAKEAWAYS
1.  **Duration** is the linear approximation of price sensitivity; it is accurate only for small moves.
2.  **Convexity** is the second-order correction; it ensures you don't underestimate the bond's value in large rate shifts.
3.  **DV01** is the primary dollar risk metric used for hedging and daily P&L.
4.  **Effective Duration** is mandatory for bonds with options because it accounts for stochastic cash flows.
5.  **Volatility Matters:** Sensitivity (duration) without probability (yield volatility) provides an incomplete risk picture.
