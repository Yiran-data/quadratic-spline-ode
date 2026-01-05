# quadratic-spline-ode
Quadratic spline collocation method for solving first-order ODEs, with convergence and error analysis.

---

## Overview

This project implements a **quadratic spline collocation method (m = 2)** for solving first-order ordinary differential equations (ODEs):

\[
y' = f(x, y), \quad y(x_0) = y_0.
\]

Instead of advancing the solution using standard one-step methods (e.g. Euler or Runge–Kutta), the solution is approximated on each subinterval by a **piecewise quadratic spline**.  
The spline is constructed to satisfy both interpolation and differential constraints, resulting in an **implicit update** at each step.

The method is validated through numerical experiments and error analysis, confirming the expected theoretical convergence orders.

---

## Motivation

Spline-based methods provide a natural way to incorporate **smoothness and derivative information** into numerical ODE solvers.  
Compared with explicit time-stepping schemes, spline collocation methods offer improved accuracy while remaining conceptually simple.

This project explores a quadratic spline approach as a balance between **low-order explicit methods** and more complex high-order schemes, with a particular focus on **convergence behavior and error scaling**.

---

## Method Description

On each subinterval \([x_i, x_{i+1}]\), a quadratic spline \(S(x)\) is constructed such that:

- \(S(x_i) = y_i\)
- \(S'(x_i) = f(x_i, y_i)\)
- \(S'(x_{i+1}) = f(x_{i+1}, y_{i+1})\)

The unknown value \(y_{i+1}\) is determined by solving a **nonlinear implicit condition**, which arises from enforcing the differential equation at the right endpoint.  
This implicit equation is solved numerically using a root-finding procedure.

---

## Numerical Experiments and Results

The method was tested on several first-order ODEs with known analytical solutions.  
The global error was measured for a range of step sizes and analyzed on a log–log scale.

The figure below shows the **global error versus step size**, together with reference slopes.  
The numerical results closely align with an \(O(h^2)\) trend, confirming the **second-order global accuracy** of the quadratic spline method.

The same convergence behavior was consistently observed across multiple test problems, demonstrating the robustness of the approach.

![Global error convergence plot](figures/global_error_convergence.png)

**Figure.** Log–log plot of global error versus step size for the quadratic spline method.  
The numerical results align closely with the \(O(h^2)\) reference slope, confirming second-order convergence.

---

## Features

- Quadratic spline collocation method for first-order ODEs  
- Implicit update step solved via nonlinear root-finding  
- Global error analysis with observed \(O(h^2)\) convergence  
- Local error behavior consistent with \(O(h^3)\) theoretical predictions  
- Fully reproducible numerical experiments in Jupyter notebooks  

---

## How to Run

Clone the repository and run the notebook in Jupyter:

```bash
git clone https://github.com/Yiran-data/quadratic-spline-ode.git
cd quadratic-spline-ode
pip install -r requirements.txt
jupyter notebook numerical_methods_quadratic_spline.ipynb
