Photometric Analysis of Open Cluster Platais 2 (HIP 5671)This repository contains the full analysis, data products, and documentation for the photometric study of the open star cluster Platais 2. This project was a collaborative effort by the SSS Team as part of the International School for Young Astronomers (ISYA) 2024.📜 Table of ContentsProject SummaryAuthorsMethodologyResults and DiscussionRepository StructureHow to Reproduce the AnalysisFuture Work📖 Project SummaryOpen star clusters are crucial laboratories for studying stellar evolution, as their member stars share a common origin, age, and chemical composition. This project focuses on Platais 2 (HIP 5671), an open cluster with limited coverage in existing scientific literature, making it a valuable target for new analysis.Observations were conducted at McDonald Observatory (LCOGT) using a 0.35-meter telescope with B and V filters. The collected data was processed to generate a Hertzsprung-Russell (HR) diagram and classify the cluster's stellar population. Our findings indicate that Platais 2 is a moderately young cluster, with an estimated age of 100-300 million years, and is predominantly composed of K-type and F-type stars.✍️ AuthorsAyoub Sarri - University of Algiers 1, AlgeriaSena Aleyna Şentürk - Akdeniz University, TurkeySam Samuneti - University of Nigeria, Nigeria🛠️ MethodologyThe analysis was performed using Python with standard astronomical libraries (Astropy, NumPy, Pandas, SciPy, Matplotlib). The complete workflow is detailed in the code/HR-diagram.ipynb notebook and follows these key steps:Data Extraction: Raw FITS files from the B and V filters were processed to extract flux, right ascension (RA), and declination (Dec) for each detected stellar source.Coordinate Matching: A KD-Tree algorithm was used for efficient nearest-neighbor matching of stars between the B and V filter images based on their celestial coordinates.Magnitude Calculation: The instrumental magnitudes (B_mag, V_mag) and the B-V color index were calculated from the flux measurements. A reference star was used for calibration.Stellar Classification: Each star was classified into a spectral type (O, B, A, F, G, K, M) based on its B-V color index, which serves as a proxy for its effective temperature.Visualization: The results were visualized by generating an HR diagram and a pie chart showing the spectral type distribution of the cluster's population.📊 Results and DiscussionThe final analysis yielded a clear Hertzsprung-Russell diagram for the Platais 2 cluster, enabling the determination of its age and stellar composition.Hertzsprung-Russell (HR) DiagramThe HR diagram plots the apparent V-band magnitude against the B-V color index. The main sequence turn-off point suggests that the cluster is moderately young. The diagram shows a well-defined main sequence with a population of stars evolving towards the giant branch.Figure 1: The Hertzsprung-Russell diagram for Platais 2. The color bar indicates the effective temperature of the stars.Spectral Type DistributionThe analysis of the stellar population reveals a dominance of K-type (36.4%) and F-type (22.7%) stars. The relatively small presence of hotter O and B-type stars is consistent with the cluster's estimated age, as these more massive stars would have already evolved off the main sequence.Figure 2: The distribution of spectral types within the observed members of the cluster.📂 Repository StructureA clean directory structure is used to keep the project organized.platais-2-photometry/
│
├── 📜 README.md
│
├── 📂 code/
│   └── 📓 HR-diagram.ipynb
│
├── 📂 data/
│   └── (This is where the raw FITS files should be placed)
│
├── 📂 output/
│   ├── 📊 HR_diagram.png
│   ├── 📊 spectral_type_distribution.png
│   └── 📄 OPEN_CLUSTER-final.csv
│
├── 📂 report/
│   ├── 📄 ISYA.pdf
│   └── 📄 PRESENTATION-SSS.pptx
│
├── 📋 requirements.txt
└── 🚫 .gitignore
🚀 How to Reproduce the AnalysisTo run this analysis on your own machine, follow these steps:Clone the Repository:git clone [your-repository-url]
cd platais-2-photometry
Set up a Virtual Environment (Recommended):python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
Install Dependencies:pip install -r requirements.txt
Add Data:Place your raw FITS files into the /data directory.Run the Notebook:Launch Jupyter and run the cells in code/HR-diagram.ipynb. The notebook will process the data and save the final plots and CSV file to the /output directory.Important: In the notebook, update the data directory path from 'DATA OF OPEN CLUSTER/' to '../data/'.🔭 Future WorkBased on our initial findings, this research can be expanded in several ways:Isochrone Fitting: To obtain a more precise age and distance modulus for the cluster.Metallicity Analysis: To better understand the chemical composition of the stars.Deeper Photometric Surveys: To uncover fainter, less massive members of the cluster and create a more complete stellar census.
