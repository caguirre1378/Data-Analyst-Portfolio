---
layout: single
title: "Operations Techniques: Optimization & Decision Models"
excerpt: "Applied OR toolkit across six real-world scenarios: queues, payoff/regret, Monte Carlo, LP, decision trees, and BILP."
classes: wide
category: or
tags: [operations-research, optimization, queuing, monte-carlo, linear-programming, decision-tree, bilp, lingo, excel]
permalink: /projects/operations-techniques/
weight: 30
thumbnail: /assets/images/ops-kpi-splash.png
---

> **Scope** — Applied management science to six practical problems in retail, manufacturing, and services.  
> **Methods** — Queues (M/M/c), payoff & regret, Monte Carlo, LP, decision tree (EMV), BILP.  
> **Tools** — Excel (Solver), LINGO.

---

## Project overview
**Course:** Operations & Supply Chain Management (Fall 2023)  
This project demonstrates how classic **operations research** techniques drive decisions in the wild—staffing to cut balking, stocking under uncertainty, choosing equipment, evaluating lawsuits, and assigning machinists to minimize makespan. Models were built in **Excel** (with Solver) and **LINGO**, with sensitivity where appropriate.

---

## At a glance
- **Queues:** Poisson arrivals / exponential service modeled as **M/M/c**; staff level chosen to reduce P(wait>5min) and balking risk.  
- **Uncertainty:** Payoff/regret tables across demand scenarios; **EV**, **optimistic**, **pessimistic** criteria with sensitivity.  
- **Simulation:** **Monte Carlo** (20 trials) for new-product unit profit; mean, σ, and 95% CI.  
- **LP:** Copier choice minimizing daily cost under throughput & time constraints.  
- **Decision tree:** **EMV** comparison, settle vs. trial.  
- **BILP:** Machinist→machine assignment to minimize total production time with skill constraints.

---

## Problems & solutions

### A) Customer checkout optimization (Queueing)
**Objective.** Reduce balking via cashier allocation.  
**Model.** Arrivals ~ **Poisson** (λ), service ~ **Exponential** (μ) per server; systems evaluated for **c = 1,2,3**.  
**Result.** **Three cashiers** meet the 5-minute wait objective; utilization drops into a stable region and balking falls materially.

---

### B) Specialty steak stocking (Decision under uncertainty)
**Objective.** Choose weekly order qty to maximize profit.  
**Method.** Payoff & regret tables across demand levels; criteria: **Expected Value**, **Optimistic**, **Pessimistic**; plus sensitivity.  
**Result.** **35 lbs** maximizes **EV** (≈ **$79**/wk). Robust under reasonable demand shifts.

---

### C) New product profitability (Monte Carlo)
**Objective.** Assess unit profit under cost uncertainty.  
**Method.** 20-trial **Monte Carlo** on purchase, labor, and transport costs;  
\[
\text{Profit} = \text{Price} - \text{Purchase} - \text{Labor} - \text{Transport}
\]  
**Result.** Mean profit **$6.90**, σ **$2.27**; **95% CI** ≈ **[$4.46, $9.34]**. Product looks viable pending risk appetite.

---

### D) Copier selection for a law office (LP)
**Objective.** Minimize daily operating cost while meeting job volume.  
**Method.** **Linear Program** with decision variables = hours/jobs on each copier; constraints for capacity and time; cost in objective.  
**Result.** **High-speed copier** is cheaper by **$11.20/day** given throughput and wage structure.

---

### E) Patent infringement decision (Decision tree / EMV)
**Objective.** Settle or go to trial.  
**Method.** Decision tree with probabilities for win/lose and associated payoffs/costs; compute **EMV**.  
**Result.** **Go to trial** (EMV ≈ **$1.8M**) dominates **settle** (EMV ≈ **$1.5M**).

---

### F) Machinist assignment (BILP)
**Objective.** Minimize makespan for one part across 4 machines (metal lathe, turning, milling, radial drill).  
**Method.** **Binary Integer LP**: \(x_{ij}\in\{0,1\}\) indicates machinist *i* on machine *j*; each machinist/machine used once; skill rule: **Machinist 3 cannot work Turning**.  
**Result.** Optimal assignment:
- M3 → Metal Lathe  
- M1 → Turning  
- M2 → Milling  
- M4 → Radial Drill  
**Total time:** **100 minutes**.

---

## How to run
**Requirements.** Excel (Solver add-in), LINGO.  

1) **Open workbooks / LINGO files** and review the module tabs (A–F).  
2) **Adjust parameters** (arrival/service rates, demand probabilities, costs, run counts).  
3) **Solve**  
   - Excel: *Data → Solver* on each tab.  
   - LINGO: run the `.lng` models; tweak bounds/constraints as needed.  
4) **Validate** with quick sensitivity: change rates, costs, or probabilities and observe policy stability.

---

## Testing & robustness
- **Constraint checks:** infeasibles flagged; bounds tightened iteratively.  
- **Sensitivity:** varied demand, costs, service rates; decisions remained stable in practical ranges.  
- **Repeatability:** simulation seeds and Solver settings documented for reproducibility.

---

## Links
- **Workbook & LINGO scripts** — <https://github.com/caguirre1378/Data-Analyst-Portfolio>

---

*Updated: December 1, 2023*
