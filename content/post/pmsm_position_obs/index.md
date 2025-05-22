---
author: kayson
title: Position Observer
date: 2025-05-03
description: 
categories:
    - MOTOR
    - CONTROL
tags: 
    - PMSM
    - MODEL
    - Observer
math: true
---
# Back-EMF Observer

Back-EMF observer based on *R*&*L* Modeling

*d-q* Voltage
$$
\begin{aligned}
    u_d &= (R_s + p L_d )i_d - {\omega_e L_q} i_q \\ 
    u_q &= (R_s + p L_q )i_q + {\omega_e L_d} i_d + e_q \\
\end{aligned}
$$

Back-EMF $e_q = \omega_e {\it\Psi_f}$

