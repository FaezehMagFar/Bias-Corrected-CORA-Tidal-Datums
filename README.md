# Regime-Aware Bias-Corrected Spatially Continuous Tidal Datums for the U.S. Gulf and Atlantic Coasts from NOAA Coastal Ocean Reanalysis
> Regime-Aware Bias-Corrected Spatially Continuous Tidal Datums for the U.S. Gulf and Atlantic Coasts from NOAA Coastal Ocean Reanalysis
> Maghsoodifar F., Moftakhari H., Sweet W., Callahan J., & Luettich R.  
> Submitted as a Data Descriptor to *Scientific Data*

This repository provides the **full dataset, code, and documentation** for the study.
The work delivers high-resolution (≈500 m) maps of Mean Higher High Water (MHHW) and Great Diurnal Range (GT) at 89 115 coastal CORA nodes. A regime-aware bias-correction framework—combining hierarchical clustering, XGBoost, spatial k-nearest-neighbor regression, and Gaussian Process Regression—aligns CORA V1.1 tidal datums with 223 NOAA accepted tidal-datum stations, cutting held-out RMSE by ~90 % for MHHW and ~80 % for GT.

---

## Data sources

* NOAA Coastal Ocean Reanalysis (CORA) V1.1 hourly water levels  
* NOAA CO-OPS accepted tidal datums & station metadata  
* GEBCO_2025 global elevation grid  
* NOAA CO-OPS Tidal Analysis Datum Calculator (TADC)
---

## Contact

Faezeh Maghsoodifar — fmaghsoodifar@crimson.ua.edu  
Hamed Moftakhari — hmoftakhari@ua.edu
