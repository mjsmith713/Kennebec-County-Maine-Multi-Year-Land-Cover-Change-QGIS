# Kennebec County, Maine: Multi-Year Habitat & Land-Cover Change Trajectory Analysis (2023–2026)

## Project Overview
This GIS analysis quantifies multi-year land-cover and wildlife habitat dynamics across **Kennebec County, Maine** (**608,305.7 acres** / **2,461.73 km²**) from **2023 to 2026** using **QGIS** (`EPSG:32619` / WGS 84 UTM Zone 19N, 30m × 30m resolution). By applying base-10 positional raster encoding, four annual classified habitat rasters (`Hab_Bin_2023` through `Hab_Bin_2026`) were synthesized into a single chronological trajectory raster covering **2,735,251 pixels**.

The workflow tracks landscape stability, disturbance, and habitat transitions—with a conservation focus on **Forests / Deer Covering Areas**, **Non-Forest Wetlands**, **Deer Wintering Areas (DWA)**, and **Maine Conserved Lands (MCL)**.

## Land-Cover & Habitat Encoding Schema
Annual land-cover classifications were standardized into five primary categories and reclassified into annual binary habitat rasters (`Hab_Bin_2023`–`Hab_Bin_2026`) for trajectory modeling:

| Land-Cover Class | Category Name | Habitat Bin Code | Ecological & Spatial Role in Kennebec County |
| :---: | :--- | :---: | :--- |
| **1** | Water | `0` (Masked / Water) | Lakes, ponds, Kennebec River corridor, and open waterbodies |
| **2** | Non-Forest Wetlands | `1` (Suitable Habitat) | Emergent marshes, bogs, fens, and riparian scrub-shrub wetlands |
| **3** | **Forests / Deer Covering Areas** | `1` (Suitable Habitat) | Coniferous and mixed forest stands providing critical winter shelter |
| **4** | Developed Areas | `2` (Non-Habitat) | Impervious surfaces, residential/commercial infrastructure, and roadways |
| **5** | Vegetation (Open) | `1` / `2` (Context-Dependent) | Agricultural fields, pastures, shrublands, and regenerating cover |

## Methodology: Base-10 Positional Raster Encoding
Using the **QGIS Raster Calculator**, annual habitat rasters were multiplied by ascending powers of 10 so each decimal digit preserves a specific year:

```text
("Hab_Bin_2023@1" * 1) + ("Hab_Bin_2024@1" * 10) + ("Hab_Bin_2025@1" * 100) + ("Hab_Bin_2026@1" * 1000)
```

* **Positional Reading (Right to Left):** 1s place = 2023, 10s place = 2024, 100s place = 2025, 1,000s place = 2026.
* **Two-Stage Classification:** The 80 unique 4-digit trajectory bins (`Habitat_Trajectory_2023_2024_2025_2026`) were subsequently grouped into six ecological summary classes (`Trajectory_Summary_2023_2024_2025_2026`).

## County-Wide Ecological Trajectory Summary (2023–2026)

| Summary Code | Ecological Trajectory Category | Pixel Count (30m) | Area (Acres) | Area (km²) | % of County |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **1** | **Persistent Stable Habitat** | `2,034,204` | **452,396.5** | 1,830.78 | **74.37%** |
| **6** | **Temporary Disturbance / Rotational Cover** | `290,358` | **64,574.1** | 261.32 | **10.62%** |
| **3** | **Persistent Waterbodies** | `219,840` | **48,891.3** | 197.86 | **8.04%** |
| **5** | **Confirmed Habitat Regrowth (2023–2026)** | `125,470` | **27,903.9** | 112.92 | **4.59%** |
| **2** | **Persistent Developed / Non-Habitat** | `47,042` | **10,461.9** | 42.34 | **1.72%** |
| **4** | **Confirmed Habitat Loss (2023–2026)** | `18,337` | **4,078.1** | 16.50 | **0.67%** |
| **Total** | **Kennebec County Study Area** | **`2,735,251`** | **`608,305.7`** | **`2,461.73`** | **`100.00%`** |

## Key Findings
* **Net Habitat Gain (+23,825.8 Acres):** Confirmed Habitat Regrowth (**27,903.9 acres**) outpaced Confirmed Habitat Loss (**4,078.1 acres**) by a **6.8-to-1 ratio** across the 2023–2026 timeframe.
* **High Core Habitat Stability:** Nearly three-quarters of Kennebec County (**74.37%**, or **452,396.5 acres**) remained uninterrupted **Persistent Stable Habitat** across all four years.
* **Active Forest & Agricultural Dynamics:** Roughly **10.62%** (**64,574.1 acres**) experienced **Temporary Disturbance or Rotational Cover** (such as timber harvesting, seasonal water fluctuations, or agricultural rotation).

## Repository Structure
```text
├── docs/
│ ├── Kennebec_County_Final_README.pdf
│ ├── Kennebec_County_Technical_Methodology.pdf
│ └── Kennebec_County_Trajectory_Stats_Report.pdf
├── outputs/
│ └── [Final QGIS Print Layout Map PNG]
├── stats/
│ ├── Kennebec_Trajectory_Stats.csv
│ └── kennebec_trajectory_summary_stats.csv
└── README.md
```

