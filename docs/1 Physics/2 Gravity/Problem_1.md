Great — you’re diving into Kepler’s Third Law, a foundational concept in orbital mechanics. Here's a structured Markdown document outline with integrated Python code, explanations, and visualizations for your task. You can use this in a Jupyter notebook or Markdown environment like JupyterBook or GitHub Pages.

---

#  Gravity — Kepler's Third Law: Orbital Period and Radius

##  Motivation

Kepler's Third Law elegantly relates the time a planet takes to orbit a star to its distance from it. This principle is not only a tool for astronomy but a bridge between observational data and Newtonian physics. In its Newtonian form, the law reveals the gravitational force's role in maintaining celestial motion.

---

##  Derivation: Kepler’s Third Law for Circular Orbits

We begin with Newton’s Law of Universal Gravitation and centripetal force:

$$
F_{\text{gravity}} = \frac{G M m}{r^2}, \quad F_{\text{centripetal}} = \frac{m v^2}{r}
$$

Set these equal for circular motion:

$$
\frac{G M m}{r^2} = \frac{m v^2}{r} \Rightarrow v^2 = \frac{G M}{r}
$$

Orbital period $T$ relates to speed and circumference:

$$
T = \frac{2\pi r}{v} \Rightarrow T^2 = \frac{4\pi^2 r^3}{G M}
$$

This is **Kepler's Third Law** in Newtonian form.

---

##  Implications for Astronomy

* **Mass of Planets/Stars**: If $r$ and $T$ are known, one can solve for $M$, the mass of the central body.
* **Distance Estimation**: Useful for determining the distance of moons or satellites from planets.
* **Comparative Analysis**: Enables comparisons between exoplanet systems and our own Solar System.

---

##  Real-World Examples

### Moon's Orbit around Earth

* Orbital Radius: \~384,400 km
* Period: \~27.3 days

Use Kepler’s law to solve for Earth’s mass.

### Planets in the Solar System

We'll compare multiple planets’ orbital periods and distances to verify $T^2 \propto r^3$.

---

##  Python Simulation and Verification

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # gravitational constant (m^3 kg^-1 s^-2)
M_sun = 1.989e30  # mass of the Sun (kg)

# Planetary data (AU and years)
planets = {
    "Mercury": (0.39, 0.24),
    "Venus": (0.72, 0.62),
    "Earth": (1.00, 1.00),
    "Mars": (1.52, 1.88),
    "Jupiter": (5.20, 11.86),
    "Saturn": (9.58, 29.46),
}

r_values = np.array([r for r, T in planets.values()])
T_values = np.array([T for r, T in planets.values()])

# Plot T^2 vs r^3
r3 = r_values**3
T2 = T_values**2

plt.figure(figsize=(8, 6))
plt.plot(r3, T2, 'o-', label='Planets')
plt.xlabel(r'Orbital Radius $r^3$ (AU$^3$)')
plt.ylabel(r'Orbital Period $T^2$ (years$^2$)')
plt.title("Verification of Kepler's Third Law")
plt.grid(True)
plt.legend()
plt.show()
```

###  Analysis

You’ll see the graph is linear, confirming:

$$
T^2 \propto r^3
$$

---

##  Elliptical Orbits and Extensions

For elliptical orbits, Kepler's Third Law still holds when using the **semi-major axis** $a$ instead of radius:

$$
T^2 = \frac{4\pi^2 a^3}{G M}
$$

---