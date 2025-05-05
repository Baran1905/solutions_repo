Investigating the Dynamics of a Forced Damped Pendulum
1. Theoretical Foundation
Governing Equation
The forced damped pendulum is governed by the nonlinear differential equation:
$ddot{\theta} + 2\beta\dot{\theta} + \omega_0^2\sin(\theta) = A\cos(\omega t)$
where:

(\theta(t)): Angular displacement (rad)
(\beta): Damping coefficient (s⁻¹)
(\omega_0 = \sqrt{g/l}): Natural frequency (rad/s), with (g = 9.81 , \text{m/s}^2), (l): pendulum length (m)
(A): Driving amplitude (rad/s²)
(\omega): Driving frequency (rad/s)
(t): Time (s)

Small-Angle Approximation
For small angles ((\theta \ll 1)), (\sin(\theta) \approx \theta), reducing the equation to:
[\ddot{\theta} + 2\beta\dot{\theta} + \omega_0^2\theta = A\cos(\omega t)]
This is a linear forced damped oscillator. The solution is the sum of a homogeneous solution ((\theta_h)) and a particular solution ((\theta_p)):

Homogeneous solution (underdamped, (\beta < \omega_0)):

[\theta_h(t) = e^{-\beta t} \left( C_1 \cos(\omega_d t) + C_2 \sin(\omega_d t) \right), \quad \omega_d = \sqrt{\omega_0^2 - \beta^2}]

Particular solution:

Assume (\theta_p(t) = D_1 \cos(\omega t) + D_2 \sin(\omega t)). Solving yields:
[D_1 = \frac{A (\omega_0^2 - \omega^2)}{(\omega_0^2 - \omega^2)^2 + (2\beta\omega)^2}, \quad D_2 = \frac{2A\beta\omega}{(\omega_0^2 - \omega^2)^2 + (2\beta\omega)^2}]
The steady-state amplitude is:
[D = \frac{A}{\sqrt{(\omega_0^2 - \omega^2)^2 + (2\beta\omega)^2}}]
Resonance
Resonance occurs when (\omega \approx \omega_0), maximizing (D). Without damping ((\beta = 0)), the amplitude diverges at (\omega = \omega_0). Damping limits the amplitude, and the peak shifts slightly. Resonance increases energy transfer, amplifying oscillations.
2. Analysis of Dynamics
Parameter Effects

Damping ((\beta)): High (\beta) reduces amplitude and stabilizes motion; low (\beta) permits chaos.
Driving amplitude ((A)): Large (A) drives the system into nonlinear regimes, potentially chaotic.
Driving frequency ((\omega)): Near (\omega_0), resonance occurs; far from (\omega_0), quasiperiodic or chaotic motion emerges.

Transition to Chaos
The nonlinear (\sin(\theta)) term causes complex dynamics at high (A) or specific (\omega). Motion transitions from periodic (locked to the driving frequency) to chaotic (sensitive to initial conditions). Phase portraits show closed loops for periodic motion and tangled trajectories for chaos. Poincaré sections display few points for periodic motion and scattered points for chaos.
3. Practical Applications
The model applies to:

Energy harvesting: Oscillatory motion in piezoelectric devices converts mechanical energy to electrical.
Suspension bridges: Periodic forces (wind, traffic) can induce resonant or chaotic vibrations.
Electrical circuits: Driven RLC circuits mirror the pendulum’s dynamics, used in signal processing.
Biomechanics: Models human gait or robotic locomotion under periodic forcing.

Extensions to Real-World Scenarios

Nonlinear damping: Include velocity-dependent terms (e.g., (|\dot{\theta}|\dot{\theta})).
Non-periodic forcing: Model random or multi-frequency inputs.
Coupled systems: Analyze interactions in multi-pendulum setups.

4. Implementation
Below is a Python script to simulate the pendulum, visualize time series, phase portraits, Poincaré sections, and a bifurcation diagram.
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Parameters
g = 9.81  # m/s^2
l = 1.0   # pendulum length (m)
omega0 = np.sqrt(g / l)  # natural frequency
beta = 0.1  # damping coefficient
A = 1.5     # driving amplitude
omega = 2.0 # driving frequency
t_span = (0, 100)  # time span
dt = 0.01  # time step
t_eval = np.arange(0, 100, dt)
theta0, omega0_init = 0.1, 0.0  # initial conditions

# Differential equation
def pendulum(t, y, beta, omega0, A, omega):
    theta, omega = y
    return [omega, -2 * beta * omega - omega0**2 * np.sin(theta) + A * np.cos(omega * t)]

# Solve ODE
sol = solve_ivp(pendulum, t_span, [theta0, omega0_init], method='RK45', t_eval=t_eval,
                args=(beta, omega0, A, omega))
