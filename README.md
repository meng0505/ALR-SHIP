# ALR-SHIP

ALR-SHIP is an azimuth low-resolution SAR ship detection dataset constructed from GF-3 C-band SLC data. It is designed for ship detection under the 2-D asymmetric resolution mode (2-D-ARM), where ship targets appear as azimuth-compressed ultra-thin stripe-like responses.

## Dataset Overview

ALR-SHIP contains 367 GF-3 offshore SLC scenes collected from multiple regions during 2020.01–2024.09. Four azimuth-resolution settings are provided: 87.5 m, 175 m, 262.5 m, and 350 m. Each resolution subset contains 2,978 image patches and 4,032 ship instances. The scene-level split includes 300 train scenes and 67 test scenes.

| Item | Description |
|---|---|
| Data source | GF-3 C-band SLC data |
| Scene type | Offshore |
| Annotation type | HBB |
| Azimuth-resolution settings | 87.5 m, 175 m, 262.5 m, 350 m |
| Range resolution | 3 m |
| Patch size | 480 × (110–232) pixels |
| Scene-level SAR scenes | 367 |
| Patch images per resolution | 2,978 |
| Ship instances per resolution | 4,032 |

## Dataset Split

The dataset is split at the scene level to avoid scene leakage. All azimuth-resolution subsets follow the same scene-level split.

| Item | Statistics |
|---|---:|
| Train / test scenes | 300 / 67 |
| Train / test patches | 2,082 / 896 |
| Train / test instances | 2,753 / 1,279 |

## Auxiliary Sea-State Distribution

Sea-state statistics are derived from ERA5 daily mean significant wave height ($H_s$) according to WMO sea-state ranges. These statistics are used only for dataset characterization and are not used as training or evaluation labels.

| Sea-state category | $H_s$ range | Scenes | Percentage |
|---|---:|---:|---:|
| 1-Calm-rippled | 0–0.1 m | 1 | 0.27% |
| 2-Smooth | 0.1–0.5 m | 52 | 14.17% |
| 3-Slight | 0.5–1.25 m | 218 | 59.40% |
| 4-Moderate | 1.25–2.5 m | 85 | 23.16% |
| 5-Rough | 2.5–4.0 m | 11 | 3.00% |

## Image-Derived Sea-Clutter Statistics

Sea-clutter statistics are image-derived relative indicators computed from SAR intensity images. They are used to characterize background complexity rather than physical sea-clutter labels. The clutter score is obtained by combining normalized image-texture indicators, including background standard deviation, coefficient of variation, texture entropy, edge density, and local standard deviation.

| Metric | Mean | Std | Range |
|---|---:|---:|---:|
| Clutter score | 0.674 | 0.075 | 0.201–0.762 |
| Background std | 0.210 | 0.013 | 0.148–0.228 |
| Coefficient of variation | 0.664 | 0.112 | 0.580–1.326 |
| Texture entropy | 6.896 | 0.941 | 3.137–7.704 |
| Edge density | 0.371 | 0.003 | 0.345–0.376 |
| Local std mean | 0.198 | 0.027 | 0.078–0.226 |

## Notes

- The sea-state statistics are auxiliary environmental statistics derived from ERA5 significant wave height and WMO sea-state ranges.
- The sea-clutter statistics are image-derived relative metrics and should not be interpreted as physical sea-clutter labels.
- Each azimuth-resolution subset contains the same scene-level samples and annotations, enabling paired comparison across different azimuth-resolution settings.
