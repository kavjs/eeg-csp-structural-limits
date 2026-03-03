# eeg-csp-structural-limits
Investigation of CSP stability under electrode constraints and additive noise in consumer-grade EEG.

Structural Stability of CSP Under Electrode Constraints
Problem

Consumer EEG systems operate under:

Limited electrode count

Low signal-to-noise ratio

Variable impedance

This work evaluates whether increasing spatial dimensionality improves or destabilizes CSP performance under additive noise.

Method

Dataset: Mendeley Motor Imagery Limb EEG

Task: Binary motor imagery (Left vs Right)

Bandpass: 8–30 Hz

Model: CSP (4 components) + LDA

Evaluation: 5-fold cross-validation

Noise model: Gaussian noise injected at test time

Metric: Mean accuracy ± std, delta vs baseline

Key Findings

Accuracy ceiling near chance (~50–52%)

Narrow CSP dominance window (6–10 channels)

Performance degrades at higher channel counts

Additive noise reduces CSP advantage

Final locked configuration: 6 symmetric channels

Limitations

Consumer-grade dataset

No artifact rejection pipeline

Stationarity assumption of CSP

Small effect sizes

Limited generalization

Hardware Implications

Increasing electrodes does not guarantee improved discrimination

Covariance instability increases with dimensionality

Signal quality likely more critical than channel count

Hardware improvements may outweigh algorithmic tuning
