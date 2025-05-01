---
author: kayson
title: PMSM model
date: 2025-04-29
description: Modeling of permanent magnet synchronous motor.
categories:
    - MOTOR
tags: 
    - PMSM
math: true
---

# PMSM model

## Transformation

### CLARK / 3s-2s

$$
\begin{aligned}
    \begin{bmatrix} \alpha \\ \beta \\ 0 \\ \end{bmatrix} &= \frac{2}{3}
    \begin{bmatrix*}
        1          & -1/2       & -1/2        \\
        0          & \sqrt{3}/2 & -\sqrt{3}/2 \\
        1/\sqrt{2} & 1/\sqrt{2} & 1/\sqrt{2}  \\
    \end{bmatrix*}
    \begin{bmatrix} a \\ b \\ c \\ \end{bmatrix}  
    = \pmb{T}_{\text{3s-2s}} \begin{bmatrix} a \\ b \\ c \\ \end{bmatrix} \\
    \begin{bmatrix} a \\ b \\ c \\ \end{bmatrix} &= \phantom{-}
    \begin{bmatrix*}
        1    & 0           & 1/\sqrt{2} \\
        -1/2 & \sqrt{3}/2  & 1/\sqrt{2} \\
        -1/2 & -\sqrt{3}/2 & 1/\sqrt{2} \\
    \end{bmatrix*}
    \begin{bmatrix} \alpha \\ \beta \\ 0 \\ \end{bmatrix}  
    =\pmb{T}_{\text{3s-2s}}^{-1}\begin{bmatrix} \alpha \\ \beta \\ 0 \\ \end{bmatrix}
\end{aligned}
$$

### PARK / 2s-2r

$$
\begin{aligned}
    {\begin{bmatrix} d \\ q \\ \end{bmatrix}} &=
    {\begin{bmatrix*}
        \phantom{-}\cos\theta_e & -\sin\theta_e \\
        \phantom{-}\sin\theta_e & \phantom{-}\cos\theta_e\\
    \end{bmatrix*}}
    {\begin{bmatrix} \alpha \\ \beta \end{bmatrix}}
    ={\pmb{T}_{\text{2s-2r}}}
    {\begin{bmatrix} \alpha \\ \beta \end{bmatrix}}\\
    {\begin{bmatrix} \alpha \\ \beta \end{bmatrix}} &=
    {\begin{bmatrix*}
        \phantom{-}\cos\theta_e & \phantom{-}\sin\theta_e \\
        -\sin\theta_e & \phantom{-}\cos\theta_e\\
    \end{bmatrix*}}
    {\begin{bmatrix} d \\ q \end{bmatrix}}    =
    {\pmb{T}_{\text{2s-2r}}^{-1}}
    {\begin{bmatrix} d \\ q \end{bmatrix}  }
\end{aligned}
$$

## *a-b-c*

### voltage

$$
\begin{aligned}
    {\pmb{u_s}} &= \pmb{R_s i_s}+ \frac{d}{dt} \pmb{\it{\Psi_s}}
\end{aligned}
$$

$$
\begin{aligned}
    {\begin{bmatrix} u_a \\ u_b \\ u_c \\ \end{bmatrix}} &=
    {\begin{bmatrix} R_s & 0 & 0 \\ 0 & R_s & 0 \\ 0 & 0 & R_s \\ \end{bmatrix}}
    {\begin{bmatrix} i_a \\ i_b \\ i_c \\ \end{bmatrix}} +p
    {\begin{bmatrix} \it{\Psi}_a \\ \it{\Psi}_b \\ \it{\Psi}_c \\ \end{bmatrix}}
    \\ &=
    {\begin{bmatrix} R_s & 0 & 0 \\ 0 & R_s & 0 \\ 0 & 0 & R_s \\ \end{bmatrix}}
    {\begin{bmatrix} i_a \\ i_b \\ i_c \\ \end{bmatrix}} +p
    {\begin{Bmatrix}
        {\begin{bmatrix}
            L_{aa} & M_{ab} & M_{ac} \\
            M_{ba} & L_{bb} & M_{bc} \\
            M_{ca} & M_{cc} & L_{cc} \\
        \end{bmatrix}}
        {\begin{bmatrix} i_a \\ i_b \\ i_c \\ \end{bmatrix}} +
        {\begin{bmatrix} \it{\Psi}_{fa} \\ \it{\Psi}_{fb} \\ \it{\Psi}_{fc} \\ \end{bmatrix}}
    \end{Bmatrix}} \\
