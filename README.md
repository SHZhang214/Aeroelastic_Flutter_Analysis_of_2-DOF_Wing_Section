# Aeroelastic Flutter Analysis of a 2-DOF Wing Section

## Overview
This project models and analyses **aeroelastic flutter** in a 2-degree-of-freedom (2-DOF) wing section using a coupled **heave–pitch system**.

Flutter is a dynamic instability that occurs when aerodynamic forces feed energy into a structure, causing oscillations to grow. This project demonstrates how flutter can be predicted using **linear system modelling and eigenvalue analysis**.

---

## Physical Model

The governing equations are:

m ḧ + S α̈ + K_h h = L  

S ḧ + I α̈ + K_α α = M  

Where:
- m: mass  
- I: moment of inertia  
- S: inertial coupling  
- K_h, K_α: stiffness  

---

## Aerodynamic Model

Effective angle of attack:

α_eff = α − ḣ / U + (c / 2U) α̇  

Lift:

L = 2π ρ U² c α_eff  

Moment:

M = (π/2) ρ U² c² (α + (c / 4U) α̇)

This introduces **velocity-dependent forces**, which are essential for flutter.

---

## Methodology

The equations of motion are written in matrix form:

M ẍ + C ẋ + K x = 0

where:

x = [h, α]^T

This second-order system is converted into a first-order state-space form:

ẋ = A x

where the state vector is:

x = [h, α, ḣ, α̇]^T

and the system matrix A is constructed as:

A = [  0        I  
     -M⁻¹(K + K_aero)   -M⁻¹ C ]

Flutter is identified by computing the eigenvalues of A:

- Stable: real part of eigenvalue < 0  
- Flutter onset: real part = 0  
- Unstable: real part > 0  

The flutter speed is determined by sweeping airflow velocity and detecting where the system transitions from stable to unstable.
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
