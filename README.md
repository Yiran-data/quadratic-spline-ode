# quadratic-spline-ode
“Quadratic spline method for solving ODEs with error analysis.

## 📖 Overview
This project implements a **quadratic spline method (m=2)** for solving first-order ordinary differential equations (ODEs):

\[
y' = f(x, y), \quad y(x_0) = y_0
\]

The method constructs piecewise quadratic splines on each subinterval, enforcing:
- \(S(x_i) = y_i\)
- \(S'(x_i) = f(x_i, y_i)\)
- \(S'(x_{i+1}) = f(x_{i+1}, y_{i+1})\)

with \(y_{i+1}\) determined by solving a nonlinear condition via root-finding.

---

## ✨ Features
- Quadratic spline collocation method for ODEs  
- Nonlinear solver for implicit update step  
- Error analysis included:
  - Global error ~ **O(h²)**
  - Local error ~ **O(h³)**
- Log–log error plots with reference slopes for convergence validation  

---

## 📊 Example Results
- Tested on problems with known analytical solutions  
- Observed error behavior matches the expected second-order global accuracy  

*(You can add a figure here, e.g., an error plot from the notebook)*

---

## 🚀 How to Run
Clone this repository and run the notebook in Jupyter:

```bash
git clone https://github.com/Yiran-data/quadratic-spline-ode.git
cd quadratic-spline-ode
pip install -r requirements.txt
jupyter notebook numerical_methods_quadratic_spline.ipynb
