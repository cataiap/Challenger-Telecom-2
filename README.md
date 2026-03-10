# Challenger Telecom 2 - Predicción de Cancelación de Clientes

## Descripción
Este proyecto corresponde a la continuación del Challenger Telecom X, enfocado en el análisis predictivo de cancelación de clientes (**Churn**).

A partir del dataset tratado en la Parte 1, se desarrolló un flujo completo de preparación de datos, análisis exploratorio orientado a modelado, selección de variables, entrenamiento de modelos predictivos y análisis de importancia de variables, con el objetivo de identificar los factores que más influyen en la cancelación de clientes y proponer estrategias de retención.

---

## Objetivo
Construir modelos de clasificación capaces de predecir la cancelación de clientes en Telecom X y, a partir de sus resultados, identificar patrones relevantes para apoyar decisiones estratégicas de retención.

---

## Contenido del repositorio
- `Challenger_2.ipynb` → Notebook principal con todo el desarrollo del análisis y modelado.
- `datos_tratados_telecomx.csv` → Dataset tratado y utilizado como base para esta segunda etapa del proyecto.

---

## Flujo de trabajo realizado

### 1. Carga del archivo tratado
Se utilizó el dataset limpio y preparado en la Parte 1 del desafío, asegurando consistencia en la información utilizada para el modelado.

### 2. Eliminación de columnas irrelevantes
Se excluyeron variables que no aportaban valor predictivo o generaban redundancia, como:
- `customerID`
- variables originales en texto que ya tenían versión binaria
- variable objetivo en texto (`Churn`) para dejar `Churn_bin` como target

### 3. Encoding
Se aplicó **one-hot encoding** a las variables categóricas restantes para dejar el dataset completamente en formato numérico y compatible con algoritmos de Machine Learning.

### 4. Verificación de la proporción de cancelación
Se analizó la distribución de la variable objetivo:
- **No canceló:** 73.46%
- **Sí canceló:** 26.54%

Esto mostró un **desbalance moderado** entre clases.

### 5. Normalización / estandarización
Se evaluó su necesidad y se decidió no aplicarla en esta etapa, ya que los modelos elegidos fueron basados en árboles, los cuales no dependen de la escala de las variables.

### 6. Correlación y selección de variables
Se construyó la matriz de correlación para identificar relaciones entre variables y su asociación con `Churn_bin`.

Entre las variables más relacionadas con la cancelación destacaron:
- `Contract_Month-to-month`
- `tenure`
- `InternetService_Fiber optic`
- `PaymentMethod_Electronic check`
- `Charges.Monthly`
- `Charges.Total`

### 7. Análisis dirigido
Se profundizó el análisis en variables clave como:
- **Tiempo de contrato (`tenure`) × Cancelación**
- **Gasto total (`Charges.Total`) × Cancelación**

Se utilizaron boxplots y scatter plots para visualizar patrones y tendencias.

### 8. Separación de datos
Se dividió el dataset en:
- **70% entrenamiento**
- **30% prueba**

Usando `stratify=y` para mantener la proporción de churn en ambos conjuntos.

### 9. Creación de modelos
Se construyeron dos modelos de clasificación:
- **Árbol de Decisión**
- **Random Forest**

### 10. Evaluación de modelos
Se evaluaron con las siguientes métricas:
- Accuracy
- Precision
- Recall
- F1-score
- Matriz de confusión

#### Resultados en prueba

**Árbol de Decisión**
- Accuracy: **0.7326**
- Precision: **0.4966**
- Recall: **0.5152**
- F1-score: **0.5057**

**Random Forest**
- Accuracy: **0.7814**
- Precision: **0.6083**
- Recall: **0.4955**
- F1-score: **0.5462**

El modelo con mejor desempeño general fue **Random Forest**.

### 11. Importancia de variables
A partir del Random Forest, se identificaron como variables más importantes:
- `Charges.Total`
- `tenure`
- `Cuentas_Diarias`
- `Charges.Monthly`
- `Contract_Month-to-month`
- `InternetService_Fiber optic`
- `PaymentMethod_Electronic check`
- `PaperlessBilling_bin`
- `Contract_Two year`
- `Partner_bin`

---

## Principales hallazgos
Los factores más asociados a la cancelación de clientes fueron:

- **Menor antigüedad del cliente**
- **Contratos mes a mes**
- **Servicio de fibra óptica**
- **Pago mediante electronic check**
- **Cobros mensuales más altos**
- **Menor gasto acumulado total, asociado a menor permanencia**

Por otro lado, variables asociadas a menor probabilidad de cancelación fueron:
- contratos de 1 o 2 años
- mayor `tenure`
- servicios como `OnlineSecurity` y `TechSupport`

---

## Conclusiones
El análisis permitió identificar que la cancelación en Telecom X no ocurre al azar, sino que se concentra en perfiles de clientes bien definidos. El modelo **Random Forest** logró el mejor desempeño global para la predicción de churn, aunque todavía mostró señales de sobreajuste, por lo que existe espacio para mejoras futuras mediante ajuste de hiperparámetros y técnicas complementarias.

Desde una perspectiva de negocio, los resultados sugieren enfocar estrategias de retención en:
- clientes nuevos o con baja permanencia
- contratos mensuales
- clientes con método de pago `Electronic check`
- segmentos con servicio de fibra óptica
- clientes con cargos mensuales elevados

---

## Tecnologías utilizadas
- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

---

## Cómo ejecutar el proyecto
1. Abrir el archivo `Challenger_2.ipynb` en Google Colab o Jupyter Notebook.
2. Verificar que el archivo `datos_tratados_telecomx.csv` esté disponible en el repositorio.
3. Ejecutar las celdas en orden.

---

## Autor
Proyecto desarrollado por **Catalina / Cataiap** como parte del Challenger Telecom X - Parte 2.
