# Landfast sea-ice InSAR: coherence onset and 2-D deformation at Cambridge Bay

Two winters (2018–19 and 2020–21) of Sentinel-1 ascending and descending InSAR
over the landfast sea ice of Dease Strait, near Cambridge Bay, Nunavut. The work
answers two questions:

1. **When does the ice become fixed?** This is the coherence onset.
2. **How does it move afterwards?** The motion is split into east–west and vertical components.

The results were presented by Ananthanarayanan B and Shamjid P, School of
Digital Sciences, Digital University Kerala, as a poster at
[ECRS 2026](https://sciforum.net/event/ECRS2026), the 6th International
Electronic Conference on Remote Sensing (MDPI, online, 19–21 October 2026),
session S2 · SAR Remote Sensing. The abstract is at
https://sciforum.net/paper/34580.

## Key results

- **2018–19:** the ice consolidated once, on 30 January, and stayed coherent to early April.
- **2020–21:** the ice consolidated **49 days later**, on 20 March, after an earlier attempt failed. Coherent area reached 55% in late February, collapsed to 16% in early March, then recovered.
- **12-day pairs are required.** In 2020–21, coherence was 0.78–0.81 at 12 days but 0.54 at 24 days.
- **The later winter was more mobile.** At P4, 8.2 km offshore, the horizontal rate nearly tripled (−0.43 → −1.18 cm/day) and the vertical motion reversed sign (−0.18 → +1.42 cm/day).
- **Accuracy.** Displacements agree with Chen et al. (2021) to within 2 cm where they can be compared directly. Precision from a land control is ±1.6 cm (2018–19) and ±0.7 cm (2020–21).

## Contents

| Path | What it is |
|---|---|
| `InSAR_CambridgeBay_FINAL_2019.ipynb` | Final pipeline, winter 2018–19 |
| `InSAR_CambridgeBay_FINAL_2021.ipynb` | Final pipeline, winter 2020–21 |
| `figures/figures_2019/`, `figures/figures_2021/` | 11 figures per winter: study area, coherence time series and maps, descending and ascending interferograms, fringe evolution, Goldstein filtering, LOS time series, horizontal and vertical maps, H/V time series |
| `figures/fig_talk_cross_winter.png` | Comparison of the two winters |
| `Final/InSAR_CambridgeBay_Results.docx` | Results document containing all the figures |
| `ECRS2026_Poster_LandfastIce_CambridgeBay_allpoints.pptx` | Final ECRS 2026 poster (A0 portrait) |
| `CambridgeBay_LandfastIce_InSAR_10min.pptx`, `..._15min.pptx` | Talk versions (10 and 15 minutes) |
| `InSAR_SeaIce_CambridgeBay_2021.ipynb`, `InSAR_SeaIce_CambridgeBay_Real.ipynb` | Earlier draft notebooks that reproduce Chen et al. (2021). They are kept for the record and are superseded by the FINAL notebooks. |

## Method in brief

- **Data:** Sentinel-1 IW SLC, consecutive 12-day pairs. Descending passes are S1A (HH) and ascending passes are S1B (VV).
- **Processing:** ASF HyP3 `INSAR_GAMMA` at 20×4 looks (≈80 m), with wrapped phase, DEM, incidence angle and look vectors. Search and job submission use `asf_search` and `hyp3_sdk`.
- **Coherence onset:** the share of the ice with coherence above 0.4 is tracked every 12 days. Onset is the date this share stays above 50%.
- **Deformation:** SBAS displacement, with ramps removed over land and referenced to a fixed land point (RP). Ascending and descending results are decomposed into east–west and vertical motion at four sea-ice points, P1–P4 (1.2–8.2 km offshore). A second land point, P5, is the control.

## Running

The notebooks run on ASF OpenSARLab. They need:
- a NASA Earthdata login, entered when the notebook runs (no credentials are stored here);
- HyP3 processing credits.

The SAR data and HyP3 products are not stored in this repository.

## Reference

Chen, Z. *et al.* (2021). InSAR monitoring of Arctic landfast sea ice deformation
using L-band ALOS-2, C-band Radarsat-2 and Sentinel-1. *Remote Sensing*, 13(22),
4570. https://doi.org/10.3390/rs13224570
