# Decadal Dataset of Offshore Weather and Normalized Wind-Solar Power Yield (Beibu Gulf, China)

## Overview
This repository contains a comprehensive 10-year (2016–2025) hourly dataset detailing offshore weather conditions and normalized renewable power generation for 16 deep-sea grids in the Beibu Gulf, China. The complete dataset contains 1,402,752 data rows efficiently structured into 32 CSV files (UTF-8 encoded). It is specifically designed to support long-term climate evolution analysis and the siting and sizing optimization of future offshore wind farms and solar photovoltaic (PV) arrays.

## Repository Structure
To avoid software limitations (such as Excel maximum row caps) and to enhance accessibility, the massive repository is split into two primary sub-datasets:

1. **Historical Weather Dataset** (16 CSV files)
2. **Normalized Power Yield Dataset** (16 CSV files)

---

## 1. Historical Weather Dataset
This sub-dataset provides the fundamental environmental metrics recorded sequentially at an hourly resolution.

### Data Dictionary
| Variable | Unit | Description |
| :--- | :--- | :--- |
| **SITE** | - | A textual identifier assigned to each location (S1 to S16). Users can easily select one specific site to study without typing long coordinate numbers. |
| **LON** | °E | The longitude position of the site measured in decimal degrees East. |
| **LAT** | °N | The latitude position of the site measured in decimal degrees North. |
| **YEAR** | - | Calendar year (2016–2025). |
| **SE** | - | Weather season indicator (1=Spring, 2=Summer, 3=Autumn, 4=Winter). |
| **MO / DY** | - | Calendar month (1–12) and specific day of the month (accounting for leap years). |
| **HR** | h | Exact hour of the day in a standard 24-hour UTC format (0–23). |
| **WS10M** | m/s | Wind speed measured at a standard height of 10 meters above the sea surface. |
| **WD10M** | ° | Direction from which the wind is blowing (0°–360°), crucial for avoiding energy losses caused by turbines blocking each other. |
| **SDI** | W/m² | Direct sunlight reaching the ocean surface. This gives the basic energy input needed for solar generation calculations. |
| **T2M** | °C | Air temperature at a height of 2 meters. Critical for calculating extreme heat loss affecting solar panel efficiency. |

---

## 2. Normalized Power Yield Dataset
This sub-dataset translates the raw weather variables into actual renewable power production using physical engineering models. The outputs are provided on a highly adaptable 1.0 per-unit (p.u.) basis.

### Data Dictionary
| Variable | Unit | Description |
| :--- | :--- | :--- |
| *(Time/Space)* | - | Shares the exact same spatial (SITE, LON, LAT) and chronological (YEAR, SE, MO, DY, HR) indexing columns as above. |
| **P_WIND** | p.u. | Calculated wind power output normalized from 0 to 1.0. This is derived from a physical model that includes real technical limits (cut-in, rated, and cut-out speeds for storm protection). |
| **P_PV** | p.u. | Calculated solar PV power output normalized from 0 to 1.0. This includes generation efficiency penalties (power loss) caused by the panels overheating under intense sunlight. |

---

## Usage Guidelines for Engineers
The power metrics (`P_WIND` and `P_PV`) are deliberately maintained on a **1.0 per-unit (p.u.)** scale. This makes the data incredibly flexible for any engineering project. Researchers can directly multiply these normalized columns by the rated Megawatt (MW) capacity of their chosen commercial wind turbine or solar PV module. 

This provides a straightforward baseline to project actual electricity yields for offshore capacity planning (Siting and Sizing) without building complex physical or thermal models from scratch.
