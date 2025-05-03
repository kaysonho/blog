---
author: kayson
title: Sensorless Control based on EEMF Observer
date: 2025-05-03
description: Sensorless control based on EEMF observer.
categories:
    - MOTOR
    - CONTROL
tags: 
    - PMSM
    - MODEL
    - EEMF
    - SENSORLESS
    - OBSERVER
math: true
---

# PMSM EEMF Model

## Voltage Equation

Define $(L_d-L_q)(\omega_e i_d -p i_q)+{\omega_e{\it\Psi_f}}$ as extended electromotive force, EEMF.  
Rewritten the *α-β* voltage equation,
$$
\begin{aligned}
    {\begin{bmatrix} u_\alpha \\ u_\beta \\ \end{bmatrix}}
    &=
    {\begin{bmatrix*}[c]
        R_s+p L_d & \omega_e (L_d-L_q)\\
        -\omega_e (L_d-L_q) & R_s +pL_d
    \end{bmatrix*}}
    {\begin{bmatrix} i_{\alpha} \\ i_{\beta} \\ \end{bmatrix}}
    +
    {\begin{Bmatrix} (L_d-L_q)(\omega_e i_d -p i_q)+{\omega_e{\it\Psi_f}} \end{Bmatrix}}
    {\begin{bmatrix*}[r] -\sin\theta_e \\ \cos\theta_e \\ \end{bmatrix*}}
\end{aligned}
$$
    
Rewritten the *d-q* voltage equation,

$$
\begin{aligned}
    {\begin{bmatrix} u_d \\ u_q \end{bmatrix}}
    &=
    {\begin{bmatrix*}[r]
        R_s+p L_d & -{\omega_e L_q} \\
        {\omega_e L_q} & R_s+p L_d
    \end{bmatrix*}}
    {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}}
    +
    {\begin{Bmatrix} (L_d-L_q)(\omega_e i_d -p i_q)+{\omega_e{\it\Psi_f}} \end{Bmatrix}}
    {\begin{bmatrix*}[r] 0 \\ 1 \\ \end{bmatrix*}}
\end{aligned}
$$


