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

La variable objetivo para el problema de clasificación es:

`default.payment.next.month`

que indica si el cliente incurre en incumplimiento de pago el siguiente mes.

Enlace de descarga del dataset:

https://archive.ics.uci.edu/ml/datasets/default+of+credit+card+clients

---

## 3. Instrucciones para reproducir el proyecto

Para reproducir los resultados del proyecto se deben seguir los siguientes pasos.

### 1. Clonar el repositorio

```bash
git clone https://github.com/AdrianaRochaVedia/ML-credit-risk-scoring.git
cd ML-credit-risk-scoring
