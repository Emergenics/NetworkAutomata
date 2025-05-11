# Biological Relevance of Dynamic Regions Across Ruleset Ablations (TargetProtein Subgraph)

## 1. Introduction
This analysis investigates the biological relevance of the **dynamically active regions** identified in simulations of various Network Automaton rulesets applied to the AIFM1 subgraph. By performing functional enrichment analysis on the gene sets corresponding to these dynamic regions, we assess which ruleset components contribute to generating dynamically organized patterns that are associated with known biological functions.

The dynamically active regions were identified using a consistent metric (time-averaged absolute state change over the final 20% window) and thresholded at the 80th percentile across all nodes.

## 2. Comparative Enrichment Analysis Table
The table below summarizes the functional enrichment results (GO Biological Process) for the dynamic region identified in each simulation run:

*(Table generation failed: 'tabulate' library missing. Install it.)*

_**Table Columns:**_
- **Dynamic Region Size:** Number of nodes in the dynamic region for that run.
- **Mapped Genes:** Number of unique gene symbols mapped from the dynamic region nodes.
- **Significant Terms:** Number of GO BP terms found to be significantly enriched (Adj. P < 0.05).
- **Top Term:** The GO BP term with the most significant adjusted P-value.
- **Top Term Adj P:** The adjusted P-value for the Top Term.

## 3. Interpretation of Biological Relevance
Based on the comparative enrichment analysis:

- **H+P Reference (2D):** The dynamic region from the baseline H+P run did not show significant enrichment (2612 terms found). This suggests that while it generated dynamic activity, that activity was not spatially organized in a way that strongly highlights GO BP functions under the chosen parameters and dynamic region definition.
- **H+4D-Bio (AIFM1):** The dynamic region from the 4D Biological run did not show significant enrichment (2700 terms found).
- Interpretation Note: P-Only run enrichment data missing.
- Interpretation Note: H-Only run enrichment data missing.

Conclusion: Comparing the number and nature of significant terms across runs allows us to infer which ruleset components are most effective at generating dynamically active regions that are biologically interpretable via GO enrichment.

---