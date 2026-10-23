---
layout: page
title: Temperatura crítica de superconductores
description: Regresión con ensambles (Stacking, XGBoost, Random Forest) sobre 21 263 materiales; R² = 0.93.
img: assets/img/proj_tc.jpg
stack: ["Scikit-learn", "XGBoost", "Stacking", "R² 0.93"]
importance: 3
category: inteligencia artificial
github: https://github.com/ruribebejarano/Prediccion-de-la-temperatura-critica-en-superconductores-con-modelos-de-aprendizaje-automatico
---

[Código en GitHub](https://github.com/ruribebejarano/Prediccion-de-la-temperatura-critica-en-superconductores-con-modelos-de-aprendizaje-automatico)

Predicción de la **temperatura crítica (Tc)** de materiales superconductores a partir de 81 descriptores derivados de su composición química (dataset NIMS, 21 263 muestras).

### Pipeline

- Winsorización para manejar valores extremos de Tc.
- Reducción de dimensionalidad: _variance threshold_ y análisis de colinealidad (Pearson > 0.7).
- Modelos: Ridge polinomial, SVR (RBF), XGBoost, Random Forest y un **Stacking Regressor** como meta-modelo.

### Resultados

| Modelo | R² | RMSE |
| :--- | :---: | :---: |
| Stacking Ensemble | **0.93** | **9.21 K** |
| Random Forest | 0.93 | 9.30 K |
| XGBoost | 0.93 | 9.31 K |
| Polynomial Ridge | 0.87 | 14.21 K |
| SVR | 0.84 | 13.79 K |

**Tecnologías:** Python · Scikit-learn · XGBoost · Pandas · NumPy · Google Colab
