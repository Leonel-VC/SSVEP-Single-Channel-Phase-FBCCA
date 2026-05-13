# Data: Benchmark SSVEP Dataset

## Source
This dataset was introduced by Wang et al. (2017) and is publicly available for research purposes.

**Citation:**  
Wang, Y., Chen, X., Gao, X., & Gao, S. (2017). A Benchmark Dataset for SSVEP-Based Brain-Computer Interfaces. *IEEE Transactions on Neural Systems and Rehabilitation Engineering*, 25(10), 1746–1752. doi: 10.1109/TNSRE.2016.2627556

## Download Instructions

Download the dataset from the official source:  
http://bci.med.tsinghua.edu.cn/download.html

Look for "Benchmark dataset for SSVEP-based BCI" (also known as the 40-target SSVEP dataset).

## Required Files

After downloading, place the following files in this `data/` directory:

```
data/
├── S1.mat
├── S2.mat
├── ...
├── S35.mat
├── Freq_Phase.mat
└── subject_info_35_dataSets.txt
```

## File Descriptions

| File | Content |
|------|---------|
| `S1.mat` to `S35.mat` | EEG recordings for 35 subjects. Each file contains a 4D array: `[64 channels × 1500 time points × 40 targets × 6 blocks]` |
| `Freq_Phase.mat` | Stimulus frequencies and phases for all 40 targets (JFPM coding) |
| `subject_info_35_dataSets.txt` | Metadata about subjects (age, gender, experience level) |

## Data Format Details

- **Sampling rate:** 250 Hz (after downsampling from original 1000 Hz)
- **Channels:** 64 (full cap, reference at Cz)
- **Trial length:** 6 seconds (0.5 s cue + 5 s stimulation + 0.5 s blank)
- **Stimuli:** Joint Frequency-Phase Modulation (JFPM)
  - Frequencies: 8.0 Hz to 15.8 Hz (step 0.2 Hz)
  - Phases: 0 to 0.5π × 39 rad
