# Single-Channel SSVEP BCI with Phase-Enhanced FBCCA

## Overview

This repository contains the code and results for a study investigating whether explicit phase information from joint frequency-phase modulated (JFPM) stimuli can improve single-channel SSVEP-based brain-computer interface (BCI) decoding.

**Key finding:** Adding phase features to Filter Bank Canonical Correlation Analysis (FBCCA) improves single-channel classification accuracy from 62.30% to 65.38% at the Oz electrode (2-second window), with the largest gains (+8 percentage points) at shorter 1-second windows.

## Authors

- **Leonel Vázquez Carrasco**
- **Julie Verne Henriksen**

*Course: 22053 Principles of Brain-Computer Interfaces*

## Repository Structure

```
├── data/ # Dataset instructions (download manually)
| └── README.md # How to obtain the Benchmark SSVEP dataset
├── figures/ # Generated plots (SVG format)
├── results/ # CSV output files
│ ├── summary/ # Main results tables
│ ├── single_channel/ # Oz channel per-subject results
│ └── nine_channel/ # 9-channel baseline results
├── src/ # Python source code
│ └── legacy_original_script.ipynb # Runs all code
├── requirements.txt # Python dependencies
├── report.pdf # Full project report
└── README.md # This file
```

## Requirements

### Python environment

```bash
pip install -r requirements.txt
```

## Dataset

This project uses the Benchmark SSVEP Dataset by Wang et al. (2017). The dataset is not included in this repository due to size and licensing restrictions.

To obtain the data:
1. Read the instructions in ``` data/README.md ```
2. Download from the official source: http://bci.med.tsinghua.edu.cn/download.html
3. Place the ``` .mat ``` files in the ``` data/ ``` folder

## Usage

Run FBCCA and FBCCA+Phase on all 9 occipital-parietal channels, the multi-channel FBCCA baseline and the time-window grid search:

```bash
python src/legacy_original_script.ipynb
```

## Key Results

### Single-channel performance (2-second window, Oz electrode)

| Method | Accuracy (%) | ITR (bits/min) |
|------|------|------|
| FBCCA alone | 62.30 ± 26.01 | 59.67 ± 33.51 |
| FBCCA + Phase | 65.38 ± 26.56 | 64.43 ± 34.74 |
| Improvement | +3.08 (p < 0.0001) | +4.76 (p < 0.0001) |

### Time-window analysis (Oz electrode)

| Window (s) | FBCCA (%) | FBCCA+Phase (%) | Δ (%) |	p-value |
|------|------|------|------|------|
| 0.75 | 20.48 | 27.71 | +7.24 | < 0.0001 |
| 1.00 | 31.56 | 39.56 | +8.00 | < 0.0001 |
| 1.50 | 49.45 | 54.82 | +5.37 | < 0.0001 |
| 2.00 | 62.30 | 65.55 | +3.08 | < 0.0001 |

### 9-channel baseline (2-second window)

| Method | Accuracy (%) | ITR (bits/min) |
|------|------|------|
| FBCCA alone | 90.50 ± 12.94 | 101.84 ± 22.45 |
| FBCCA + Phase | 90.38 ± 13.22 | 101.72 ± 22.91 |
| Improvement | -0.12 (n.s.) | -0.12 (n.s.) |

Phase features provide meaningful gains only in the single-channel (resource-constrained) setting.

## Figures

All figures are available in ``` figures/ ``` as SVG files:

| Figure | Description |
|------|------|
| ``` Results_schannel.svg ``` | Accuracy/ITR across 9 channels |
| ``` Results_subject_sch.svg ``` | Per-subject results for Oz channel |
| ``` Results_subjects_9_channels.svg ``` | Per-subject results for 9 channels |
| ``` Results_subject_best_channel_per_subject.svg ``` | Per-subject results for best individual channel |
| ``` Results_tw_grid_All9.svg ``` | Time-window grid search for 9 channels |
| ``` Results_tw_grid_Oz.svg ``` | Time-window grid search for single channel |

## Reproducing Results from Scratch

1. Clone this repository
2. Download the dataset (see ``` data/README.md ```)
3. Install dependencies: ``` pip install -r requirements.txt ```
4. Run the three main scripts (see Usage section above)
5. Generated results will match the CSV files in ``` results/ ```

## License

This project is licensed under the MIT License - see the LICENSE file for details.

The dataset is provided for academic research purposes only; please cite the original authors.

## Acknowledgments

* Professor Sadasivan Puthusserypady for guidance (DTU course 22053)
* Chen et al. (2015) for the original FBCCA implementation
* Wang et al. (2017) for the benchmark dataset
* All 35 subjects who participated in the original data collection
