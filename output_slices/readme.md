# Output Slices

This folder holds **grayscale layer images** produced by unsupervised methods on solar data. The pipeline can run in two ways; details are in [UNSUPERVISED_ML.md](../UNSUPERVISED_ML.md).

| Mode | Input | What each pixel represents |
|------|--------|------------------------------|
| **Stack mode** | Several aligned images (e.g. different times) | One brightness value **per input image** at that pixel |
| **Single-image mode** | One image | **Brightness** plus **horizontal and vertical position** (each scaled to 0–1) |

**Stack mode** uses PCA, NMF, ICA, and Robust PCA (RPCA). **Single-image mode** uses PCA, NMF, ICA, and **K-means**; **RPCA is stack-only** (it needs multiple observations per pixel to separate low-rank background from sparse anomalies).

---

## Stack mode (this folder)

Decomposition layers from **stacking** multiple solar images: each pixel is a small vector across those images, and the methods extract a few patterns as full-frame images.

### PCA

| stack_pca_1 | stack_pca_2 | stack_pca_3 |
|-------------|-------------|-------------|
| ![stack_pca_1](stack_pca_1.png) | ![stack_pca_2](stack_pca_2.png) | ![stack_pca_3](stack_pca_3.png) |

### NMF

| stack_nmf_1 | stack_nmf_2 | stack_nmf_3 |
|-------------|-------------|-------------|
| ![stack_nmf_1](stack_nmf_1.png) | ![stack_nmf_2](stack_nmf_2.png) | ![stack_nmf_3](stack_nmf_3.png) |

### ICA

| stack_ica_1 | stack_ica_2 | stack_ica_3 |
|-------------|-------------|-------------|
| ![stack_ica_1](stack_ica_1.png) | ![stack_ica_2](stack_ica_2.png) | ![stack_ica_3](stack_ica_3.png) |

### Robust PCA (background vs. anomalies)

| stack_rpca_background | stack_rpca_anomalies |
|----------------------|----------------------|
| ![stack_rpca_background](stack_rpca_background.png) | ![stack_rpca_anomalies](stack_rpca_anomalies.png) |

**Files in this folder (stack mode):** `stack_pca_1.png`, `stack_pca_2.png`, `stack_pca_3.png`, `stack_nmf_1.png`, `stack_nmf_2.png`, `stack_nmf_3.png`, `stack_ica_1.png`, `stack_ica_2.png`, `stack_ica_3.png`, `stack_rpca_background.png`, `stack_rpca_anomalies.png`.

---

*Designed by Dang.*
