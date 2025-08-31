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
This project applied a range of **operations research (OR)** and **optimization techniques** to solve six real-world challenges. These include customer queue optimization, inventory stocking under uncertainty, new product profitability simulation, copier selection using LP, lawsuit decision modeling, and machinist assignments using BILP.

### Techniques Applied

- **Queueing Theory (M/M/c):** Optimized customer service levels.
- **Decision Analysis:** Expected value, regret, pessimistic/optimistic strategies.
- **Monte Carlo Simulation:** Modeled cost variability for a new product.
- **Linear Programming (LP):** Determined optimal copier selection for cost savings.
- **Decision Tree (EMV):** Assessed financial outcomes in legal disputes.
- **Binary Integer Linear Programming (BILP):** Minimized production time via optimized assignments.

Tools used: **Excel with Solver** and **LINGO.**

---

## Problems and Solutions

### A) Customer Checkout Optimization

**Objective:** Reduce customer balking by optimizing cashier allocation using queueing theory.  
**Approach:**  
- Modeled customer arrivals with a **Poisson process** and service time as **Exponential.**
- Simulated scenarios with 1, 2, and 3 cashiers using **M/M/c** logic.
- Calculated utilization, probability of waiting >5 min, and balking impact.

**Result:** Using **3 cashiers** significantly reduced wait times and met the operational target.

---

### B) Specialty Steak Stocking

**Objective:** Determine the best weekly stocking level to maximize profit.  
**Approach:**  
- Developed **payoff and regret tables** across demand levels.
- Used **Expected Value, Optimistic, and Pessimistic** criteria.
- Ran **sensitivity analysis** to assess robustness under demand changes.

**Result:** Ordering **35 lbs** optimized expected profit at **$79/week.**

---

### C) New Product Profitability (Monte Carlo)

**Objective:** Simulate profit per unit given variable input costs.  
**Approach:**  
- Conducted **20 trials** of Monte Carlo simulation.  
- Calculated profit per unit as:  
  \[ 	ext{Profit} = 	ext{Price} - 	ext{Purchase} - 	ext{Labor} - 	ext{Transport} \]

**Result:**  
- Mean: **$6.90**, Standard Deviation: **$2.27**
- **95% CI:** [**$4.46, $9.34**]
- Product is viable pending risk appetite.

---

### D) Copier Selection (Linear Programming)

**Objective:** Choose the more cost-effective copier.  
**Approach:**  
- Built **LP model** with copier speeds, costs, and constraints.
- Objective function minimized daily cost.

**Result:** **High-speed copier** saved **$11.20/day** compared to regular copier.

---

### E) Patent Infringement Decision (Decision Tree / EMV)

**Objective:** Decide whether to settle or go to trial.  
**Approach:**  
- Constructed a **decision tree** modeling win/loss outcomes, costs, and probabilities.
- Calculated **Expected Monetary Value (EMV)** for both paths.

**Result:** **Go to trial** yielded higher EMV (**$1.8M**) over settling (**$1.5M**).

---

### F) Machinist Assignment (BILP)

**Objective:** Assign machinists to machines minimizing total production time.  
**Approach:**  
- Used **Binary Integer LP** to assign 4 machinists to 4 machines.
- Constraint: **Machinist 3** cannot operate Turning machine.

**Result:**  
- M3 → Metal Lathe  
- M1 → Turning  
- M2 → Milling  
- M4 → Radial Drill  
- **Total Time:** **100 minutes**

---

## How to Run

**Requirements:** Excel with Solver, LINGO

**Instructions:**  
1. Download Excel workbook and LINGO scripts.  
2. Adjust parameters for each module (costs, rates, demand).  
3. Run:  
   - Excel: *Data → Solver* on each tab  
   - LINGO: Execute models; customize constraints  

4. Review results, validate with sensitivity tests.

---

## Testing & Validation

- **Constraint checks:** Infeasibles flagged and resolved.  
- **Sensitivity:** Stress-tested decisions against input variability.  
- **Repeatability:** Documented seeds and solver settings for reproducibility.

---

## Contribution Guidelines

**Code of Conduct:** Respectful, constructive collaboration is expected.  
**Workflow:** Fork-pull-request model. Branches for features/improvements.  
**Style Guide:** Clear naming, consistent formatting, inline documentation.

**Licensing:** Educational use under course guidelines.

---

## Future Work

- Automate modules for web dashboard integration.  
- Integrate predictive modeling for dynamic inputs.  
- Expand scope to include stochastic optimization.

---

## Links

- [GitHub Repository](https://github.com/caguirre1378/Data-Analyst-Portfolio)

---

*Updated: December 1, 2023*
