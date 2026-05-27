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
