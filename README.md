# Natural Catastrophe Events Classification Pipeline

This repository contains an end-to-end pipeline for ingesting, cleaning, clustering, and classifying media headlines related to natural catastrophe events. The goal is to assign each headline into one of five hazard categories: Earthquake, Flood, Volcano, Tornado, and Wildfire.

---

## Pipeline Overview

- **Exploratory Data Analysis (01_EDA):** dataset inspection, missing values, date ranges, title statistics  
- **Data Cleaning (02_Cleaning):** regex filter → spaCy NER gate → MiniLM semantic filter, with logging of row counts  
- **Feature Engineering (03_Feature_Engineering):** build TF‑IDF and MiniLM embedding matrices, compare via silhouette  
- **Clustering & Model Selection (04_Clustering):** elbow analysis, hyperparameter sweeps (K‑Means, Agglomerative, Spectral, HDBSCAN), evaluate Silhouette & Davies–Bouldin, finalize Agglomerative(n=5, average)  

---

## Key Results

- **Cleaning:** 91479 raw → 2869 high‑precision event titles  
- **Feature Engineering:** MiniLM embeddings (384d) silhouette 0.145 vs TF‑IDF (1838d) silhouette 0.053  
- **Clustering:** AgglomerativeClustering(n_clusters=5, linkage='average') achieved silhouette 0.178, DB 2.189 with full coverage  
- **Final Labels:** `outputs/natcat_titles_labelled.csv` associating each title to one of the five hazards  
