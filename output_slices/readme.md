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

## Single-image mode (second method)

When you pass **only one** image, the program does not build a vector “across time” at each pixel. Instead, each pixel is described by **three numbers**: intensity and normalized **x** and **y** position (see [UNSUPERVISED_ML.md](../UNSUPERVISED_ML.md) — *When you give it one image*).

From that representation:

- **PCA, NMF, and ICA** still produce **one grayscale image per layer** (component / part / source), same ideas as in stack mode but now separating variation driven by **brightness and where on the disk** the pixel sits, not variation across multiple frames.
- **K-means** groups pixels that are similar in **brightness and position** into **K** clusters. **K-means is only used in single-image mode.** Each cluster is saved as its own image: pixels in that cluster keep their brightness; other pixels are dark (e.g. `kmeans_1.png`, `kmeans_2.png`, … for *K* groups).

**Not used in single-image mode:** Robust PCA (reserved for multi-image stacks).

If you run single-image mode, add the exported PNGs here (or a subfolder) and optional markdown tables, the same way the stack outputs above are documented.
