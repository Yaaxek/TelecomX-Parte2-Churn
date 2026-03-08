# 📡 Telecom X – Parte 2 | Predicción de Churn

## 🎯 Propósito del Proyecto  

El objetivo principal de este proyecto es desarrollar modelos predictivos capaces de identificar qué clientes tienen mayor probabilidad de cancelar sus servicios (**churn**), utilizando variables relevantes del comportamiento del cliente.  

La empresa busca anticiparse a la cancelación para implementar estrategias de retención efectivas. Para ello, se construyó un pipeline robusto que incluye preparación de datos, análisis exploratorio (EDA), modelado predictivo y evaluación comparativa de modelos.

---

## 📂 Estructura del Proyecto  

El repositorio está organizado de la siguiente manera:

- **TelecomX_Parte2_Churn.ipynb**  
  Cuaderno principal con todo el análisis, desde la exploración hasta el modelado final.

- **datos_tratados.csv**  
  Dataset limpio y procesado utilizado para el modelado.

- **champion_model.pkl**  
  Modelo final serializado listo para realizar predicciones.

- **README.md**  
  Documentación del proyecto.

- **visualizaciones/** (opcional)  
  Carpeta con gráficos generados durante el análisis.

---

## ⚙️ Preparación de los Datos  

### 🔹 Clasificación de variables  

Las variables fueron clasificadas en dos tipos principales:

**Variables numéricas:**  
- tenure  
- Charges.Monthly  
- Charges.Total  
- Cuentas_Diarias  

**Variables categóricas:**  
tipo de contrato, servicios contratados, método de pago, tipo de internet, entre otras.

---

### 🔹 Transformaciones aplicadas  

Durante la preparación de los datos se realizaron las siguientes etapas:

- limpieza y verificación de valores faltantes  
- codificación de variables categóricas mediante **one-hot encoding**  
- estandarización de variables numéricas en modelos sensibles a escala  
- balanceo de clases mediante **SMOTE**

Estas transformaciones permitieron preparar los datos para el modelado predictivo.

---

### 🔹 División de datos  

El dataset fue dividido en:

- **80% para entrenamiento**  
- **20% para prueba**  

Se utilizó estratificación para mantener la proporción de churn en ambos conjuntos.

---

## 🤖 Modelado Predictivo  

Se entrenaron y compararon los siguientes modelos:

- Dummy Baseline  
- Regresión Logística  
- KNN  
- Random Forest  
- **Random Forest + SMOTE + GridSearch (modelo final)**

---

## 📌 Justificación del modelo final  

El modelo seleccionado fue:

👉 **Random Forest con SMOTE optimizado mediante GridSearch**

Porque:

- obtuvo el mejor recall (~0.746 en test)  
- mantuvo buen equilibrio entre precisión y recall  
- presentó estabilidad entre entrenamiento y prueba  
- mostró buen desempeño en métricas adicionales como ROC y AUC  

Esto lo convierte en el modelo más adecuado para predecir churn.

---

## 📊 Análisis Exploratorio de Datos (EDA)  

Durante el análisis exploratorio se identificaron patrones relevantes:

- los clientes con menor antigüedad presentan mayor churn  
- los contratos mensuales tienen mayor riesgo de cancelación  
- los cargos mensuales elevados se asocian con mayor churn  
- servicios como **TechSupport** y **OnlineSecurity** reducen la cancelación  

### 📈 Visualizaciones utilizadas  

- heatmaps de correlación  
- boxplots (tenure vs churn, gastos vs churn)  
- scatter plots  
- pairplots  

---

## 📌 Variables más relevantes  

Las variables más influyentes según el modelo final fueron:

- **tenure**  
- **Contract_Month-to-month**  
- **Contract_Two year**  
- **Charges.Monthly**  
- **Charges.Total**  
- **Cuentas_Diarias**  
- **TechSupport**  
- **OnlineSecurity**

Estas variables explican gran parte del comportamiento de cancelación.

---

## ▶️ Instrucciones para ejecutar el proyecto  

### 🔹 1. Instalar dependencias  

Para ejecutar el proyecto, es necesario contar con Python 3.9 o superior e instalar las siguientes bibliotecas:

- pandas  
- numpy  
- matplotlib  
- seaborn  
- scikit-learn  
- imbalanced-learn  

Estas librerías permiten realizar la limpieza y transformación de los datos, visualizaciones, construcción de modelos predictivos y balanceo de clases.

---

### 🔹 2. Ejecutar el notebook  

Para ejecutar el análisis:

1. abrir el archivo **TelecomX_Parte2_Churn.ipynb** en Google Colab o Jupyter Notebook  
2. asegurarse de que el archivo **datos_tratados.csv** esté en el mismo entorno  
3. ejecutar todas las celdas en orden  

El notebook contiene todo el flujo completo del proyecto, desde el análisis exploratorio hasta el modelo final.

---

## 📦 Uso del modelo final  

El modelo final se encuentra serializado en el archivo:

**champion_model.pkl**

Para utilizarlo:

- cargar el archivo en el entorno de trabajo  
- importar pickle  
- cargar el modelo  
- ejecutar predicciones con nuevos datos  

El modelo ya incluye el pipeline completo, por lo que no es necesario volver a escalar ni balancear manualmente los datos.

---

## 📌 Requisitos para nuevas predicciones  

Para obtener predicciones correctas:

- los nuevos datos deben tener las mismas variables que el dataset original  
- deben mantener el mismo formato de codificación  
- deben respetar el orden de columnas utilizado en el entrenamiento  

---

## 🧾 Conclusión  

El análisis permitió identificar que la cancelación de clientes está influida principalmente por:

- la antigüedad del cliente  
- el tipo de contrato  
- el nivel de gasto  
- los servicios contratados  

El modelo desarrollado permite anticipar la cancelación y apoyar estrategias de retención basadas en datos.

---

## 🚀 Misión del Proyecto  

La misión fue desarrollar un pipeline sólido para predecir churn y sentar las bases para estrategias de retención en Telecom X.  

Este proyecto integra análisis exploratorio, modelado predictivo y recomendaciones estratégicas en un flujo completo de ciencia de datos.
