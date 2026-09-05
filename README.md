# Variational Quantum Eigensolver (VQE) Notebook

This repository contains a hands-on, educational Jupyter Notebook demonstrating the **Variational Quantum Eigensolver (VQE)**—a flagship hybrid quantum-classical algorithm designed for Noisy Intermediate-Scale Quantum (NISQ) hardware.

The notebook illustrates how a parameterized quantum circuit (Ansatz) interacts with a classical optimizer to iteratively calculate the **Ground State Energy ($E_0$)** of physical systems using the Variational Principle:

$$E(\theta) = \langle \psi(\theta) \vert H \vert \psi(\theta) \rangle \ge E_0$$

---

## What Happens in This Notebook?

1. **System & Hamiltonian Construction:** Physical systems (spin chains and molecules) are converted into a qubit Hamiltonian $H$ represented as Pauli operator strings ($X, Y, Z, I$).
2. **Circuit Initialization (Ansatz):** Parameterized quantum circuits $\vert{}\psi(\theta)\rangle$ prepare trial states on quantum hardware.
3. **Energy Expectation Measurement:** The quantum simulator evaluates the energy score $E(\theta)$ for current parameters.
4. **Classical Optimization Loop:** A classical optimizer (Gradient Descent / Adam) updates parameter angles $\theta$ to minimize energy until convergence to $E_0$.
5. **Validation:** Calculated VQE ground state energy is validated against exact classical matrix diagonalization ($E_0$).

---

## Included Examples

### Example 1: Quantum Magnet (1D Ising Model)

* **Domain:** Condensed Matter Physics
* **Description:** Models a 3-qubit (3-spin) chain interacting via nearest-neighbor spin couplings ($Z \otimes Z$) subject to a transverse external magnetic field ($X$).
* **Goal:** Find the lowest energy magnetic alignment configuration across the spin chain.
* **Key Takeaway:** Demonstrates smooth, monotonic gradient descent convergence toward the exact spin-system floor.

### Example 2: Chemical Simulation (Hydrogen Molecule - $H_2$)

* **Domain:** Quantum Chemistry & Material Science
* **Description:** Uses PennyLane's quantum chemistry engine (`qchem`) to construct the full 4-qubit electronic Hamiltonian for an $H_2$ molecule at its equilibrium bond distance ($0.742 \text{ Å}$).
* **Goal:** Calculate the molecular ground state energy in Hartrees ($E_0 \approx -1.136160 \text{ Ha}$).
* **Key Takeaway:** Demonstrates chemistry state preparation using a Hartree-Fock base state ($\vert{}1100\rangle$) and a `DoubleExcitation` gate to simulate electron pair interactions.

---

## Tech Stack

* **Framework:** PennyLane (`pennylane`)
* **Scientific Computing:** NumPy / SciPy
* **Visualization:** Matplotlib
