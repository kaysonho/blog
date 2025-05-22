---
author: kayson
title: Field-Weakening Control
date: 2025-05-03
description: 
categories:
    - MOTOR
    - CONTROL
tags: 
    - PMSM
    - MODEL
math: true
---

Voltage
$$
\begin{aligned}
    u_d &= (R_s + p L_d )i_d - {\omega_e L_q} i_q \\ 
    u_q &= (R_s + p L_q )i_q + {\omega_e L_d} i_d + \omega_e {\it\Psi_f}
\end{aligned}
$$


Torque
$$
\begin{aligned}
    T_e &= \frac{3}{2}\; p_n[(L_d-L_q)i_d i_q + {\it\Psi_f} i_q]
\end{aligned}
$$

Current limit condition
电流极限环
$$
\begin{aligned}
    i_d^2+i_q^2 \le I_{max}^2
\end{aligned}
$$

Voltage limit condition
电压极限环
$$
\begin{aligned}
    u_d^2 + u_q^2 \le U_{max}^2
\end{aligned}
$$

$$
\begin{aligned}
    (\omega_e L_q i_q)^2+(\omega_e L_d i_d + \omega_e {\it\Psi_f})^2 &\le U_{max}^2
\end{aligned}
$$

# Field-weakening


# Reference

[1] [Matlab PMSM Drive Characteristics and Constraint Curves](https://www.mathworks.com/help/mcb/ug/pmsm-characteristics-constraint-curves.html)
[2] [Matlab Field-Weakening Control](https://www.mathworks.com/discovery/field-weakening-control.html)
