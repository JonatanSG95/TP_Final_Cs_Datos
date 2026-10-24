# Análisis y Predicción del Porcentaje de Grasa Corporal

## Descripción del proyecto

Proyecto de análisis de datos y Machine Learning orientado a la estimación del porcentaje de grasa corporal (*Body Fat*) a partir de mediciones antropométricas.

El trabajo explora los datos, identifica valores atípicos, analiza las relaciones entre variables y compara distintos modelos de regresión para evaluar su capacidad predictiva. Finalmente, se desarrolla una red neuronal utilizando TensorFlow/Keras.

## Objetivos

- Realizar un análisis exploratorio de los datos (EDA).
- Identificar valores atípicos y posibles errores de medición.
- Analizar la correlación entre las variables antropométricas.
- Establecer un modelo de referencia (*baseline*) mediante una fórmula basada en el IMC.
- Entrenar y comparar distintos algoritmos de Machine Learning.
- Evaluar los modelos mediante métricas de error y capacidad predictiva.

## Tecnologías utilizadas

- **Python** — Lenguaje de programación.
- **Pandas y NumPy** — Manipulación y procesamiento de datos.
- **Matplotlib y Seaborn** — Visualización y análisis exploratorio.
- **Scikit-learn** — Preprocesamiento, validación cruzada, entrenamiento y evaluación de modelos.
- **TensorFlow / Keras** — Construcción y entrenamiento de una red neuronal.
- **Jupyter Notebook** — Entorno de desarrollo y documentación del análisis.

## Dataset

El conjunto de datos contiene mediciones antropométricas de 252 registros, incluyendo variables como:

- Edad (*Age*).
- Peso (*Weight*).
- Altura (*Height*).
- Circunferencias corporales (*Neck*, *Chest*, *Abdomen*, *Hip*, entre otras).
- Porcentaje de grasa corporal (*BodyFat*).

La variable objetivo es `BodyFat`, mientras que las demás mediciones se utilizan como variables predictoras.

Durante el preprocesamiento se excluye `Density` para evitar la fuga de información (*data leakage*) y se filtran registros con valores de altura o porcentaje de grasa corporal considerados inválidos para el análisis.

## Metodología

### 1. Análisis exploratorio de datos

- Inspección de la estructura y los tipos de datos.
- Verificación de valores nulos.
- Detección de valores atípicos mediante diagramas de caja.
- Análisis de correlaciones entre variables.

### 2. Modelo de referencia

Se utiliza una estimación basada en el índice de masa corporal (IMC) y la edad para establecer una referencia con la que comparar los modelos de Machine Learning.

### 3. Comparación de modelos

Se evalúan diferentes algoritmos de regresión mediante validación cruzada de cinco particiones (*5-fold cross-validation*):

- Regresión Lineal Múltiple.
- Ridge Regression.
- Lasso Regression.
- Elastic Net.
- Random Forest Regressor.
- Gradient Boosting Regressor.
- Support Vector Regression (SVR).

La comparación permite analizar el desempeño de cada algoritmo y seleccionar alternativas según sus resultados.

### 4. Selección de variables

Se utiliza Lasso Regression con escalado de características para estudiar la relevancia de las variables predictoras y detectar aquellas cuyos coeficientes se reducen a cero.

### 5. Red neuronal

Se desarrolla una red neuronal densa para abordar el problema como una tarea de regresión.

La arquitectura incorpora capas densas con activación ReLU, una capa Dropout para regularización y una capa de salida lineal. El entrenamiento utiliza el optimizador Adam y Early Stopping para limitar el sobreajuste.

Los datos se dividen en conjuntos de entrenamiento y prueba, y las variables predictoras se estandarizan antes del entrenamiento.

## Métricas de evaluación

Se utilizan las siguientes métricas para comparar el desempeño de los modelos:

- **MAE (Mean Absolute Error):** mide el error absoluto medio de las predicciones.
- **RMSE (Root Mean Squared Error):** penaliza en mayor medida los errores grandes.
- **R² (Coeficiente de determinación):** permite evaluar qué proporción de la variabilidad de la variable objetivo explica el modelo.

## Cómo ejecutar el proyecto

1. Clonar el repositorio:

   ```bash
   git clone https://github.com/JonatanSG95/TP_Final_Cs_Datos.git
   cd TP_Final_Cs_Datos
   ```

2. Instalar las dependencias:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn tensorflow jupyter
   ```

3. Colocar el archivo `bodyfat.xls` en el directorio desde el que se ejecutará el notebook.

4. Abrir Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

5. Abrir `Proyecto Final.ipynb` y ejecutar las celdas en orden.

**Nota:** el notebook carga `bodyfat.xls` mediante `pandas.read_csv`, por lo que el archivo debe tener contenido delimitado por comas, aunque su extensión sea `.xls`.

## Autoría

Proyecto desarrollado como trabajo final integrador, con fines académicos y de aprendizaje en análisis de datos y Machine Learning.
