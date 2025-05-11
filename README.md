# Notebook 1: "*The Network IS the Computation*"

### **The Foundational Hypothesis: *The Network IS the Computation***

#### This work is driven by the hypothesis that in complex, interconnected systems – from the brain to biological pathways – the **network structure itself, coupled with local interaction rules, directly embodies and performs computation.** Global function and behavior are not merely correlated with network activity but are the *emergent result* of this network-based computation.

### **Biological Networks as a Computational Substrate:**

#### Biological systems, particularly PPI networks, offer a rich substrate to test this hypothesis. Their complex topology and the dynamic nature of protein interactions suggest that pathways don't just passively relay signals but actively *compute* cellular responses based on inputs and internal states. Traditional static analysis often misses this computational essence.

### **The Network Automaton Approach:**

To explore this, we utilize a **Network Automaton**:
1.  We represent the biological system (AIFM1 pathway) as a graph `G`.
2.  Nodes (proteins) maintain an internal state `S_i(t)` (here, an abstract 5D vector).
3.  Local rules `f` (our "H/P" inspired ruleset: `hdc_5d_step_vectorized`) dictate state transitions based *only* on a node's current state and its neighbors': `S_i(t+1) = f(S_i(t), {S_j(t) | j ∈ Neighbors(i)}, rule_params)`.
4.  We simulate this local computation iteratively across the network.

### **Demonstrating Network Computation:**

The core goal is to demonstrate that this network-based computation yields **emergent global states** (like the "Red Region") that are **functionally meaningful**. We validate this by:

*   Identifying the emergent pattern (Cell 11).
*   Testing if this pattern corresponds to known biological functions via GO Enrichment (Cell 12).
*   Showing that this dynamically computed pattern reveals functional insights distinct from static network properties (Cell 11.1, 12.2).

### **Why Biology?** Successfully demonstrating "*The Network IS the Computation*" in a complex, real-world biological system offers profound implications for understanding cellular function and potentially developing novel computational approaches applicable to biotech, bioinformatics, and medicine. This notebook aims to provide compelling evidence for this theoretical perspective through concrete simulation and analysis.
---
---
# What is a Network Automaton?

---

#### 🔹 **Basic Definition**
A **Network Automaton (NA)** is a computational system where nodes in a network update their states based on simple local rules and the structure of their connections. Unlike cellular automata, which operate on regular grids, NAs evolve over arbitrary graphs, allowing topology itself to influence behavior.

---

#### 🔹 **Formal Definition**

A **Network Automaton (NA)** is a quadruple:

**NA = (G, S, R, T)**, where:

-   **G = (V, E)** is a (possibly weighted or directed) graph with node set **V** and edge set **E** defining the system topology.
-   **S** is the finite or continuous set of possible internal states for each node (e.g., binary, categorical, N-dimensional vectors like the 5D state `[u, v, w, x, y]` used in this project).
-   **R** is a local update rule, often expressed as a function mapping the state of a node and its neighbors to the node's next state, potentially influenced by global parameters **Θ**:
    **R: S × P(S) × Θ → S**
    or more explicitly for node *i*:
    **Sᵢ(t+1) = R(Sᵢ(t), {Sⱼ(t) | j ∈ N(i)}, Θ)**
    where **N(i)** is the neighborhood of node *i* defined by **E**, and **P(S)** represents an aggregation or the set of neighbor states.
-   **T** is the transition mechanism, typically applying **R** synchronously or asynchronously across all nodes in **V** to evolve the system over discrete time steps *t*.

---

#### 🔹 **Descriptive Definition**
A **Network Automaton** is like a cellular automaton but built on any kind of network or graph, not just a grid. Each point (node) in the network has a state, and it updates that state based on simple rules considering its own state and the states of its direct connections (neighbors). The key difference is that the specific **pattern of connections**—the network's topology—fundamentally shapes how information flows and what overall behaviors can emerge from the system.

---

#### 🔹 **Why Network Automata Matter**
-   They generalize cellular automata to complex network structures.
-   They allow complex, global dynamics and patterns to emerge from simple, local interactions.
-   They serve as powerful models for diverse systems like biological networks (genes, proteins, neurons), social systems, technological networks, and knowledge graphs.
-   They directly embody the principle that network structure actively participates in computation.
-   They provide the foundational model system for studying Emergenics, including phenomena like phase transitions and self-organization controlled by topology.

---
---

# What is a Computational Fabric?

---

#### 🔹 **Basic Definition (Concise)**
A **Computational Fabric (CF)** is the **dynamic medium** formed by a Network Automaton's specific structure (graph topology), node states, and local rules working in concert. It's the active "material" of the system where computation emerges, and the fabric's properties (like its computational capabilities or phase behavior) are directly tuned by the network's structure.

---

#### 🔹 **Formal Definition (Extending NA)**

