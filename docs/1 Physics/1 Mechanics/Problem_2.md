import numpy as np
import matplotlib.pyplot as plt
 
 
# Pendulum parameters
gamma = 0.2      # Damping coefficient
omega0 = 1.0     # Natural frequency
A = 1.2          # Driving force amplitude
omega = 0.666    # Driving force frequency

# Time parameters
dt = 0.01
T = 200
n = int(T/dt)

# Initial conditions
theta = np.zeros(n)
omega_dot = np.zeros(n)
theta[0] = 0.2
omega_dot[0] = 0

# Driving force
t = np.linspace(0, T, n)

# Function for derivatives
def derivatives(theta, omega_dot, t):
    dtheta_dt = omega_dot
    domega_dt = -gamma * omega_dot - omega0**2 * np.sin(theta) + A * np.cos(omega * t)
    return dtheta_dt, domega_dt

# Runge-Kutta 4th-order integration
for i in range(n - 1):
    k1_theta, k1_omega = derivatives(theta[i], omega_dot[i], t[i])
    k2_theta, k2_omega = derivatives(theta[i] + 0.5*dt*k1_theta, omega_dot[i] + 0.5*dt*k1_omega, t[i] + 0.5*dt)
    k3_theta, k3_omega = derivatives(theta[i] + 0.5*dt*k2_theta, omega_dot[i] + 0.5*dt*k2_omega, t[i] + 0.5*dt)
    k4_theta, k4_omega = derivatives(theta[i] + dt*k3_theta, omega_dot[i] + dt*k3_omega, t[i] + dt)

    theta[i+1] = theta[i] + (dt/6)*(k1_theta + 2*k2_theta + 2*k3_theta + k4_theta)
    omega_dot[i+1] = omega_dot[i] + (dt/6)*(k1_omega + 2*k2_omega + 2*k3_omega + k4_omega)

# Plotting
plt.plot(t, theta)
plt.title("Angular Displacement vs Time")
plt.xlabel("Time")
plt.ylabel("Theta")
plt.grid()
plt.show()
