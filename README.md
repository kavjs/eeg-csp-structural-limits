eeg-csp-structural-limits

Structural Stability of CSP Under Electrode Constraints and Additive Noise

This project investigates the structural stability of Common Spatial Patterns (CSP) under constrained electrode configurations and additive noise, simulating consumer-grade EEG conditions.

Rather than maximizing classification accuracy, the objective is to identify performance limits and robustness boundaries under realistic hardware constraints.

Problem

Consumer EEG systems operate under structural limitations:
* Limited electrode count
* Low signal-to-noise ratio (SNR)
* Variable impedance
* Reduced spatial resolution

Under these conditions, increasing spatial dimensionality does not necessarily improve discriminability and may destabilize covariance-based methods such as CSP.

This study evaluates how channel count and additive noise influence CSP performance relative to a baseline classifier.

Dataset

* Source: Mendeley Motor Imagery Limb EEG
* Task: Binary motor imagery (Left vs Right)
* Bandpass Filter: 8–30 Hz

Method

* Spatial Filtering: CSP (4 components, frozen in final evaluation)
* Classifier: Linear Discriminant Analysis (LDA)
* Evaluation: 5-fold cross-validation
* Noise Model: Gaussian noise injected at test time

Metrics

* Mean accuracy ± standard deviation
* ΔAccuracy (CSP − Baseline)

No hyperparameter tuning was performed after final configuration lock.

Experimental Structure

* Channel reduction sweep (2–16 channels)
* Identification of CSP dominance regime
* Aggressive reduction stress test (5 channels)
* Final symmetric configuration lock (6 channels)
* Clean vs noisy comparison (STD = 0, 1)

The focus is structural sensitivity, not optimization.

Key Findings

* Accuracy ceiling remains near chance (~50–52%)
* CSP exhibits a narrow dominance window (~6–10 channels)
* Performance degrades at higher channel counts
* Additive noise compresses CSP advantage
* Six symmetric channels represent the smallest configuration showing positive Δ under noise (effect size <0.3%)
* Channel configuration impacts performance more strongly than noise magnitude

Limitations

* Consumer-grade dataset
* No artifact rejection pipeline
* Stationarity assumption inherent to CSP
* Small effect sizes
* Limited generalization beyond this dataset

This work isolates structural effects rather than pursuing performance maximization.

Hardware Implications

* Increasing electrode count does not guarantee improved discrimination
* Covariance instability increases with dimensionality
* Signal quality likely outweighs channel quantity
* Hardware improvements (electrode quality, SNR) may provide larger gains than algorithmic tuning
* CSP operates within a narrow structural stability regime under constrained conditions

eeg-csp-structural-limits/
│
├── requirements.txt
│
├── notebooks/
│   ├── day11_channel_reduction.ipynb
│   ├── day13_pre_lock_eval.ipynb
│   └── day15_final_lock.ipynb
│
├── results/
│   ├── day13_pre_lock_5ch_results.csv
|   ├── day13_pre_lock_comparison_plot.png
|   ├── day13_pre_lock_delta_plot.png
│   ├── day15_final_6ch_results.csv
│   ├── day15_final_comparison_plot.png
│   └── day15_final_delta_plot.png
│
├── report/
│   └── CSP_Structural_Limits.pdf
│
└── README.md

This project maps the structural boundary conditions of CSP under electrode constraints and additive noise.

The primary bottleneck appears to be signal quality and spatial resolution rather than hyperparameter configuration.

The results define realistic performance expectations for CSP in consumer-grade EEG systems.
