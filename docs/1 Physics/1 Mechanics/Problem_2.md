# Forced Damped Pendulum Simulation and Analysis

import numpy as np
import matplotlib.pyplot as plt

# === Parameters ===
gamma = 0.2         # Damping coefficient
omega0 = 1.0        # Natural frequency (sqrt(g/L))
A = 1.2             # Driving force amplitude
omega = 0.666       # Driving force frequency
dt = 0.01           # Time step
T = 200             # Total time
n = int(T/dt)       # Number of steps

# === Initial Conditions ===
theta = np.zeros(n)
omega_dot = np.zeros(n)
theta[0] = 0.2      # Initial angle
omega_dot[0] = 0.0  # Initial angular velocity
t = np.linspace(0, T, n)

# === Differential Equation ===
def derivatives(theta, omega_dot, t):
    dtheta_dt = omega_dot
    domega_dt = -gamma * omega_dot - omega0**2 * np.sin(theta) + A * np.cos(omega * t)
    return dtheta_dt, domega_dt

# === Runge-Kutta 4th Order Integration ===
for i in range(n - 1):
    k1_theta, k1_omega = derivatives(theta[i], omega_dot[i], t[i])
    k2_theta, k2_omega = derivatives(theta[i] + 0.5 * dt * k1_theta, omega_dot[i] + 0.5 * dt * k1_omega, t[i] + 0.5 * dt)
    k3_theta, k3_omega = derivatives(theta[i] + 0.5 * dt * k2_theta, omega_dot[i] + 0.5 * dt * k2_omega, t[i] + 0.5 * dt)
    k4_theta, k4_omega = derivatives(theta[i] + dt * k3_theta, omega_dot[i] + dt * k3_omega, t[i] + dt)

    theta[i+1] = theta[i] + (dt / 6) * (k1_theta + 2 * k2_theta + 2 * k3_theta + k4_theta)
    omega_dot[i+1] = omega_dot[i] + (dt / 6) * (k1_omega + 2 * k2_omega + 2 * k3_omega + k4_omega)

# === Plot: Angular Displacement vs Time ===
plt.figure(figsize=(10, 4))
plt.plot(t, theta, label="Theta(t)")
plt.title("Forced Damped Pendulum: Angular Displacement vs Time")
plt.xlabel("Time")
plt.ylabel("Theta (rad)")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()

# === Plot: Phase Space ===
plt.figure(figsize=(6, 6))
plt.plot(theta, omega_dot, lw=0.5)
plt.title("Phase Space: Theta vs Angular Velocity")
plt.xlabel("Theta (rad)")
plt.ylabel("Omega (rad/s)")
plt.grid(True)
plt.tight_layout()
plt.show()

# === Plot: Poincare Section ===
poincare_t = np.arange(0, T, 2*np.pi/omega)
poincare_indices = [int(i/dt) for i in poincare_t if int(i/dt) < len(theta)]
poincare_theta = theta[poincare_indices]
poincare_omega = omega_dot[poincare_indices]

plt.figure(figsize=(6, 6))
plt.scatter(poincare_theta, poincare_omega, s=1)
plt.title("Poincare Section")
plt.xlabel("Theta (rad)")
plt.ylabel("Omega (rad/s)")
plt.grid(True)
plt.tight_layout()
plt.show()
