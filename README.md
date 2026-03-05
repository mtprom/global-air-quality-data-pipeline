# Global Urban Air Quality Analysis

**Authors:**
**Maclain Prom** – Data pipeline architecture, data collection, integration, analysis, and visualization implementation
**Diego Marquez** – Project documentation and report writing support

---

# Overview

This project analyzes the relationship between urban population size and air quality across the **500 most populated cities in the world**.

A fully automated data pipeline was built to collect air quality measurements from an external API, integrate them with global population data, and produce statistical analysis and visualizations.

The goal was to test a common assumption: **do larger cities consistently experience worse air pollution?**

To answer this, the project combines global city population data with real-time **Air Quality Index (AQI)** measurements and processes everything through a reproducible Python workflow.

---

# Tech Stack

The project focuses on **data engineering, automation, and reproducible analytics pipelines**.

### Core Languages

* **Python**

### Data Engineering & Workflow

* **Snakemake** – workflow orchestration and pipeline reproducibility
* **Requests** – API data collection
* **Pandas** – data cleaning, transformation, and integration

### Analysis & Visualization

* **NumPy** – numerical analysis
* **Matplotlib / Seaborn** – statistical visualization

### Infrastructure & Tooling

* **Git / GitHub** – version control
* **YAML configuration** – pipeline configuration management
* **CSV-based structured datasets** – intermediate and final outputs

---

# Data Sources

### Global Population Data

City population and geographic coordinate data were sourced from the **SimpleMaps World Cities dataset**, which contains over 48,000 global cities.

From this dataset, the **500 most populated cities** were selected as the base dataset for analysis.

### Air Quality Data

Air pollution measurements were retrieved using the **Google Maps Air Quality API**.

For each city coordinate, the API returns:

* Air Quality Index (AQI)
* Air quality category (Good, Poor, etc.)
* Dominant pollutant (PM2.5, PM10, O₃, etc.)
* Collection timestamp

These responses were collected programmatically and stored for integration with population data.

---

# Pipeline Architecture

The project is structured as a **fully reproducible data pipeline**.

```
Data Acquisition
        ↓
API Data Collection
        ↓
Data Cleaning & Validation
        ↓
Dataset Integration
        ↓
Statistical Analysis
        ↓
Visualization Generation
```

Each stage of the pipeline is implemented as a separate Python module and orchestrated using **Snakemake** to ensure reproducibility.

Core pipeline scripts include:

* `acquire_data.py`
* `collect_air_quality.py`
* `clean_and_integrate.py`
* `analysis_and_viz.py`
* `run_all.py`

The workflow automatically produces cleaned datasets, statistical summaries, and visualization outputs.

---

# Key Analysis

After integration, the final dataset contains **population, geographic coordinates, and air quality metrics for nearly 500 global cities**.

The analysis explores several questions:

* Whether population size correlates with air pollution
* How air quality varies by geographic region
* Which pollutants dominate in major urban areas
* Which cities appear as statistical outliers

The primary result shows that **population alone is not a strong predictor of air quality**. Large cities do not consistently produce worse pollution levels than mid-sized cities, suggesting that infrastructure, environmental policies, and geography play larger roles.

---

# Reproducibility

The project is designed to be reproducible from raw data collection through final analysis.

To reproduce the pipeline:

1. Download the **SimpleMaps World Cities dataset**
2. Place `worldcities.csv` in the `data/` directory
3. Add a Google Air Quality API key to `config.yaml`
4. Install dependencies

```
pip install -r requirements.txt
pip install snakemake
```

5. Run the full workflow

```
snakemake --cores 1
```

The pipeline will automatically:

* collect AQI data
* clean and integrate datasets
* compute statistics
* generate visualizations

All intermediate data, logs, and outputs are stored within the repository structure.

---

# Project Structure

```
FinalSub/
├── Snakefile
├── run_all.py
├── acquire_data.py
├── collect_air_quality.py
├── clean_and_integrate.py
├── analysis_and_viz.py
├── config.yaml
├── requirements.txt
│
├── data/
│   ├── worldcities.csv
│   ├── top_500_cities.csv
│   ├── integrated_cities_air_quality_final.csv
│   ├── descriptive_statistics.csv
│   ├── correlation_matrix.csv
│   └── viz/
│       ├── population_vs_aqi.png
│       ├── geographic_distribution.png
│       └── aqi_by_category.png
```

---

# Highlights

* Built a **fully automated data engineering pipeline** for external API data collection and analysis
* Integrated **global population datasets with environmental data**
* Implemented **reproducible workflows using Snakemake**
* Designed **modular data processing architecture**
* Produced **automated statistical analysis and visualizations**
* Generated a **global dataset of urban air quality measurements**

---

# License

This project is for research and educational use.
Population data is derived from the SimpleMaps dataset, and air quality measurements were retrieved via the Google Maps Air Quality API.
