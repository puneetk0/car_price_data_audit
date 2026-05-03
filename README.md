# Data Heist: Stage 4 — Car Price Prediction Quality Audit

## Project Overview
This repository contains the completion of Stage 4 of the **DATA HEIST** competition at Rishihood University. The core objective of this project was to perform a complete 7-domain data quality audit on a synthetic Car Price Prediction dataset.

The original dataset contained 2,500 rows and 10 columns. It was deliberately seeded with structural anomalies and business-rule violations to test auditing capabilities. After a thorough cleaning and transformation process, the dataset was reduced to 2,250 valid records, enriched with newly derived metrics and an audit flag.

## Repository Structure
```
.
├── README.md                        # Project documentation
├── dashboard/
│   └── car_dashboard.html           # Interactive visual dashboard showcasing findings
├── data/
│   ├── processed/
│   │   └── car_price_cleaned.csv    # Cleaned dataset (2,250 rows × 14 columns)
│   └── raw/
│       └── car_price_prediction_with_missing.csv  # Original dataset with seeded anomalies
└── docs/
    └── DataHeist_Technical_Report.docx  # Comprehensive technical report detailing the audit
```

## Audit Domains & Highlights
The audit encompassed seven primary domains:
1. **D6 – Completeness:** Identified and removed 250 completely blank ghost rows (10% of dataset).
2. **D4 – Deduplication:** Removed 250 exact duplicates and flagged 131 near-duplicates.
3. **D2 – Formatting:** Corrected float representations of IDs and Years, and standardized categorical strings to prevent hidden mismatches.
4. **D7 – Categorical:** Corrected 221 Tesla fuel type errors (originally labeled as Diesel/Hybrid/Petrol instead of Electric).
5. **D3 – Relational:** Identified 377 EV engine size anomalies where electric vehicles carried combustion-like engine displacement.
6. **D1 – Statistical:** Spotted business-rule violations such as 592 'New' cars with mileage over 50,000 miles, and 515 'Like New' cars with over 100,000 miles. Also detected a kurtosis of -1.2 across variables, statistically confirming a synthetic uniform distribution.
7. **D5 – Visual/Trend:** Found a weak price-year correlation (-0.377) and a near-zero mileage-year correlation, further proving the dataset's synthetic nature as these contradict real-world market trends.

## Creative Metrics
To deeply understand the structural patterns of the data, 8 creative, out-of-the-box metrics were derived, including:
- **Mileage Realism Index (MRI):** `Mileage ÷ Car Age` (helps to identify statistically impossible low/high usage).
- **Depreciation Paradox:** Flagged instances where older cars cost more than newer cars of the exact same model.
- **Condition-Mileage-Year Triangle Score:** A composite 0-100 score validating internal consistency per record.
- **Phantom Mileage Detection:** Identified cars marked as "New" but with over 50,000 miles accumulated.

## Deliverables
- **Raw Data (`data/raw/`):** Contains all the original seeded errors for reproduction of the audit.
- **Cleaned Data (`data/processed/`):** Cleaned data enriched with `Car_Age`, `MRI`, `Triangle_Score`, and `Audit_Flag` columns.
- **Technical Report (`docs/`):** Full methodology, observations, and detailed audit logs.
- **Visual Dashboard (`dashboard/`):** An interactive HTML dashboard to explore the insights and anomalies visually.

## Author & Submission
- **Event:** DATA HEIST - Stage 4
- **Institution:** Rishihood University
- **Date:** April 17, 2026
- **Submission Platform:** battleofminds.vercel.app
