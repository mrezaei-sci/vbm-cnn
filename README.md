# vbm-cnn
**Preprocessing, feature extraction, and deep-learning classification pipeline for ADNI T1-weighted MRI data**

---

## Table of Contents
1. [Overview](#overview)
2. [Repository Structure](#repository-structure)
3. [Requirements](#requirements)
4. [Installation](#installation)
5. [Data Access](#data-access)
6. [Running the Analysis](#running-the-analysis)
7. [Reproducing Key Results](#reproducing-key-results)
8. [Contributing](#contributing)
9. [License](#license)
10. [Citation](#citation)
11. [Contact](#contact)

---

## Overview
This repository contains all code and instructions to reproduce our published pipeline for early Alzheimer’s disease (AD) classification, combining voxel-based morphometry (VBM) preprocessing with deep-learning models. Specifically, we:

- Preprocess T1-weighted MRI scans (SPM12 + CAT12)
- Extract structural features: total intracranial volume (TIV), gray matter (GM) volume, white matter (WM) volume, cerebrospinal fluid (CSF) volume, and cortical thickness
- Convert features into multi-bit heatmap images (3-, 4-, 8-, and 16-bit)
- Train and evaluate Convolutional Neural Networks (CNN) and Fully Connected Networks (FCN)

All raw MRI data are sourced from the Alzheimer’s Disease Neuroimaging Initiative (ADNI). The data-use agreement prevents us from hosting images here, but you can fetch the exact scans used via our download script.

## Repository Structure
```bash
vbm-cnn/             # Root directory
├── code/            # Analysis notebooks and scripts
│   └── VBM_Final.ipynb
├── data/            # Data download scripts (no raw MRI files included)
│   └── fetch_adni.sh
├── results/         # (Optional) Figures, trained models, and outputs
├── .gitignore       # Lists files/folders to exclude from git
├── LICENSE          # MIT License
├── README.md        # This file
└── requirements.txt # Python dependencies
```

## Requirements
- Linux or macOS (bash shell) or Windows with WSL
- Python 3.8+  
- [LONI CLI](https://github.com/loni/lonicli) for ADNI data download
- Jupyter Notebook or JupyterLab for `.ipynb` files

## Installation
1. **Clone the repository**
   ```bash
   git clone https://github.com/mrezaei-sci/vbm-cnn.git
   cd vbm-cnn
   ```
2. **Create a virtual environment** (recommended)
   ```bash
   python3 -m venv venv
   source venv/bin/activate    # macOS/Linux
   venv\Scripts\activate     # Windows (PowerShell)
   ```
3. **Install Python dependencies**
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```
4. **Install LONI CLI**
   ```bash
   pip install lonicli
   ```

## Data Access
Due to data-use restrictions, raw ADNI MRI scans are not stored in this repository. To download the exact T1-weighted MPRAGE scans used in our analysis:

1. Register for an ADNI account at [http://adni.loni.usc.edu](http://adni.loni.usc.edu).
2. Ensure you have your LONI credentials (username/password).
3. Run the fetch script:
   ```bash
   bash data/fetch_adni.sh
   ```
   This will prompt for your username and download all required scans into `data/raw/`.

> **Note:** The script uses the LONI CLI. If you prefer another method (e.g., manual download), place the MRI files into `data/raw/` with the same directory structure.

## Running the Analysis
1. **Launch Jupyter Notebook**
   ```bash
   jupyter notebook code/VBM_Final.ipynb
   ```
2. **Follow the notebook cells**:
   - **Sections 1–4:** Preprocessing and feature extraction
   - **Sections 5–7:** Heatmap generation and image conversion
   - **Sections 8–10:** Model training (CNN and FCN)
   - **Sections 11–12:** Evaluation and figures

3. **Modify parameters** as needed in the notebook (e.g., bit-depth, model hyperparameters).

## Reproducing Key Results
- **Figure 1–2 (VBM pipeline & heatmaps):** Run preprocessing and heatmap cells to generate `results/fig1.png` and `results/fig2.png`.
- **Figure 3–4 (Model architectures & training curves):** Run model training cells; resulting plots will be saved under `results/`.
- **Table 5–6 (Performance metrics):** Evaluation cells automatically print tables; use `--format markdown` option if needed.

## Contributing
Contributions are welcome! Please open an issue or submit a pull request to:

- Fix bugs
- Add new features or model architectures
- Improve documentation

## License
This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

## Citation
If you use this code or data pipeline in your work, please cite:

> Rezaee, M., et al. (2025). *Integrating Biologically Informed Voxel-Based Morphometry and Multi-Bit Heatmap Conversions for Early Alzheimer’s Disease Classification.* NeuroImage. [DOI pending]

## Contact
For questions or help reproducing the results, please contact:

**Mohammad Rezaei**  
Biomedical Engineering, University of Tehran
Email: [moh.rezaei@ut.ac.ir](mailto:moh.rezaei@ut.ac.ir)  
Linkedin: [Mohammad Rezaei]([https://www.linkedin.com/in/mohammad-rezaei-rze2001?lipi=urn%3Ali%3Apage%3Ad_flagship3_profile_view_base_contact_details%3Bsm54gBFySymrZjSia0m4YA%3D%3D)

