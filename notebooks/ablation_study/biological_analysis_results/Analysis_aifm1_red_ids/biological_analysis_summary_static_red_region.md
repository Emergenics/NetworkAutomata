## Biological Relevance Analysis: 'aifm1_red_ids.txt' (Static Red Region)

This analysis examines the biological relevance of the **static** 'Red Region' nodes identified at the final simulation step of the H+P Reference Run (ablation_01). These node IDs were loaded from the file `aifm1_red_ids.txt`.

- **Static Red Region Size (from `aifm1_red_ids.txt`):** 707 nodes
- **Mapped Gene Symbols:** 707 unique symbols (via STRING API)

_(Note: The static Red Region in `aifm1_red_ids.txt` was defined as nodes where Final Activation - Final Inhibition > 0.5 in the H+P Reference Run (ablation_01) run.)_

### Functional Enrichment Analysis (GO Biological Process)
Significant enrichment was found for 3038 GO Biological Process terms (Adjusted P-value < 0.05).
The top enriched term is: **Translation (GO:0006412)** (AdjP=1.55e-47).

The full enrichment results table is saved as `red_region_enrichment_results.csv`.
A bar plot visualizing the top terms is saved as `red_region_enrichment_plot.png`.

Conclusion: The **static Red Region** from the H+P Reference simulation run is significantly enriched for specific biological processes, supporting the biological relevance of this definition of the emergent pattern.

Analysis results (including CSVs and plot) are saved in the directory: `biological_analysis_results/Analysis_aifm1_red_ids`