# RETINEXPLAIN: Explainable Retinal Disease Detection

An explainable AI pipeline for multi-label retinal disease classification combining **EfficientNet-B0, Concept Bottleneck Learning, fuzzy logic, and Genetic Programming-based Fuzzy Pattern Trees**.

## Overview

RETINEXPLAIN is an MSc Artificial Intelligence & Machine Learning dissertation project developed to investigate an interpretable alternative to conventional black-box deep learning approaches for retinal disease classification.

The pipeline combines deep visual feature extraction with clinically meaningful concepts and symbolic fuzzy reasoning, enabling the final classification decisions to be represented through interpretable rules rather than relying solely on an opaque neural network.

## Methodology

RETINEXPLAIN consists of four main stages:

### 1. Deep Feature Extraction

A pretrained **EfficientNet-B0** is used as the visual feature extractor. The backbone is frozen while the subsequent components are trained for the retinal disease classification task.

### 2. Concept Bottleneck Layer

The extracted visual features are mapped to six clinically meaningful retinal concepts:

- Haemorrhage
- Drusen
- Disc Pallor
- Vessel Tortuosity
- Red Spot
- Exudate

### 3. Adaptive Fuzzification

The concept scores, together with patient demographic information, are transformed into fuzzy representations using adaptive triangular membership functions.

### 4. Fuzzy Pattern Tree Classification

A **Fuzzy Pattern Tree (FPT)** classifier is evolved using **Genetic Programming**. The resulting symbolic structures provide interpretable relationships between the clinical concepts and predicted disease categories.

## Dataset

The experiments were conducted using the **ODIR-5K (Ocular Disease Intelligent Recognition)** dataset.

- **5,684 retinal fundus images**
- Multi-label ocular disease classification
- Patient-level data split

The dataset is not included in this repository.

**Dataset:**  
https://www.kaggle.com/datasets/andrewmvd/ocular-disease-recognition-odir5k

## Results

| Model | Accuracy | Macro F1 |
|---|---:|---:|
| Interpretable Baseline | 46.16% | 0.4243 |
| **RETINEXPLAIN** | **56.28%** | **0.4243** |
| Black-box EfficientNet-B0 | **61.05%** | — |

RETINEXPLAIN improved raw accuracy from **46.16% to 56.28%** compared with the strongest simple interpretable baseline, while maintaining a comparable Macro F1 score.

The evolutionary experiments were evaluated across **30 independent runs**, with a paired statistical significance test resulting in **p < 0.0001**.

The black-box EfficientNet-B0 achieved higher accuracy (**61.05%**), but does not provide the same level of decision transparency as the proposed interpretable pipeline.

## Interpretability

A key objective of RETINEXPLAIN is to make the classification process more transparent.

Analysis of the evolved models showed that **4 of 7 diagnostic branches reduced to a single clinical concept**, producing compact decision structures based on clinically meaningful retinal features.

This demonstrates the potential of combining deep visual representations with fuzzy reasoning and evolutionary symbolic models to obtain interpretable predictions.

## Experiments

The repository contains notebooks covering:

- EfficientNet-B0 baseline
- Interpretable baseline models
- Soft-F1 fitness optimisation
- Soft-MCC fitness optimisation
- Weighted-RMSE fitness optimisation
- Statistical comparison across evolutionary runs

