# Adaptive Step Size Strategies for Inexact First-Order Methods

![Suboptimality Plot](./summary_plot.png) 
*Figure 1: Comparison of optimization trajectories under persistently inexact gradients.*

## 📌 Project Overview
This project investigates the convergence behavior of **inexact first-order methods** under **strong convexity**. 
In practical machine learning and large-scale optimization, exact gradient information is often unavailable due to numerical errors, truncation, or partial computations.

We analyze how different step size strategies govern the trade-off between **descent progress** and **error accumulation**. This work provides both theoretical recursions and numerical validations of adaptive heuristics designed to mitigate error-induced stagnation.

## 🚀 Key Research Questions
- **Can adaptive step sizes remove the error floor** without sacrificing efficiency? 
- How do step size choices govern convergence when gradients are **persistently inexact**?
- When do adaptive heuristics help, and where are their fundamental limits? 

## 🛠 Proposed Methods
We propose and compare two adaptive step size rules based on observable **gradient instability**:

1. **Method I: Continuous Scaling Rule** 
   Adjusts the step size smoothly based on the magnitude of gradient discrepancy:
   $$\alpha_{k} = \text{clip}\left(\frac{c}{1+||g_k - g_{k-1}||}, \alpha_{min}, \alpha_{max}\right)$$ 、

2. **Method II: Threshold-Based Switching Rule** 
   Alternates between aggressive constant steps and conservative diminishing steps based on relative instability $\tau$.

## 📊 Core Findings
Based on our convergence analysis and numerical experiments:
- **Constant Step Size**: Fast initial progress but converges only to a bounded **error neighborhood** (error floor).
- **Diminishing Step Size**: Ensures **exact convergence** by suppressing persistent errors, though it is often overly conservative.
- **Adaptive Strategies**: Successfully **interpolate** between the two regimes—maintaining fast early progress while partially alleviating error-induced stagnation.



## 🧪 Experimental Scenarios
We demonstrate the utility of adaptive methods in several practical cases where problem constants are unknown:
- **Mis-specified Lipschitz Constants**: Adaptive rules alleviate excessive conservatism when $L$ is overestimated.
- **Finite-Difference Gradients**: Handles deterministic errors introduced by numerical approximations.

## 📂 Repository Structure
- `src/`: Core implementation of inexact gradient descent and adaptive rules.
- `notebooks/`: Reproducible scripts for all figures in the report.
- `docs/`: Includes the full 18-page technical report and the one-page visual summary.
