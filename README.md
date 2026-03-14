# Hubbard Parameter Optimizer

A collection of Python scripts for automated optimization of Hubbard U parameters in Quantum ESPRESSO calculations using Bayesian optimization.

## Description

This tool automatically finds the optimal Hubbard U parameter that reproduces experimental band gaps by:

- Running sequential Quantum ESPRESSO calculations (SCF → NSCF → Bands)
- Analyzing band structure results
- Using Gaussian Process regression to suggest next U values
- Continuing until target band gap precision is achieved

## Features

- **Bayesian Optimization** with Expected Improvement acquisition function
- **Automated workflow** for Quantum ESPRESSO calculations
- **Comprehensive logging** of all iterations
- **Visualization** of optimization progress

## Requirements

### System Requirements
- Python 3.7 or higher
- Quantum ESPRESSO (6.5 or later recommended) with `pw.x` and `bands.x` executables in PATH

### Python Dependencies
```bash
numpy
scipy
matplotlib
```

## Installation

### №1 Clone from GitHub
- git clone https://github.com/Ruslan-Akhmerov/single-object-Bayesian-optimization.git
- cd Optz
