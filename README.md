# student-ctd-cme-shock-local-hedge

Simple educational project to model local CTD to CME hedge ratios across rate shocks using duration and convexity adjusted DV01 relationships.

The goal of this project is NOT to create a production Treasury futures pricing engine.

The goal is to visualize how:

- local DV01 changes as rates move
- convexity changes exposure
- hedge ratios evolve across shocks
- Treasury futures conversion factors amplify or reduce CME-equivalent exposure

---

# Core Idea

A hedge ratio is not always static.

As rates move:

- bond prices change
- local DV01 changes
- convexity changes local slope exposure
- hedge relationships evolve

This project recalculates the local CTD:CME hedge ratio at every shock point.

---

# Important Formulas

## CME Equivalent Exposure

CME-equivalent exposure is estimated using simplified conversion factor relationships.

### CME Modified Duration

```math
D_{CME} = \frac{D_{CTD}}{CF}
```

### CME Convexity

```math
C_{CME} = \frac{C_{CTD}}{CF}
```

---

# Convexity Adjusted Shock Pricing

For each shock value:

```math
P_{shock} = P_0 \left(1 - D_{mod}\Delta y + \frac{1}{2}C(\Delta y)^2\right)
```

Where:

- \( \Delta y \) = shock in decimal form
- 50bp = 0.005

---

# Local DV01

This project focuses on LOCAL DV01 evolution across shocks.

```math
DV01_{local} \approx \frac{P_{shock}(D_{mod} - C\Delta y)}{10000}
```

---

# Local Hedge Ratio

The local CTD:CME hedge ratio is estimated as:

```math
H_{local} = \frac{DV01_{CTD,local}}{DV01_{CME,local}}
```

This ratio evolves across shocks rather than remaining perfectly static.

---

# Important Observations / Epiphanies

## DV01 Changes As Rates Move

As rates rise:

- bond prices fall
- local DV01 falls

As rates fall:

- bond prices rise
- local DV01 rises

This project helped reinforce that bond exposure itself evolves across rate shocks.

---

## Treasury Futures Are Built Around A 6% Framework

Treasury futures conversion factors are structurally linked to a hypothetical 6% yield framework.

Observations:

- As CTD coupon/yield characteristics approach 6%, conversion factors tend toward 1
- Lower coupon environments can create conversion factors below 1
- Lower CF values amplify CME-equivalent duration, convexity, and local DV01 exposure

This can create situations where CME-equivalent exposure becomes significantly larger than raw CTD intuition.

---

## The Hedge Is Local

One of the most important realizations from this project:

A hedge is not a lock.

Even if current DV01 is matched:

- convexity changes exposure
- local DV01 evolves
- hedge ratios drift across shocks

The hedge relationship itself changes as rates move.

---

# Simplified Assumptions

NOTE:

- This model uses simplified estimated conversion factors
- This project focuses only on relative DV01 relationships
- A par assumption of 100 is used throughout
- This is an educational local hedge engine, not a production Treasury futures pricing model

---

# Why I Built This

I wanted a simple way to visualize:

- how convexity changes local exposure
- how Treasury futures conversion mechanics affect risk
- and why fixed income hedges are often local rather than static

Simple.

Honest.

Useful.
