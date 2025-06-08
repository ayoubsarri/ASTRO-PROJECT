````markdown
# Photometric Analysis of Open Cluster Platais 2 (HIP 5671)

This repository contains the full analysis, data products, and documentation for the photometric study of the open star cluster **Platais 2**. This project was a collaborative effort by the SSS Team as part of the International School for Young Astronomers (ISYA) 2024.

---

## 📖 Table of Contents

1. [Project Summary](#project-summary)  
2. [Authors](#authors)  
3. [Methodology](#methodology)  
   - [Data Extraction](#data-extraction)  
   - [Coordinate Matching](#coordinate-matching)  
   - [Magnitude Calculation](#magnitude-calculation)  
   - [Stellar Classification](#stellar-classification)  
   - [Visualization](#visualization)  
4. [Results and Discussion](#results-and-discussion)  
   - [Hertzsprung–Russell Diagram](#hertzsprungrussell-diagram)  
   - [Spectral Type Distribution](#spectral-type-distribution)  
5. [Repository Structure](#repository-structure)  
6. [How to Reproduce the Analysis](#how-to-reproduce-the-analysis)  
7. [Future Work](#future-work)  
8. [License](#license)  

---

## 📜 Project Summary

Open star clusters are crucial laboratories for studying stellar evolution, as their member stars share a common origin, age, and chemical composition.  
This project focuses on **Platais 2 (HIP 5671)**, an open cluster with limited coverage in existing literature.  

- **Observatory:** McDonald Observatory (LCOGT)  
- **Telescope:** 0.35 m  
- **Filters:** B and V  

We processed raw images to build a Hertzsprung–Russell (HR) diagram and classify the stellar population. Our findings indicate that Platais 2 is a **moderately young cluster** (∼100–300 Myr), dominated by **K-type (36.4 %)** and **F-type (22.7 %)** stars.

---

## ✍️ Authors

- **Ayoub Sarri** — University of Algiers 1, Algeria  
- **Sena Aleyna Şentürk** — Akdeniz University, Turkey  
- **Sam Samuneti** — University of Nigeria, Nigeria  

---

## 🛠️ Methodology

The analysis pipeline is implemented in Python using:

- Astropy  
- NumPy  
- Pandas  
- SciPy  
- Matplotlib  

Full workflow in [`code/HR-diagram.ipynb`](code/HR-diagram.ipynb).

### Data Extraction

- **Input:** Raw FITS images in B and V filters  
- **Process:**  
  - Source detection  
  - Aperture photometry  
  - Extract flux, RA, Dec  

### Coordinate Matching

- Use a **KD-Tree** nearest-neighbor search to pair B/V detections by celestial coordinates.

### Magnitude Calculation

Calculate instrumental magnitudes and color index:

```python
B_mag = -2.5 * np.log10(flux_B) + ZP_B
V_mag = -2.5 * np.log10(flux_V) + ZP_V
color_BV = B_mag - V_mag
````

* **Zero points** (ZP\_B, ZP\_V) set using a reference star.

### Stellar Classification

Map **B–V** color to spectral types (O, B, A, F, G, K, M) via standard color–temperature relations.

### Visualization

* **HR Diagram:** V-band magnitude vs. B–V color, color-coded by effective temperature.
* **Spectral Distribution:** Pie chart of spectral types.

---

## 📊 Results and Discussion

### Hertzsprung–Russell Diagram

![HR Diagram](output/HR_diagram.png)

The well-defined main sequence and turn-off point confirm a cluster age of \~100–300 Myr.

### Spectral Type Distribution

![Spectral Types](output/spectral_type_distribution.png)

| Spectral Type | Fraction (%) |
| ------------- | ------------ |
| K             | 36.4         |
| F             | 22.7         |
| G             | 18.2         |
| A             | 13.6         |
| M             | 6.8          |
| B             | 2.3          |
| O             | 0.0          |

The dominance of K- and F-type stars is consistent with the cluster’s age.

---

## 📂 Repository Structure

```
platais-2-photometry/
├── README.md
├── code/
│   └── HR-diagram.ipynb
├── data/
│   └── *.fits                   # Raw FITS files go here
├── output/
│   ├── HR_diagram.png
│   ├── spectral_type_distribution.png
│   └── OPEN_CLUSTER-final.csv
├── report/
│   ├── ISYA.pdf
│   └── PRESENTATION-SSS.pptx
├── requirements.txt
└── .gitignore
```

---

## 🚀 How to Reproduce the Analysis

1. **Clone the repository**

   ```bash
   git clone https://github.com/ayoubsarri/ASTRO-PROJECT
   cd platais-2-photometry
   ```

2. **Create a virtual environment**

   ```bash
   python -m venv venv
   source venv/bin/activate      # Windows: venv\Scripts\activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Add your data**
   Place raw FITS files into the `data/` directory.

5. **Run the analysis notebook**

   ```bash
   jupyter notebook code/HR-diagram.ipynb
   ```

   > **Tip:** Update the data path in the notebook from `'DATA OF OPEN CLUSTER/'` to `'../data/'` if needed.

6. **View outputs**
   Generated plots and `OPEN_CLUSTER-final.csv` will appear in the `output/` folder.

---

## 🔭 Future Work

* **Isochrone Fitting:** Constrain age & distance modulus more precisely.
* **Metallicity Analysis:** Determine cluster chemical composition.
* **Deeper Surveys:** Include fainter members for a complete census.



```