\end{aligned}
$$

### flux leakage

$$
\begin{aligned}
    {\pmb{\it{\Psi_s}}}={\pmb{L_s i_s}}+{\pmb{\it{\Psi_f}}}
\end{aligned}
$$

$$
\begin{aligned}
    {\begin{bmatrix} \it{\Psi}_a \\ \it{\Psi}_b \\ \it{\Psi}_c \\ \end{bmatrix}} &=
    {\begin{bmatrix}
        L_{aa} & M_{ab} & M_{ac} \\
        M_{ba} & L_{bb} & M_{bc} \\
        M_{ca} & M_{cc} & L_{cc} \\
    \end{bmatrix}}
    {\begin{bmatrix} i_a \\ i_b \\ i_c \\ \end{bmatrix}} +
    {\begin{bmatrix} \it{\Psi}_{fa} \\ \it{\Psi}_{fb} \\ \it{\Psi}_{fc} \\ \end{bmatrix}}
    \\ &=
    {\begin{bmatrix}
        L_{aa} & M_{ab} & M_{ac} \\
        M_{ba} & L_{bb} & M_{bc} \\
        M_{ca} & M_{cc} & L_{cc} \\
    \end{bmatrix}}
    {\begin{bmatrix} i_a \\ i_b \\ i_c \\ \end{bmatrix}} + {\it\Psi_f}
    {\begin{bmatrix*}[l]
        \cos(\theta_e) \\
        \cos(\theta_e-2\pi/3) \\
        \cos(\theta_e+2\pi/3) \\
    \end{bmatrix*}}
\end{aligned}
$$

$$
\begin{aligned}
    {\begin{bmatrix}
        L_{aa} & M_{ab} & M_{ac} \\
        M_{ba} & L_{bb} & M_{bc} \\
        M_{ca} & M_{cc} & L_{cc} \\
    \end{bmatrix}}
    &=
    {\begin{bmatrix*}[l]
        \phantom{-}L_{s0}\;+L_{s2}\cos(2(\theta_e)) & -M_{s0}+L_{s2}\cos(2(\theta_e-\pi/3)) & -M_{s0}+L_{s2}\cos(2(\theta_e+\pi/3)) \\
        -M_{s0}+L_{s2}\cos(2(\theta_e-\pi/3)) & \phantom{-}L_{s0}\;+L_{s2}\cos(2(\theta_e-2\pi/3)) & -M_{s0}+L_{s2}\cos(2(\theta_e)) \\
        -M_{s0}+L_{s2}\cos(2(\theta_e+\pi/3)) & -M_{s0}+L_{s2}\cos(2(\theta_e)) &\phantom{-}L_{s0}\;+L_{s2}\cos(2(\theta_e+2\pi/3)) \\
    \end{bmatrix*}}
\end{aligned}
$$

## *α-β*

### *a-b-c* to *α-β*

