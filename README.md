```markdown
# 🌕 MoonHabitableZone: Python Toolkit for Exomoon Detection and Stability Zone Analysis  

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17366586.svg)](https://doi.org/10.5281/zenodo.17366586)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![Stars](https://img.shields.io/github/stars/swayamsikarwar/MoonHabitableZone?style=social)](https://github.com/swayamsikarwar/MoonHabitableZone/stargazers)

---

## 📘 Overview  

**MoonHabitableZone** is a Python-based research project that explores the potential existence of **moons around exoplanets** using data-driven analysis and a newly proposed **Moon Stability Zone (MSZ)** formula.  
It combines **astrophysics**, **data science**, and **machine learning** to identify exoplanets that may host stable moons, expanding our understanding of planetary system dynamics beyond the Solar System.  

This repository contains the implementation for the paper:  
> **“Discovery of Potential Moons Around Exoplanets: Data Analysis Using Python and Development of a Moon Stability Zone Formula”**  
> — *Swayam Singh Sikarwar, Ankit Sharma, Jagriti Singh Thakur*  

---

## 🧠 Scientific Motivation  

Since the discovery of the first exoplanet in 1992, thousands of such planets have been found — yet **exomoons** remain one of astronomy’s greatest mysteries. Moons play critical roles in planetary stability, climate regulation, and habitability. Detecting and characterizing exomoons can provide valuable insights into the **formation and evolution** of planetary systems.  

The **Moon Stability Zone (MSZ)** defines the orbital region where a moon can remain stable — bounded by:  
- **Stable Radius** → the planet’s gravitational influence limit (outer bound)  
- **Roche Limit** → the inner limit where tidal forces disrupt moon orbits  

If  
\[
\text{Moon Diameter} < \text{MSZ}
\]  
then the moon can exist in a **stable orbit**.

---

## 🪐 Key Features  

- 📊 **Data Analysis** of NASA Exoplanet Archive datasets  
- 🧮 Calculates **Hill Radius**, **Roche Limit**, and **Moon Stability Zone**  
- 🤖 Integrates **Machine Learning (Decision Tree Classifier)** to detect potential moons  
- 📈 Produces detailed visualizations (Matplotlib + Seaborn)  
- 🔭 Validated against known Solar System moons (Earth–Moon, Jupiter–Europa, Saturn–Titan)  

---

```

````
---

## ⚙️ Installation  

Clone the repository and install required packages:  

```bash
git clone https://github.com/swayamsikarwar/MoonHabitableZone.git
cd MoonHabitableZone
pip install -r requirements.txt

---

## 🚀 Usage

Run the analysis directly from the command line:

```bash
python scripts/moon_stability_zone.py
```

Or explore the step-by-step workflow interactively:

```bash
jupyter notebook notebooks/MoonHabitableZone.ipynb
```

Outputs include:

* Calculated Hill Radius and Roche Limit for each exoplanet
* Stability Zone visualization
* Machine learning classification results

---

## 🧩 Methodology

1. **Data Collection**

   * Source: NASA Exoplanet Archive
   * Extracted features: planetary mass, radius, orbital period, host star mass & temperature

2. **Data Cleaning & Filtering**

   * Removed nulls, duplicates, and systems sharing the same host star
   * Focused on exoplanets with Transit Time Variation (TTV > 0)

3. **Computation of Orbital Parameters**

   * Hill Radius
   * Roche Limit
   * Moon Stability Zone (MSZ = Stable Radius − Roche Limit)

4. **Machine Learning Integration**

   * Decision Tree Classifier used for binary classification (`has_moon` vs `no_moon`)
   * Evaluated using **accuracy**, **precision**, **recall**, and **F1/F₂** scores

5. **Validation**

   * Tested with real Solar System data (Earth, Jupiter, Saturn)
   * Verified predicted stability zones align with known moon orbits

---

## 🌟 Results

| Exoplanet      | Stability Zone (km) | Potential Moon | Validation         |
| -------------- | ------------------- | -------------- | ------------------ |
| **TOI 1130 b** | Stable              | ✅ Likely Host  | Supported by model |
| **TOI 1266 b** | Stable              | ✅ Likely Host  | Supported by model |
| Earth (Test)   | 378,029 km          | ✅ Moon stable  | Verified           |
| Jupiter–Europa | 628,900 km          | ✅ Moon stable  | Verified           |
| Saturn–Titan   | 1,140,000 km        | ✅ Moon stable  | Verified           |

✅ The **MSZ formula** reliably matches known stable moon systems.
✅ The **Decision Tree model** achieved **80% accuracy** with high recall and F₂ score (focus on minimizing false negatives).

---

## 📊 Visualization Examples

* **Correlation Matrix:** identifies feature relationships
* **Scatter Plots:** planet mass vs. Hill radius
* **MSZ Chart:** shows regions where moons remain stable

*(Visual outputs are saved in the `results/visualizations/` folder.)*

---

## 🔬 Scientific Contribution

* Introduces a **new analytical formula** (Moon Stability Zone) for exomoon detection.
* Combines **orbital dynamics** with **data science** for reproducible research.
* Identifies **new candidate systems** that may host moons.
* Provides a foundation for **future exomoon habitability studies**.

---


## 📚 References

* **NASA Exoplanet Archive** — [https://exoplanetarchive.ipac.caltech.edu/](https://exoplanetarchive.ipac.caltech.edu/)
* Harris et al. (2020). *Array Programming with NumPy.* Nature, 585, 357–362.
* McKinney, W. (2010). *Data Structures for Statistical Computing in Python.*
* Kipping, D.M. (2011). *Transit Timing Effects Due to an Exomoon.* MNRAS.
* Murray & Dermott (1999). *Solar System Dynamics.* Cambridge University Press.

---

## 🪄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Authors

| Name                      | Institution   | Role                           |
| ------------------------- | ------------- | ------------------------------ |
| **Swayam Singh Sikarwar** | SDBCE, Indore | Lead Researcher & Developer    |
| **Jagriti Singh Thakur**  | SDBCE, Indore | Research Co-Author             |

---

## 🌌 Acknowledgements

Special thanks to:

* **NASA Exoplanet Science Institute** for open data access
* **Python scientific community** for their tools and contributions
* **Zenodo** for preserving open scientific software

---

### 🔗 DOI

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17366586.svg)](https://doi.org/10.5281/zenodo.17366586)

---

> *"Exploring the unseen moons of distant worlds — one dataset at a time."* 🌙

```
