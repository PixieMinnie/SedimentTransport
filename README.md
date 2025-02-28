# Sediment Transport Model

## Overview
This Python script calculates sediment transport rates based on flow velocity, bed slope, sediment grain size, and water depth. The model estimates shear stress and determines whether sediment transport occurs, visualizing the relationship between shear stress and transport rates.

## Features
- Computes shear stress using given hydraulic parameters
- Determines sediment transport rates based on a critical threshold
- Plots the sediment transport rate as a function of shear stress

## Dependencies
The script requires the following Python libraries:
- `numpy` for numerical operations
- `matplotlib` for visualization

To install these dependencies, run:
```bash
pip install numpy matplotlib (pip3, if you have Python3 and have not reassigned pip3 to pip)
```

## Usage
1. Clone the repository or download the script.
2. Run the script using:
   ```bash
   python sediment_transport.py
   ```
3. The program outputs:
   - Shear stress value
   - Sediment transport rate (if transport occurs)
   - A plot visualizing sediment transport as a function of shear stress

## Methodology
The model follows these steps:
1. Compute shear stress (τ) using:
   ```
   τ = ρ_w * g * h * S
   ```
2. Compare τ with the critical shear stress (τ_c).
   - If τ > τ_c, sediment transport occurs.
   - If τ ≤ τ_c, no transport happens.
3. Compute sediment transport rate:
   ```
   q_s = 8 * (τ - τ_c) ^ 1.5 (if τ > τ_c)
   ```
4. Generate a plot showing the sediment transport rate variation with shear stress.

## Output
- **Numerical values**: Displays calculated shear stress and sediment transport rate.
- **Graph**: A plot of shear stress vs. sediment transport rate.

## Future Enhancements
- Incorporate real-world river data.
- Adapt for varying sediment sizes and bed conditions.
- Integrate with GIS tools for spatial analysis.

## Author
Developed by Minal Londhe

