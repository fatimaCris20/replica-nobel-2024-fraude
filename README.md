# Réplica: detección de fraude bancario con ML y XAI (Nobel et al., 2024)

Réplica del artículo:

> Nobel, S. M. N., Sultana, S., Singha, S. P., Chaki, S., Mahi, M. J. N., Jan, T., Barros, A., & Whaiduzzaman, M. (2024). *Unmasking Banking Fraud: Unleashing the Power of Machine Learning and Explainable AI (XAI) on Imbalanced Data*. **Information, 15**(6), 298. https://doi.org/10.3390/info15060298

Autora de la réplica: **Fátima Abregú**, Ingeniería de Sistemas, Universidad de Lima.

## Objetivo

Reproducir el flujo del artículo y comparar mis resultados con los de los autores:

1. **Datos:** PaySim, un dataset sintético de dinero móvil (unos 6,3 millones de transacciones, de las cuales alrededor del 0,13 % son fraude).
2. **Preparación:** LabelEncoder, MinMaxScaler, división 80/20 y SMOTE.
3. **Modelado:** regresión logística, XGBoost, árbol de decisión y SVM lineal.
4. **Evaluación y XAI:** accuracy, precisión, recall, F1 y AUC, más explicaciones con SHAP y LIME.

## Cómo ejecutarlo

1. Abre `replica_nobel_2024.ipynb` en [Google Colab](https://colab.research.google.com) (Archivo → Subir notebook).
2. Ve a **Entorno de ejecución → Ejecutar todo**. El dataset se descarga solo desde Kaggle con `kagglehub`.
3. Tarda entre 10 y 15 minutos con una muestra del 10 %.

## Decisiones de la réplica

| Decisión | Motivo |
|---|---|
| Muestra estratificada del 10 % | Para que corra en Colab gratuito. Mantiene el mismo porcentaje de fraude. |
| SMOTE aplicado solo al conjunto de entrenamiento | Evita la fuga de datos. El artículo no aclara este punto. |
| `LinearSVC` en vez de `SVC(kernel="linear")` | Es la misma SVM lineal, pero viable con más de un millón de filas. |
| Extensión: XGBoost con `learning_rate = 0.1` | Es un aporte propio para comparar con el valor del artículo (0.001). |

## Resultados

Los valores del artículo son con SMOTE y para la clase fraude.

| Modelo | F1 artículo | F1 réplica | AUC artículo | AUC réplica |
|---|---|---|---|---|
| Regresión logística | 0,89 | [__] | 0,94 | [__] |
| XGBoost | 0,92 | [__] | 1,00 | [__] |
| Árbol de decisión | 0,86 | [__] | 0,84 | [__] |
| SVM lineal | 0,48 | [__] | — | [__] |

**Conclusión:** [completar después de ejecutar]

## Requisitos

Python 3.10 o superior: `pandas`, `scikit-learn`, `xgboost`, `imbalanced-learn`, `shap`, `lime`, `matplotlib`, `seaborn` y `kagglehub`. Colab ya trae la mayoría, y el notebook instala las que faltan.
