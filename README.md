# 🏛️ States & Crime Clustering Project

**Author:** Erin Weiss  
👉 [**US Arrests Clustering Project (Interactive HTML Report)**](https://erin-weiss.github.io/articles/clustering-project.html)

---

## 📘 Overview

This project applies **unsupervised learning techniques** to the classic **USArrests** dataset, uncovering hidden crime-rate patterns across all 50 U.S. states. The analysis uses both **K-means clustering** and **hierarchical clustering** to segment states by their levels of violent crime.

The goal is to identify meaningful groups of states based on:

- **Murder** arrests  
- **Assault** arrests  
- **Rape** arrests  
- **UrbanPop** (percent of residents living in urban areas)

---

## ⚙️ Approach

Using **R** and **Quarto**, I explored multiple clustering methods and evaluated the structure of the dataset to determine an appropriate number of clusters.

Key steps included:

- Loading, examining, and summarizing the **USArrests** dataset  
- Scaling variables to ensure equal influence in distance calculations  
- Running **K-means clustering** for *k = 2, 3, 4, 5*  
- Visualizing cluster assignments and centroids  
- Computing **WCSS (Within-Cluster Sum of Squares)** and generating an **Elbow Plot**  
- Evaluating cluster quality using the **Gap Statistic**  
- Performing **hierarchical clustering** (complete linkage) with and without scaling  
- Comparing cluster shapes, separation, and interpretability  

---

## 📊 Key Insights

- States cluster naturally into distinct **crime-rate profiles**, with clear separation between low-crime and high-crime groups.  
- **K = 4** provides the strongest balance of interpretability, stability, and explained variation.  
- Higher-crime states tend to group together across all methods, with **Murder**, **Assault**, and **Rape** rates driving cluster separation more strongly than **UrbanPop**.  
- **Urbanization level** does *not* consistently correlate with violent crime, contradicting common assumptions.  
- Without scaling, the **Assault** variable dominates hierarchical clustering; scaling is essential for balanced results.  
- K-means clusters remain relatively stable and interpretable across k = 3–5, but **k = 5 overfits**, creating redundant sub-clusters.

---

## 🧩 Selected Results

### K-Means Findings

- **K = 2**: Basic split into high-crime vs. low-crime states  
- **K = 3**: A middle-crime group emerges  
- **K = 4**: Best-defined structure — two higher-crime clusters and two lower-crime clusters  
- **K = 5**: Excessive fragmentation; clusters overlap heavily  

### Hierarchical Clustering

- **Unscaled data**: Assault dominates, creating skewed clusters  
- **Scaled data**: Produces clearer, more balanced groupings  
- Dendrograms show nested structure, confirming K-means patterns  

---

## 🧰 Tools Used

- **Language:** R  
- **Libraries:**  
  `tidyverse`, `cluster`, `factoextra` 

- **Techniques:**  
  - Scaling and standardization  
  - K-means clustering  
  - Hierarchical clustering (complete linkage)  
  - Elbow method  
  - Gap statistic  
  - Cluster profiling  

- **Reporting:** Quarto (`.qmd`) → HTML  

---

## 🔗 Links

- **Live Github Page:** [Github Page](https://erin-weiss.github.io/Clustering-Analysis-US-Arrests/) 
- **GitHub Repository:** [View Source Code](https://github.com/Erin-Weiss/Clustering-Analysis-US-Arrests)
- **Portfolio Page:** [View on Portfolio](https://erin-weiss.github.io/articles/clustering-project.html)
