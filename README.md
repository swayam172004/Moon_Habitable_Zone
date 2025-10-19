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