![image](https://github.com/user-attachments/assets/4ccaa232-99c6-4d31-829a-3042c5af8655)


# 📦 Mining Test-Scope Dependencies in Maven Central [ goblin-test-scope-analysis-paper ]

## 🧪 Overview and Goal

This repository contains the data, scripts, and methodology used in the study *“Mining and Analyzing Test-Scope Dependencies in the Maven Ecosystem”*. The focus of this research is to investigate the structure, popularity, and vulnerability exposure of artifacts used exclusively under the `test` scope in Maven projects.

By leveraging the [Goblin Framework](https://github.com/Goblin-Ecosystem/goblinDependencyMiner), we extracted and enriched dependency data with CVE metrics and semantic tags. Our goal is to understand the security and maintenance implications of test-scope dependencies — a class of dependencies often overlooked in traditional software ecosystem analyses.

---

## 🔍 Research Questions

This study addresses the following research questions:

1. **RQ1: What are the predominant artifact categories in test-scope dependencies?**  
   - Categorization of test-related libraries (e.g., mocking, logging, testing frameworks).
   - Distribution analysis of tags retrieved from Maven Central.

2. **RQ2: Is there a correlation between the number of dependencies and the number of CVEs?**  
   - Quantitative analysis of dependency count versus CVE exposure.

3. **RQ3: Do test-scope dependencies follow different security trends compared to other scopes?**  
   - Comparative boxplots and scatter plots.
   - Exploration of artifact popularity versus risk.

---

## ⚙️ Methodology

### 🛠️ Data Collection

1. **Goblin Deployment**  
   - Goblin was deployed in a dedicated cloud environment (Oracle Cloud Infrastructure) using a VM.Standard2.4 instance.
   - The stack included Neo4j (graph database), JupyterLab (analysis), and the Weaver API (metric enrichment).

2. **Artifact Extraction**  
   - A complete list of Maven artifacts and their associated dependency scopes was retrieved using Goblin.
   - Focus was placed on artifacts linked to the `test` scope.

3. **Tag Enrichment**  
   - A Selenium-based script was used to scrape `sonar.typetag` labels from [mvnrepository.com](https://mvnrepository.com), covering ~650,000 artifacts.

4. **Metric Weaving**  
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

---

## 📁 Repository Structure

```bash
├── data/
│   ├── raw/                  # Extracted raw data from Goblin
│   ├── enriched/             # CVE-enriched CSVs with tags
│   └── figures/              # All plots used in the paper
│
├── scripts/
│   ├── selenium_scraper.py   # Script to mine tags from mvnrepository
│   ├── goblin_query.ipynb    # Jupyter notebook for graph queries
│   └── analysis.ipynb        # Final plots and statistical analysis
│
├── imgs/
│   ├── methodology.png
│   └── scope_analysis.png
│
└── README.md
