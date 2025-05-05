Investigating the Dynamics of a Forced Damped Pendulum
1. Theoretical Foundation
Governing Equation
The motion of a forced damped pendulum is described by the nonlinear second-order differential equation:

𝜃
¨
+
2
𝛽
𝜃
˙
+
𝜔
0
2
sin
⁡
(
𝜃
)
=
𝐴
cos
⁡
(
𝜔
𝑡
)
θ
¨
 +2β 
θ
˙
 +ω 
0
2
​
 sin(θ)=Acos(ωt)
Where:

𝜃
(
𝑡
)
θ(t): Angular displacement (rad)

𝛽
β: Damping coefficient (
𝑠
−
1
s 
−1
 )

𝜔
0
=
𝑔
𝑙
ω 
0
​
 = 
l
g
​
 
​
 : Natural frequency (
𝑟
𝑎
𝑑
/
𝑠
rad/s)

𝑔
=
9.81
 
𝑚
/
𝑠
2
g=9.81 m/s 
2
 : Gravitational acceleration

𝑙
l: Pendulum length (m)

𝐴
A: Driving amplitude (
𝑟
𝑎
𝑑
/
𝑠
2
rad/s 
2
 )

𝜔
ω: Driving frequency (
𝑟
𝑎
𝑑
/
𝑠
rad/s)

𝑡
t: Time (s)

2. Linear Approximation (Small-Angle)
For small angles (
𝜃
≪
1
θ≪1), the equation simplifies using 
sin
⁡
(
𝜃
)
≈
𝜃
sin(θ)≈θ:

𝜃
¨
+
2
𝛽
𝜃
˙
+
𝜔
0
2
𝜃
=
𝐴
cos
⁡
(
𝜔
𝑡
)
θ
¨
 +2β 
θ
˙
 +ω 
0
2
​
 θ=Acos(ωt)
This linear nonhomogeneous ODE has the general solution:

𝜃
(
𝑡
)
=
𝜃
ℎ
(
𝑡
)
+
𝜃
𝑝
(
𝑡
)
θ(t)=θ 
h
​
 (t)+θ 
p
​
 (t)
Homogeneous Solution (Underdamped case: 
𝛽
<
𝜔
0
β<ω 
0
​
 ):
𝜃
ℎ
(
𝑡
)
=
𝑒
−
𝛽
𝑡
(
𝐶
1
cos
⁡
(
𝜔
𝑑
𝑡
)
+
𝐶
2
sin
⁡
(
𝜔
𝑑
𝑡
)
)
,
𝜔
𝑑
=
𝜔
0
2
−
𝛽
2
θ 
h
​
 (t)=e 
−βt
 (C 
1
​
 cos(ω 
d
​
 t)+C 
2
​
 sin(ω 
d
​
 t)),ω 
d
​
 = 
ω 
0
2
​
 −β 
2
 
​
 
Particular Solution:
Assume:

𝜃
𝑝
(
𝑡
)
=
𝐷
1
cos
⁡
(
𝜔
𝑡
)
+
𝐷
2
sin
⁡
(
𝜔
𝑡
)
θ 
p
​
 (t)=D 
1
​
 cos(ωt)+D 
2
​
 sin(ωt)
Solving yields:

𝐷
1
=
𝐴
(
𝜔
0
2
−
𝜔
2
)
(
𝜔
0
2
−
𝜔
2
)
2
+
(
2
𝛽
𝜔
)
2
,
𝐷
2
=
2
𝐴
𝛽
𝜔
(
𝜔
0
2
−
𝜔
2
)
2
+
(
2
𝛽
𝜔
)
2
D 
1
​
 = 
(ω 
0
2
​
 −ω 
2
 ) 
2
 +(2βω) 
2
 
A(ω 
0
2
​
 −ω 
2
 )
​
 ,D 
2
​
 = 
(ω 
0
2
​
 −ω 
2
 ) 
2
 +(2βω) 
2
 
2Aβω
​
 
The steady-state amplitude is:

𝐷
=
𝐷
1
2
+
𝐷
2
2
=
𝐴
(
𝜔
0
2
−
𝜔
2
)
2
+
(
2
𝛽
𝜔
)
2
D= 
D 
1
2
​
 +D 
2
2
​
 
​
 = 
(ω 
0
2
​
 −ω 
2
 ) 
2
 +(2βω) 
2
 
​
 
A
​
 
3. Resonance and Nonlinear Dynamics
Resonance Behavior
Resonance occurs when 
𝜔
≈
𝜔
0
ω≈ω 
0
​
 , resulting in a peak in amplitude. Damping 
(
𝛽
>
0
)
(β>0) prevents divergence, shifting the peak frequency slightly and reducing the amplitude.

Parameter Influence
Damping (
𝛽
β): High damping suppresses oscillations and chaos; low damping allows richer dynamics.

Driving Amplitude (
𝐴
A): Higher 
𝐴
A induces stronger nonlinearities, possibly leading to chaos.

Driving Frequency (
𝜔
ω): Near resonance causes large periodic responses; far from resonance may result in quasiperiodic or chaotic behavior.

4. Transition to Chaos
The full nonlinear equation with 
sin
⁡
(
𝜃
)
sin(θ) (no small-angle approximation) enables chaotic dynamics due to sensitivity to initial conditions.

Periodic Motion: Closed loops in phase space.

Chaotic Motion: Irregular, fractal-like paths; sensitive to initial conditions.

Tools:

Phase Portraits: Visualize trajectory behavior.

Poincaré Sections: Sample the state once per period of driving force.

