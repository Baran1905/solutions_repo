# Problem 2import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Parameters (can be varied for experimentation)
g = 9.81        # gravity (m/s^2)
L = 1.0         # length of pendulum (m)
b = 0.5         # damping coefficient
A = 1.2         # amplitude of driving force
omega_d = 2/3   # driving frequency

# Small-angle approximation: sin(theta) ~ theta
# Full nonlinear equation: theta'' + b*theta' + (g/L)*sin(theta) = A*cos(omega_d * t)

def pendulum(t, y):
    theta, omega = y
    dtheta_dt = omega
    domega_dt = -b * omega - (g / L) * np.sin(theta) + A * np.cos(omega_d * t)
    return [dtheta_dt, domega_dt]

# Initial conditions and time span
y0 = [0.2, 0.0]  # small initial angle and zero initial angular velocity
t_span = (0, 100)
t_eval = np.linspace(*t_span, 5000)

# Solve using Runge-Kutta method (RK45)
sol = solve_ivp(pendulum, t_span, y0, t_eval=t_eval)

# Plot time series
plt.figure(figsize=(10, 4))
plt.plot(sol.t, sol.y[0], label='Theta (rad)')
plt.xlabel('Time (s)')
plt.ylabel('Angular Displacement')
plt.title('Forced Damped Pendulum Motion')
plt.legend()
plt.grid(True)
plt.tight_layout()
plt.show()

# Plot phase space (theta vs omega)
plt.figure(figsize=(6, 6))
plt.plot(sol.y[0], sol.y[1])
plt.xlabel('Theta (rad)')
plt.ylabel('Angular Velocity (rad/s)')
plt.title('Phase Space')
plt.grid(True)
plt.tight_layout()
plt.show()

# Poincaré Section
poincare_t = np.arange(0, 100, 2*np.pi/omega_d)
poincare_theta = np.interp(poincare_t, sol.t, sol.y[0])
poincare_omega = np.interp(poincare_t, sol.t, sol.y[1])

plt.figure(figsize=(6, 6))
plt.plot(poincare_theta, poincare_omega, 'o', markersize=2)
plt.xlabel('Theta (rad)')
plt.ylabel('Angular Velocity (rad/s)')
plt.title('Poincaré Section')
plt.grid(True)
plt.tight_layout()
plt.show()
