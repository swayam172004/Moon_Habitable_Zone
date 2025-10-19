# MoonHabitableZone

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17366586.svg)](https://doi.org/10.5281/zenodo.17366586)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10%2B-blue)](https://www.python.org/)

> **MoonHabitableZone** — a research toolkit to compute Hill radius, Roche limit and a Moon Stability Zone (MSZ) for exoplanet systems. Includes reproducible notebooks and example scripts for candidate detection.

---

## Table of contents

- [About](#about)
- [Features](#features)
- [Install](#install)
- [Quick usage (Python)](#quick-usage-python)
- [MSZ formula (explanation)](#msz-formula-explanation)
- [Example output](#example-output)
- [Running the demo / site](#running-the-demo--site)
- [Citation](#citation)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## About

MoonHabitableZone computes orbital stability regions for potential moons around exoplanets by combining established orbital mechanics (Hill sphere) with Roche limit calculations and a derived Moon Stability Zone (MSZ). The repo contains:

- scripts/ — core analysis scripts
- notebooks/ — interactive Jupyter notebooks
- results/ — example outputs & visualizations
- web/ — (optional) `index.html` demo and interactive visualizations for GitHub Pages

> **Note:** GitHub `README.md` must be plain Markdown. Interactive JavaScript or `<script>` elements do not run in the README. For interactive demos, use GitHub Pages (see below).

---

## Features

- Hill radius & Roche limit calculations
- MSZ calculation (inner = Roche limit; outer = fraction of Hill radius)
- Example Decision-Tree classifier pipeline (notebooks)
- Reproducible visualization outputs saved in `results/visualizations`
- DOI-backed release (Zenodo)

---

## Install

```bash
git clone https://github.com/swayamsikarwar/MoonHabitableZone.git
cd MoonHabitableZone
python -m venv venv
source venv/bin/activate    # macOS / Linux
# venv\Scripts\activate     # Windows
pip install -r requirements.txt
pip install numpy scipy pandas matplotlib scikit-learn jupyter
"""
msz.py
Simple functions: Hill radius, Roche limit (fluid), and MSZ bounds.
"""

import math

G = 6.67430e-11  # m^3 kg^-1 s^-2

def hill_radius(a_m, m_planet_kg, m_star_kg):
    """
    Compute Hill radius: R_H = a * (m / (3M))^(1/3)
      - a_m: semi-major axis (m)
      - m_planet_kg: planet mass (kg)
      - m_star_kg: star mass (kg)
    Returns R_H in meters.
    """
    return a_m * (m_planet_kg / (3.0 * m_star_kg)) ** (1.0 / 3.0)

def planet_density(m_planet_kg, r_planet_m):
    """
    Mean density of the planet (kg/m^3)
    """
    volume = (4.0 / 3.0) * math.pi * r_planet_m**3
    return m_planet_kg / volume

def roche_limit_fluid(r_planet_m, rho_planet, rho_satellite=3000.0):
    """
    Roche limit for a fluid satellite (approx):
      d_roche = 2.44 * R_p * (rho_p / rho_s)^(1/3)
    - r_planet_m: planet radius in meters
    - rho_planet: planet mean density (kg/m^3)
    - rho_satellite: assumed satellite density (kg/m^3), default 3000 kg/m^3
    Returns Roche limit in meters.
    """
    return 2.44 * r_planet_m * (rho_planet / rho_satellite) ** (1.0 / 3.0)

def msz_bounds(a_m, m_planet_kg, r_planet_m, m_star_kg, rho_satellite=3000.0, outer_fraction=0.5):
    """
    Compute MSZ bounds:
      - inner bound = Roche limit (fluid)
      - outer bound = outer_fraction * Hill radius (conservative)
    Returns tuple: (roche_limit_m, outer_bound_m)
    """
    rho_p = planet_density(m_planet_kg, r_planet_m)
    roche = roche_limit_fluid(r_planet_m, rho_p, rho_satellite)
    h = hill_radius(a_m, m_planet_kg, m_star_kg)
    outer = outer_fraction * h
    return roche, outer

if __name__ == "__main__":
    # Example: Earth around Sun
    m_earth = 5.97219e24
    r_earth = 6.371e6
    a_earth = 1.495978707e11
    m_sun = 1.98847e30

    roche, outer = msz_bounds(a_earth, m_earth, r_earth, m_sun)
    print("Earth (test):")
    print(f" Roche limit (m): {roche:.3e}")
    print(f" MSZ outer bound (m): {outer:.3e}")
