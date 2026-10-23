---
layout: page
lang: en
permalink: /en/projects/8_project/
title: Superconductor critical temperature
description: Ensemble regression (Stacking, XGBoost, Random Forest) on 21,263 materials; R² = 0.93.
img: assets/img/proj_tc.jpg
stack: ["Scikit-learn", "XGBoost", "Stacking", "R² 0.93"]
importance: 3
category: artificial intelligence
github: https://github.com/ruribebejarano/Prediccion-de-la-temperatura-critica-en-superconductores-con-modelos-de-aprendizaje-automatico
---

[Code on GitHub](https://github.com/ruribebejarano/Prediccion-de-la-temperatura-critica-en-superconductores-con-modelos-de-aprendizaje-automatico)

Prediction of the **critical temperature (Tc)** of superconducting materials from 81 descriptors derived from their chemical composition (NIMS dataset, 21,263 samples).

### Pipeline

- Winsorization to handle extreme Tc values.
- Dimensionality reduction: variance threshold and collinearity analysis (Pearson > 0.7).
- Models: polynomial Ridge, SVR (RBF), XGBoost, Random Forest and a **Stacking Regressor** as meta-model.

### Results

| Model | R² | RMSE |
| :--- | :---: | :---: |
| Stacking Ensemble | **0.93** | **9.21 K** |
| Random Forest | 0.93 | 9.30 K |
| XGBoost | 0.93 | 9.31 K |
| Polynomial Ridge | 0.87 | 14.21 K |
| SVR | 0.84 | 13.79 K |

**Technologies:** Python · Scikit-learn · XGBoost · Pandas · NumPy · Google Colab
