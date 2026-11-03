# ARSF synthetic OFDM dataset

Generated from the signal model implemented in the supplied ARSF `dataset.py` and `config.py`.

## Contents

- `cells/*.npz`: one archive per SNR / noise-uncertainty operating point (and repeat).
- `manifest.csv`: condition, split sizes, output file, and seed information.
- `dataset_metadata.json`: parameters used during generation.

## Arrays in each NPZ file

- `X_train`, `X_val`, `X_test`: complex64 arrays shaped `(observations, samples)`.
- `y_train`, `y_val`, `y_test`: int32 arrays; `0 = H0` (noise only), `1 = H1` (OFDM + noise).
- `snr_db`, `delta_db`, `n_samples`, `repeat`: scalar condition metadata.

## Generation settings

- Seed: 42
- Default split sizes: 600 train / 400 validation / 600 test (balanced H0/H1).
- Repeats: 1
- Sample-size scaling dataset included: False

## Load a cell in Python

```python
import numpy as np
data = np.load('cells/<cell-file>.npz')
X_train = data['X_train']
y_train = data['y_train']
X_val = data['X_val']
y_val = data['y_val']
X_test = data['X_test']
y_test = data['y_test']
```

This is simulated data, not an over-the-air or SDR capture.
