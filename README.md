# Worm-like Chain (WLC) Under Tension

This repository contains a Python implementation of a Monte Carlo simulation for a semi-flexible polymer (Worm-like Chain) subjected to an external tensile force.
Instead of simulating discrete beads, this code models the filament by sampling the Fourier coefficients of its curvature function, allowing for the generation of smooth, continuous equilibrium conformations.

## Physics

The **Worm-like Chain (WLC)** model describes a semi-flexible polymer defined by its contour length $L$ and its persistence length ξ (a measure of stiffness).

The total energy of the system in this simulation is defined by the Hamiltonian:

$$H = E_{bending} + E_{potential}$$

1.  **Bending Energy:** The energy cost to bend the filament, integrated along the arc length $s$:
    $$E_{bending} = \frac{1}{2} k_B T l_p \int_0^L \kappa(s)^2 ds$$
    *Where k(s) is the local curvature.*

2.  **Potential Energy:** The energy contribution from an external force $F$ pulling the filament along the x-axis:
    $$E_{potential} = - \vec{F} \cdot \vec{r}_{end} = - F x(L)$$

*Note: The simulation assumes units where k_BT = 1.*

## Features

* **Fourier Mode Sampling:** Instead of perturbing Cartesian coordinates, the algorithm perturbs the Fourier coefficients of the curvature $\kappa(s)$. This ensures naturally smooth filament shapes.
* **Metropolis-Hastings Algorithm:** Uses Markov Chain Monte Carlo (MCMC) to sample equilibrium states based on the Boltzmann distribution $P \propto e^{-\Delta E}$.
* **Reconstruction:** Reconstructs the tangent angle $\theta(s)$ and Cartesian coordinates $(x, y)$ via integration.
* **Visualization:** Automatically generates a plot of the filament shape with the applied force vector.

## Dependencies

The project requires the following Python libraries:

* `numpy` (Numerical operations)
* `matplotlib` (Plotting)
* `scipy` (Integration via `cumulative_trapezoid`)

You can install them via pip:

```bash
pip install numpy matplotlib numpy
pip install numpy matplotlib matplotlib
pip install numpy matplotlib scipy