$$
\begin{aligned}
    {\begin{bmatrix} u_a \\ u_b \\ u_c \\ \end{bmatrix}} &=
    {\begin{bmatrix} R_s & 0 & 0 \\ 0 & R_s & 0 \\ 0 & 0 & R_s \\ \end{bmatrix}}
    {\begin{bmatrix} i_a \\ i_b \\ i_c \\ \end{bmatrix}} +p
    {\begin{Bmatrix}
        {{\begin{bmatrix}
            L_{aa} & M_{ab} & M_{ac} \\
            M_{ba} & L_{bb} & M_{bc} \\
            M_{ca} & M_{cc} & L_{cc} \\
        \end{bmatrix}}}
        {\begin{bmatrix} i_a \\ i_b \\ i_c \\ \end{bmatrix}} +{\it\Psi_f}
        {\begin{bmatrix*}[l]
            \cos(\theta_e) \\
            \cos(\theta_e-2\pi/3) \\
            \cos(\theta_e+2\pi/3) \\
        \end{bmatrix*}}
    \end{Bmatrix}} \\
    {\pmb{T}_{\text{3s-2s}}^{-1}\begin{bmatrix} u_\alpha \\ u_\beta \\ \end{bmatrix}} &=
    {\begin{bmatrix} R_s & 0 & 0 \\ 0 & R_s & 0 \\ 0 & 0 & R_s \\ \end{bmatrix}}
    {\pmb{T}_{\text{3s-2s}}^{-1}\begin{bmatrix} u_\alpha \\ u_\beta \\ \end{bmatrix}} +p
    {\begin{Bmatrix}
        {{\begin{bmatrix}
            L_{aa} & M_{ab} & M_{ac} \\
            M_{ba} & L_{bb} & M_{bc} \\
            M_{ca} & M_{cc} & L_{cc} \\
        \end{bmatrix}}}
        \pmb{T}_{\text{3s-2s}}^{-1}{\begin{bmatrix} i_{\alpha} \\ i_{\beta} \\ \end{bmatrix}} + {\it\Psi_f}
        {\begin{bmatrix*}[l]
            \cos(\theta_e) \\
            \cos(\theta_e-2\pi/3) \\
            \cos(\theta_e+2\pi/3) \\
        \end{bmatrix*}}
    \end{Bmatrix}} \\
    {\begin{bmatrix} u_\alpha \\ u_\beta \\ \end{bmatrix}} &= \pmb{T}_{\text{3s-2s}}
    {\begin{bmatrix} R_s & 0 & 0 \\ 0 & R_s & 0 \\ 0 & 0 & R_s \\ \end{bmatrix}}
    {\pmb{T}_{\text{3s-2s}}^{-1}\begin{bmatrix} u_\alpha \\ u_\beta \\ \end{bmatrix}} + \pmb{T}_{\text{3s-2s}}\;p
    {\begin{Bmatrix}
        {{\begin{bmatrix}
            L_{aa} & M_{ab} & M_{ac} \\
            M_{ba} & L_{bb} & M_{bc} \\
            M_{ca} & M_{cc} & L_{cc} \\
        \end{bmatrix}}}
        \pmb{T}_{\text{3s-2s}}^{-1}{\begin{bmatrix} i_{\alpha} \\ i_{\beta} \\ \end{bmatrix}} +{\it\Psi_f}
        {\begin{bmatrix*}[l]
            \cos(\theta_e) \\
            \cos(\theta_e-2\pi/3) \\
            \cos(\theta_e+2\pi/3) \\
        \end{bmatrix*}}
    \end{Bmatrix}} \\
\end{aligned}
$$

$$
\begin{aligned}
    &{\pmb{T}_{\text{3s-2s}}}
    {\begin{bmatrix} R_s & 0 & 0 \\ 0 & R_s & 0 \\ 0 & 0 & R_s \\ \end{bmatrix}}
    {\pmb{T}_{\text{3s-2s}}^{-1}} =
    {\begin{bmatrix} R_s & 0\\ 0 & R_s \end{bmatrix}} \\
    &{\pmb{T}_{\text{3s-2s}}}
    {{\begin{bmatrix}
        L_{aa} & M_{ab} & M_{ac} \\
        M_{ba} & L_{bb} & M_{bc} \\
        M_{ca} & M_{cc} & L_{cc} \\
    \end{bmatrix}}}
    {\pmb{T}_{\text{3s-2s}}^{-1}} =
    {\begin{bmatrix*}[r]
        L_{s0}+M_{s0}+3/2\;L_{s2}\cos(2(\theta_e)) & 3/2\;L_{s2}\sin(2(\theta_e))       \\
        3/2\;L_{s2}\sin(2(\theta_e))             & L_{s0}+M_{s0}-3/2\;L_{s2}\cos(2(\theta_e)) \\
    \end{bmatrix*}} \\
    &{\pmb{T}_{\text{3s-2s}}}
    {\begin{bmatrix*}[l]
        \cos(\theta_e) \\
        \cos(\theta_e-2\pi/3) \\
        \cos(\theta_e+2\pi/3) \\
    \end{bmatrix*}} =
    {\begin{bmatrix*}[l]
        \cos(\theta_e) \\
        \sin(\theta_e)
    \end{bmatrix*}}
\end{aligned}
$$

### *α-β* voltage

$$
\begin{aligned}
    {\pmb{u_{\alpha\beta}}} &= \pmb{R_s i_{\alpha\beta}}+ \frac{d}{dt} \pmb{\it{\Psi_{\alpha\beta}}}
\end{aligned}
$$

