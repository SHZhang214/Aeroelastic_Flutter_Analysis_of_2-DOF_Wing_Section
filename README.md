# Aeroelastic Flutter Analysis of a 2-DOF Wing Section

## Overview
This project models and analyses **aeroelastic flutter** in a 2-degree-of-freedom (2-DOF) wing section using a coupled **heave–pitch system**.

Flutter is a dynamic instability that occurs when aerodynamic forces feed energy into a structure, causing oscillations to grow. This project demonstrates how flutter can be predicted using **linear system modelling and eigenvalue analysis**.

---

## Physical Model

The wing section has two degrees of freedom:

- **Heave (h)** — vertical displacement  
- **Pitch (α)** — rotation about the elastic axis  

The governing equations are derived from Newton’s second law:


m \ddot{h} + S \ddot{\alpha} + K_h h = L



S \ddot{h} + I \ddot{\alpha} + K_\alpha \alpha = M


Where:
- \(m\): mass  
- \(I\): moment of inertia  
- \(S = m x_\alpha\): inertial coupling  
- \(K_h, K_\alpha\): structural stiffness  

---

## Aerodynamic Model

A **quasi-steady thin airfoil model** is used:

\[
\alpha_{\text{eff}} = \alpha - \frac{\dot{h}}{U} + \frac{c}{2U}\dot{\alpha}
\]

\[
L = 2\pi \rho U^2 c \, \alpha_{\text{eff}}
\]

\[
M = \frac{\pi}{2} \rho U^2 c^2 \left(\alpha + \frac{c}{4U}\dot{\alpha}\right)
\]

This introduces **velocity-dependent forces**, which are essential for flutter.

---

## Methodology

The equations are rewritten in matrix form:

\[
M \ddot{x} + C \dot{x} + K x = 0
\]

and converted into a **state-space system**:

\[
\dot{x} = A x
\]

Flutter is identified by computing the eigenvalues of matrix \(A\):

- Stable: Re(λ) < 0  
- Flutter: Re(λ) = 0  
- Unstable: Re(λ) > 0  

---

## Features

- 2-DOF aeroelastic model (heave–pitch coupling)
- Quasi-steady aerodynamic force modelling
- State-space formulation
- Eigenvalue-based flutter detection
- Parametric study of torsional stiffness \(K_\alpha\)
- Visualisation of:
  - Growth rate vs velocity
  - Flutter speed vs stiffness

---

## Results

The model demonstrates:

- A **critical flutter speed** where stability is lost  
- Increasing torsional stiffness **raises flutter speed**  
- Instability arises from **coupling between heave and pitch modes**
