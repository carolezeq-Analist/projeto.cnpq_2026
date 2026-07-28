# projeto.cnpq_2026
# Vegetation-Pasture Detection in Três Lagoas, MS

## Monitoring Land Use Change in the Brazilian Cerrado using MODIS and Random Forest

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

##  Overview

This project analyzes land use change in **Três Lagoas, Mato Grosso do Sul, Brazil**, focusing on the conversion between native vegetation and pasture in the Cerrado biome. Using **MODIS NDVI time series data (2018-2024)** and **Random Forest classification**, we detect vegetation loss, project future scenarios, and create an **Environmental Risk Index (ERI)**.

###  Key Objectives

- **Detect vegetation-to-pasture conversion** between 2018 and 2024
- **Project land use trends** to 2030 using linear modeling
- **Calculate Environmental Risk Index (ERI)** integrating:
  - Land use change patterns
  - Proximity to water bodies (MapBiomas data)
  - Terrain slope (SRTM DEM)
- **Validate** classification against MapBiomas reference data
- **Visualize** results through interactive and static maps

---

##  Study Area

**Três Lagoas, Mato Grosso do Sul, Brazil**
- **Biome**: Cerrado (Brazilian Savanna)
- **Coordinates**: 52.80°W to 51.57°W, 21.20°S to 19.61°S
- **Total area**: ~14,000 km²

---

##  Data Sources

| Data Type | Source | Resolution | Years |
|-----------|--------|------------|-------|
| **NDVI** | MODIS MOD13Q1 | 250m, 16-day composite | 2018, 2024 |
| **Land Cover** | MapBiomas Collection 8 | 30m | 2018, 2024 |
| **Elevation** | SRTM DEM | 30m | - |
| **Hydrography** | MapBiomas / OSM | - | - |
| **Protected Areas** | Brazilian Protected Areas Database | - | - |

---

##  Methodology

### 1. Data Processing
MODIS NDVI → Feature Extraction → Random Forest Classification → Change Detection → Risk Assessment
MapBiomas → Feature Extraction 
SRTM DEM → Feature Extraction 


### 2. Classification Features
- NDVI 2018 (dry season: May-September)
- NDVI 2024 (dry season)
- Delta NDVI (2024 - 2018)

### 3. Environmental Risk Index (ERI)
ERI = 0.4 × Change + 0.3 × Hydrography + 0.3 × Slope

- **Change**: Vegetation-to-pasture conversion (2018-2024)
- **Hydrography**: Proximity to water bodies
- **Slope**: Terrain steepness from SRTM

---

##  Results

### Classification Performance
| Metric | Value |
|--------|-------|
| **Overall Accuracy** | 94.8% |
| **Kappa Coefficient** | 0.894 |
| **F1-Score** | 0.948 |

### Land Use Changes (2018-2024)
| Metric | Value |
|--------|-------|
| Vegetation → Pasture | 13,643 ha |
| Pasture → Vegetation | 13,631 ha |
| Stable Areas | 56.4% |

### Environmental Risk Assessment
| Risk Level | Area (ha) | Percentage |
|------------|-----------|------------|
| 🟢 Low | 15,531 | 24.8% |
| 🟠 Medium | 35,956 | 57.5% |
| 🔴 High | 11,012 | 17.6% |

### 2030 Projection
| Land Use | Projected Area |
|----------|---------------|
| Vegetation | 42,450 ha |
| Pasture | 20,050 ha |

Site: https://carolezeq-analist.github.io/projeto.cnpq_2026/
---

##  Installation

### Requirements
```bash
pip install -r requirements.txt
geopandas>=0.12.0
pandas>=1.5.0
numpy>=1.24.0
rasterio>=1.3.0
rioxarray>=0.14.0
matplotlib>=3.7.0
folium>=0.14.0
scikit-learn>=1.2.0
scipy>=1.10.0
osmnx>=1.3.0
elevation>=1.1.3
earthaccess>=0.6.0
