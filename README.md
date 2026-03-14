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
git clone https://github.com/Ruslan-Akhmerov/single-object-Bayesian-optimization.git

### №2 Prepare input files
In your working directory (where run_optimization.py is located), you need to have the following input files for your compound:
- {compound}.scf.in
- {compound}.nscf.in
- {compound}.band.in
- {compound}_bands.pp.in

### №3 Configure parameters
1) Edit run_optimization.py (If necessary)
2) In the update_hubbard_u function, find the lines with orbital names and modify them for your system:
```bash
# Find these lines and change 'Mn1-3d' and 'Mn2-3d' 
# to match your atom and orbital names
if 'U Mn1-3d' in line:      # → for example: 'U Ni-3d'
    parts = line.split()
    old_u = float(parts[2])
    parts[2] = f"{new_u:.4f}"
    line = ' '.join(parts) + '\n'
    updated = True
elif 'U Mn2-3d' in line:    # → for example: 'U Fe-3d'
    parts = line.split()
    old_u = float(parts[2])
    parts[2] = f"{new_u:.4f}"
    line = ' '.join(parts) + '\n'
    updated = True
```

### №4 Run

```python run_optimization.py ```