Bifurcation Diagrams: Show changes in system behavior as a parameter (e.g., 
𝐴
A) varies.

5. Practical Applications
Energy Harvesting: Piezoelectric generators converting oscillations to electrical power.

Structural Engineering: Modeling bridges and buildings under dynamic forces.

Electronics: Analogs in RLC circuits and resonance behavior.

Biomechanics & Robotics: Gait analysis and driven limb movement.

6. Computational Implementation
Numerical Simulation in Python (Runge-Kutta)
python
Kopyala
Düzenle
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Constants
g = 9.81
l = 1.0
omega0 = np.sqrt(g / l)
beta_values = [0.05, 0.1, 0.5]
A = 1.5
omega = 2.0
t_span = (0, 100)
dt = 0.01
t_eval = np.arange(*t_span, dt)
theta0, omega0_init = 0.1, 0.0

# Differential equation
def pendulum(t, y, beta, omega0, A, omega):
    theta, omega_dot = y
    return [omega_dot, -2*beta*omega_dot - omega0**2*np.sin(theta) + A*np.cos(omega*t)]

# Time Series for Different Damping
plt.figure(figsize=(10, 6))
for beta in beta_values:
    sol = solve_ivp(pendulum, t_span, [theta0, omega0_init], t_eval=t_eval, args=(beta, omega0, A, omega))
    plt.plot(sol.t, sol.y[0], label=f'β = {beta}')
plt.xlabel('Time (s)')
plt.ylabel(r'$\theta$ (rad)')
plt.title('Time Series for Different Damping Coefficients')
plt.legend()
plt.grid(True) 
plt.show()

# Phase Portrait (β = 0.1)
sol = solve_ivp(pendulum, t_span, [theta0, omega0_init], t_eval=t_eval, args=(0.1, omega0, A, omega))
theta, omega_dot = sol.y
plt.figure(figsize=(8, 6))
plt.plot(theta, omega_dot)
plt.xlabel(r'$\theta$ (rad)')
plt.ylabel(r'$\dot{\theta}$ (rad/s)')
plt.title('Phase Portrait (β = 0.1)')
plt.grid(True) 
plt.show()

# Poincaré Section
T = 2 * np.pi / omega
poincare_times = np.arange(0, sol.t[-1], T)
indices = np.searchsorted(sol.t, poincare_times)
plt.figure(figsize=(8, 6))
plt.scatter(theta[indices], omega_dot[indices], s=10)
plt.xlabel(r'$\theta$ (rad)')
plt.ylabel(r'$\dot{\theta}$ (rad/s)')
plt.title('Poincaré Section (β = 0.1)')
plt.grid(True) 
plt.show()

# Resonance Curve
omega_range = np.linspace(0.5, 3.0, 100)
amplitude = A / np.sqrt((omega0**2 - omega_range**2)**2 + (2 * 0.1 * omega_range)**2)
plt.figure(figsize=(10, 6))
plt.plot(omega_range, amplitude)
plt.axvline(omega0, color='r', linestyle='--', label=r'$\omega_0$')
plt.xlabel('Driving Frequency ω (rad/s)')
plt.ylabel('Amplitude (rad)')
plt.title('Resonance Curve (β = 0.1)')
plt.legend()
plt.grid(True) 
plt.show()

# Bifurcation Diagram
A_range = np.linspace(0.5, 2.5, 100)
theta_bifurcation = []
t_span_bif = (0, 200)
t_eval_bif = np.arange(100, 200, dt)
for A_val in A_range:
    sol_bif = solve_ivp(pendulum, t_span_bif, [theta0, omega0_init], t_eval=t_eval_bif, args=(0.1, omega0, A_val, omega))
    T = 2 * np.pi / omega
    poincare_indices = np.searchsorted(sol_bif.t, np.arange(100, 200, T))
    theta_bifurcation.extend(sol_bif.y[0][poincare_indices])
A_bifurcation = np.repeat(A_range, len(poincare_indices))
plt.figure(figsize=(10, 6))
plt.scatter(A_bifurcation, theta_bifurcation, s=1, alpha=0.5)
plt.xlabel('Driving Amplitude $A$ (rad/s²)')
plt.ylabel(r'$\theta$ (rad)')
plt.title('Bifurcation Diagram (β = 0.1)')
plt.grid(True) 
plt.show()
7. Simulation Outputs
Time Series: Shows 
𝜃
(
𝑡
)
θ(t) for various 
𝛽
β, illustrating damping effects.

Phase Portrait: 
𝜃
θ vs. 
𝜃
˙
θ
˙
 , reveals system behavior (e.g., limit cycles).

Poincaré Section: Captures system at driving period intervals, indicating periodicity or chaos.

Resonance Curve: Visualizes steady-state amplitude vs. driving frequency.

Bifurcation Diagram: Demonstrates transitions from periodic to chaotic regimes as 
𝐴
A increases.

8. Limitations and Extensions
Limitations
Small-angle approximation fails at large amplitudes.

Linear damping may not capture real-world friction accurately.

Assumes purely periodic forcing.

Extensions
Nonlinear damping models (e.g., quadratic or Coulomb friction).

Stochastic forcing to simulate real-world variability.

Coupled pendulums for multi-body interactions and synchronization phenomena.

Conclusion
The forced damped pendulum encapsulates rich physical behavior, transitioning from periodic to chaotic motion depending on system parameters. Through numerical simulations and analytical insight, one can explore the complexity of non-linear dynamics, resonance, and chaos — relevant across engineering, physics, and applied sciences.