theta, omega_dot = sol.y[0], sol.y[1]
t = sol.t

# Time series
plt.figure(figsize=(10, 4))
plt.plot(t, theta, label=r'$\theta(t)$')
plt.xlabel('Time (s)')
plt.ylabel(r'$\theta$ (rad)')
plt.title('Time Series')
plt.legend()
plt.grid(True)
plt.savefig('time_series.png')
plt.show()

# Phase portrait
plt.figure(figsize=(8, 6))
plt.plot(theta, omega_dot, label='Phase trajectory')
plt.xlabel(r'$\theta$ (rad)')
plt.ylabel(r'$\dot{\theta}$ (rad/s)')
plt.title('Phase Portrait')
plt.legend()
plt.grid(True)
plt.savefig('phase_portrait.png')
plt.show()

# Poincaré section
T = 2 * np.pi / omega
poincare_times = np.arange(0, t[-1], T)
poincare_indices = np.searchsorted(t, poincare_times)
theta_poincare = theta[poincare_indices]
omega_poincare = omega_dot[poincare_indices]

plt.figure(figsize=(8, 6))
plt.scatter(theta_poincare, omega_poincare, s=10, label='Poincaré section')
plt.xlabel(r'$\theta$ (rad)')
plt.ylabel(r'$\dot{\theta}$ (rad/s)')
plt.title('Poincaré Section')
plt.legend()
plt.grid(True)
plt.savefig('poincare_section.png')
plt.show()

# Resonance curve
omega_range = np.linspace(0.5, 3.0, 100)
amplitude = A / np.sqrt((omega0**2 - omega_range**2)**2 + (2 * beta * omega_range)**2)

plt.figure(figsize=(10, 4))
plt.plot(omega_range, amplitude, label='Amplitude')
plt.axvline(omega0, color='r', linestyle='--', label=r'$\omega_0$')
plt.xlabel(r'Driving Frequency $\omega$ (rad/s)')
plt.ylabel('Amplitude (rad)')
plt.title('Resonance Curve')
plt.legend()
plt.grid(True)
plt.savefig('resonance_curve.png')
plt.show()

# Bifurcation diagram
A_range = np.linspace(0.5, 2.5, 100)
theta_bifurcation = []
t_span_bif = (0, 200)
t_eval_bif = np.arange(100, 200, dt)

for A in A_range:
    sol_bif = solve_ivp(pendulum, t_span_bif, [theta0, omega0_init], method='RK45',
                        t_eval=t_eval_bif, args=(beta, omega0, A, omega))
    theta_bif = sol_bif.y[0]
    poincare_indices_bif = np.searchsorted(sol_bif.t, np.arange(100, 200, T))
    theta_bifurcation.extend(theta_bif[poincare_indices_bif])

A_bifurcation = np.repeat(A_range, len(poincare_indices_bif))

plt.figure(figsize=(10, 6))
plt.scatter(A_bifurcation, theta_bifurcation, s=1, alpha=0.5)
plt.xlabel('Driving Amplitude $A$ (rad/s²)')
plt.ylabel(r'$\theta$ (rad)')
plt.title('Bifurcation Diagram')
plt.grid(True)
plt.savefig('bifurcation_diagram.png')
plt.show()

Output Description

Time Series: Plots (\theta(t)), showing periodic or chaotic oscillations.
Phase Portrait: Displays (\theta) vs. (\dot{\theta}), revealing periodic loops or chaotic trajectories.
Poincaré Section: Samples states every driving period, with few points for periodic motion and scattered points for chaos.
Resonance Curve: Shows steady-state amplitude vs. (\omega), peaking near (\omega_0).
Bifurcation Diagram: Plots (\theta) at Poincaré times vs. (A), showing transitions from periodic (lines) to chaotic (dense regions) behavior.

5. Limitations and Extensions
Limitations

Small-angle approximation: Invalid for large (\theta), missing nonlinear effects.
Linear damping: Assumes constant (\beta), ignoring complex friction models.
Periodic forcing: Limits applicability to non-periodic systems.

Suggestions for Realism

Nonlinear damping: Use terms like (|\dot{\theta}|\dot{\theta}).
Non-periodic forcing: Introduce random or multi-frequency drives.
Coupled pendulums: Model multi-pendulum interactions.
3D motion: Extend to spherical pendulums for more complex dynamics.

6. Conclusion
The forced damped pendulum reveals a spectrum of behaviors, from resonance to chaos, governed by damping, driving amplitude, and frequency. Simulations and visualizations, including bifurcation diagrams, highlight these transitions, offering insights into oscillatory systems across physics and engineering. Extensions like nonlinear damping could further enhance the model’s realism.
