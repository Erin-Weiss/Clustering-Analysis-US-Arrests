# Crime Pattern Segmentation Across U.S. States Using Clustering Analysis

**Author:** Erin Weiss
[Portfolio](https://erin-weiss.github.io/index.html) | [LinkedIn](https://www.linkedin.com/in/erinweiss3/) | [GitHub](https://github.com/Erin-Weiss)

[View the Full Interactive Report](https://erin-weiss.github.io/articles/clustering-project.html) | [Live GitHub Page](https://erin-weiss.github.io/Clustering-Analysis-US-Arrests/)

---

## Objective

Segment all 50 U.S. states into meaningful groups based on violent crime arrest rates using unsupervised learning. By applying both K-means clustering and hierarchical clustering to the USArrests dataset, this analysis uncovers hidden crime-rate profiles across states — the same type of pattern discovery that businesses use for customer segmentation, market analysis, and risk-tier classification. The project evaluates multiple values of *k*, compares clustering methods, and identifies the optimal segmentation for interpretability and stability.

---

## Dataset

| Property | Detail |
|----------|--------|
| Source | USArrests.csv |
| Observations | 50 U.S. states |
| Features | Murder, Assault, UrbanPop, Rape |
| Target Variable | Unsupervised (no target) |

---

## Methodology

1. **Data Preparation** — Loaded and inspected the USArrests dataset for completeness, structure, and summary statistics across all four features.
2. **Standardization** — Scaled all variables to mean 0 and standard deviation 1 to ensure equal influence in distance calculations and prevent high-variance features like Assault from dominating.
3. **K-Means Clustering (k = 2–5)** — Ran `kmeans()` with `nstart = 20` across multiple cluster counts to evaluate segmentation quality at each level of granularity.
4. **Cluster Evaluation** — Computed Within-Cluster Sum of Squares (WCSS), generated an Elbow Plot, and applied the Gap Statistic to determine the optimal number of clusters.
5. **Hierarchical Clustering** — Performed complete-linkage hierarchical clustering on both scaled and unscaled data to compare dendrogram structure and assess the impact of standardization.
6. **Method Comparison** — Compared K-means and hierarchical results for cluster shape, separation, and interpretability to arrive at a final recommendation.

---

## Results

| Cluster Count | Method | Assessment |
|---------------|--------|------------|
| K = 2 | K-Means | Basic high-crime vs. low-crime split |
| K = 3 | K-Means | A middle-crime group emerges |
| **K = 4** | **K-Means** | **Best-defined structure — balanced, interpretable, stable** |
| K = 5 | K-Means | Overfitting — redundant sub-clusters with heavy overlap |
| K = 4 | Hierarchical (scaled) | Clear dendrogram structure confirming K-means patterns |

**Key findings:**

- States cluster naturally into distinct crime-rate profiles, with clear separation between low-crime and high-crime groups — directly analogous to how businesses identify distinct customer segments or risk tiers.
- **K = 4** provides the strongest balance of interpretability, stability, and explained variation, producing two higher-crime clusters and two lower-crime clusters.
- **Murder**, **Assault**, and **Rape** rates drive cluster separation more strongly than **UrbanPop**, indicating that urbanization level does *not* consistently correlate with violent crime — contradicting a common assumption.
- Without scaling, the Assault variable dominates hierarchical clustering entirely, demonstrating why feature standardization is essential for balanced, reliable segmentation in any domain.
- Hierarchical clustering on scaled data produces dendrogram structure that confirms and enriches the K-means results, providing nested insight into how states relate at different levels of granularity.

---

## Business Value

The clustering techniques demonstrated here are the same methods organizations use across industries to drive data-informed decisions. Customer segmentation, where companies group users by behavior to tailor marketing and product strategy, relies on K-means and hierarchical clustering at scale. Risk-tier classification in insurance and finance uses similar approaches to stratify portfolios. This project reinforces the fundamentals that underpin those workflows: choosing and comparing clustering methods, evaluating cluster quality, and interpreting the resulting segments in a meaningful way.

---

## Tech Stack

| Category | Tool |
|----------|------|
| Language | `R` |
| Core Libraries | `tidyverse`, `cluster`, `factoextra` |
| Clustering Methods | `kmeans()`, `hclust()` (complete linkage) |
| Evaluation Metrics | WCSS / Elbow Plot, Gap Statistic |
| Reporting | Quarto (`.qmd`) rendered to HTML |

---

## Repository Structure

```
Clustering-Analysis-US-Arrests/
├── data/
│   └── USArrests.csv                             # Source dataset
├── clustering_case_study.qmd                     # Quarto analysis notebook
├── docs/
│   ├── clustering_case_study_files/              # Rendered figures and assets
│   └── index.html                                # Rendered HTML report (GitHub Pages)
└── README.md
```

---

## How to Reproduce

```bash
git clone https://github.com/Erin-Weiss/Clustering-Analysis-US-Arrests.git
cd Clustering-Analysis-US-Arrests
```

Open `clustering_case_study.qmd` in RStudio and render with Quarto. The notebook contains the full analysis pipeline including data inspection, scaling, K-means clustering across multiple values of *k*, hierarchical clustering with and without scaling, elbow plot and gap statistic evaluation, and cluster profiling. Requires R with the `tidyverse`, `cluster`, and `factoextra` packages installed.

---

## Future Work

- Apply cluster labels as features in supervised models (e.g., logistic regression, random forest) for crime-risk prediction or policy recommendation.
- Incorporate additional socioeconomic features (e.g., poverty rate, education level, unemployment) to enrich state profiles.
- Compare K-means and hierarchical results with density-based methods such as DBSCAN to evaluate robustness to outliers.
- Explore dimensionality reduction (PCA) as a preprocessing step before clustering for higher-dimensional extensions of this analysis.
