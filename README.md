# Trabajo Práctico 2: Comparación de Modelos Supervisados (Clasificación)

## Objetivo del Trabajo

Diseñar y ejecutar un experimento de aprendizaje supervisado utilizando **Validación Cruzada (K=5)** para comparar el rendimiento y la estabilidad de tres modelos de clasificación clásicos. El objetivo fue seleccionar el modelo que mejor generaliza utilizando la métrica **ROC AUC**.

---

## Dataset Utilizado

* **Nombre:** Wine Quality Red (winequality-red.csv)
* **Origen:** UCI Machine Learning Repository
* **Variable Objetivo:** quality. Se transformó en un problema de **Clasificación Binaria**: 1 (Alta Calidad, mayor o igual a 7) y 0 (Baja Calidad, menor a 7).
* **Partición:** 70% Entrenamiento, 15% Validación, 15% Prueba (Estratificada).
* **Preprocesamiento:** Se aplicó **Estandarización (StandardScaler)** a todas las variables predictoras.

---

## Modelos Comparados y Resultados Clave

Se compararon tres modelos con hiperparámetros por defecto: Logistic Regression, K Neighbors Classifier y Decision Tree Classifier.

| Modelo | CV Mean AUC (Generalización Esperada) | CV Std AUC (Estabilidad) | Train AUC (Sobreajuste) |
| :--- | :--- | :--- | :--- |
| **LogisticRegression** | **0.8698** | 0.0320 | 0.8791 |
| KNeighborsClassifier | 0.8154 | 0.0267 | 0.9457 |
| DecisionTreeClassifier | 0.7084 | 0.0405 | 1.0000 |

## Principales Hallazgos y Conclusiones

### 1. Modelo Ganador y Generalización

* **Selección:** La **Regresión Logística** fue seleccionada como el mejor modelo. Ofreció el **rendimiento promedio más alto (0.8698)** combinado con una excelente estabilidad, demostrando ser el mejor generalizador entre los tres.
* **Descarte:** El Árbol de Decisión mostró un **sobreajuste severo** (Train AUC = 1.0000), resultando en la menor capacidad de generalización.

### 2. Evaluación Final vs. Expectativa

La Regresión Logística fue evaluada en el conjunto de Prueba final:

* **Rendimiento Esperado (CV Mean AUC):** 0.8698
* **Rendimiento Real (ROC AUC Prueba):** **0.8086**

**Conclusión:** El rendimiento final en la Prueba fue **inferior** a lo estimado por la Validación Cruzada (una caída de -0.0612). Esto implica que el conjunto de Prueba era más desafiante o menos representativo que el conjunto de entrenamiento. Sin embargo, el valor de **0.8086** sigue siendo un resultado sólido y confirma a la Regresión Logística como la mejor opción.