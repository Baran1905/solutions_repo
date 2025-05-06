# Problem 2
Escape Velocities and Cosmic Velocities
Definitions and Physical Meaning

First Cosmic Velocity (v₁): The minimum speed required for an object to achieve a stable circular orbit around a celestial body, also known as orbital velocity. It balances the gravitational pull with the centripetal force needed for circular motion.
Second Cosmic Velocity (v₂): The escape velocity, the minimum speed needed for an object to escape the gravitational influence of a celestial body without further propulsion. At this speed, the object's kinetic energy equals the gravitational potential energy at the surface.
Third Cosmic Velocity (v₃): The velocity required for an object to escape the gravitational influence of a star system (e.g., the Solar System) and enter interstellar space. It accounts for escaping both the planet's and the star's gravitational fields.

Mathematical Derivations
First Cosmic Velocity (v₁)
For a circular orbit, the gravitational force provides the centripetal force:F_g = \frac{G M m}{r^2} = \frac{m v_1^2}{r$Solving for ( v_1 ):v_1 = \sqrt$frac{G M}{r}$Where:

( G ): Gravitational constant (( 6.67430 \times 10^{-11} , \text{m}^3 \text{kg}^{-1} \text{s}^{-2} ))
( M ): Mass of the celestial body (kg)
( r ): Radius of the orbit (typically the body's radius for surface-launched orbits, in meters)

Second Cosmic Velocity (v₂)
The escape velocity is derived from energy conservation, where the kinetic energy equals the gravitational potential energy:$frac{1}{2} m v_2^2 = \frac{G M m}{r$Solving for ( v_2 ):v_2 = \sqrt$frac{2 G M}{r}$Note that ( v_2 = \sqrt{2} \cdot v_1 ), meaning the escape velocity is ( \sqrt{2} ) times the orbital velocity.
Third Cosmic Velocity (v₃)
The third cosmic velocity is the speed needed to escape the star's gravitational field from the planet's orbit. It is derived by considering the escape velocity from the star (e.g., the Sun) at the planet's orbital distance, combined with the planet's escape velocity. The simplified formula for a planet at distance ( R ) from the star (mass ( M_s )) is:v_3 \approx \sqrt{v_2^2 + v_$text{esc,sun}}^2$Where  v_$text{esc,sun}} = \sqrt$frac{2 G M_s}{R}} , and ( R ) is the distance from the star (e.g., Earth's distance from the Sun, ~1 AU).
Parameters Affecting Velocities

Mass of the Celestial Body (M): Higher mass increases gravitational pull, increasing all cosmic velocities.
Radius of the Body (r): Larger radius reduces the velocity required, as the object is farther from the center of gravity.
Distance from the Star (R): For ( v_3 ), the planet's distance from the star affects the escape velocity from the star's gravitational field.

Python Implementation and Visualization
The following Python script calculates the first, second, and third cosmic velocities for Earth, Mars, and Jupiter, and visualizes the results using Matplotlib.

import numpy as np
import matplotlib.pyplot as plt

Constants
G = 6.67430e-11  # Gravitational constant (m^3 kg^-1 s^-2)M_sun = 1.989e30  # Mass of the Sun (kg)AU = 1.496e11     # Astronomical unit (m)
Celestial body data: [Mass (kg), Radius (m), Distance from Sun (m)]
bodies = {    'Earth': [5.972e24, 6.371e6, 1.0 * AU],    'Mars': [6.417e23, 3.390e6, 1.524 * AU],    'Jupiter': [1.898e27, 6.991e7, 5.204 * AU]}
Calculate velocities
v1 = {}  # First cosmic velocity (orbital)v2 = {}  # Second cosmic velocity (escape)v3 = {}  # Third cosmic velocity (interstellar)
for body, (mass, radius, dist_sun) in bodies.items():    # First cosmic velocity    v1[body] = np.sqrt(G * mass / radius) / 1000  # Convert to km/s    # Second cosmic velocity    v2[body] = np.sqrt(2 * G * mass / radius) / 1000  # Convert to km/s    # Third cosmic velocity (approximation)    v_esc_sun = np.sqrt(2 * G * M_sun / dist_sun)  # Escape velocity from Sun    v3[body] = np.sqrt(v2[body]**2 + (v_esc_sun / 1000)**2)  # Combine, in km/s
Visualization
bodies_list = list(bodies.keys())v1_values = [v1[body] for body in bodies_list]v2_values = [v2[body] for body in bodies_list]v3_values = [v3[body] for body in bodies_list]
x = np.arange(len(bodies_list))width = 0.25
plt.figure(figsize=(10, 6))plt.bar(x - width, v1_values, width, label='First Cosmic Velocity (v₁)', color='blue')plt.bar(x, v2_values, width, label='Second Cosmic Velocity (v₂)', color='orange')plt.bar(x + width, v3_values, width, label='Third Cosmic Velocity (v₃)', color='green')
plt.xlabel('Celestial Body')plt.ylabel('Velocity (km/s)')plt.title('Cosmic Velocities for Earth, Mars, and Jupiter')plt.xticks(x, bodies_list)plt.legend()plt.grid(True, axis='y')plt.savefig('cosmic_velocities.png')