$$
\begin{aligned}
    {\begin{bmatrix} u_\alpha \\ u_\beta \\ \end{bmatrix}} &=
    {\begin{bmatrix} R_s & 0\\ 0 & R_s \end{bmatrix}}
    {\begin{bmatrix} u_\alpha \\ u_\beta \\ \end{bmatrix}} + p
    {\begin{bmatrix*}[l]
        {\it\Psi_{\alpha}} \\
        {\it\Psi_{\beta}} \\
    \end{bmatrix*}}
    \\ &=
    {\begin{bmatrix} R_s & 0\\ 0 & R_s \end{bmatrix}}
    {\begin{bmatrix} i_\alpha \\ i_\beta \\ \end{bmatrix}} + p
    {\begin{Bmatrix}
        {{\begin{bmatrix}
            L_{\alpha\alpha} & M_{\alpha\beta} \\
            M_{\beta\alpha}  & L_{\beta\beta}  \\
        \end{bmatrix}}}
        {\begin{bmatrix} i_{\alpha} \\ i_{\beta} \\ \end{bmatrix}} +
        {\begin{bmatrix*}[l]
            {\it\Psi_{f\alpha}} \\
            {\it\Psi_{f\beta}} \\
        \end{bmatrix*}}
    \end{Bmatrix}} \\
\end{aligned}
$$

### *α-β* flux leakage

$$
\begin{aligned}
    {\pmb{\it{\Psi_{\alpha\beta}}}}={\pmb{L_{\alpha\beta} i_{\alpha\beta}}}+{\pmb{\it{\Psi_{f\alpha\beta}}}}
\end{aligned}
$$

$$
\begin{aligned}
    {\begin{bmatrix*}[l]
        {\it\Psi_{\alpha}} \\
        {\it\Psi_{\beta}} \\
    \end{bmatrix*}} &=
    {{\begin{bmatrix}
        L_{\alpha\alpha} & M_{\alpha\beta} \\
        M_{\beta\alpha}  & L_{\beta\beta}  \\
    \end{bmatrix}}}
    {\begin{bmatrix} i_{\alpha} \\ i_{\beta} \\ \end{bmatrix}} +
    {\begin{bmatrix*}[l]
        {\it\Psi_{f\alpha}} \\
        {\it\Psi_{f\beta}} \\
    \end{bmatrix*}} \\ &=
    {{\begin{bmatrix}
        L_{\alpha\alpha} & M_{\alpha\beta} \\
        M_{\beta\alpha}  & L_{\beta\beta}  \\
    \end{bmatrix}}}
    {\begin{bmatrix} i_{\alpha} \\ i_{\beta} \\ \end{bmatrix}} + {\it\Psi_f}
    {\begin{bmatrix*}[l]
        \cos\theta_e \\
        \sin\theta_e \\
    \end{bmatrix*}}
\end{aligned}
$$

$$
\begin{aligned}
    {{\begin{bmatrix}
        L_{\alpha\alpha} & M_{\alpha\beta} \\
        M_{\beta\alpha}  & L_{\beta\beta}  \\
    \end{bmatrix}}}
    &=
    {\begin{bmatrix*}[r]
        L_{s0}+M_{s0}+3/2\;L_{s2}\cos(2(\theta_e)) & 3/2\;L_{s2}\sin(2(\theta_e))       \\
        3/2\;L_{s2}\sin(2(\theta_e))             & L_{s0}+M_{s0}-3/2\;L_{s2}\cos(2(\theta_e)) \\
    \end{bmatrix*}} \\
    &=
    {\begin{bmatrix*}[r]
        (L_d+L_q)/2+(L_d-L_q)/2\;\cos(2(\theta_e)) & (L_d-L_q)/2\;\sin(2(\theta_e))       \\
        (L_d-L_q)/2\;\sin(2(\theta_e))             & (L_d+L_q)/2-(L_d-L_q)/2\;\cos(2(\theta_e)) \\
    \end{bmatrix*}}\\
    &=
    {\begin{bmatrix*}[r]
        \Sigma L+\Delta L\;\cos(2(\theta_e)) &          \Delta L\;\sin(2(\theta_e)) \\
                 \Delta L\;\sin(2(\theta_e)) & \Sigma L-\Delta L\;\cos(2(\theta_e)) \\
    \end{bmatrix*}}
\end{aligned}
$$

## *d-q*

### *α-β* to *d-q*

