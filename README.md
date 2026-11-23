# Kennebec-County-Maine-Multi-Year-Land-Cover-Change-QGIS
Multi-year (2023-2026) land-cover change trajectory analysis in QGIS using base-10 positional raster encoding and unique value area reporting.
# Kennebec County, Maine: Multi-Year Land-Cover Change Trajectory Analysis (2023–2026)

## Project Overview
This GIS analysis evaluates multi-year land-cover transitions across **Kennebec County, Maine** from **2023 to 2026** using **QGIS**. By applying base-10 positional raster encoding, each pixel's complete four-year land-cover history is preserved within a single integer value, enabling targeted tracking of habitat shifts—particularly changes affecting **Forests / Deer Covering Areas** and **Non-Forest Wetlands**.

## Land-Cover Classification Schema
Each annual input raster was reclassified into five standardized land-cover categories:

| Class Value | Land-Cover Category | Ecological & Spatial Relevance |
| :---: | :--- | :--- |
| **1** | Water | Lakes, ponds, rivers, and open water bodies |
| **2** | Non-Forest Wetlands | Emergent marshes, bogs, fens, and scrub-shrub wetlands |
| **3** | Forests / Deer Covering Areas | Coniferous/mixed forest stands providing winter shelter and wildlife cover |
| **4** | Developed Areas | Impervious surfaces, residential/commercial infrastructure, and roadways |
| **5** | Vegetation | Agricultural fields, grasslands, shrublands, and regenerating open vegetation |

## Methodology: Base-10 Positional Raster Encoding
Using the **QGIS Raster Calculator**, annual classified rasters (`2023` through `2026`) were multiplied by ascending powers of 10 so each decimal digit represents a specific year:

```text
("2023_class@1" * 1) + ("2024_class@1" * 10) + ("2025_class@1" * 100) + ("2026_class@1" * 1000)
```

### Interpreting Trajectory Bin IDs (Read Right to Left)
* **1s Place (`* 1`):** 2023 Class
* **10s Place (`* 10`):** 2024 Class
* **100s Place (`* 100`):** 2025 Class
* **1,000s Place (`* 1000`):** 2026 Class

**Example Trajectory (`4333`):** A pixel classified as **Forests / Deer Covering Areas (`3`)** from 2023 to 2025 that transitioned to **Developed Areas (`4`)** in 2026 (`3 + 30 + 300 + 4000 = 4,333`).

## Key Findings *(Update with Unique Values Report)*
* **Persistent Deer Cover (`3333`):** `[Insert Pixel Count]` pixels (`[Insert Acres / sq km]`)
* **Forest / Deer Cover to Developed (`4333` / `4433`):** `[Insert Pixel Count]` pixels (`[Insert Acres / sq km]`)
* **Dominant Overall Transition:** `[Insert Top Change Trajectory & Area]`

## Repository Structure
```text
├── docs/
│ ├── Kennebec_County_Project_README.pdf
│ ├── Kennebec_County_Technical_Methodology.pdf
│ └── Kennebec_County_Trajectory_Worksheet.pdf
├── outputs/
│ └── [Final QGIS Print Layout Map PNG]
├── stats/
│ └── [Unique Values Report CSV]
└── README.md
```
