![image](https://github.com/user-attachments/assets/4ccaa232-99c6-4d31-829a-3042c5af8655)


# 📦 Mining Test-Scope Dependencies in Maven Central [ goblin-test-scope-analysis-paper ]

## 🧪 Overview and Goal

This repository contains the data, scripts, and methodology used in the study *“Mining and Analyzing Test-Scope Dependencies in the Maven Ecosystem”*. The focus of this research is to investigate the structure, popularity, and vulnerability exposure of artifacts used exclusively under the `test` scope in Maven projects.

By leveraging the [Goblin Framework](https://github.com/Goblin-Ecosystem/goblinDependencyMiner), we extracted and enriched dependency data with CVE metrics and semantic tags. Our goal is to understand the security and maintenance implications of test-scope dependencies — a class of dependencies often overlooked in traditional software ecosystem analyses.

---

## 🔍 Research Questions

This study addresses the following research questions:

1. **RQ1: What are the most common artifact categories associated with test-scope dependencies in the Maven ecosystem?**  
    - Rationale: This question investigates the frequent types of libraries used for testing purposes and their distribution in the ecosystem.

2. **RQ2: How do dependencies within test-scope artifacts correlate with the number of CVEs?**
    - Rationale: This question investigates how the presence of certain dependencies within test-scope artifacts might relate to security vulnerabilities (CVEs).

3. **RQ3: Does a higher number of dependencies in test-scope artifacts result in a higher number of CVEs?**
    - Rationale: This question investigates whether projects with more test-scope dependencies tend to have more vulnerabilities.

4. **RQ4: Are there certain artifact categories within the test scope that tend to have fewer security vulnerabilities (CVEs)?**
    - Rationale: This question investigates whether some categories of test-scope libraries are more secure than others.

5. **RQ5: How do the dependencies within test-scope artifacts impact the vulnerability profile of software projects using them?**
    - Rationale: This question investigates the overall effect that test-scope dependencies have on the vulnerability landscape of projects that utilize them.

---

## ⚙️ Methodology

### 🛠️ Data Collection

1. **Goblin Deployment**  
   - Goblin was deployed in a dedicated cloud environment (Oracle Cloud Infrastructure) using a VM.Standard2.4 instance.
   - The stack included Neo4j (graph database), JupyterLab (analysis), and the Weaver API (metric enrichment).

2. **Artifact Extraction**  
   - A complete list of Maven artifacts and their associated dependency scopes was retrieved using Goblin.
   - Focus was placed on artifacts linked to the `test` scope.
 
3. **Metric Weaving**  
   - Goblin Weaver was used to compute:
     - Direct CVEs (`CVE`)
     - Aggregated CVEs (`CVE_AGGREGATED`)
     - Freshness and dependency structure metrics

---

### 🧼 Data Analysis

- **Data Cleaning**  
  - Filtered artifacts missing metadata, tags, or with no test-scope relevance.

- **Categorization**  
  - Grouped artifacts by macro-tags such as `Testing`, `Mocking`, `Logging`, `Assertion`, etc.

- **Statistical Analysis**  
  - Produced boxplots, scatter plots, and time series graphs.
  - Correlated CVE count, dependency popularity, and release timeline.


