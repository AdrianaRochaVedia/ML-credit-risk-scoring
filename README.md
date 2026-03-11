# Credit Risk Scoring con Machine Learning

## 1. Objetivo del caso

El objetivo de este proyecto es desarrollar modelos de aprendizaje automático que permitan analizar el comportamiento financiero de los clientes de tarjetas de crédito y anticipar posibles situaciones de incumplimiento de pago (default).

A partir de información demográfica, financiera y del historial de pagos de los clientes, se busca identificar patrones que permitan mejorar la toma de decisiones en la gestión del riesgo crediticio.

En el proyecto se abordan dos tareas analíticas principales:

- **Regresión:** estimar el monto de pago futuro del cliente.
- **Clasificación:** predecir si un cliente entrará en default el siguiente mes.

---

## 2. Dataset

El dataset utilizado corresponde al **Default of Credit Card Clients Dataset**, que contiene información financiera y demográfica de clientes de tarjetas de crédito en Taiwán durante el año 2005.

El conjunto de datos incluye aproximadamente **30,000 registros** y variables relacionadas con:

- límite de crédito  
- características sociodemográficas  
- historial de pagos  
- montos facturados  
- montos pagados  

En este proyecto se consideran dos variables objetivo:

- **PAY_AMT:** utilizada para un problema de regresión orientado a estimar el monto de pago futuro del cliente.
- **default.payment.next.month:** utilizada para un problema de clasificación binaria que permite predecir si el cliente incurrirá en incumplimiento de pago el siguiente mes.

**Enlace de descarga del dataset**

https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients

---

## 3. Instrucciones para reproducir el proyecto

Para reproducir los resultados del proyecto se deben seguir los siguientes pasos.

### 1. Clonar el repositorio

```bash
git clone https://github.com/AdrianaRochaVedia/ML-credit-risk-scoring.git
cd ML-credit-risk-scoring
```

### 2. Instalar las dependencias

```bash
pip install -r requirements.txt
```

### 3. Ejecutar el notebook

Abrir el notebook del proyecto en **Jupyter Notebook** o **Google Colab** y ejecutar todas las celdas para reproducir el análisis y los modelos entrenados.

---

## 4. Metodología

El proyecto sigue un flujo típico de trabajo en Machine Learning orientado al análisis de riesgo crediticio:

1. **Entendimiento del problema de negocio**  
   Definición del objetivo del caso y análisis del contexto financiero relacionado con el riesgo de incumplimiento de pago.

2. **Análisis exploratorio de datos (EDA)**  
   Exploración de las variables del dataset para identificar patrones, relaciones entre variables y posibles problemas como desbalance de clases.

3. **Preprocesamiento de datos**

   - División del dataset en conjuntos de entrenamiento, validación y prueba utilizando *Stratified Shuffle Split*.  
   - Generación de nuevas variables mediante *feature engineering*.  
   - Escalado de variables numéricas utilizando **StandardScaler**.  
   - Implementación de pipelines reproducibles utilizando **ColumnTransformer** y **Pipeline**.

4. **Entrenamiento y comparación de modelos**

   Se evaluaron distintos algoritmos de Machine Learning para tareas de regresión y clasificación:

   - Regresión Logística  
   - Árboles de Decisión  
   - Support Vector Machines (SVC)  
   - Gradient Boosting (XGBoost y LightGBM)

5. **Optimización de hiperparámetros**

   Ajuste de hiperparámetros mediante **RandomizedSearchCV** con validación cruzada para mejorar el desempeño del modelo.

6. **Evaluación del modelo**

   Se utilizaron métricas como:

   - ROC-AUC  
   - Recall  
   - Precision  
   - F1-score  

   Además se realizó un **análisis de umbral (threshold)** para ajustar el comportamiento del modelo según criterios de negocio.

---

## 5. Resultados principales

Entre los modelos evaluados, **LightGBM optimizado** obtuvo el mejor desempeño general en términos de capacidad de discriminación entre clientes que entran en default y aquellos que no.

| Modelo | AUC | Recall | Precision | F1 |
|------|------|------|------|------|
| Baseline | 0.7215 | 0.2464 | 0.7109 | 0.3660 |
| Regresión Logística (L2) | 0.7231 | 0.6209 | 0.4039 | 0.4895 |
| Árbol de Decisión | 0.7440 | 0.5388 | 0.5049 | 0.5213 |
| SVC | 0.7620 | 0.5712 | 0.4974 | 0.5317 |
| LightGBM Tuned | **0.7822** | **0.6209** | 0.4782 | **0.5403** |

El modelo **LightGBM Tuned** alcanzó el mayor valor de **AUC**, lo que indica una mejor capacidad para distinguir entre clientes con riesgo de incumplimiento y aquellos que cumplen con sus pagos.

Además, se realizó un **análisis de umbral (threshold)** para ajustar el comportamiento del modelo según criterios de negocio, priorizando la detección de clientes con mayor riesgo de default y reduciendo el impacto de falsos negativos.

---

## 6. Consideraciones éticas

Los modelos de riesgo crediticio pueden tener implicaciones importantes en decisiones financieras que afectan a las personas. Por esta razón, es importante considerar aspectos éticos en su desarrollo y aplicación.

Entre los principales aspectos a considerar se encuentran:

- evitar sesgos en los datos que puedan generar discriminación hacia ciertos grupos
- garantizar transparencia en los modelos utilizados
- utilizar las predicciones como apoyo a la toma de decisiones y no como único criterio

El uso responsable de modelos de Machine Learning en el ámbito financiero debe buscar siempre un equilibrio entre eficiencia predictiva, equidad y transparencia.
