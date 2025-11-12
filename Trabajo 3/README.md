# Trabajo Practico 3: Aprendizaje No-Supervisado (PCA y K-Means)

## Objetivo del Trabajo

Disenar un experimento de Aprendizaje No-Supervisado para comparar la calidad de la agrupacion **K-Means** sobre un dataset en tres estados distintos:
1.  **Original Estandarizado.**
2.  **Reducido a 2 Componentes Principales (PCA).**
3.  **Reducido por Seleccion de Caracteristicas (Analisis de Correlacion).**

La evaluacion se realizo utilizando el **Metodo del Codo** y el **Silhouette Score** para determinar la coherencia del clustering.

---

## Dataset Utilizado

* **Nombre:** World Happiness Report 2023.
* **Caracteristicas:** 7 variables numericas clave relacionadas con la felicidad (Puntuacion, PBI, Soporte Social, etc.).
* **Preprocesamiento:** Se aplico **Estandarizacion (StandardScaler)** a todas las variables numericas.

---

## Hallazgos Principales y Conclusiones

La metrica **Silhouette Score** mostro que la reduccion de dimensionalidad optimizo la calidad de los clusteres al eliminar ruido. El valor de **K optimo** fue consistentemente **2** para los tres enfoques.

| Enfoque | Dimensionalidad | Mejor Silhouette Score |
| :--- | :--- | :--- |
| **PCA (2 Componentes)** | 2 | **0.4745** |
| Original Estandarizado | 7 | 0.3640 |
| Seleccion de Caracteristicas | 6 | 0.3459 |

### Conclusiones

1.  **PCA como Mejor Agrupador:** El enfoque de **PCA** obtuvo el mejor rendimiento (0.4745), demostrando ser altamente efectivo en la eliminacion de la redundancia y el ruido del dataset, facilitando una estructura de agrupacion mas clara para K-means, incluso con solo 2 dimensiones.
2.  **K Optimo:** La estructura del dataset sugiere la existencia de **dos grandes grupos principales** de paises.
3.  **Inefectividad de la Seleccion de Caracteristicas:** La reduccion manual de caracteristicas resulto en el rendimiento mas bajo, indicando que las variables eliminadas por alta correlacion contenian varianza crucial necesaria para separar los clusteres.