$$
\begin{aligned}
    {\begin{bmatrix} u_\alpha \\ u_\beta \\ \end{bmatrix}} &=
    {\begin{bmatrix} R_s & 0\\ 0 & R_s \end{bmatrix}}
    {\begin{bmatrix} i_\alpha \\ i_\beta \\ \end{bmatrix}} + p
    {\begin{Bmatrix}
        {{\begin{bmatrix}
            L_{\alpha\alpha} & M_{\alpha\beta} \\
            M_{\beta\alpha}  & L_{\beta\beta}  \\
        \end{bmatrix}}}
        {\begin{bmatrix} i_{\alpha} \\ i_{\beta} \\ \end{bmatrix}} + {\it\Psi_f}
        {\begin{bmatrix*}[l]
            \cos\theta_e \\
            \sin\theta_e \\
        \end{bmatrix*}}
    \end{Bmatrix}} \\
    {\pmb{T}_{\text{2s-2r}}^{-1}}
    {\begin{bmatrix} u_d \\ u_q \end{bmatrix}} &=
    {\begin{bmatrix} R_s & 0\\ 0 & R_s \end{bmatrix}}
    {\pmb{T}_{\text{2s-2r}}^{-1}}
    {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} +p
    {\begin{Bmatrix}
        {{\begin{bmatrix}
            L_{\alpha\alpha} & M_{\alpha\beta} \\
            M_{\beta\alpha}  & L_{\beta\beta}  \\
        \end{bmatrix}}}
        {\pmb{T}_{\text{2s-2r}}^{-1}}
        {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} + {\it\Psi_f}
        {\begin{bmatrix*}[l]
            \cos\theta_e \\
            \sin\theta_e \\
        \end{bmatrix*}}
    \end{Bmatrix}} \\
    {\begin{bmatrix} u_d \\ u_q \end{bmatrix}} &=
    {\pmb{T}_{\text{2s-2r}}}
    {\begin{bmatrix} R_s & 0\\ 0 & R_s \end{bmatrix}}
    {\pmb{T}_{\text{2s-2r}}^{-1}}
    {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} +{\pmb{T}_{\text{2s-2r}}}\;p
    {\begin{Bmatrix}
        {{\begin{bmatrix}
            L_{\alpha\alpha} & M_{\alpha\beta} \\
            M_{\beta\alpha}  & L_{\beta\beta}  \\
        \end{bmatrix}}}
        {\pmb{T}_{\text{2s-2r}}^{-1}}
        {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} + {\it\Psi_f}
        {\begin{bmatrix*}[l]
            \cos\theta_e \\
            \sin\theta_e \\
        \end{bmatrix*}}
    \end{Bmatrix}} \\
\end{aligned}
$$

$$
\begin{aligned}
    &{\pmb{T}_{\text{2s-2r}}}
    {\begin{bmatrix} R_s & 0\\ 0 & R_s \end{bmatrix}}
    {\pmb{T}_{\text{2s-2r}}^{-1}} =
    {\begin{bmatrix} R_s & 0\\ 0 & R_s \end{bmatrix}}
    {\pmb{T}_{\text{2s-2r}}^{-1}} \\
    &{\pmb{T}_{\text{2s-2r}}} \;p
    {\begin{Bmatrix}
        {{\begin{bmatrix}
            L_{\alpha\alpha} & M_{\alpha\beta} \\
            M_{\beta\alpha}  & L_{\beta\beta}  \\
        \end{bmatrix}}}
        {\pmb{T}_{\text{2s-2r}}^{-1}}
        {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} + {\it\Psi_f}
        {\begin{bmatrix*}[l]
            \cos\theta_e \\
            \sin\theta_e \\
        \end{bmatrix*}}
    \end{Bmatrix}} \\ &= p
    {\begin{Bmatrix}
        {\pmb{T}_{\text{2s-2r}}}
        {{\begin{bmatrix}
            L_{\alpha\alpha} & M_{\alpha\beta} \\
            M_{\beta\alpha}  & L_{\beta\beta}  \\
        \end{bmatrix}}}
        {\pmb{T}_{\text{2s-2r}}^{-1}}
        {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} + {\it\Psi_f}\;
        {\pmb{T}_{\text{2s-2r}}}
        {\begin{bmatrix*}[l]
            \cos\theta_e \\
            \sin\theta_e \\
        \end{bmatrix*}}
    \end{Bmatrix}} - (p\;{\pmb{T}_{\text{2s-2r}}})
    {\begin{Bmatrix}
        {{\begin{bmatrix}
            L_{\alpha\alpha} & M_{\alpha\beta} \\
            M_{\beta\alpha}  & L_{\beta\beta}  \\
        \end{bmatrix}}}
        {\pmb{T}_{\text{2s-2r}}^{-1}}
        {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} + {\it\Psi_f}
        {\begin{bmatrix*}[l]
            \cos\theta_e \\
            \sin\theta_e \\
        \end{bmatrix*}}
    \end{Bmatrix}} \\ &= p
    {\begin{bmatrix*}[c]
        L_{s0}+M_{s0}+3/2\;L_{s2} & 0                         \\
        0                         & L_{s0}+M_{s0}-3/2\;L_{s2} \\
    \end{bmatrix*}}
    {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}}\\ &-
    {\begin{bmatrix}
        0 & \omega_e(L_{s0}+M_{s0}-3/2\;L_{s2}) \\
        -\omega_e(L_{s0}+M_{s0}+3/2\;L_{s2})  & 0  \\
    \end{bmatrix}}
    {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} - \omega_e{\it\Psi_f}
    {\begin{bmatrix} 0 \\ -1 \\ \end{bmatrix}} \\ &= p
    {\begin{bmatrix} L_d & 0 \\ 0  & L_q \\ \end{bmatrix}}
    {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} +
    {\begin{bmatrix} 0 & -{\omega_eL_q} \\ {\omega_eL_d}  & 0 \\ \end{bmatrix}}
    {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} + \omega_e{\it\Psi_f}
    {\begin{bmatrix} 0 \\ 1 \\ \end{bmatrix}}
