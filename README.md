## ICU Neutrophil-to-Lymphocyte Ratio (NLR): Data Engineering Pipeline

Real clinical lab data is rarely analysis-ready. This project tackles that head-on: I built an end-to-end pipeline that takes raw, long-format ICU laboratory records — full of duplicate entries, inconsistent unit labels, and non-numeric flags like "QNS" or "CLOT" and transforms them into a clean, validated, longitudinal dataset ready for statistical modeling.

What this project does:

Deduplicates and reshapes tens of thousands of raw lab result rows into one row per blood draw, matching White Blood Cell, Neutrophil, and Lymphocyte counts by patient and accession number

Applies a physiologic plausibility check (ANC + ALC ≤ WBC, with tolerance for rounding) to catch data entry or matching errors before they propagate downstream

Calculates the Neutrophil-to-Lymphocyte Ratio (NLR), a clinically meaningful inflammatory biomarker, only on validated records

Produces a full suite of exploratory visualizations — distribution plots, missingness heatmaps by year, and individual patient trajectory plots — to characterize data quality and biomarker behavior before any formal modeling begins

Tech stack: Python (pandas, NumPy, Matplotlib), Graphviz (data flow diagrams)

💡 Why this matters: In clinical data science, the pipeline that gets you to clean data is often more consequential — and more error-prone — than the modeling that comes after. This project documents that process transparently, including every exclusion and validation decision, so the resulting dataset is fully reproducible and audit-ready.

🚀 Possible extensions: This validation framework generalizes to any multi-analyte lab panel (e.g., liver function panels, metabolic panels) where physiologic constraints between values can be used as a built-in data quality check. It could also be adapted into an automated data quality monitoring dashboard for ongoing clinical data pipelines.