Given a Network Automaton **NA = (G, S, R, T)**, the **Computational Fabric (CF)** represents the *instantiated system* defined by a specific graph **G** and the resultant dynamics. It is characterized by:

**CF = (NA, Φ, Ω)**, where:

-   **NA = (G, S, R, T)** is the underlying Network Automaton definition specifying the components and rules.
-   **Φ** represents the set of **Topological Properties** and **Control Parameters** associated with the *specific* graph G used in the instantiation (e.g., average degree, clustering, modularity; or control parameters like WS rewiring probability *p*, SBM intra-community probability *p_intra*, RGG connection radius *r*). These parameters define the structural context and act as macroscopic knobs tuning the fabric's behavior.
-   **Ω** represents the set of **Emergent Dynamical Properties** and resultant **Computational Capabilities** exhibited by the specific system NA instance defined by G (e.g., observed phase transitions, the structure of the attractor landscape, information processing characteristics, specific values of critical exponents like γ and ν, order parameters like susceptibility χ). These properties (Ω) arise dynamically from the interplay of G, S, R, and T, and their nature is fundamentally dependent on the topological parameters (Φ).

The CF formalizes the concept that the specific topological configuration (Φ) of a Network Automaton (NA) creates a unique medium that exhibits characteristic emergent computational behaviors (Ω).

---

#### 🔹 **Descriptive Definition**
Think of the Network Automaton (nodes, edges, rules) as providing the basic "recipe" and ingredients (like yarn type and knitting instructions). The **Computational Fabric** is the specific **sweater** you knit using that recipe with a particular pattern (the network topology). Just as different knitting patterns create sweaters with different textures, elasticity, and warmth (emergent properties), different network topologies create computational fabrics with distinct dynamic behaviors, phase transitions, and ultimately, different computational abilities. The way the network is "woven" defines the fabric and what it can compute.

---

#### 🔹 **Why Computational Fabric Matters (within Emergenics)**
-   It explicitly connects the static **structure (G)** and its **properties (Φ)** to the **dynamic computational behavior (Ω)** that emerges.
-   It reframes computation not as an algorithm running *on* a substrate, but as a behavior *of* the substrate itself.
-   It allows classifying networks based on the *computational properties* of the fabric they create (e.g., WS, SBM, RGG models were shown to form fabrics belonging to distinct universality classes based on their critical exponents).
-   It underpins the goal of **designing computation by engineering structure**: creating specific network topologies (Φ) to instantiate a Computational Fabric with desired emergent properties (Ω).
-   It embodies the core Emergenics principle: **Structure IS Computation**, where the network *is* the computational medium.

---
---
# Network Automaton Dynamics & Biological Relevance

## 🔥 Overview: The Network Automaton Concept

This notebook investigates whether simulating localized, dynamic interactions on a protein-protein interaction (PPI) network can reveal **emergent functional modules** that are biologically relevant and potentially distinct from those identified by static network analysis. We employ a **Network Automaton**, a computational model where node states evolve based on local rules and network topology.

**Hypothesis:** Simulating dynamic activity propagation on a PPI graph using biologically-inspired rules can identify groups of proteins (an "emergent pattern" or "Dynamic Region") whose collective function is relevant to the initial perturbation (AIFM1 activation) and distinct from purely structural network properties.

**Core Idea & Flow:**
1.  **Network Definition:** A graph `G` is constructed representing protein-protein interactions (PPI) around a target protein (AIFM1), using data from the STRING database filtered by confidence scores (Cell 2).
2.  **State Representation:** Each protein `i` is assigned a multi-dimensional state vector `S_i(t)`. Here, we use a biologically-inspired 4D state `S = [Act, Inh, Cargo, Loc]`, representing Activation, Inhibition, Cargo Binding status, and Subcellular Location (Cell 3). *Justification: Grounding state variables to enhance biological interpretability.*
3.  **Local Update Rules:** A function `f` determines the next state: `S_i(t+1) = f(S_i(t), {S_j(t) | j ∈ Neighbors(i)}, rule_params)`. The rules (`hdc_4d_step_vectorized`, Cell 4) model activation/inhibition, cargo binding/release, location transitions, diffusion, noise, etc., governed by `rule_params` (detailed in Cell 1).
4.  **Simulation:** Starting with AIFM1 activated, rules are applied iteratively via `run_simulation_network_automaton` (Cell 5) for `MAX_SIMULATION_STEPS` (Cell 6).
5.  **Emergent Pattern Analysis:** We identify the "Dynamic Region" - nodes with high sustained activity, based on time-averaged magnitude over a window (`DYNAMIC_REGION_METRIC='time_avg_magnitude'`, `DYNAMIC_REGION_THRESHOLD_TYPE='percentile'`) (Cell 11).
6.  **Validation & Comparison:** We test the biological relevance of the Dynamic Region via GO Enrichment (Cell 12) and critically compare its composition and enrichment profile to baseline node sets derived from static graph properties (degree, RWR) (Cells 7, 11.1, 12.2).