\end{aligned}
$$

### *d-q* voltage

$$
\begin{aligned}
    {\pmb{u_{dq}}} &= {\pmb{R_s i_{dq}}}+ {\frac{d}{dt}}{\pmb{\it{\Psi_{dq}}}}+ {\omega_e}
    {\begin{bmatrix} 0 & -1 \\ 1 & 0 \\ \end{bmatrix}}
    {\pmb{\it{\Psi_{dq}}}}
\end{aligned}
$$

$$
\begin{aligned}
    {\begin{bmatrix} u_d \\ u_q \end{bmatrix}} &=
    {\begin{bmatrix} R_s & 0\\ 0 & R_s \end{bmatrix}}
    {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}}
    +p
    {\begin{bmatrix*}[l]
        {\it\Psi_{d}} \\
        {\it\Psi_{q}} \\
    \end{bmatrix*}} + {\omega_e}
    {\begin{bmatrix} 0 & -1 \\ 1 & 0 \\ \end{bmatrix}}
        {\begin{bmatrix*}[l]
        {\it\Psi_{d}} \\
        {\it\Psi_{q}} \\
    \end{bmatrix*}} \\ &=
    {\begin{bmatrix} R_s & 0\\ 0 & R_s \end{bmatrix}}
    {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} +p
    {\begin{bmatrix} L_d & 0 \\ 0  & L_q \\ \end{bmatrix}}
    {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} +
    {\begin{bmatrix} 0 & -{\omega_eL_q} \\ {\omega_eL_d}  & 0 \\ \end{bmatrix}}
    {\begin{bmatrix} i_d \\ i_q \\ \end{bmatrix}} + \omega_e{\it\Psi_f}
    {\begin{bmatrix} 0 \\ 1 \\ \end{bmatrix}}
\end{aligned}
$$

### *d-q* flux leakage

$$
\begin{aligned}
    {\pmb{\it{\Psi_{dq}}}}={\pmb{L_{dq} i_{dq}}}+{\pmb{\it{\Psi_{fdq}}}}
\end{aligned}
$$

$$
\begin{aligned}
    {\begin{bmatrix*}
        {\it\Psi_{d}} \\
        {\it\Psi_{q}} \\
    \end{bmatrix*}} =
    {{\begin{bmatrix}
        L_d & 0 \\
        0  & L_q  \\
    \end{bmatrix}}}
    {\begin{bmatrix*}[l]
        {i_d} \\
        {i_q} \\
    \end{bmatrix*}}+{\it\Psi_f}{\begin{bmatrix} 0 \\ 1 \\ \end{bmatrix}}
\end{aligned}
$$

$$
\begin{aligned}
    {{\begin{bmatrix}
        L_d & 0 \\
        0  & L_q  \\
    \end{bmatrix}}}
    &=
    {\begin{bmatrix*}[c]
        L_{s0}+M_{s0}+3/2\;L_{s2} & 0 \\
        0                         & L_{s0}+M_{s0}-3/2\;L_{s2} \\
    \end{bmatrix*}}
\end{aligned}
$$
