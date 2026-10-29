# Bias-Corrected CORA-Derived Tidal Datums

**Regime-Aware Bias-Corrected Spatially Continuous Tidal Datums for the U.S. Gulf and Atlantic Coasts from NOAA Coastal Ocean Reanalysis**

**Authors:** Faezeh Maghsoodifar, Hamed Moftakhari, William Sweet, John Callahan, and Richard Luettich  
**Manuscript status:** Data Descriptor submitted to *Scientific Data*

## Overview

This repository shares spatially distributed, bias-corrected tidal-datum estimates derived from the NOAA Coastal Ocean Reanalysis (CORA) for the U.S. Gulf and Atlantic coasts. The dataset contains corrected estimates of **mean higher high water (MHHW)** and **great diurnal range (GT)** at approximately **89,115 coastal CORA nodes**, with a nominal spatial resolution of approximately **500 m**.

The study addresses spatially varying differences between tidal datums derived from modeled coastal water levels and NOAA observational references. Its regime-aware bias-correction framework accounts for nonlinear spatial relationships and residual spatial structure, supporting more consistent coastal tidal-datum estimates.

## Repository contents

| File | Description |
| --- | --- |
| [`CORA_Derived_Corrected_MHHW_GT.gpkg`](CORA_Derived_Corrected_MHHW_GT.gpkg) | GeoPackage containing the distributed corrected MHHW and GT dataset. |
| [`README.md`](README.md) | Dataset description, sources, and access instructions. |
| [`LICENSE`](LICENSE) | Repository license terms. |

**Scope:** The current repository distributes the dataset, not the scripts used to generate or bias-correct the tidal datums.

## Tidal-datum definitions

- **MHHW (mean higher high water):** The average of the higher high-water height of each tidal day over the applicable tidal-datum epoch.
- **GT (great diurnal range):** The elevation difference between mean higher high water (MHHW) and mean lower low water (MLLW):

  $$   GT = \mathrm{MHHW} - \mathrm{MLLW}  $$

These quantities support coastal water-level interpretation, flooding assessments, and comparisons between modeled and observed tidal datums. Before combining this dataset with other elevation products, confirm the GeoPackage attribute definitions, units, and vertical references for the intended application.

## Source datasets and methods

The study draws on the following sources:

1. **NOAA Coastal Ocean Reanalysis (CORA) v1.1:** Hourly coastal water levels used to derive modeled tidal datums.
2. **NOAA CO-OPS:** Accepted observational tidal datums and station metadata used as reference information.
3. **GEBCO_2025:** Bathymetric and topographic information supporting the spatial analysis.
4. **NOAA CO-OPS Tidal Analysis Datum Calculator (TADC):** Tidal analysis and datum calculation.

The analysis derives tidal datums from CORA water levels, compares them with NOAA gauge-based references, and applies a regime-aware, spatially varying bias correction. The correction framework uses nonlinear modeling and spatial residual adjustment to improve the agreement of the derived MHHW and GT estimates with observational benchmarks.

Useful resources: [NOAA Tides & Currents](https://tidesandcurrents.noaa.gov/) · [GEBCO](https://www.gebco.net/) · [GitHub repository](https://github.com/FaezehMagFar/Bias-Corrected-CORA-Tidal-Datums)

## Access and usage

### Read the dataset in Python

Install GeoPandas in your Python environment:

```bash
python -m pip install geopandas matplotlib
```

Download the GeoPackage into your working directory, then run:

```python
import geopandas as gpd
import matplotlib.pyplot as plt

path = "CORA_Derived_Corrected_MHHW_GT.gpkg"
data = gpd.read_file(path)

print("Features:", len(data))
print("CRS:", data.crs)
print("Columns:", data.columns.tolist())
print(data.head())

# Plot feature locations without assuming a particular datum field name.
ax = data.plot(markersize=0.5, figsize=(12, 6))
ax.set_title("Bias-corrected CORA coastal tidal-datum locations")
ax.set_xlabel("X coordinate")
ax.set_ylabel("Y coordinate")
plt.tight_layout()
plt.show()
```

The code above reads the **released GeoPackage**; it does not recreate the underlying bias-correction analysis. Inspect the available attributes and metadata before selecting a field for mapping or quantitative analysis.

## Data interpretation and limitations

The released product represents **bias-corrected, CORA-derived tidal datums**, not raw NOAA gauge observations. Local accuracy and coverage may vary, and bias correction does not eliminate all uncertainties. Users should verify the spatial and vertical reference information and assess fitness for purpose before using the dataset for site-specific design, regulatory decisions, or flood-elevation comparisons.

## Citation

When using this dataset, please acknowledge this repository and the associated manuscript:

> Maghsoodifar, F., Moftakhari, H., Sweet, W., Callahan, J., & Luettich, R. *Regime-Aware Bias-Corrected Spatially Continuous Tidal Datums for the U.S. Gulf and Atlantic Coasts from NOAA Coastal Ocean Reanalysis.* Data Descriptor submitted to *Scientific Data*.

Repository: https://github.com/FaezehMagFar/Bias-Corrected-CORA-Tidal-Datums

A formal article citation and DOI should replace the manuscript-status citation once available.

## Contact

- **Faezeh Maghsoodifar** — [fmaghsoodifar@crimson.ua.edu](mailto:fmaghsoodifar@crimson.ua.edu)
- **Hamed Moftakhari** — [hmoftakhari@ua.edu](mailto:hmoftakhari@ua.edu)

## License

See the repository's [`LICENSE`](LICENSE) file for the stated MIT license terms. Attribute the underlying NOAA and GEBCO sources as appropriate when redistributing or reusing derived information.