**Target Result:** Demonstration that the dynamically derived Dynamic Region yields significant *and* relevant GO enrichment (related to AIFM1 pathways/functions) that provides unique biological insights compared to static baseline analyses.

---

## 🚀 Running the Notebook: Workflows

This notebook supports two main workflows: a standard baseline run and interactive parameter exploration.

**Workflow 1: Baseline Analysis (Recommended First Run)**

1.  **Configure:** Review and set desired baseline parameters in **Cell 1**. *(Ensure DYNAMIC_REGION_METRIC is valid)*.
2.  **Execute Sequentially:** Run cells **0 through 14** in order.
    *   **Cell 6** executes the simulation using parameters from Cell 1.
    *   **Cells 7-13** analyze and visualize the results of *this baseline run*.
    *   **Cell 14** provides a summary based on the baseline.
3.  **Review:** Examine the outputs, particularly the enrichment results (Cells 12-13), comparisons (Cell 11.1, 12.2), dynamics (Cells 6.1, 13.4, 13.5), sensitivity (Cell 13.2) and the final summary (Cell 14).

**Workflow 2: Interactive Exploration (After Baseline Run)**

1.  **Run Baseline First:** Complete Workflow 1 at least once to ensure all functions are defined and baseline results are available for comparison.
2.  **Locate Widgets:** Go to the output area of **Cell 6.3**. The interactive sliders and button should be displayed.
3.  **Adjust & Run:** Modify the `Diffusion`, `Noise` sliders. *(Note: The `Red Thresh` slider currently only sets the `RED_REGION_THRESHOLD` global, which is not directly used by the `time_avg_magnitude` metric configured in Cell 1 for identifying the Dynamic Region in Cell 11. Modifying the dynamic region threshold requires changing Cell 1 parameters like `DYNAMIC_REGION_THRESHOLD_VALUE` or `DYNAMIC_REGION_THRESHOLD_TYPE` and re-running from Cell 11)*. Click the **"Run Simulation with Sliders"** button. Wait for the simulation to complete in the output area below the button.
    *   *Effect:* This re-runs the simulation using the new dynamics parameters (Diffusion, Noise). It **overwrites** the global simulation history (`global_state_history_list`, `global_state_history_np`).
4.  **Re-Analyze:** Go to **Cell 7** and **re-execute Cells 7 through 14 sequentially**. These cells will now process and display the results based on the interactive run's parameters and history.
5.  **Iterate:** Repeat steps 2-4 to explore different parameter combinations.

**Resetting to Baseline:** To re-analyze the original baseline results after an interactive run, you must **re-execute Cell 6** (which uses Cell 1 parameters) and then re-execute Cells 7-14. If the kernel is restarted, you must run Cells 0-6 again.

---

## 🔬 Exploring the Model: Additional Analytical Cells

Beyond the core workflow and interactive widgets, this notebook includes cells for deeper analysis:

*   **Metadata Summary (Cell 4.1):** Provides a quick overview of the configuration used for the run.
*   **Animation (Cell 6.1):** Visualizes the baseline simulation's state evolution over time.
*   **PCA Trajectory (Cell 7.1):** Reduces the high-dimensional state space to 2D to visualize the overall system trajectory.
*   **Sensitivity Analysis (Cell 13.1/13.2):** Systematically tests the impact of changing `diffusion_factor`.
*   **Dynamics Analysis (Cells 13.4):** Investigates the stability and temporal evolution of the Dynamic Region using line plots and a heatmap (Cell 13.5 needs adding if desired).

These cells provide further insights complementing the main simulation and interactive exploration.

---

## 🗺️ Notebook Structure Summary

1.  **Setup & Config (Cells 0-1)**
2.  **Graph & State Prep (Cells 2-3)**
3.  **Define Logic (Cells 2.2, 4, 5)**: Visualization Func, Rule Def, Sim Runner
4.  **(Info) Metadata Summary (Cell 4.1)**
5.  **Run Baseline Simulation (Cell 6)**
6.  **(Optional) Visualize Dynamics (Cell 6.1)**: Animation
7.  **(Optional) Interactive Exploration (Cells 6.2-6.3)**: Widgets & Re-run Logic
8.  **Analyze Results (Cells 7-11)**: Formatting, Baseline Calcs, PCA, Plots, Dynamic Region ID *(Operates on LAST run)*
9.  **Biological Validation (Cells 12-13)**: GO Enrichment (Dynamic Region & Baselines), Plot *(Operates on LAST run's Dynamic Region)*
10. **(Optional) Deeper Analysis (Cells 13.1-13.4)**: Sensitivity, Stability/Dynamics Plots *(Operates mostly on Baseline Run, check cell descriptions)*
11. **Summarize (Cell 14)**
Copyright 2025 Michael G. Young II, Emergenics Foundation

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.