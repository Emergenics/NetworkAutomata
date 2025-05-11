# Dynamic Analysis of Emergent Regions Across Ruleset Ablations

## 1. Introduction
This analysis quantifies and compares the characteristics of dynamically active regions emergent from different Network Automaton ruleset configurations applied to the AIFM1 subgraph. Unlike analyses focused solely on static convergence, we identify regions exhibiting sustained dynamic activity using a consistent metric.

A **Dynamic Region** is defined here as nodes whose Time-Avg Abs Change (|Act_t+1-Act_t|, |Inh_t+1-Inh_t|) over the final 20% of simulation steps is above the 80th percentile of this metric across all nodes in the final step.

## 2. Comparative Dynamic Metrics Table
The table below summarizes key dynamic metrics for each ruleset variant:

*(Table generation failed: 'tabulate' library missing. Install it.)*

_**Metrics Key:**_
- **Dynamic Region Size:** Number of nodes identified as belonging to the Dynamic Region.
- **Dynamic Metric Threshold:** The actual threshold value (from the 80th percentile) used to define the Dynamic Region for each run.
- **Time-Avg Abs Change (|Act_t+1-Act_t|, |Inh_t+1-Inh_t|) (Avg in Region):** The average value of the Time-Avg Abs Change (|Act_t+1-Act_t|, |Inh_t+1-Inh_t|) for *only* the nodes identified as being in the Dynamic Region.
- **Jaccard vs [Baseline]:** Jaccard Index overlap between the Dynamic Region node set and static baseline node sets (Top Degree, Top RWR).

## 3. Interpretation of Dynamic Characteristics
Based on the dynamic metrics presented:

- **Harmonic Drives Dynamic Activity:** Runs where the Harmonic term is active (e.g., H-Only) show high average dynamic metric values in their dynamic regions (1.4488), indicating sustained fluctuations. Their dynamic regions are likely composed of nodes participating in persistent oscillatory or complex activity.
- **Pheromone Alone Leads to Low Activity:** The Pheromone Only run shows very low average dynamic metric values in its dynamic region (0.0008), consistent with system decay towards a near-static homogeneous state. Its dynamic region may be small or non-existent.
- **Combined H+P Dynamics:** The baseline H+P run also shows a high average dynamic metric (1.4521), confirming that the Harmonic term remains a driver of activity even when Pheromone is present.
- **Placeholder Dynamics:** The H+3D-PH (Coupled) run shows an average dynamic metric of 1.4456, suggesting sustained dynamic activity. This indicates that simply adding placeholder dimensions does not suppress the Harmonic-driven dynamics.
- **Placeholder Dynamics:** The H+5D-PH (Coupled) run shows an average dynamic metric of 1.4448, suggesting sustained dynamic activity. This indicates that simply adding placeholder dimensions does not suppress the Harmonic-driven dynamics.
- **Placeholder Dynamics:** The H+5D-PH (Decoupled) run shows an average dynamic metric of 1.4463, suggesting sustained dynamic activity. This indicates that simply adding placeholder dimensions does not suppress the Harmonic-driven dynamics.
- **Placeholder Dynamics:** The H+4D-Bio (AIFM1) run shows an average dynamic metric of 1.3820, suggesting sustained dynamic activity. This indicates that simply adding placeholder dimensions does not suppress the Harmonic-driven dynamics.

Regarding overlap with static baselines:
- Jaccard Indices measure the similarity of the Dynamic Region node set to static node sets (Top Degree, Top RWR).
- Low Jaccard Indices suggest that the nodes identified as dynamically active are largely distinct from those highlighted by static network properties alone, supporting the idea that the NA reveals unique functional groupings.
- Non-zero Jaccard Indices indicate some correlation, which is expected if static properties influence dynamics.

## 4. Conclusion on Dynamic Properties
This dynamic analysis confirms that the Harmonic term is the primary driver of sustained, heterogeneous dynamic activity in the network automaton. The Pheromone mechanism alone (at tested parameters) leads to system decay. Simply increasing state dimensionality with passive placeholder dynamics does not significantly alter the fundamental dynamic regime driven by the Harmonic term. The biological 4D state shows similar dynamic characteristics to the abstract placeholder runs, suggesting its biological grounding is in the *interpretation* of the states/rules rather than fundamentally different overall dynamic complexity at this level.

The degree of overlap between dynamically identified regions and static baselines highlights that dynamic simulations can reveal distinct sets of potentially important nodes compared to static topological analysis.

---