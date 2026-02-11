
# Healthcare Claims Lakehouse Analytics (Microsoft Fabric + Medallion + Power BI)

## Overview
This project implements a healthcare claims analytics platform using Microsoft Fabric Lakehouse and a Medallion architecture (Bronze → Silver → Gold). The Gold layer is used to power an interactive Power BI dashboard for operational and financial insights.

## Business Goals
- Monitor claim volume trends
- Track denial rate and claim outcomes
- Analyze charge vs paid performance
- Compare performance by state and provider specialty
- Support drill-down analysis for investigation

## Data Sources
This project simulates three claim intake channels:
- Clinic intake file (CSV/Excel)
- Online portal submissions (OLTP)
- External partner feed (XML)

## Architecture
**Medallion Flow**
Bronze (raw claims) → Silver (clean/validated claims) → Gold (analytics tables) → Power BI



## Medallion Layers
### Bronze
- `bronze_claims` (raw loaded claims)

### Silver
- `silver_claims` (clean + validated)
- `silver_rejects` (invalid rows with reason)

### Gold
- `gold_claims_summary_monthly`
- `gold_payments_summary_monthly`
- `gold_claims_by_state_specialty`
- `gold_demographics_ageband_sex`

## Power BI Dashboard
Pages:
1. Executive Overview
2. Geography & Specialty
3. Demographics



## How to Reproduce
1. Upload `data/raw_input/claims_bronze.csv` to Fabric Lakehouse
2. Run notebook `01_bronze_to_silver.ipynb`
3. Run notebook `02_silver_to_gold.ipynb`
4. Build Power BI report using Gold tables

## Repository Structure
---

## Future Improvements
- Add incremental refresh
- Add more validation rules
- Add additional gold tables for CPT/ICD10 denial drivers
