# Problem 1

## Kepler's Third Law: Orbital Period and Radius

### Derivation of the Relationship for Circular Orbits

For a body in circular orbit, the gravitational force provides the centripetal force required for circular motion. Let’s derive Kepler’s Third Law step-by-step.

**Step 1: Gravitational Force**

The gravitational force between two masses ( M ) (central body) and ( m ) (orbiting body) at distance ( r ) (orbital radius) is:

$F_g = \frac{G M m}{r^2}$

$$where ( G ) is the gravitational constant (( G \approx 6.674 \times 10^{-11} , \text{m}^3 \text{kg}^{-1} \text{s}^{-2} )).$$

**Step 2: Centripetal Force**

For circular motion, the centripetal force required to keep the orbiting body moving at speed ( v ) in a circular path of radius ( r ) is:

$F_c = \frac{m v^2}{r}$

**Step 3: Equate Forces**

Since the gravitational force provides the centripetal force:

$frac{G M m}{r^2} = \frac{m v^2}{r}$

Simplify by canceling ( m ) (assuming ( m \neq 0 )) and multiplying through by ( r ):

$frac{G M}{r} = v^2$

**Step 4: Orbital Velocity**

The orbital period ( T ) is the time taken for one complete orbit. The circumference of the circular orbit is ( 2\pi r ), so the orbital velocity ( v ) is:

$v = \frac{2\pi r}{T}$

Square the velocity:

$v^2 = \frac{4\pi^2 r^2}{T^2}$

**Step 5: Substitute and Simplify**

Substitute $( v^2 )$ into the force balance equation:

$frac{G M}{r} = \frac{4\pi^2 r^2}{T^2}$ 

Multiply through by $( T^2 )$:

$frac{G M T^2}{r} = 4\pi^2 r^2$ 

**Rearrange:**

$T^2 = \frac{4\pi^2 r^3}{G M}$

This is Kepler’s Third Law for circular orbits, showing that the square of the orbital period (( T^2 )) is proportional to the cube of the orbital radius (( r^3 )):

$T^2 \propto r^3$

The constant of proportionality is $frac{4\pi^2}{G M} , which depends on the mass of the central body.

**Implications for Astronomy**

Kepler’s Third Law is a powerful tool in astronomy with several key applications:





Determining Planetary Masses: By measuring the orbital period ( T ) and radius ( r ) of a satellite or planet, the mass of the central body ( M ) can be calculated using:

$M = \frac{4\pi^2 r^3}{G T^2}$

This is commonly used to estimate the masses of planets and stars by observing their moons or orbiting companions.





Calculating Orbital Distances: If the mass of the central body is known (e.g., the Sun), the orbital radius of a planet can be determined from its orbital period, or vice versa.



Exoplanet Detection: Kepler’s Third Law helps in characterizing exoplanetary systems by relating the orbital periods and distances of planets around distant stars.



Satellite Orbits: The law is used to design orbits for artificial satellites, ensuring they maintain stable periods and altitudes.

### Real-World Examples

**The Moon’s Orbit Around Earth**





Orbital Radius: Approximately ( r = 384,400 , \text{km} = 3.844 \times 10^8 , \text{m} )



Orbital Period: Approximately ( T = 27.32 , \text{days} = 2.36 \times 10^6 , \text{s} )



Earth’s Mass: Using Kepler’s Third Law:

$M = \frac{4\pi^2 r^3}{G T^2}$

$M = \frac{4\pi^2 (3.844 \times 10^8)^3}{6.674 \times 10^{-11} \cdot (2.36 \times 10^6)^2}$

$M \approx 5.97 \times 10^{24} , \text{kg}$

This matches Earth’s known mass, confirming the validity of the law.

**Planets in the Solar System**

For planets orbiting the Sun (( M \approx 1.989 \times 10^{30} , \text{kg} )), Kepler’s Third Law can be simplified. Expressing ( r ) in astronomical units (AU, where 1 AU is Earth’s orbital radius) and ( T ) in years, the constant $frac{4\pi^2}{G M}  becomes approximately 1, so:

$T^2 \approx r^3$

For example, Jupiter’s orbital radius is about 5.2 AU, so its period is:

$T \approx \sqrt{(5.2)^3} \approx 11.86 , \text{years}$

This agrees with observations.

**Computational Model**

Below is a Python script that simulates circular orbits and verifies Kepler’s Third Law by plotting $( T^2 )$ versus $( r^3 )$.

 import numpy as np import matplotlib.pyplot as plt

**Constants**

G = 6.674e-11 # Gravitational constant $(m^3 kg^-1 s^-2)$ M_sun = 1.989e30 # Mass of the Sun (kg) AU = 1.496e11 # 1 AU in meters year = 3.156e7 # 1 year in seconds

Function to calculate orbital period

$def orbital_period(r, M): return np.sqrt((4 * np.pi2 * r3) / (G * M))$

Orbital radii (in AU, converted to meters)

$radii_au$ = $np.array(0.39, 0.72, 1.0, 1.52, 5.2, 9.58, 19.18, 30.07)$ # Mercury to Neptune radii = radii_au * AU

Calculate periods

periods = orbital_period(radii, M_sun) / year # Convert to years

Verify $T^2$ vs $r^3$

$T_squared = periods2 r_cubed = radii_au3$

### Plotting

### 📈 Kepler's Third Law Plot

```python
plt.figure(figsize=(10, 6))
plt.scatter(r_cubed, T_squared, color='blue', label='Planets')
plt.plot(r_cubed, r_cubed, color='red', linestyle='--', label='T^2 = r^3')
plt.xlabel('r^3 (AU^3)')
plt.ylabel('T^2 (years^2)')
plt.title('Kepler’s Third Law: T^2 vs r^3')
plt.legend()
plt.grid(True)
plt.savefig('kepler_third_law.png')
plt.close()
```

### Simulate circular orbit visualization

```python
def plot_orbit(r, title):
    theta = np.linspace(0, 2*np.pi, 100)
    x = r * np.cos(theta) / AU
    y = r * np.sin(theta) / AU

    plt.figure(figsize=(6, 6))
    plt.plot(x, y, label=f'Orbit (r = {r/AU:.2f} AU)')
    plt.scatter([0], [0], color='orange', s=100, label='Sun')
    plt.xlabel('X (AU)')
    plt.ylabel('Y (AU)')
    plt.title(title)
    plt.legend()
    plt.grid(True)
    plt.axis('equal')
    plt.savefig(f'orbit_{r/AU:.2f}.png')
    plt.close()
```

### Plot orbits for Earth and Jupiter

$plot_orbit(1.0 * AU, 'Earth’s Orbit') plot_orbit(5.2 * AU, 'Jupiter’s Orbit')$