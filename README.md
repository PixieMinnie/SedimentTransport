# SedimentTransport
# Basic sediment transport python code
import numpy as np
import matplotlib.pyplot as plt

# Given parameters (typical values)

U = 1.5         # Flow velocity (m/s)
S = 0.01        # Bed slope (dimensionless)
D50 = 0.02      # Median grain size (m)
h = 0.5         # Water depth (m)
rho_w = 1000    # Water density (kg/m**3)
rho_s = 2650    # Sediment density (kg/m**3)
g = 9.8         # Gravity (m/s**2)

# Compute shear stress

tau = rho_w * g * h * S

print (f"Shear Stress (T) = {tau:.2f} Pa")

#---------------------------------------------------------------------------------

# Critical shear stress for sediment motion
tau_c = 0.3  # Adjust based on grain size and river conditions

# Compute sediment transport only if τ > τ_c
if tau > tau_c:
    q_s = 8 * (tau - tau_c) ** 1.5
else:
    q_s = 0 # No movement if below threshold

print (f"Sediment transport rate (q_s) = {q_s:.2f} m**2/s")

#----------------------------------------------------------------------------------

# Define range of shear stresses
tau_values = np.linspace(0, 2, 100)  # Vary τ from 0 to 2 Pa

# Compute q_s for each τ
qs_values = np.where(tau_values > tau_c, 8 * np.power(np.maximum(tau_values - tau_c, 0), 1.5) , 0)

# Plot results
plt.figure(figsize=(8, 5))
plt.plot(tau_values, qs_values, label="Sediment Transport Rate", color="b")
plt.axvline(tau_c, linestyle="--", color="r", label="Critical Shear Stress")
plt.xlabel("Shear Stress (τ)")
plt.ylabel("Sediment Transport Rate (q_s)")
plt.title("Sediment Transport Model")
plt.legend()
plt.grid()
plt.show()
